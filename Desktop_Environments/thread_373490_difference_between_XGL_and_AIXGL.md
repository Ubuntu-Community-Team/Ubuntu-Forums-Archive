---
title: "difference between XGL and AIXGL"
date: 2007-03-01
forum: Desktop Environments
---

### Post by The_k3rnel on 2007-03-01
Hello all,

I got Beryl working yesterday on Ub 6.10. 

All very very nice and apart from the odd crash, which I was expecting due to it being in development, it's great. One query though: I don't seem to have any borders on my windows like I did under Gnome. This is annoying because I can't figure out how to minise them!

I notice under one of the menus on the beryl manager that I have a choice of using either automatic, Nvidia, gxl or aiglx. Clearly auto is obvious, but could someone please explain what the rest mean? I'm guessing that nvidia will use my graphics card direct as opposed to the other options which are software acceleration (are they!?!) 

Cheers

---

### Post by wataboutbob on 2007-03-01
Hi,

Had the same issue. Corrected it after changing DefaultDepth to 24 and restarting. you might want to read through the How To thread for beryl.

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Towards the end of the thread, there have been a couple of people who have had the same issue which was solved by changing the defaultdepth. Give it a shot. It worked for me.

As far as the difference between AIglx and XGL... don't have a clue. Sorry.

EDIT: included beryl thread.

---

