---
title: "cool idea but how feasable is it"
date: 2006-02-23
forum: Desktop Environments
---

### Post by somuchfortheafter on 2006-02-23
Currently I have one monitor a 17" flat crt. I am looking at purchasing 1 17"lcd at a time and eventually put them together to make once desktop looking space. I just had a great idea but I do not know how it would work out. Is it possible to have one screen act as my current display(meaning that it works the way one monitor systems do) while allowing me to use the second monitor as a screen for my other system via xdmcp, then allowing me to  switch between the two by just moving my mouse to the other screen?

---

### Post by suRoot on 2006-02-23
Well I know you can bring a remote display to a second X session on your box & then access it using ctrl+alt+f8 (f12), depending upon the display number.  May be a way to do what you're asking, but this is as close as I know of.  Here are some docs that may be of help...

[http://www.linux.com/howtos/Remote-X-Apps-9.shtml](http://www.linux.com/howtos/Remote-X-Apps-9.shtml)

---

### Post by zoroko on 2006-02-23
[QUOTE=somuchfortheafter]Currently I have one monitor a 17" flat crt. I am looking at purchasing 1 17"lcd at a time and eventually put them together to make once desktop looking space. I just had a great idea but I do not know how it would work out. Is it possible to have one screen act as my current display(meaning that it works the way one monitor systems do) while allowing me to use the second monitor as a screen for my other system via xdmcp, then allowing me to  switch between the two by just moving my mouse to the other screen?[/QUOTE]



Ive seen that done with two linux boxes, and even a linux and windows box. Theres some software that does it really well, I forgot what it was called. If you find it, let us know, id like to see it myself.

---

### Post by lamego on 2006-02-23
You should be able to do it by using two different Xorg config files, one setup to use the 1st screen and another for the second. Then you start a X server for the 1st, and a X query with the second.
How to do this depends on the graphics driver you are using (I am assume your board supports dual monitors).

---

### Post by Mr_J_ on 2006-02-23
twinview?? or dual head monitors?? I admit I know nothing of what I'm talking about...
Sounds like dual head to me with some configurations in terms of what opens where...

Sorry I can't be more help.

---

### Post by somuchfortheafter on 2006-02-23
well i guess now i shall start googling

---

