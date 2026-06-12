---
title: "help with javascript"
date: 2010-02-21
forum: Education &amp; Science
---

### Post by sxmaxchine on 2010-02-21
I'm trying to make a program using Javascript what im trying to Write a program that is prompted for a users name 5 times and displays all the names together at the end (one per line). i know that it doesnt have anything to do with ubuntu but i just realy want an answer.

thanks for the help.

---

### Post by sxmaxchine on 2010-02-21
i solved my problem this is my result code:

<html>
<head>
<script type="text/javascript">
<!--
function prompter() {
	var i;
	for(i=0;i<5;i++){
		var reply = prompt("Hello there good looking!  What's your name?", "");
		document.write (reply);
		document.write ("<br />")		
	}
}
//-->

</script>

</head>
<body>
<input type="button" onclick="prompter()" value="Say my name!">
</body>
</html>

---

