---
title: "How do i get another OS that is installed on my computer on another side of the cube?"
date: 2010-07-09
forum: Desktop Environments
---

### Post by brann22 on 2010-07-09
Ok, well, I've been playing around with the cube in CCSM and I've seen some videos on youtube that have windows XP on one side of the cube and on the other three sides, it still has Ubuntu. I was wondering how i would do that? If it makes a difference, I wanted to do that with Vista instead of XP.

---

### Post by Yarui on 2010-07-09
I would imagine they are running the OS in a virtual machine.  If the entire side of the cube is the other OS they are probably putting the virtual machine in fullscreen mode.

---

### Post by renfrew on 2010-07-09
Based on what you're saying it sounds like the youtube videos are of XP running in a virtualbox or vmware session, running full screen on one of Compiz's workspaces.  Virtualbox and vmware are two of a number of applications that let you run another os in a windowed or full screen session as if it were the native OS on your machine.  Collectively they are called virtual machines.  I don't use a virtual machine on my system but if you google virtualbox or vmware you'll find many tutorials on how to install/configure it on your machine.  It doesn't matter if it's XP or Vista or '98 or, gasp!!, ME, there are ways to run any version of Windows(tm) in a Virtual Machine.  Virtualbox is in the repositories btw... you can check by running `apt-cache search virtualbox` from the comamnd-line (minus the quotes).

---

### Post by QIII on 2010-07-09
Something implicit in the posts above that may not be obvious to you is that the video you are seeing does not represent a multi-boot system with both OSs running simultaneously.

---

### Post by Yarui on 2010-07-09
> **QIII said:**
> Something implicit in the posts above that may not be obvious to you is that the video you are seeing does not represent a multi-boot system with both OSs running simultaneously.
Good point, I had forgotten by the time I started responding that the original poster had said that.

---

