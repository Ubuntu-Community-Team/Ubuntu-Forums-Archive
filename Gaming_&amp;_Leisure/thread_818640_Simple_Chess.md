---
title: "Simple Chess"
date: 2008-06-04
forum: Gaming &amp; Leisure
---

### Post by Vrekk on 2008-06-04
Hey i was playing chess, the one that comes with ubuntu, and nocited that there is a 3d chess setting.  But when i try to enable it, i get this error 
You are unable to play in 3D mode due to the following problems:
No Python OpenGL support
No Python GTKGLExt support

Please contact your system administrator to resolve these problems, until then you will be able to play chess in 2D mode.
can any one help, i know my video card can handle it

---

### Post by Perfect Storm on 2008-06-05
Try with;
```
sudo apt-get install python-opengl python-gtkglext1
```

---

### Post by Vrekk on 2008-06-05
thanks

---

### Post by Keith Fox on 2009-06-15
I have installed 3 required packages one of them was what you requested.  I can't remember the other two off the top of my head.  I'm running Linux Mint Gloria and was playing this basic chess game, tried to play in 3d and it told me to install those 3 packages so i did that.  Now it crashes when I try to open the game, instantly.  Is this something I'm doing wrong or a programming problem?  How can I report this to Linux?

---

