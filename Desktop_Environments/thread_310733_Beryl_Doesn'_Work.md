---
title: "Beryl Doesn' Work"
date: 2006-12-01
forum: Desktop Environments
---

### Post by Tim Sawyer on 2006-12-01
I'm trying to get Beryl to work on an amd64 nvidia machine and it's not a happy bunny.

beryl-xgl gives me a segmentation fault after saying that it has found XGL, and everytime I switch to the beryl theme is crashes (signal 11) and then uses the fall-back display manager.

I installed beryl and the nvidia drivers from:

deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main
deb [http://ubuntu.lupine.me.uk/](http://ubuntu.lupine.me.uk/) edgy lrm-amd64

Anyone got any ideas?

ta,

Tim.

---

### Post by igknighted on 2006-12-01
The first thing I would recommend is that you ditch XGL... Since you are using NVIDIA, get the latest driver (1.0.9xxx) and then install the beryl packages and boot into a normal session.  Then run 'beryl-manager' in the terminal and voile!  Beryl via AIGLX, much much simpler.

---

### Post by Tim Sawyer on 2006-12-02
Thanks for that.  How do I remove XGL?

Compiz works but I'm having trouble getting it to give me window title bars in KDE.

Tim.

---

### Post by _simon_ on 2006-12-02
To remove XGL you follow the steps you took to install it, but in reverse :)

---

### Post by Tim Sawyer on 2006-12-02
Sorted.  Removed xserver-xgl.

beryl-xgl doesn't crash now, it does this:

tjs@horus:~$ beryl-xgl
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl-xgl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl-xgl: No RandR extension
tjs@horus:~$

My /var/log/Xorg.0.log file contains 
tjs@horus:/var/log$ grep RandR Xorg.0.log
(==) RandR enabled
(==) RandR enabled
(==) RandR enabled
(==) RandR enabled

so I'm confused!

beryl-manager causes my taskbar to disappear and all the windows have no title bars!

---

