<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>FF TopUp BD</title>

<style>
*{
    box-sizing:border-box;
}

body{
    margin:0;
    font-family:Arial, sans-serif;
    background:#0b1020;
    color:#fff;
}

/* Header */
header{
    text-align:center;
    padding:28px 15px;
    background:linear-gradient(135deg,#6c2cff,#ff2d75);
}

header h1{
    margin:0;
    font-size:30px;
}

header p{
    margin:8px 0 0;
    font-size:14px;
}

/* Main */
.container{
    width:100%;
    max-width:520px;
    margin:auto;
    padding:18px;
}

/* Card */
.card{
    background:#151c32;
    padding:20px;
    margin-bottom:18px;
    border-radius:18px;
    box-shadow:0 5px 20px rgba(0,0,0,.35);
}

.card h2{
    margin-top:0;
    font-size:20px;
}

/* Input */
label{
    display:block;
    margin-top:12px;
    margin-bottom:6px;
    font-size:14px;
}

input,
select{
    width:100%;
    padding:14px;
    border:none;
    outline:none;
    border-radius:10px;
    font-size:16px;
    background:#fff;
    color:#111;
}

/* Packages */
.packages{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:12px;
    margin-top:15px;
}

.package{
    padding:18px 10px;
    background:#222b48;
    border:2px solid transparent;
    border-radius:14px;
    text-align:center;
    cursor:pointer;
    transition:.2s;
}

.package:hover{
    border-color:#ff2d75;
    transform:scale(1.02);
}

.package.active{
    border-color:#ff2d75;
    background:#302052;
}

.diamond{
    font-size:20px;
    font-weight:bold;
}

.price{
    margin-top:7px;
    color:#ffd34d;
    font-size:17px;
    font-weight:bold;
}

/* Selected package */
#selected{
    margin-top:18px;
    padding:12px;
    border-radius:10px;
    background:#202944;
    text-align:center;
    color:#ddd;
}

/* Payment */
.payment-box{
    margin-top:10px;
}

.payment-number{
    display:none;
    margin-top:12px;
    padding:13px;
    background:#202944;
    border-radius:10px;
    text-align:center;
}

/* Button */
button{
    width:100%;
    margin-top:18px;
    padding:15px;
    border:none;
    border-radius:12px;
    background:linear-gradient(90deg,#6c2cff,#ff2d75);
    color:white;
    font-size:18px;
    font-weight:bold;
    cursor:pointer;
}

button:active{
    transform:scale(.98);
}

/* Notice */
.notice{
    font-size:13px;
    color:#aaa;
    line-height:1.6;
}

/* Order result */
#orderResult{
    display:none;
    margin-top:15px;
    padding:15px;
    background:#10251b;
    border:1px solid #1fa463;
    border-radius:12px;
    line-height:1.8;
}

/* Support */
.support{
    text-align:center;
}

.support p{
    color:#bbb;
}

/* Footer */
footer{
    text-align:center;
    padding:25px 10px;
    color:#888;
    font-size:13px;
}

@media(max-width:380px){
    .packages{
        grid-template-columns:1fr;
    }
}
</style>
</head>


<body>

<!-- HEADER -->
<header>

    <h1>🔥 FF TopUp BD</h1>

    <p>Fast & Easy Free Fire Top-Up</p>

</header>


<div class="container">


<!-- PLAYER INFORMATION -->
<div class="card">

    <h2>🆔 Player Information</h2>

    <label>Free Fire UID</label>

    <input
        id="uid"
        type="number"
        inputmode="numeric"
        placeholder="আপনার Free Fire UID লিখুন"
    >


    <label>Server</label>

    <select id="server">

        <option value="Bangladesh">
            🇧🇩 Bangladesh
        </option>

        <option value="Asia">
            🌏 Asia
        </option>

    </select>

</div>


<!-- DIAMONDS -->
<div class="card">

    <h2>💎 Select Diamonds</h2>

    <div class="packages">


        <div
            class="package"
            onclick="selectPack(this,'25 Diamonds','25')"
        >

            <div class="diamond">
                💎 25 Diamonds
            </div>

            <div class="price">
                ৳25
            </div>

        </div>


        <div
            class="package"
            onclick="selectPack(this,'50 Diamonds','45')"
        >

            <div class="diamond">
                💎 50 Diamonds
            </div>

            <div class="price">
                ৳45
            </div>

        </div>


        <div
            class="package"
            onclick="selectPack(this,'100 Diamonds','85')"
        >

            <div class="diamond">
                💎 100 Diamonds
            </div>

            <div class="price">
                ৳85
            </div>

        </div>


        <div
            class="package"
            onclick="selectPack(this,'310 Diamonds','250')"
        >

            <div class="diamond">
                💎 310 Diamonds
            </div>

            <div class="price">
                ৳250
            </div>

        </div>

    </div>


    <p id="selected">
        কোনো Diamond Package নির্বাচন করা হয়নি
    </p>

