# numbersFact
This is a web application that gets random number facts doing a response from AJAX and using the numbers api.  It gives random facts when entering a number.
<!DOCTYPE>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta.3/css/bootstrap.min.css" integrity="sha384-Zug+QiDoJOrZ5t4lssLdxGhVrurbmBWopoEl+M6BdEfwnCJZtKxi1KgxUyJq13dy" crossorigin="anonymous">
    <style>
        #fact{
            display:none;
        }
    
    
    </style>
    
    <title>Number Facts</title>    
    </head>
<body class="bg-dark">
    <div class="container">
    <div class="row">
        <div class="col-md-6 mx-auto">
        <div class="card bg-primary text-white mt-5 p-4">
            <h1>Number Facts</h1> 
            <p>Enter a number and get a random fact</p>
            <input type="number" class="form-control form-control-lg" id="numberInput" placeholder="Enter any number...">
            <div id="fact" class="card-body">
            <h4 class="card-title">Number fact</h4>
                <p id="factText" class="card-text"></p>
                
            </div>
            </div>
        </div>
        </div>
    </div>
    
    <script>
    //Create variables    
    let fact = document.querySelector('#fact');
    let factText = document.querySelector('#factText');
    let number = document.querySelector('#numberInput');
        
    //Add event listner to number input
    numberInput.addEventListener('input', getFactAjax);
        
    //Function to get fact Ajax
    function getFactAjax(){
        let number = numberInput.value;
        
        let xhr = new XMLHttpRequest();
        xhr.open('GET','http://numbersapi.com/'+number);
        
        xhr.onload = function(){
            if(this.status===200 && number!=''){
               fact.style.display = 'block';
            factText.innerText = this.responseText;    
               }
        }
        
        xhr.send();
    }    
        
    
    </script>
    </body>



</html>
