<html>
  <head>
    <title>test</title>
  </head>
  <body>
    <input type="button" value="ボタン" onClick="drawing()">

    <div id="img_div">
    </div>


    <!-- scriptタグが読み込まれる前に指定するdivが読み込まれている必要があるので、
      scriptタグは最後に置いた。
      これが一番良いのかはわからない -->
    <script>
      // 選ぶ画像の数
      let number_of_tags = 10;
       // 最初に空のimgタグを作っておく
      function createImageTag(tag_number, parent_tag_id) {
        for(let i = 0; i < tag_number; i++){
          let img_tag = document.createElement("img");
          // idはimg0, img1, img2～　となる
          img_tag.setAttribute("id", "img" + String(i));
          let parent_tag = document.getElementById(parent_tag_id);
          document.body.appendChild(img_tag);
        }
      }
      // 第一引数→作る数、第二引数→作ったものを親要素にするタグ
      createImageTag(number_of_tags, "img_div");
      // 0.png, 1.png～というように画像の名前は数字に設定しておく
      function choosingImage(tag_number){
        // ランダムな数字を格納する配列
        let chosen_numbers = [];
        for(let i = 0; i < tag_number; i++){
          // ランダムな数字を配列に入れる
          let random_number = Math.floor(Math.random()*number_of_tags);
          chosen_numbers.push(random_number);
        }
        for(let i = 0; i < tag_number; i++){
          // 配列の数字を参照し、その番号の画像を表示
          // idを取り出す（idは連番）
          let img_tag = document.getElementById("img" + String(i));
          // 配列を参照
          img_tag.setAttribute("src", String(chosen_numbers[i]) + ".png");
        }
      }
      // ボタンを押すと呼ばれる関数
      function drawing() {
        choosingImage(number_of_tags);
      }
    </script>
  </body>
</html>
