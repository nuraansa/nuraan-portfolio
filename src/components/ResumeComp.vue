<template>
    <div id="resume"></div>
    <div class="bg">
        <h1 class="display-1 text-center p-4" data-aos="zoom-in">Resume</h1>
        <div class="container p-1 text-start w-50">
            <hr>
            <div class="row border-bottom" style="margin: 20px; margin-top: 10px; font-size: 20px">
                <div class="col border-end">DOB: 14 February 2000</div>
                <div class="col">Age: 23</div>
            </div>
            <div class="row border-bottom" style="margin: 20px; font-size: 20px">
                <div class="col border-end">City: Cape Town</div>
                <div class="col">Email: nuraansa1@gmail.com</div>
            </div>
            <div class="row border-bottom" style="margin: 20px; font-size: 20px">
                <div class="col border-end">Language: English</div>
                <div class="col">Cell: 012-345-6789</div>
            </div>
            <div class="row border-bottom" style="margin: 25px; font-size: 25px">
                <div class="col border-end text-center"><a href="https://www.linkedin.com/in/nuraan-samodien-154315282/"
                        target="_blank">View LinkedIn</a>
                </div>
                <div class="col text-center"><a
                        href="https://drive.google.com/file/d/1OFU4pQxRyhzB8y9E6ed9a9kDURg17vpH/view?usp=share_link"
                        target="_blank">Download CV</a></div>
            </div>
        </div>

        <div class="container" id="res1">
            <h1 class="display-3 p-5" data-aos="zoom-in">Education</h1>
            <div class="card p-4 edu text-start shadow-lg mx-auto" data-aos="fade-up">
                <div class="row g-0">
                    <div class="col-md-8" v-for="item in education" :key="item.id">
                        <div class="card-body ex">
                            <h5 class="card-title">{{ item.year }}</h5>
                            <p class="card-text">{{ item.description }}</p>
                            <hr>
                        </div>
                    </div>
                    <div class="col-md-4" id="imagee">
                        <img src="https://i.postimg.cc/MGsGH8GH/asal-lotfi-8e-PZbdxnpi0-unsplash.jpg" alt="img"
                            class="w-100 book">
                        <!-- <img src="https://i.postimg.cc/bJwBtJb3/reading.jpg" class="img-fluid" alt="..."> -->
                    </div>
                </div>
            </div>
        </div>
        <div class="container">
            <h1 class="display-3 p-5" data-aos="zoom-in">Experience</h1>
            <div class="row">
                <div class="col" v-for="item in experience" :key="item.id">
                    <div class="card p-5 text-start edu mx-auto shadow-lg" data-aos="fade-up" style="max-width: 30rem;">
                        <div class="card-body">
                            <h5 class="card-title">{{ item.year }}</h5>
                            <p class="card-text">{{ item.description }}</p>
                        </div>
                        <div class="card-footer bg-transparent">{{ item.place }}</div>
                    </div>
                </div>
            </div>
        </div>
        <h1 class="display-3 p-5" data-aos="zoom-in">Soft Skills</h1>
        <div class="container-fluid" id="soft" data-aos="fade-up">
            <div class="card in shadow-lg w-50">
                <div class="row" id="row">
                    <div class="col text-center p-0">
                        <ul class="list-group list-group-flush rounded">
                            <li class="list-group-item border-end ss p-3">Problem solving
                            </li>
                            <li class="list-group-item border-end ss p-3">Communication
                            </li>
                            <li class="list-group-item border-end ss p-3">Addaptability</li>
                        </ul>
                    </div>
                    <div class="col text-center p-0">
                        <ul class="list-group list-group-flush rounded">
                            <li class="list-group-item ss p-3">Critical thinking</li>
                            <li class="list-group-item ss p-3">Time management</li>
                            <li class="list-group-item ss p-3">Teamwork</li>
                        </ul>
                    </div>
                </div>
            </div>
            <div class="container-fluid">
                <h1 class="display-3 p-5" data-aos="zoom-in">Technical Skills</h1>
                <div class="row row-cols-1 row-cols-sm-2 row-cols-lg-3 row-cols-md-3 d-flex mx-auto g-2" id="col">
                    <div class="col" id="pad" v-for="item in skills" :key="item.id">
                        <div class="card skill shadow-lg mx-auto" data-aos="fade-up">
                            <div class="card-body p-4
                            ">
                                <i :class="item.icon" :key="item.id" style="color: #5E8B7E;"></i>
                                <h4 class="card-text">{{ item.skill }}</h4>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <router-link to="/projects" id="res" class="btn btn-light m-3 p-3 ">View Projects</router-link>
        </div>
    </div>
</template>

<script>
export default {
    computed: {
        education() {
            return this.$store.state.education
        },
        experience() {
            return this.$store.state.experience
        },
        skills() {
            return this.$store.state.skills
        }
    },
    mounted() {
        this.$store.dispatch('fetchEducation'),
            this.$store.dispatch('fetchExperience'),
            this.$store.dispatch('fetchSkills')

    }
}
</script>

<style scoped>
.colu {
    display: flex;
    justify-content: center;
    align-items: center;
}

.bg {
    background: #A7C4BC;
}

h1 {
    text-shadow: 2px 2px #DFEEEA;
}

h4 {
    text-shadow: 2px 2px #DFEEEA;
}

.ss {
    background-color: #DFEEEA;
}

a {
    color: #2F5D62;
    text-decoration: none;
}

a:hover {
    color: #5E8B7E;
}

.info {
    width: 45rem;
}

.ex {
    padding: 1px;
}

@media(width < 980px) {
    #res1 {
        padding: 0;
    }
}

@media (width <768px) {
    .book {
        height: 40rem !important;
        width: 100% !important;
        margin-top: 0 !important;
        object-fit: fill;
        display: none;
    }

    #imagee {
        display: none;
    }

    #res1 {
        width: 100% !important;
    }

    .card-text {
        display: flex;
        flex-wrap: wrap;
        width: 80%;
    }

    .card-body {
        padding: 10px;
    }

    .edu {
        padding: 0 !important;
    }
}

#col {
    margin: 0 !important;
}

@media (width < 711px) {
    .card-text {
        width: 70%;
    }
}

@media(width<622px) {
    .card-text {
        width: 60%;
    }
}

#border {
    border-right: 1px solid black;
}




@media (width < 580px) {
    .card-text {
        width: 50%;
    }
}

@media (width < 469px) {
    .card-text {
        width: 40%;
    }
}

@media (width<392px) {
    .card-text {
        width: 30%;
        margin-right: 0 !important;
    }
}

@media (width<293) {
    .card-text {
        width: 19%;
    }
}

@media (width<690px) {
    li {
        width: 100% !important;
    }
}

.edu {
    background-color: #DFEEEA;
    width: 60rem;
}

#pad {
    padding: 1rem !important;
}

#soft {
    padding: 0;
}

.card-body {
    padding: 0;
    width: 100% !important;
    height: 100% !important;
}

.book {
    margin-top: -24rem;
}

.list-group-item {
    width: 100%;
}

.skill {
    background-color: #b3d3ca;
    margin-bottom: 2rem;
}

#res {
    text-decoration: none;
    color: #DFEEEA;
    background: #5E8B7E;
}

.text-start {
    width: 100%;
}

#soft {
    margin: 0 !important;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.p-5 {
    width: 100% !important;
}

@media (width < 690px) {
    #row {
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
}

.in {
    width: 100%;
}

#res:hover {
    background: #DFEEEA;
    color: #5E8B7E;
    border: 2px solid #5E8B7E;
    text-decoration: none;
}
</style>