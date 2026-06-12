---
title: "Problem with PLplot and xwin (X11)"
date: 2008-04-06
forum: Education &amp; Science
---

### Post by m3n on 2008-04-06
Hi, guys. I seem to have a problem. 
I'm kinda new to Ubuntu and to linux in general, and I'm trying to install PLplot from the svn at their project site at sourceforge. I have also used the synaptec packages I could find. It all seems to work all well, but I can't get the xwin output to work. When I ccmake the plplot svn, It says X11_FOUND:0 and the Xwin-option cannot be set to YES. So I guess that Cmake with this svn does not recognize X11 anywhere, but why?

All comments/tips are appreciated. :)

---

### Post by vancheese on 2008-04-08
Have you installed the development packages for X11?

---

### Post by m3n on 2008-04-08
I figured out what the problem was last night after reading and trying out stuff, and it was as you say - I didnt have the xorg-dev package. So thanks for answering. It works great now :)

---

