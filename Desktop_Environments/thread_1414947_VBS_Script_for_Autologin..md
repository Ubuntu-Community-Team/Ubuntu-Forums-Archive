---
title: "VBS Script for Autologin."
date: 2010-02-24
forum: Desktop Environments
---

### Post by hariks0 on 2010-02-24
Can somebody point out what is wrong in this script? It inputs login id and password but just would not login.

```
WScript.Quit Main

Function Main
  Set IE = WScript.CreateObject("InternetExplorer.Application", "IE_")
  IE.Visible = True
  IE.Navigate "http://www.website.com/_layouts/login.aspx?ReturnUrl=%2f_layouts%2fAuthenticate.aspx%3fSource%3d%252f&Source=%2f"

  Wait IE
  With IE.Document
    .getElementByID("login_UserName").value = "1234"
    .getElementByID("login_password").value = "12345"

    .getElementByID("ctl00").Submit
  End With
End Function

Sub Wait(IE)
  Do
    WScript.Sleep 500
  Loop While IE.ReadyState < 4 And IE.Busy 
  Do
    WScript.Sleep 500

  Loop While IE.ReadyState < 4 And IE.Busy 
End Sub

Sub IE_OnQuit
  On Error Resume Next
  WScript.StdErr.WriteLine "IE closed before script finished."
  WScript.Quit
End Sub

```

