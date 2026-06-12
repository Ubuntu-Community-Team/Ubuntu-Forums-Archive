---
title: "Screen Stuck In Zoom Or Magnification"
date: 2017-04-15
forum: Desktop Environments
---

### Post by epringi on 2017-04-15
My son mashed my keyboard and now it's stuck in zoom mode.  I've tried [super-key / windows key]+everything, no dice.  I've googled my face off and can't find out what he did. :P  Hoping someone can help!

Thanks!

---

### Post by RobGoss on 2017-04-16
Did you try another keyboard that may be the easiest fix if the keyboard is damaged ?

---

### Post by Frogs Hair on 2017-04-16
You might try Ctrl  + [-] key . Check if you have enabled any tools such as Kmag also.

---

### Post by epringi on 2017-04-17
I figured it out.  Mostly.  No key combination worked though, which they should have, according to my research.

In ~/.kde/share/config/kwinrc there was this line:
[FONT=courier new]
[Effect-Zoom]
InitialZoom=1.2

[/FONT]I just removed the ".2" from the file.

I hope this helps anyone else experiencing this.  If you don't have KDE, maybe at least grepping your home dir for some incarnation of zoom or magnification will turn something up.

---

### Post by epringi on 2017-04-17
The keys are used with other things, so I knew they were at least operational. ;)

I did however check for kmag and it was disabled.

---

