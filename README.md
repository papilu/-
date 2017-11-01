<html>
 2 <head>
 3     <meta charset="UTF-8">
 4     <title>Document</title>
 5     <style type="text/css">
 6         .lightbox{
 7             position: fixed;
 8             top: 0px;
 9             left: 0px;
10             height: 100%;
11             width: 100%;
12             z-index: 7;
13             opacity: 0.3;
14             display: block;
15             background-color: rgb(0, 0, 0);
16         }
17         .pop{
18             position: absolute;
19             left: 50%;
20             width: 894px;
21             margin-left: -447px;
22             z-index: 9;
23         }
24     </style>
25     <script src="Scripts/pdf.js" type="text/javascript"></script>
26     <script type="text/javascript">
27         function showPdf() {
28             var container = document.getElementById("container");
29             container.style.display = "block";
30             var url = 'Scripts/jQuery经典入门教程(绝对详细).pdf';
31             PDFJS.workerSrc = 'Scripts/pdf.worker.js';
32             PDFJS.getDocument(url).then(function getPdfHelloWorld(pdf) {
33                 pdf.getPage(1).then(function getPageHelloWorld(page) {
34                     var scale = 1;
35                     var viewport = page.getViewport(scale);
36                     var canvas = document.getElementById('the-canvas');
37                     var context = canvas.getContext('2d');
38                     canvas.height = viewport.height;
39                     canvas.width = viewport.width;
40                     var renderContext = {
41                         canvasContext: context,
42                         viewport: viewport
43                     };
44                     page.render(renderContext);
45                 });
46             });
47         }
48     </script>
49 </head>
50 <body>
51     <h1><a href="javascript:void(0)" target="_blank" onclick="showPdf()">显示pdf文档</a></h1>
52     <div id="container" style="display: none;">
53         <div class="lightbox"></div>
54         <div id="pop" class="pop">
55             <canvas id="the-canvas"></canvas>
56         </div>
57     </div>
58 </body>
59 </html>
