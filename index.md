<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NAUCI KORISTECI</title>
    <link rel="icon" href="favicon.ico" sizes="16x16" type="image/png">
    <style>
        .neznam {
            background-color: #ff6d6d;
        }

        .onako {
            background-color: #e6e625;
        }

        .znam {
            background-color: #85ff85;
        }
        #submit{
            padding: 40px 120px;
            border-radius: 0px;
            background: white;
            border: 3px solid lightgray;
        }
        #submit:hover{
            background: lightgray;
        }p{
            font-size: 30px;
            font-weight: bold;
        }
        textarea{
            height: 20px;
        }
        #divhere{
            height:280px;
            max-height:280px;
            overflow: scroll;
        }
        #myBar {
            width: 1%;
            height: 30px;
            background-color: rgb(167, 167, 167);
            text-align: center; /* To center it horizontally (if you want) */
            line-height: 30px; /* To center it vertically */
            color: white;
        }
        .breaktime{
            color: red;
            background-image: url(slika.jpg);
            background-size: cover;
            background-position: center;
            font-size: 310px;
            z-index: 100;
            position: fixed;
            left: 0px;
            top: -722px;
            padding: 22% 0px;
            width: 100%;
        }
        #body{
            background-image: url(download.gif);
    background-size: cover;
    padding: 20px;
    background-color: #ffffff7a !important;
        }
        body{
            margin: 0px;
        }
        
        
    </style>
</head>
<body title="Ne razmisljaj mnogo">
<div id="body" >

   
    <p>UBACI TEKST I KLIKNI DUGME, NAUCI KORISTECI!</p>
    <textarea type="text" id="here" value="" >

    </textarea>
    <button id="submit" onclick="getDancers()">SAMO PRELAZI BRZO, ne kreativno, nego pravo</button>
    <button id="" onclick="RemoveLastRow()">RemoveLastRow</button>
    <button id="neznam" class="neznam" onclick="neZnam()">0</button>
    <button id="onako" class="onako" onclick="Onako()">0</button>
    <button id="znam" class="znam" onclick="Znam()">0</button>
    <div id="divhere">
        <br><br><br><br><br><br><br>
    </div>
    <button id="submit" onclick="location.reload();">AKO SI ZAVRSIO IDEMO DALJE</button>
    <div id="myProgress">
        <div id="myBar">0%</div>
    </div>
    <div>
        <h6 id="seconds-counter" title="Mozak moze samo 25 minuta da se fokusira na jednu stvar"> 25:00
            </canvas>
        </h6>
        <script>
            var r=10;
            var cancel;
            function pad(d) {
                return (d < 10) ? '0' + d.toString() : d.toString();
            }
            function WorkTime(){
                var timeis = 1500.0;
                var el = document.getElementById('seconds-counter');
                function incrementSeconds() {
                    if(timeis==0){
                        myStopFunction();
                        BreakTime();
                    }
                    timeis-=1;
                    el.innerText = "" + pad(Math.floor(timeis/60)) + ":" + pad( Math.round((timeis/60-Math.floor(timeis/60))*60)) + "";
                }
                cancel = setInterval(incrementSeconds, 1000);
                el.classList.remove("breaktime");
            
            }
            WorkTime();
            function myStopFunction() {
                clearInterval(cancel);
            }
            function BreakTime(){
                var timeis = 300.0 - 1;
                notifyMe();

                var el = document.getElementById('seconds-counter');
                el.classList.add("breaktime");
                

                function incrementSeconds() {
                    if(timeis==0){
                        myStopFunction();
                        WorkTime();
                    }
                    timeis-=1;
                    el.innerText = "" + pad(Math.floor(timeis/60)) + ":" + pad( Math.round((timeis/60-Math.floor(timeis/60))*60)) + "";
                }
                cancel = setInterval(incrementSeconds, 1000);
            }

           
            
        </script>
    </div>
