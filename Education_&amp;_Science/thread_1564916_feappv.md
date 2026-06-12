---
title: "feappv"
date: 2010-08-31
forum: Education &amp; Science
---

### Post by mautho07 on 2010-08-31
Hello,
I'm very new with Ubuntu and Linux.
Now I wanted to install "feappv" which I need for university.
You can download it at [http://www.ce.berkeley.edu/projects/feap/feappv/](http://www.ce.berkeley.edu/projects/feap/feappv/)

At the makefile.in there is a line which I don't know what I have to plug in:

# What options to be used by the loader
LDOPTIONS = -L/usr/X11R6/lib -lX11 -lm

I think this is the reason why there is a error when making the archive.

I'm really a beginner in Linux, but I hope anybody can help me with this.
Oh, I'm using Ubuntu 10.04!

Mautho

---

### Post by lordhaworth on 2010-08-31
Hi,

Can you show us what the error message is that you are getting?

---

### Post by mautho07 on 2010-08-31
...
...
x11u.c:1314: error: ‘DIGWin’ has no member named ‘x_scale’
x11u.c:1314: error: ‘DIGWin’ has no member named ‘x_offset’
x11u.c:1315: error: ‘DIGWin’ has no member named ‘current_y’
x11u.c:1315: error: ‘DIGWin’ has no member named ‘y_len’
x11u.c:1315: error: ‘DIGWin’ has no member named ‘y_scale’
x11u.c:1315: error: ‘DIGWin’ has no member named ‘y_offset’
x11u.c:1316: error: ‘DIGWin’ has no member named ‘current_x’
x11u.c:1316: error: ‘DIGWin’ has no member named ‘current_y’
x11u.c:1318: error: ‘DIGWin’ has no member named ‘x_scale’
x11u.c:1318: error: ‘DIGWin’ has no member named ‘x_offset’
x11u.c:1319: error: ‘DIGWin’ has no member named ‘y_len’
x11u.c:1319: error: ‘DIGWin’ has no member named ‘y_scale’
x11u.c:1319: error: ‘DIGWin’ has no member named ‘y_offset’
make[2]: *** [/home/.../Dokumente/feappv/ver22/Feappv.a(x11u.o)] Fehler 1

---

### Post by mautho07 on 2010-09-17
Does nobody now what this error-message is? Or which directory it is I have to type in as LDOPTIONS?

---

### Post by Krolist on 2011-07-19
Does feappv work without X11?

---

