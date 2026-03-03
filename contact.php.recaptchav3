<?php
// ========== berlin add ========
header("Content-Type: text/html; charset=UTF-8");

use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\Exception;

require 'src/PHPMailer.php';
require 'src/SMTP.php';
require 'src/Exception.php';
// ========== berlin add end =========

function h($string) {
  return htmlspecialchars($string, ENT_QUOTES, 'UTF-8');
}

if (!empty($_POST['website'])) {
  die('Spam detected.');
}

//===== use google reCAPTCHA v3, berlin ====
if ($_SERVER["REQUEST_METHOD"] == "POST") {
  $recaptcha_secret = '6Lfc3GUrAAAAAOWU21ZYeVKeXcPtxeKkbJUnqU5-'; // my secret
  $recaptcha_response = $_POST['g-recaptcha-response'];

  $response = file_get_contents(
      "https://www.google.com/recaptcha/api/siteverify?secret=" . $recaptcha_secret .
      "&response=" . $recaptcha_response
  );
  $response_keys = json_decode($response, true);

  if ($response_keys["success"] && $response_keys["score"] >= 0.5) {
        //echo "you got a score : $response_keys[score]";
   } 
  else {
    die('Spam detected.');
  }
}

if(isset($_POST["name"])) {
  $message =
    "<table width='519' height='100%' border='1' align='center' cellpadding='8' cellspacing='2' bordercolor='#39C'>                                              
      <tr>                                                
          <td  colspan='2' bgcolor='#39C'>
          <div align='center'><font color='#FFF' size='5'>contact us</font></div></td>
      </tr>
      
      <tr >                                                
          <td width='113'><div align='right'><font color='#668' size='2' face='Arial'>Name :</font></div></td>
          <td><font color='#00F'>".h($_POST["name"])."</font></td>
      </tr>
      
      <tr >                                                
          <td><div align='right'><font color='#668' size='2' face='Arial'>Country :</font></div></td>
          <td><font color='#00F'>".h($_POST["country"])."</font></td>
      </tr>                                            
      
      <tr >                                                
          <td><div align='right'><font color='#668' size='2' face='Arial'>Company :</font></div></td>
      	<td><font color='#00F'>".h($_POST["company"])."</font></td>
      </tr>
                                                    
      <tr >                                                
          <td><div align='right'><font color='#668' size='2' face='Arial'>E-mail :</font></div></td>
          <td><font color='#00F'>".h($_POST["email"])."</font></td>
      </tr>
                                                    
      <tr >
          <td><div align='right'><font color='#668' size='2' face='Arial'>Contact Phone :</font></div></td>
          <td><font color='#00F'>".h($_POST["tel"])."</font></td>
      </tr>
      
      <tr >
          <td><div align='right'><font color='#668' size='2' face='Arial'>Subject :</font></div></td>
          <td><font color='#00F'>".h($_POST["subject"])."</font></td>
      </tr>
                                                    
      <tr >                                                
          <td><div align='right'><font color='#668' size='2' face='Arial'>Contents :</font></div></td>    
          <td><font color='#00F'>".nl2br(h($_POST["contents"]))." </font></td>
      </tr>
                                                     
      <tr bgcolor='#39C' >                                                
          <td height='100%' colspan='2'><div align='center' ></div></td>
      </tr>
    </table>";
  
  // ===== hinet not support mail() function ===== 
  //$MailTo="sales@sendtek.com";
  //$headers = "MIME-Version: 1.0\n";
  //$headers .= "Content-type: text/html;\n";
  //$headers .= "From: Contact Us<sales@sendtek.com>\n";
  //$headers .= "Bcc:\n";
  //$title = "SendTek[Contact Us] ";
  //$title .= h($_POST["subject"]);
  //mail($MailTo,$title,$message,$headers); // berlin mark
  	 
  // ===== use PHPMailer instead =====
  $mail = new PHPMailer(true);
  $mail->CharSet = 'UTF-8';  // make sure content is UTF-8 
  	 
  try {
    $mail->isSMTP();
    $mail->Host       = 'www.hibox.hinet.net';
    $mail->SMTPAuth   = true;
    $mail->Username   = 'berlin@sendtek.com';         
    $mail->Password   = 'cblpad';           
    $mail->SMTPSecure = 'tls';
    $mail->Port       = 587;

    $mail->setFrom('sales@sendtek.com', 'Contact Us');
    $mail->addAddress('sales@sendtek.com');        
    //$name =  h($_POST['name']);
    //$email = h($_POST['email']);
    //$mail->addReplyTo($email, $name);

    $mail->isHTML(true);
   	$mail->Subject = h($_POST['subject']);
	  $mail->Body = "$message";
    $mail->send();
  } catch (Exception $e) {
    echo "Message could not be sent. Mailer Error: {$mail->ErrorInfo}";
  }
  	 
  $_POST["test"]="";
  echo "<script language='javascript'> alert('Thank you very much for your contact information. We will get in touch with you as quickly as possible. ');</script>";
}
?>