</div> 
    <script>
        var elem = document.getElementById("body");

        function openFullscreen() {
            if (elem.requestFullscreen) {
                elem.requestFullscreen();
            } else if (elem.mozRequestFullScreen) { /* Firefox */
                elem.mozRequestFullScreen();
            } else if (elem.webkitRequestFullscreen) { /* Chrome, Safari and Opera */
                elem.webkitRequestFullscreen();
            } else if (elem.msRequestFullscreen) { /* IE/Edge */
                elem.msRequestFullscreen();
            }

        }
        window.onload = function(){ openFullscreen();};
        var array;
        var i=0;
        var jedan, dva, tri;
        jedan = 0; dva = 0; tri = 0;
        var k=0;
        var submit = document.getElementById("submit");
        var neznam = document.getElementById("neznam");
        var onako = document.getElementById("onako");
        var znam = document.getElementById("znam");
        function getDancers() {
            openFullscreen();
            notifyMe();
            var textarea = document.getElementById("here");
            var divhere = document.getElementById("divhere");
            array = textarea.value.split("\n");
            console.log("getDancers -> textarea.value.split(n)", textarea.value.split("\n"))
            var novired = document.createElement("p");
            novired.textContent = array[i];
            divhere.appendChild(novired);
           // submit.remove();
        }
        function getNewRow() {
            k++;
            if (k%2==0){
                i++;
                RemoveLastRow();
                i++;  
                var novired = document.createElement("p");
                novired.textContent = array[i];
                divhere.appendChild(novired);
                novired.scrollIntoView();
            } 
            else{
                var novired = document.createElement("p");
                novired.textContent = "{???}";
                divhere.appendChild(novired);
                novired.scrollIntoView();
            }
        }
        function RemoveLastRow() {
            i--;
            divhere.children[divhere.children.length - 1].remove();
        }
        window.onkeydown = CheckKey;

        function CheckKey(e) {
            
             if (e.keyCode == '49' || e.keyCode == '97') {//jedan
                neZnam();
            } else if (e.keyCode == '50' || e.keyCode == '98') {//dva
                Onako();
            } else if (e.keyCode == '51' || e.keyCode == '99') {//tri
                Znam();
            }else if (e.keyCode == '109') {//minus
                RemoveLastRow()
            }
            console.log(i)
        }

        function neZnam(e) {
           
            if (k%2==0){ jedan++;}
            neznam.textContent=jedan;
            ColorRed();
            getNewRow();
            Progress();
        }
        function Onako(e) { 
            
            if (k%2==0){dva++;}
            onako.textContent=dva;
            ColorYelow();
            getNewRow();
            Progress();
        }
        function Znam(e) { 
           
            if (k%2==0){  tri++;}
            znam.textContent=tri;
            ColorGreen();
            getNewRow();
            Progress();
        }
        function ColorRed(){
            divhere.children[divhere.children.length - 1].style.color = "#ff6d6d";
            divhere.children[divhere.children.length - 1].style.fontSize = "14px";
        }
        function ColorYelow(){
            divhere.children[divhere.children.length - 1].style.fontSize = "14px";
            divhere.children[divhere.children.length - 1].style.color = "#e6e625";
        }
        function ColorGreen(){
            divhere.children[divhere.children.length - 1].style.fontSize = "14px";
            divhere.children[divhere.children.length - 1].style.color = "#85ff85";
        }
        
        function Progress(){
            var ii = 0;
            var elem = document.getElementById("myBar");
            var width= (100/array.length)*i;
            elem.style.width = width + "%";
            if(width>99.99){
                elem.innerHTML = "BRAVO! idemo dalje";
            }
            else{
            elem.innerHTML = "You can do it!";
            elem.style.background= "#85ff85";
            }
        }

        function notifyMe() {
            
    if (!window.Notification) {
        console.log('Browser does not support notifications.');
    } else {
        // check if permission is already granted
        if (Notification.permission === 'granted') {
            // show notification here
            console.log("granted");
            var notify = new Notification('Hi there!', {
                body: 'Isteklo ti vreme, sad daj mozgu da se relaksira 5 minutaa?',
                icon: 'https://bit.ly/2DYqRrh',
            });
        } else {
            
            console.log("not granted");
            // request permission from user
            Notification.requestPermission().then(function (p) {
                if (p === 'granted') {
                    // show notification here
                    var notify = new Notification('Hi there!', {
                        body: 'Isteklo ti vreme, sad daj mozgu da se relaksira 5 minutaa',
                        icon: 'https://bit.ly/2DYqRrh',
                    });
                } else {
                    console.log('User blocked notifications.');
                }
            }).catch(function (err) {
                console.error(err);
            });
        }
    }

    var audio = new Audio('alarm.mp3');
    audio.play();
}
        

    </script>
</body>

</html>