---
title: "Bad performance on ATI 9600 XT with Xgl"
date: 2006-10-12
forum: Desktop Environments
---

### Post by Saubazi on 2006-10-12
I got Xgl running by following several howtos but I am having a problem
which I thought I saw in place or two. Well firstly it starts slow but then 
when I for example open firebird it messes up the screen and opens extremely slow - typing and so on gets slow.

Same if I now try to shutdown or so the buttons hibernate and shutdown have disappeared - is there a remedy for this?

---

### Post by Happydude123 on 2006-10-12
I am also having a problem similar to this!

I have a 9200.

My mouse and the little gnome splash load liek normal but when I open other programs like firefox or a terminal It feels like I am watching a slideshow.

---

### Post by igknighted on 2006-10-12
Do both of you have an advanced window manager (i.e. compiz/beryl) running?  Xgl is only a framework (like X.org) for which to run a window manager (like KDM) over.  It is beryl/compiz that provide the performance and eye-candy, until you install one of these and configure it, the system will run as you describe it under Xgl.

---

### Post by Saubazi on 2006-10-13
Yes, I do but I did not actually test it since I was so focused on this Xgl problem. I'll give it a go and report back.

---

### Post by Saubazi on 2006-10-13
Ok, it is no better really - I started with:
compiz --indirect-rendering --strict-binding --replace

EDIT: found out that gconf does not work anymore - instead I tried:
compiz --indirect-rendering --strict-binding --replace dbus csm

result is better but windows don't have handles at all and starting firefox still resembles a slideshow

---

