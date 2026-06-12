---
title: "Odd gray screen upon XGL startup"
date: 2007-04-24
forum: Desktop Effects &amp; Customization
---

### Post by Mr Greencastle on 2007-04-24
Hi, I have Beryl under Xgl on my ATI xpress 1100, everything works perfectly.
However, when starting Xgl, which is my regular login I get an odd grayish screen, and my cursor is a large black ''x''.

It quickly changes from this to my regular desktop, and everything is perfect. It bothers me that it does this as it is ugly, and that was why I installed Beryl in the first place, for the eye candy.

Any help would be greatly appreciated!

---

### Post by kbzona on 2007-04-24
If you dont want to see the ugly gray pattern you must add "-br" option to the xgl session
ie. startxgl.sh

where it says something like this at the beginning.... notice that i added -br  just next to -ac

Xgl :1 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer &

---

### Post by Mr Greencastle on 2007-04-24
Yep, that worked, thanks!
This is why the Linux community is kickass!

---

### Post by Obnesence on 2007-04-24
Thanks this solved my problem too.  However, now when I try to start beryl it fails and the menu bar disappears.  And windows lose their edges and are unmovable.  Any thoughts?

---

