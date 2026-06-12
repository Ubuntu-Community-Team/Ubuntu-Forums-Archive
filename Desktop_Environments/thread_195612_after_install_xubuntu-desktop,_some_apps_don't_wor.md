---
title: "after install xubuntu-desktop, some apps don't work anymore"
date: 2006-06-13
forum: Desktop Environments
---

### Post by hanzj on 2006-06-13
I have been running Ubuntu gnome for a long time, and I thought of trying xubuntu. So I did "sudo apt-get install xubuntu-desktop."

Then I logged on to Xubuntu session. I tried running two programs, but they no longer work. The first is X-Lite.
~$ xtensoftphone 
*** glibc detected *** free(): invalid pointer: 0x08610a80 ***
Aborted



:~$ firefox
(QFA)Talkback error: Can't initialize.
/opt/firefox/run-mozilla.sh: line 131: 21291 Segmentation fault      "$prog" ${1+"$@"}


Before installing xubuntu-desktop, they were working in Ubuntu gnome.

I logged in to the Ubuntu gnome session to see if they work.  But they don't. They give the same errors. What happened?


I re-installed X-Lite, but it didn't help. I tried changing from ALsa to OSS (right-clicking volume applet--> preferences-->change dropdown box from ALSA to OSS), but that didn't help.

---

