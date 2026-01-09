# HTML-Day-18
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Secure Comment Box (XSS Protected)</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 600px;
            margin: 50px auto;
            padding: 20px;
        }
        #commentInput {
            width: 70%;
            padding: 8px;
            margin-right: 10px;
        }
        button {
            padding: 8px 16px;
        }
        #comments {
            margin-top: 20px;
            border-top: 2px solid #ccc;
            padding-top: 20px;
        }
        #comments p {
            background: #f0f0f0;
            padding: 10px;
            margin: 10px 0;
            border-radius: 4px;
        }
        .safe {
            background: #d4edda;
            border: 2px solid #28a745;
            padding: 15px;
            margin-bottom: 20px;
            border-radius: 4px;
        }
    </style>
</head>
<body>

    <div class="safe">
        <strong>Secure Version:</strong> This comment box is protected from XSS attacks.
    </div>

    <h3>Comment Box</h3>
    <input id="commentInput" placeholder="Type your comment..." />
    <button onclick="postComment()">Post</button>

    <div id="comments"></div>

    <script>
        function postComment() {
            const comment = document.getElementById("commentInput").value;

            const p = document.createElement("p");
            p.textContent = comment;  // XSS protection

            document.getElementById("comments").appendChild(p);
            document.getElementById("commentInput").value = "";
        }
    </script>

</body>
</html>
