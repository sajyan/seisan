# seisan

<html lang="ja">
<head>

<meta charset="UTF-8">

<style type="text/css">
   
li {
   list-style: none;
}
li:before {
   content: "● ";
}

input {
   border: none;
   width: 80px;
   font-size: 14px;
   padding: 2px;
}

input:hover {
   background-color: #eee;
}

input:focus {
   background-color: #ccf;
}

input:not(:focus) {
   text-align: right;
}

table {
   border-collapse: collapse;  
}

td {
   border: 1px solid #999;
   padding: 0;
}

tr:first-child td, td:first-child {
   background-color: #ccc;
   padding: 1px 3px;
   font-weight: bold;
   text-align: center;
}

footer {
   font-size: 80%;
}
   
.red {color:#ff0000;}
.grey {color:#ffffff; background:#999999;}
.blue {color:#0000ff;}
.waku {border:2px dotted #99cc66;
     line-height: 200%;
     padding: 10px;}

body { background-color: #00fff5; }
   
   </style>

   <script src="seisann.js"></script>

   </head>
   
   <body>

<h1><span class="blue"><strong>簡易、支払い＆精算計算</strong></span></h1>

<ul>
<li> <input type="button" id="btn1" value="精算計算  " onclick="btn1Click();" />  ←　支払い＆精算計算、開始ボタン</li>
</ul>

 

<script>  
//ボタン１をクリックした時の処理
function btn1Click(){

   var selects = prompt('参加人数を入力！');

   var selectss = prompt('支払った人の人数を入力！');

   var koukin = prompt('繰越金からの補助額を入力！');
   
var nama = [];
   for (var i=0; i<selectss; i++){
     nama[i] = prompt("支払った人の名前を入力");
   }  

var menu = [];    
   for (var i=0; i<selectss; i++){
     menu[i] = prompt(nama[i] + "さんの支払金額を入力");
   }

document.write("各自の支払金額は<br>")
   for (var i=0; i<menu.length; i++){
     document.write(nama[i] + "さん：" + menu[i] + "円 <br>")
   }
   
//各自の会計額を計算
   
var kasann = [];
     kasann[0] = menu[0];
   for (var i=0; i<selectss-1; i++){
kasann[i+1] = Math.round (Number(kasann[i]) + Number(menu[i+1]));
     }
   
var kasan = Math.round (Number(kasann[i]) - Number(koukin))
     
//各自の分担分を計算

var buntan = Math.round (Number(kasan)/Number(selects));

//各自の割り勘分を計算

var wari = [];
   for (var i=0; i<selects; i++){
   wari[i] = Math.round (Number(menu[i]) - Number(buntan));
     }

var kasann = kasann[selectss-1]
   
document.write("<br>経費の総額：" + kasann + "円<br>")
     
document.write("繰越金からの補助額：" + koukin + "円<br>")

document.write("精算金額の総額：" + kasan + "円<br>")
   
document.write("参加人数は：" + selects + "人<br>")
     
document.write("一人当たりの分担：" + buntan + "円<br>")

document.write("<br>支払った人への払い戻し金額は<br>")
   for (var i=0; i<menu.length; i++){
     document.write(nama[i] + "さん：" + wari[i] + "円 <br>")
   }

document.write ("<br>以上、お帰りも気を付けて、来年も元気に再開～(^^)/<br><br>");
    
var str = "戻る";
document.write(str.link("https://sajyan.github.io/seisan/"));
   
       document.bgColor = "#00ffd8";
       document.fgColor = "blue";
   
}

       </script>

       </body>
   
</html> 
<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
<!-- フッタ -->
<footer>
Copyright 2020/01/31 Sajyan
</footer>
