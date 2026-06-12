---
title: "Wine Default Font"
date: 2006-06-13
forum: Desktop Environments
---

### Post by electronerdz on 2006-06-13
I am using the latest Wine, but somehow, Wine has decided to change the default font for all of its controls to some script type font. How can I tell Wine to use a different font for the default? There is no more config file, where there was a default font setting.

---

### Post by anasofiapaixao on 2006-08-14
**EDIT:** I figured it out!!! ^_^ What basically happens is that on a clean wine install the ~/.wine/drive_c/Windows/Fonts folder is totally empty, and the the first program to install additional fonts will trigger a funny behaviour...

While the folder is empty, the default font is that one we always know and hate. But when ttf fonts are copied to the folder, **wine will set as default the first copied font**! So my workaround is...

a) Rename the fonts folder to anything else and create a new one (so that the fonts folder is empty;
b) Open some random wine app (winecfg does the trick) and TADA... default serif font is back!
c) To pick up a different font as default, copy the selected one to fonts and re-open winecfg.
d) Be happy on the inside.
e) Don't forget to restore all the fonts in the renamed fonts folder to the actual one.

There must be some other way to do this, but looking at the lack of info on the topic TO HELL WITH THAT, this just WORKS!! :D

---

### Post by damoisture on 2008-02-07
Thank you so much! That is the simplest fix, and I can't believe it was this hard to find.

EDIT:

Nevermind, didn't work. Thanks though!

RE-EDIT:

Working again!

---

### Post by MunkyJunky on 2008-02-16
Found this through search, and ye haveth gone fixed my problems! Thank you!! 

Have a cookie. :)

---

### Post by chronographer on 2008-02-18
Gee thanks, this worked a treat and was sooooo simple!

---

