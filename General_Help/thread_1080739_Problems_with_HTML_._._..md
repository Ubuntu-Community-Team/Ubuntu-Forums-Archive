---
title: "Problems with HTML . . ."
date: 2009-02-25
forum: General Help
---

### Post by noseforsharpies on 2009-02-25
Hello, everyone. I'm new to the Ubuntu forums ( and to Ubuntu
itself ), and I had some questions. I've just started learning HTML from a guide, and I'm already tripping up. This is the HTML document I'm trying to tinker with:

<html>
<head>
<title>My first HTML document</title>
</head>
<body>
<h2>My first HTML document</h2>
Hello, <i>World Wide Web!</i>
<p>
Greetings from<br>
<a href=”http://www.ora.com”>O'Reilly & Associates</a>
<p>
Composed with care by:
<cite>Derek</cite>
<br>&copy;2000 and beyond
</body>
</html>

Hopefully it formats correctly. Anyway, I've been saving it as a '.html' file, opening that file with Firefox, and all I get is a page with the actual code on it . . . not what it's supposed to be. So someone tell me how stupid I am and what I'm doing wrong. Thanks, guys.

Peace,
Derek.

---

### Post by ja660k on 2009-02-25
in terminal
sudo mv yourHTMLDoc.html /var/www/index.html

then in firefox type in localhost
and enter

hopefully that'll work

---

### Post by dkulchenko on 2009-02-25
ja660k, there is absolutely no point in using a web server to open HTML documents. They open fine without one.

noseforsharpies, could you please post a screenshot? Go to the page in Firefox where it gives the not working code, and press the Print Screen (or PrtScr) button on your keyboard (it should be right above Insert). Save it somewhere on your computer and attach it here.

---

### Post by simeon87 on 2009-02-25
What editor are you using? Perhaps it's saving with a weird character encoding or with weird characters.. because pasting that in gedit and saving (extention and location don't matter) should work for Firefox.

---

### Post by bodhi.zazen on 2009-02-25
Your code works as is in firefox for me.

I saved it a a file "test.html" (without quotes) on my desktop, right click -> open with firefox

The url is : 

```
file:///home/user/Desktop/test.html
```

---

### Post by mb_webguy on 2009-02-25
> **ja660k said:**
> in terminal
sudo mv yourHTMLDoc.html /var/www/index.html

then in firefox type in localhost
and enter

hopefully that'll work

Not if he doesn't have Apache installed, it won't.

If your html file formatted correctly, it should open in your web browser without doing anything special.  I copied your text into a file called test.html, opened it in Firefox, and it worked just fine.  (Though that's technically not a well-formatted html document, I'll forgive you since you're just starting out. ;))

EDIT:  CRAP!!! Ninja'd by THREE people?!?   Well, at least one of them was Bodhi...  ;)

---

### Post by bodhi.zazen on 2009-02-25
Oh thank god I beat out mb_webguy ( J/K :lolflag: )

---

### Post by noseforsharpies on 2009-02-25
What editor should I be using? I'm using OpenOffice, mostly because I assumed it would work . . . the same code worked for someone else, apparently, so I'm not sure what the deal is.

---

### Post by noseforsharpies on 2009-02-25
Here's a screenshot, if I can work it right.

---

### Post by simeon87 on 2009-02-25
> **noseforsharpies said:**
> What editor should I be using? I'm using OpenOffice, mostly because I assumed it would work . . . the same code worked for someone else, apparently, so I'm not sure what the deal is.

Ok, indeed it doesn't work through OOo. You should be using an editor has allows you to save the HTML and nothing more. You could try gedit for a start, see Applications > Accessories > Text Editor. Simply paste the code in there and save it as a .html file. Then it'll work in Firefox.

---

### Post by bodhi.zazen on 2009-02-25
Try either saving the file as a text file or copy-paste that code into gedit, then save it as test.html

My guess is OOO is saving your file with <XML> (which is I believe the default behavior).

Try opening the file with gedit, you will see the extra code.

---

### Post by noseforsharpies on 2009-02-25
Oh, hell. I used gedit and it worked perfectly. Heh . . . Thanks for the help, guys. I didn't see an option to save it as '.html' in gedit, so I figured it wouldn't work right. Thanks, again! And remember, I just recovered from twenty-one years of Vista.

---

### Post by bodhi.zazen on 2009-02-25
Beat by simeon87 :(

---

### Post by mb_webguy on 2009-02-25
> **bodhi.zazen said:**
> Beat by simeon87 :(

I guess we're getting slow in our old age.  ;)

---

### Post by Iowan on 2009-02-25
> **noseforsharpies said:**
> What editor should I be using? I'm using OpenOffice, mostly because I assumed it would work . . . the same code worked for someone else, apparently, so I'm not sure what the deal is.May have TOO much app for the job.  Most of the HTML books I've been reading lately suggest  NOT using an editor such as Word (OOo is probably in the same boat) because the formatting gets in the way.  They recommend Notepad (**gedit** or **nano** by comparison) for editing.

I got outtyped, too... at least I'm in good company.
I didn't realize that Vista had been around for 21 years...
I should quit while I can.

---

### Post by dkulchenko on 2009-02-25
Wow... This must be a new record. A thread solved in 23 minutes, with 15 posts. :)

---

