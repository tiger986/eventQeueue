## Customized Simple Event Queue
#### JS code
```javascript
var taskArr = [];
var timer = null;
var done = null;
var flag = 1;
$(".box").find("p").click(function(){
    var n = $(this).index();
    var m = n * 1000;    
    var fun = function(){
        setTimeout(function(){
            console.log(n + "---" + m); 
            flag = 1;
        }, m);          
    }
    taskArr.push(fun);
});

function go(){
    flag = 0;
    done = taskArr.shift();
    done();
}

setInterval(function(){
    if(taskArr.length && flag){
        go();
    }
}, 100);

