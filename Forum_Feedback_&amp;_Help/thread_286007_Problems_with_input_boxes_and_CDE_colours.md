---
title: "Problems with input boxes and CDE colours"
date: 2006-10-27
forum: Forum Feedback &amp; Help
---

### Post by Rhapsody on 2006-10-27
I've been fiddling around with my KDE display settings a lot, and found that a varient on the CDE colour scheme is very much to my liking. Unfortunately, the input boxes on these boards don't seem to work very well with it.

The background colour is specificed to be a very light brown, and the system text colour is assumed to be black or any other dark colour. When this assumption is right, it all works very well. But with the white text of the CDE colour scheme, it's nearly unreadable!

I've attached a screenshot of this to my message. As should be obvious, it's not easy to type like this. I can just use a colour scheme with dark text, but isn't it possible to specify the text colour as well? This would make the forum a lot more friendly to various colour schemes.

---

### Post by ubuntu-geek on 2006-10-27
That would be something in your theme. :( The colors we use for text boxes are a grey/black combo.

---

### Post by Rhapsody on 2006-10-27
Well I know my theme is making input box text white, but I've seen other forums with with white input boxes that have black text, regardless of my colour scheme. So it's certainly something that's possible to specify, it just doesn't happen here. As far as I can tell, either the coding on this forum doesn't specify a text colour, or the code that does isn't working.

But if it's not possible to do that on this board software, then it must be possible to make a different theme with darker colours. I've also seen a forum that does this, and it works well.

I usually wouldn't ask about something like this, but the Ubuntu Forums are the 'odd-one out' in this while all other forums I visit can handle just about everything I can throw at them, this one falters.

---

### Post by Mockskin on 2006-10-27
Lalala. 

Symptom.
Problem.
User fix. (firefox + stylish extension)

@ ubuntu-geek: Very few websites actually define the input colors for some reason. It's bad style to just assume everyone's text colors will look fine on your chosen background. You're already redefining the borders and such, so why not the text color as well?

---

### Post by Rhapsody on 2006-10-27
Well I found a fix for it anyway. Using the Stylish Firefox extension, I changed this:

```
textarea, .bginput
{
	background: #eaeada;
	font-size: 1.1em/1.5em;
	border: 1px solid #816647;
}
```

in [http://ubuntuforums.org/clientscript/vbulletin_css/style-0b0f8cc3-00032.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-0b0f8cc3-00032.css) to this:

```
textarea, .bginput
{
	color: #000000;
	background: #eaeada;
	font-size: 1.1em/1.5em;
	border: 1px solid #816647;
}
```

I've found this makes the text in input boxes black. If this isn't an ugly kludge with other side-effects (and I don't see anyway) you may wish to make this a permanant CSS change.

---

### Post by mssever on 2006-11-26
Back in the 3.0 browser days, Netscape used a gray default page background while IE used white. I learned quickly that you can get into trouble if you fail to specify a color and rely on the defaults instead.

I always make a complete font specification in the CSS body selector--including color, font, relative size, etc. I then simply override it when necessary. That way, problems of this kind only happen to Google Toolbar users (Google Toolbar changes the background-color of input boxes it can autocomplete, but doesn't bother to set the color; forced me to stop using a dark background for form fields).

I think it would be great if these forums would do something similar.

EDIT: I just glanced at the CSS and noticed that a dark color is specified on body. So, either something is incorrectly overriding that setting, or the OP's browser isn't respecting the CSS.

---