<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />

<!-- use google reCAPTCHA v3, berlin -->
<script src="https://www.google.com/recaptcha/api.js?render=6Lfc3GUrAAAAAPmlaA_NlugN-Zhqb5b5PPeZi3Gh"></script>

<title>SendTek Corporation-Contact SendTek</title>
<meta name="keywords" content="contact us,by following approaches" />
<link rel="SHORTCUT ICON" href="favicon.ico">
<link href="css/reset.css" rel="stylesheet" type="text/css" />
<link href="css/style.css" rel="stylesheet" type="text/css" />
<link href="css/form.css" rel="stylesheet" type="text/css"/>
</head>
<body>
<div id="wrapper">
<div id="header">
<div class="lg">
<a href="index.html"><img src="images/logo.png" /></a>
<!--lg --></div>
<div class="btn">
<a href="mailto:sales@sendtek.com"  target="_blank"><img src="images/email.png" /></a>
<!--btn --></div>
<!--header --></div>

<div class="nav">
<li><a href="prod-ces83x.php" class="navMenu1"></a></li>
<li><a href="schema.html" class="navMenu2"></a></li>
<li><a href="news.html" class="navMenu3"></a></li>
<li><a href="about.html" class="navMenu4"></a></li>
<li><a href="contact.php" class="navMenu5_on"></a></li>
<li><a href="index.html" class="navMenu6"></a></li>
<!--nav--></div>

<div id="bnr">
<!--bnr --></div>
<div id="contents"> 
<div class="sub">
<img src="images/contact1.jpg" />
<!--sub--></div>

<div class="main">
<body leftmargin=0 topmargin=0>

<script language="JavaScript">
  function validate(form)
  {
    return true;
  }
  
  function isFilled(elm) 
  {
    if (elm.value == "" || elm.value == null)
      return false;
    else 
      return true;
  }
  
  function checkMail(elm)
  {
    if (elm.value.indexOf("@") != "-1" && elm.value.indexOf(".") != "-1")  
      return true;  
    else 
      return false;
  }
</script>

<table> 
  <tr><td background="images/bg-title2.jpg"><h1>Contact SendTek</h1></td></tr> 
  <tr><td>
  <div class="bottom"><!--bottom--></div>
  
  <div class="form">
  <form name="form" id="contact-form" method="post" action="contact.php" >
    <fieldset>
  	<legend>For product and application information,you are kindly welcome to</br> contact us directly by following approaches.</legend>
    
    <p><label>Name：</label><input name="name" id="name" type="text" style="width:193px;" /></p>
    <p><label>Country：</label> <input name="country" id="country"  type="text" style="width:193px;" /></p>
    <p><label>Company：</label><input name="company" id="company"  type="text" style="width:250px;" /></p>
    <p><label>Email：</label><input name="email" id="email"  type="text" value="" style="width:310px;" /></p>
    <p><label>Phone：</label>	<input name="tel" id="tel"  type="text" value="" style="width:310px;" /></p>
    <p><label>Subject：</label><input name="subject" id="subject"  type="text" value="" style="width:310px;" /></p>
    <p><label>Contents：</label><textarea name="contents" rows="8" id="contents"   type="textarea" value="" style="width:310px;height:134px"></textarea></p>
    <!-- honeypot -->
    <p><input type="text" name="website" style="display:none"></p>
    </fieldset>

	  <p align="center"><button type="reset"><p>Reset</p></button><button type="button" onclick="onClick()"><p>Send</p></button></p>
	  
  </form>
	  
	<script>
    function onClick() {
      grecaptcha.ready(function() {
        grecaptcha.execute('6Lfc3GUrAAAAAPmlaA_NlugN-Zhqb5b5PPeZi3Gh', {action: 'submit'}).then(function(token) {
        
          const form = document.getElementById('contact-form');
          let input = document.createElement("input");
          input.type = "hidden";
          input.name = "g-recaptcha-response";
          input.value = token;
          form.appendChild(input);
          form.submit();
        });
      });
    }
  </script>
	  
  <!--form--></div>
	
  <div class="bottom"><!--bottom--></div>
  </td></tr>   
</table> 

<!------------------------------------------------------------------------------------------------------------------------------------------------------->
<!--main--></div>
<!--contents--></div>

<div id="footer">
Copyright(c)SendTek Corporation All rights reserved
<!--footer--></div>
<!--wrapper --></div>
</body>
</html>