The source of the site is as follows :-
```

<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <title>Sign In</title>
    <link rel="stylesheet" type="text/css" href="/_layouts/1033/styles/core.css" />
    <script language="javascript">
        function OpenPopUp()
        {
                window.open("/_layouts/dnb/retrievepassword.aspx",'RetrievePassword','height=150,width=400,scrollbars=no,toolbar=no,menubar=no,top=300,left=500');
                    
        }
        function OpenWindow()
        {
            //window.open('/_layouts/dnb/TestPurple.aspx', 'mywindow', 'width=400,height=200,left=0,top=100,screenX=0,screenY=100, toolbar=no, location=no,directories=no,status=no,menubar=no,scrollbars=no,copyhistory=yes, resizable=no, fullscreen=yes');
        }

function CheckFailureText()
{
    var varFailureText= document.getElementById('login_FailureText');
    var varFailureTextNewEmp=document.getElementById('login_FailureTextNewEmp');
    if(varFailureText.innerHTML=='Your login attempt was not successful. Please try again.')
    {
        varFailureText.appendChild(document.createElement("br"));
        varFailureText.appendChild(document.createElement("br"));
        varFailureText.innerHTML += 'Message for New employees:';
       
        varFailureTextNewEmp.innerHTML = 'To Enable loging to the site your user details should exists in database.';
        varFailureTextNewEmp.appendChild(document.createElement("br"));
        varFailureTextNewEmp.innerHTML += 'Please contact abc@xyz.com';
    }
    else
    {
    
    }
}
  </script>
  <link rel="stylesheet" type="text/css" href="/_layouts/1033/styles/core.css?rev=NYGKlN%2BMMzkLoRcu7ma9mg%3D%3D"/>

	<script type="text/javascript" language="javascript" src="/_layouts/1033/init.js?rev=bHAUG%2FMhhng8ZGdSbL8hmg%3D%3D"></script>
<script type="text/javascript" language="javascript" src="/_layouts/1033/core.js?rev=S5dt4K8TJGVTYU9HrW6enw%3D%3D"></script>

</head>
<body onload="CheckFailureText();"  style="margin-left: 0px; margin-top: 0px; margin-right: 0px; margin-bottom: 0px;">
    <form name="ctl00" method="post" action="login.aspx?ReturnUrl=%2f_layouts%2fAuthenticate.aspx%3fSource%3d%252f&amp;Source=%2f" id="ctl00">
<div>
<input type="hidden" name="__LASTFOCUS" id="__LASTFOCUS" value="" />
<input type="hidden" name="__VIEWSTATE" id="__VIEWSTATE" value="/wEPDwUJOTQ2ODg2ODA0ZGRnPlhXIolkoTALJKTXytRxvp5nbg==" />
</div>

<script type="text/javascript">
<!--
var theForm = document.forms['ctl00'];
if (!theForm) {
    theForm = document.ctl00;
}
function __doPostBack(eventTarget, eventArgument) {
    if (!theForm.onsubmit || (theForm.onsubmit() != false)) {
        theForm.__EVENTTARGET.value = eventTarget;
        theForm.__EVENTARGUMENT.value = eventArgument;
        theForm.submit();
    }
}
// -->
</script>


<script src="/WebResource.axd?d=uEMxXDyqjb7yoMHeErenqg2&amp;t=633839479093437500" type="text/javascript"></script>

<script> var MSOWebPartPageFormName = 'ctl00';</script>
<script src="/WebResource.axd?d=vB638k9e7aX2s3zXaefvqQ2&amp;t=633839479093437500" type="text/javascript"></script>
        <table id="login" cellspacing="0" cellpadding="0" border="0" style="width:100%;border-collapse:collapse;">
	<tr>
		<td>
                <table cellpadding="0" cellspacing="0" width="100%" border="2"  style="border-color:#fab617">
                <tr>
                    <td bgcolor="#2a2c8c">
                        &nbsp;
                    </td>
                </tr>
            </table>
                <br />
                <br />
                <br />
                <br />
                <br />
                <br />
                <table width="600" border="0" align="center" cellpadding="0" cellspacing="0">
                    <tr>
                        <td width="48">
                            &nbsp;</td>
                        <td >
                            </td>
                        <td width="211">
                           </td>
                        <td width="48">
                            &nbsp;</td>
                    </tr>
                    <tr>
                        <td>
                            <img src="/_layouts/images/leftcurve.gif" width="48" height="252" /></td>
                        <td background="/_layouts/images/curvepixel.gif">
                            <table width="330" border="0" cellspacing="2" cellpadding="2">
                                <tr>
                                    <td style="width: 117px">
                                        &nbsp;</td>
                                    <td width="76%">
                                        &nbsp;</td>
                                </tr>
                                <tr>
                                    <td>
                                        <span class="style1" style="font-size: smaller; font-family: Arial">Employee ID</span>
                                    </td>
                                    <td>
                                        <input name="login$UserName" type="text" id="login_UserName" autocomplete="off" class="ms-long" style="width:150px;" /></td>
                                </tr>
                                <tr>
                                    <td class="style1" style="font-size: smaller; font-family: Arial" >
                                        Password</td>
                                    <td>
                                        <input name="login$password" type="password" id="login_password" autocomplete="off" class="ms-long" style="width:150px;" /></td>
                                </tr>
                                <tr>
                                    <td style="width: 117px">
                                        &nbsp;</td>
                                    <td colspan="2" >
                                        <input type="submit" name="login$login" value="Sign In" onclick="javascript:OpenWindow();" id="login_login" class="rel-button" /></td>
                                </tr>
                                <tr>
                                    <td style="width: 117px">
                                        &nbsp;</td>
                                    <td>
                                        &nbsp;</td>
                                </tr>
                                <tr>
                                    <td style="width: 117px">
                                        &nbsp;</td>
                                    <td align="left" >
                                        <a href='javascript:OpenPopUp();' CssClass="rel-ErrorLabel" style="font-size: smaller; font-family: Arial">Forgot Password</a>
                                    </td>
                                </tr>
                            </table>
                        </td>
                        <td valign="middle" background="/_layouts/images/curvepixel.gif">
                            <img src="/_layouts/images/login_2.JPG"  /></td>
                        <td>
                            <img src="/_layouts/images/rightcurve.gif" width="48" height="252" /></td>
                    </tr>
                    <tr>
                        <td colspan="3" align="center">
                            <br />
                            
                            <br />
			<span id="login_FailureText" class="rel-ErrorLabel"></span>
                            <br />
                            <span id="login_FailureTextNewEmp" style="display:inline-block;color:Red;font-family:Arial;font-size:12px;height:26px;"></span>
                            <br />
                        </td>
                    </tr>
                </table>
                <br />
                <br />
                <br />
                <br />
                <br />
               <br />
               <table cellpadding="0" cellspacing="0" width="100%" border="2"  style="border-color:#fab617">
                <tr>
                    <td bgcolor="#2a2c8c">
                        &nbsp;
                    </td>
                </tr>
            </table>
            </td>
	</tr>
</table>
        <!--
</asp:Content>
-->
    
<div>

	<input type="hidden" name="__EVENTTARGET" id="__EVENTTARGET" value="" />
	<input type="hidden" name="__EVENTARGUMENT" id="__EVENTARGUMENT" value="" />
	<input type="hidden" name="__EVENTVALIDATION" id="__EVENTVALIDATION" value="/wEWBAKOzr4GAsXZ7f4JAr7O/rwJAqiMrcgJrClRggEDAx2fsmvo0wk+a3Y0m+U=" />
</div>

<script type="text/javascript">
<!--
WebForm_AutoFocus('login');// -->
</script>
</form>
</body>
</html>

```

---

### Post by airtonix on 2010-02-24
ubuntu can't run "windows scripting host" as far as I know.

---

### Post by hariks0 on 2010-02-24
Of course I know that. I want to use it on another windoze PC. So I thought asking it in our forum before going elsewhere.

---

