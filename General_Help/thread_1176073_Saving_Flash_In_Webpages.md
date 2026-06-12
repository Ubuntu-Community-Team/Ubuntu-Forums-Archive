---
title: "Saving Flash In Webpages"
date: 2009-06-01
forum: General Help
---

### Post by s1mp13m4n on 2009-06-01
Hello everyone.  I am trying to save or convert items that are in Flash to a format like text.  I am taking practice quizes online and I want to save that info in a format that can be referenced later like html or text.  In other words convert it and save it.  How would I go about doing that?  Thank you for the help.

---

### Post by mb_webguy on 2009-06-01
Are you talking about Flash or JavaScript?  Flash is a type of animation or video, and if there's any text in it you pretty much have to copy it by hand.  I'm sure that somewhere, someone has written some software to scan video for text, but I don't know about it.

If you're talking about JavaScript, such as used on online quizzes and surveys, then copying it is usually as simple as saving the web page.  Sometimes, the script is located in a separate file -- you'd have to look at the source code of the web page to know for sure -- but if that's the case then you just have to save that file as well.

But Flash can't be saved as text any more than any other video format can be saved as text.

---

### Post by s1mp13m4n on 2009-06-01
The practice/review tests when you right click on the page show flash settings and are interactive.  The page source shows javascript tags here is code from a page of the review


<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
<title>Student Success Chapter Quiz</title>
<script language="javascript">AC_FL_RunContent = 0;</script>
<script src="AC_RunActiveContent.js" language="javascript"></script>
</head>
<body bgcolor="#ffffff">
<!--url's used in the movie-->
<!--text used in the movie-->
<!-- saved from url=(0013)about:internet -->
<script language="javascript">
	if (AC_FL_RunContent == 0) {
		alert("This page requires AC_RunActiveContent.js.");
	} else {
		AC_FL_RunContent(
			'codebase', 'http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=8,0,0,0',
			'width', '800',
			'height', '552',
			'src', 'shell',
			'quality', 'high',
			'pluginspage', 'http://www.macromedia.com/go/getflashplayer',
			'align', 'middle',
			'play', 'true',
			'loop', 'true',
			'scale', 'showall',
			'wmode', 'window',
			'devicefont', 'false',
			'id', 'shell',
			'bgcolor', '#ffffff',
			'name', 'shell',
			'menu', 'true',
			'allowFullScreen', 'false',
			'allowScriptAccess','sameDomain',
			'movie', 'shell',
			'salign', ''
			); //end AC code
	}
</script>
<noscript>
	<object classid="clsid:d27cdb6e-ae6d-11cf-96b8-444553540000" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=8,0,0,0" width="800" height="552" id="shell" align="middle">
	<param name="allowScriptAccess" value="sameDomain" />
	<param name="allowFullScreen" value="false" />
	<param name="movie" value="shell.swf" /><param name="quality" value="high" /><param name="bgcolor" value="#ffffff" />	<embed src="shell.swf" quality="high" bgcolor="#ffffff" width="800" height="552" name="shell" align="middle" allowScriptAccess="sameDomain" allowFullScreen="false" type="application/x-shockwave-flash" pluginspage="http://www.macromedia.com/go/getflashplayer" />
	</object>

</noscript>
</body>
</html>


does this help at all?  Thanks for the help.

---

