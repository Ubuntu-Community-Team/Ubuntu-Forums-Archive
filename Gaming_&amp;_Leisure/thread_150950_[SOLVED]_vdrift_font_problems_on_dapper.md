---
title: "[SOLVED] vdrift font problems on dapper"
date: 2006-03-27
forum: Gaming &amp; Leisure
---

### Post by arnieboy on 2006-03-27
I installed the vdrift ubuntu debs and fired it up on Dapper but as one can see from the screenshot, the fonts are not visible. There is nothing informative in the terminal debug messages (even in verbose mode it shows no errors) and the ~/.vdrift/logs/fonts file is empty.
Any idea which package am missing here?
I tried installing the libsdl-ttf2 package but it did not help.
Any kind of help would be much appreciated.

---

### Post by Perfect Storm on 2006-03-27
Hmmm...under depency it says: libsdl, libsdl-image, libsdl-net, libopenal, OpenGL libs. [http://vdrift.net/staticpages/index.php/INSTALL](http://vdrift.net/staticpages/index.php/INSTALL)

Perhaps there either a bug in Dapper or in the game.

---

### Post by dimatrod on 2006-07-26
It seems it's a problem with XGL.  Try running "nonXgl vdrift" and see what happens

---

