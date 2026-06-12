---
title: "Vnc"
date: 2006-01-04
forum: Desktop Environments
---

### Post by lost1234 on 2006-01-04
I am unable to get vnc working, I have installed itbut if i type vncpasswd it says vncpasswd: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

If I type vncserver :1 it says 
New 'linuxu:1 (root)' desktop is linuxu:1

Starting applications specified in /root/.vnc/xstartup
Log file is /root/.vnc/linuxu:1.log

I check ps aux and it is not there
at least that I can tell.

please help me

---

### Post by zoiks on 2006-01-05
1) Though I haven't tried vncserver with ubuntu per se, I haven't in the past needed to enter vncpasswd before running vncserver.  The first time I ran vncserver it asked me for a password to use.

2) It looks like you have vncserver running.  "vncserver" I believe is just a wrapper for starting another program called xvnc, so you can check for that process instead.  You can confirm this by entering "vncserver -kill :1" and confirming the kill.  Or try logging in now from a different computer using vncviewer.

3) Probably not a good idea to run vncserver as root.  It should work fine as a regular user.

---

### Post by ajaym on 2006-01-11
FWIW I have EXACTLY the same problem and have so far been unable to resolve it. Even going to realvnc and downloading latest VNC didn't help. My machine is a Sempron 2800 with 64 bit extensions but I am NOT using the AMD64 kernel or anything (this is apparently implicated in some way for other people having VNC problems).

I tried symlinking the libc++ libs I have (6.0.5) but get an unresolved reference. But I can't locate a 6.2.2 version of these libs at all. Anyone out there with advice?

---

