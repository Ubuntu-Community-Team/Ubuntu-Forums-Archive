---
title: "Firefox and dark Gtk (CSS)"
date: 2008-02-26
forum: Desktop Effects &amp; Customization
---

### Post by catfacts on 2008-02-26
I have a dark gtk and really like it, but is messes up firefox so much I have been forced to not use it, I was wondering, i found /home/user/.mozilla/<jhpe.jasdk>/chrome/userContent.css which should override my gtk. But I used 
```
input {
    background-color: #FFF;
    color: #000 ;
}

* {
    color: #000;
    background: #FFF;
}
```
and it overode everything! Like background images and such. I thought that it would only do that if I had !important in the css statement. This may be more CSS related but any help on how to make FF not listen to my GTK would be great!

---

### Post by Islington on 2008-02-26
this wont be a great reply since I dont have the wxact links, however on gnomelook.org there are several "fixes" you may want to take a look at those. They are of course userconentt.css etc...

Below is my usercontent 
```

input {
	border: 2px inset white;
	background-color: white;
	color: black;
}

textarea {
	border: 2px inset white;
	background-color: white;
	color: black;
}

select {
	border: 2px inset white;
	background-color: white;
	color: black;
}
 
input[type="radio"],
input[type="checkbox"] {
	border: 2px inset white ! important;
	background-color: white ! important;
	color: ThreeDFace ! important;
}

*|*::-moz-radio {
	background-color: white;
}

button, 
input[type="reset"],
input[type="button"],
input[type="submit"] { 
	border: 2px outset white;
	background-color: #eeeeee;
	color: black;
}

body {
	background-color: white;
	color: black;
	display: block;
	margin: 8px;
}
```

---

### Post by catfacts on 2008-02-27
Thanks a million, that fixed it perfectally!!! now any hints on gaim/pidgeon.. :P jk, it isnt mozilla based so no userContent.css

---

### Post by catfacts on 2008-03-03
So, now is there anyway to fix Open Office. When your window background gets so dark, the icons go away and are replaced by text, pushing them off the screen, a fix would be great.... and also I really would like a fix for pidgen, because sometimes the same problem that i initially had with firefox happens with IMs

---

### Post by Islington on 2008-03-05
> **catfacts said:**
> So, now is there anyway to fix Open Office. When your window background gets so dark, the icons go away and are replaced by text, pushing them off the screen, a fix would be great.... and also I really would like a fix for pidgen, because sometimes the same problem that i initially had with firefox happens with IMs

OpenOffice is a bit of an ***, about fixing it, tools>options>view play around with the icon settings change them from automatic to something else?

not sure about pidgin..

---

### Post by catfacts on 2008-03-06
Thanks a bunch, i had to switch to human icon set, which looks good with my gtk, after i get over the inverted colors :P

Come on guys, pidgin and im set :P

---

### Post by joshuachad on 2008-03-06
Create a new file called .gtkrc-2.0 in your ~/.purple directory

Remember google is your friend. Took me 11.3 seconds to find this and 5.1 seconds of that was actual page loading time. Also for the firefox thing you can fix that most time in the menu with a couple button clicks as opposed to custom user content files. Edit -> Prefences -> content tab(Hence the usercontent file) ->colors. Just uncheck use system setting and or choose your own.
------------
style "purplerc_style"
{
    GtkIMHtml::hyperlink-color = "#33CCFF"
}
widget_class "*" style "purplerc_style"

style "Custom"
{   
    base[NORMAL] = "#292B29"
}
class "GtkWidget" style "Custom"> 

---

