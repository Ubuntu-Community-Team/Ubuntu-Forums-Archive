---
title: "Firefox / Page problem"
date: 2005-09-28
forum: Desktop Environments
---

### Post by DrecoZA on 2005-09-28
Please can someone help with the following problem, one of our customers has a restricted web site which we need to log into. However the hyperlinks do not work in Firefox (I have installed JRE) Is there an alternate browser I can test or is there a problem with their code ?


<html>
<head>
<base target="default">
<title>SKYTRAX - Mobile Lifestyle Solutions</title>
<script language="JavaScript">
<!--
/*
Auto Maximize Window Script- By Nick Lowe (nicklowe@ukonline.co.uk)
For full source code, 100's more free DHTML scripts, and Terms Of Use
Visit [http://www.dynamicdrive.com](http://www.dynamicdrive.com)
*/

top.window.moveTo(0,0);
if (document.all) {
top.window.resizeTo(screen.availWidth,screen.availHeight);
}
else if (document.layers||document.getElementById) {
if (top.window.outerHeight<screen.availHeight||top.window.outerWidth<screen.availWidth){
top.window.outerHeight = screen.availHeight;
top.window.outerWidth = screen.availWidth;
}
}
//-->
</script>
<link rel=stylesheet href="style.css" type="text/css">
<link rel=stylesheet href="menu_style.css" type="text/css">
<style>
</style>
</head>
<body leftmargin=0 rightmargin=0 topmargin=0 bottommargin=0>
<center>

<SCRIPT LANGUAGE=javascript>
<!--
var selected;

function hover(item)
{
	if(item != selected)
	{
		item.className = "menuHover";
	}
}

function unhover(item)
{
	if(item != selected)
	{
		item.className = "menu";
	}
}

function select(item)
{
	if(selected != null)
	{
		selected.className = "menu";
	}
	selected = item;
	item.className = "menuSelected";
}
//-->
</SCRIPT>

<table cellspacing=0 width=100% style="border: 0px;">
<tr>
	<th colspan=4>SKYTRAX - Skytrax Agent - TRM (Total Relationship Management (Pty) Ltd)</th>
</tr>
<tr>
	<td colspan=4 style="height: 15px;"></td>
</tr>
<tr>
	<a href="sta_signup.asp" title="Sign Up Client"><td id=signupLink width=25% onClick="select(this);" onMouseOut="unhover(this);" onMouseOver="hover(this);" class="menuSelected" align=center>Sign Up</td></a>
	<a href="sta_contract_status.asp" title="Contract Status"><td width=25% onClick="select(this);" onMouseOut="unhover(this);" onMouseOver="hover(this);" class="menu" align=center>Contract Status</td></a>
	<a href="settings.asp" title="Settings"><td width=25% onClick="select(this);" onMouseOut="unhover(this);" onMouseOver="hover(this);" class="menu" align=center>Settings</td></a>
	<a href="../index.asp?action=logout" target="_top"><td onClick="select(this);" onMouseOut="unhover(this);" onMouseOver="hover(this);" class="menu" align=center>Log Out</td></a>
</tr>
</table>

<SCRIPT LANGUAGE=javascript>
<!--
selected = signupLink;
//-->
</SCRIPT>

</center>
</body>
</html>

---

### Post by DrecoZA on 2005-09-28
have just installed Epiphany and have the same problem

---

### Post by yage on 2005-09-28
Try installing Opera and see if that fixes the problem 
[http://www.opera.no](http://www.opera.no)

---

