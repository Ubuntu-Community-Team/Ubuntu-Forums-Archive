---
title: "Bluefish"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Magiczero on 2006-08-25
Hi

I am building a website with Bluefish editor and i cant figure out how to change the background color.  Can someone help?

Thanks!

---

### Post by aysiu on 2006-08-25
What are you using--just straight HTML? or CSS?

---

### Post by reacocard on 2006-08-25
here's a good site: [http://yourhtmlsource.com/](http://yourhtmlsource.com/)
it has guides for html, css, javascript, even a little cgi and ssi. very easy to understand as well.

---

### Post by Magiczero on 2006-08-25
Im using HTML

---

### Post by reacocard on 2006-08-25
add this to your <body> tag
> bgcolor="#FF0000"
that make the background red. see [here]("http://yourhtmlsource.com/accessibility/nonditheringcolours.html#BGCOLOURS") for a list of other colors and their codes.

---

### Post by Magiczero on 2006-08-25
When i do that and I reload the page this is what I get

> bgcolor="#FF0000"
Tanners Website!!

Hi and welcome to my new website!! I plan to make this a cool website

I am going to try to put new things on here everyday if I can!


---

### Post by Magiczero on 2006-08-25
When i do that and I reload the page this is what I get

> bgcolor="#FF0000"
Tanners Website!!

Hi and welcome to my new website!! I plan to make this a cool website

I am going to try to put new things on here everyday if I can!



And the page is still white

HELP!

---

### Post by aysiu on 2006-08-25
*bgcolor="#ff0000"* has to be in the <BODY> tag. You don't just put it in the middle of your text.

So you want this: ```
<html>
<head></head>
<body bgcolor="#ff0000">
Tanners Website!!
<p>
Hi and welcome to my new website!! I plan to make this a cool website
<p>
I am going to try to put new things on here everyday if I can!</body></html>
``` You **don't** want this: ```
<html>
<head></head>
<body>
bgcolor="#FF0000"
Tanners Website!!
<p>
Hi and welcome to my new website!! I plan to make this a cool website
<p>
I am going to try to put new things on here everyday if I can!</body></html>
```

---