</div>


<!-- PAYMENT -->
<div class="card">

    <h2>📱 Payment Method</h2>


    <select id="payment" onchange="showPaymentNumber()">

        <option value="">
            Payment Method নির্বাচন করুন
        </option>

        <option value="bKash">
            bKash
        </option>

        <option value="Nagad">
            Nagad
        </option>

    </select>


    <div
        id="paymentNumber"
        class="payment-number"
    >
        Payment number এখানে বসান
    </div>


    <p class="notice">

        ⚠️ এটি বর্তমানে একটি ডেমো অর্ডার সিস্টেম।
        আসল পেমেন্ট নেওয়ার আগে সঠিক payment gateway
        এবং বৈধ Top-Up provider যুক্ত করুন।

    </p>


    <button onclick="order()">
        🛒 Order Now
    </button>


    <!-- ORDER RESULT -->
    <div id="orderResult"></div>

</div>


<!-- SUPPORT -->
<div class="card support">

    <h2>📞 Support</h2>

    <p>
        অর্ডার সংক্রান্ত সমস্যায় আমাদের সাথে যোগাযোগ করুন।
    </p>

</div>


</div>


<!-- FOOTER -->
<footer>

    © 2026 FF TopUp BD
    <br>
    All Rights Reserved.

</footer>


<script>

let selectedPackage = "";
let selectedPrice = "";


/* Select Diamond Package */

function selectPack(element, pack, price){

    selectedPackage = pack;

    selectedPrice = price;


    // Remove active from all packages

    document
        .querySelectorAll(".package")
        .forEach(function(item){

            item.classList.remove("active");

        });


    // Add active to selected package

    element.classList.add("active");


    // Show selected package

    document.getElementById("selected").innerHTML =
        "✅ Selected: <b>" +
        pack +
        "</b> — ৳" +
        price;

}


/* Payment Number */

function showPaymentNumber(){

    let payment =
        document.getElementById("payment").value;

    let box =
        document.getElementById("paymentNumber");


    if(payment === "bKash"){

        box.style.display = "block";

        box.innerHTML =
            "📱 bKash Number: <b>01XXXXXXXXX</b>";

    }

    else if(payment === "Nagad"){

        box.style.display = "block";

        box.innerHTML =
            "📱 Nagad Number: <b>01XXXXXXXXX</b>";

    }

    else{

        box.style.display = "none";

    }

}


/* Order */

function order(){

    let uid =
        document.getElementById("uid").value.trim();

    let server =
        document.getElementById("server").value;

    let payment =
        document.getElementById("payment").value;


    /* UID check */

    if(uid === ""){

        alert("❌ আপনার Free Fire UID লিখুন।");

        return;

    }


    /* Package check */

    if(selectedPackage === ""){

        alert("❌ একটি Diamond Package নির্বাচন করুন।");

        return;

    }


    /* Payment check */

    if(payment === ""){

        alert("❌ একটি Payment Method নির্বাচন করুন।");

        return;

    }


    /* Generate Order ID */

    let orderID =
        "FF" +
        Math.floor(
            100000 +
            Math.random() * 900000
        );


    /* Show Order */

    let result =
        document.getElementById("orderResult");


    result.style.display = "block";


    result.innerHTML =

        "<b>✅ Order Created!</b><br><br>" +

        "🧾 Order ID: <b>" +
        orderID +
        "</b><br>" +

        "🆔 UID: <b>" +
        uid +
        "</b><br>" +

        "🌏 Server: <b>" +
        server +
        "</b><br>" +

        "💎 Package: <b>" +
        selectedPackage +
        "</b><br>" +

        "💰 Price: <b>৳" +
        selectedPrice +
        "</b><br>" +

        "📱 Payment: <b>" +
        payment +
        "</b><br><br>" +

        "⚠️ এটি ডেমো অর্ডার।";


    /* Scroll to order */

    result.scrollIntoView({
        behavior:"smooth"
    });

}

</script>

</body>
</html>
