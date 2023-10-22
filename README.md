<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>temprature converter</title>
    <style>
        *{
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        }

        body{
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        color: #f05e09;
        background-image: url(temp11.jpg);
        background-repeat: no-repeat;
        background-size: cover;
        }

    .container{
        max-width: 450px;
        border: 1px solid black;
        border-radius: 18px;
        box-shadow: 100px 100px 300px  rgba(255, 255, 255, 0.4);
        font-family: sans-serif;
        padding: 20px;
        background-color: transparent;
    }

    .title{
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
        gap: 10px;
    }
    #h1{
            letter-spacing: 8px;
            color: rgb(255, 132, 0);
            
            font-size: 4rem;

        }
        @keyframes flip {
            0%{
                opacity: 0;
               
                transform-origin: bottom;
                transform: rotateX(-100deg);
                
            }
            100%{
                opacity: 1;
                color: rgb(255, 132, 0);
                transform: rotateX(0deg);
                
                /* text-decoration: underline; */
            }
        }
        span{
            /* without displaying not working, remember the property of tags & change it .  */
                display: inline-block;
                font-size: 3rem;
 
            }
            @keyframes flipspan {
            0%{
                opacity: 0;
                
                transform: rotateY(-100deg);
                
            }
           100%{
                opacity: 1;
                color: rgb(255, 132, 0);
               transform: rotateY(0deg);
               text-shadow: 5px 5px 3px black;
               /* text-decoration: underline; */
            }
        }
        #span3{
            display: inline-block;
            
            
        }
        @keyframes flipspan3 {
            0%{
                opacity: 0;
                
                transform: rotateY(-100deg);

            }
           100%{
                opacity: 1;
                color: rgb(255, 132, 0);
               transform: rotateY(360deg);
               transform-origin: left;
               text-shadow: 5px 5px 3px black;
                /* text-decoration: underline; */
           }
        }
        #span2{
            display: inline-block;
            
            /* transition: all ease 10s; */
        }
        @keyframes flipspan2 {
            0%{
                opacity: 0;
                
                transform: rotateX(-10deg);

            }
           100%{
                opacity: 1;
                color: rgb(255, 132, 0);
               transform: rotateX(360deg);
               transform-origin: bottom;
               text-shadow: 5px 5px 3px black;
                /* text-decoration: underline; */
           }
        }

    #celsius, #fahrenheit, #kelvin{
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top: 25px;
    }

    input{
        flex: 5;
        height: 60px;
        font-size: 20px;
        font-weight: 600;
        text-align: center;
        border-radius: 8px 0 0 8px;
        padding: 0 10px;
        color: #f35d0d;
    }

        .icon{
            flex: 1;
            height: 60px;
            line-height: 60px;
            padding: 0 5px;
            text-align: center;
            font-size: 30px;
            color: #f05e09;
            border-radius: 0 8px 8px 0;
        }


        .button{
            margin-top: 25px;
            text-align: center;
            /* color: greenyellow; */
        }


        .button button{
            height: 40px;
            width: 150px;
             border: none;
             outline: none;
            font-size: 25px;
            font-weight: 600;
            border-radius: 3px;
            transition: 0.3s;
        }

        .button button:hover{
            background: #08c70e;
            color: #fff;
        }


    </style>
</head>
<body>
    <div class="container">

        <div class="title">
            
            <h1 id="h1">Temprature</h1>


            <h1>   <span id="span2">C</span>
                   <span>o</span>
                   <span id="span3">n</span>
                   <span>v</span> 
                   <span>e</span> 
                   <span id="span3">r</span> 
                   <span>t</span> 
                   <span id="span2">e</span> 
                   <span id="span3">r</span>
            <span class="Temperature-icon"><i class="fa-solid fa-temperature-three-quarters"></i></span>
        </div>

        <div id="celsius">
            <input type="number" name="" placeholder=" in Celsius">
            <span class="icon">&#8451</span>
        </div>
        <div id="fahrenheit">
            <input type="number" name="" placeholder=" in Fahrenheit">
            <span class="icon">&#8457</span>
        </div>
        <div id="kelvin">
            <input type="number" name="" placeholder="in Kelvin">
            <span class="icon">&#8490</span>
        </div>

        <div class="button">
            <button>All Clear</button>
        </div>

    </div>

    <script>
        let celsiusInput = document.querySelector('#celsius > input')
        let fahrenheitInput = document.querySelector('#fahrenheit > input')
        let kelvinInput = document.querySelector('#kelvin > input')

        let btn = document.querySelector('.button button')


        function roundNumber(number){
        return Math.round(number*100)/100
            }


        /* Celcius to Fahrenheit and Kelvin */
         celsiusInput.addEventListener('input', function(){
         let cTemp = parseFloat(celsiusInput.value)
         let fTemp = (cTemp*(9/5)) + 32
         let kTemp = cTemp + 273.15

           fahrenheitInput.value = roundNumber(fTemp)
           kelvinInput.value = roundNumber(kTemp)
        })


         /* Fahrenheit to Celcius and Kelvin */
         fahrenheitInput.addEventListener('input', function(){
         let fTemp = parseFloat(fahrenheitInput.value)
         let cTemp = (fTemp - 32) * (5/9)
        let kTemp = (fTemp -32) * (5/9) + 273.15

         celsiusInput.value = roundNumber(cTemp)
         kelvinInput.value = roundNumber(kTemp)
        })

        /* Kelvin to Celcius and Fahrenheit */
        kelvinInput.addEventListener('input', function(){
         let kTemp = parseFloat(kelvinInput.value)
         let cTemp = kTemp - 273.15
         let fTemp = (kTemp - 273.15) * (9/5) + 32

         celsiusInput.value = roundNumber(cTemp)
         fahrenheitInput.value = roundNumber(fTemp)
        })


        btn.addEventListener('click', ()=>{
          celsiusInput.value = ""
         fahrenheitInput.value = ""
         kelvinInput.value = ""
        })
    </script>
</body>
</html>
