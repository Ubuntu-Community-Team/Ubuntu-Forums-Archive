---
title: "[SOLVED] Gnome is dead..."
date: 2008-08-04
forum: Desktop Environments
---

### Post by Thesuperchang on 2008-08-04
Gnome is dead... I think. So I was trying to watch some anime when my PC decided that it wouldn't output any volume in my right ear head phone. I reluctantly booted up into Vista where both head phones gave out sound. A few hours later I browsed the forum looking for a solution, I uninstalled the sound drivers (alsa I think and reinstalled.) unfortunately now gnome doesn't start up anymore, I only have command line. I tried the command,
sudo apt-get isntall gdm ubuntu-desktop
However, is does not find all packages... My current Ubuntu version is 32-bit hardy herron. Would anyone have any advice. If possible, I would like to install from CD, as my ISP are a bunch of tight ***'s.

Thanks in advance,
C. Anderson.

---

### Post by scottuss on 2008-08-04
How did you remove the drivers and what happens if you type startx on the console?

---

### Post by Thesuperchang on 2008-08-04
> **scottuss said:**
> How did you remove the drivers and what happens if you type startx on the console?

I'm currently looking for the thread that I got the instructions form. It was a huge audio trouble shooting thread.

---

### Post by Thesuperchang on 2008-08-04
The guide I used to rectify my sound problem is located here:
> [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Fortunately, when I type startx after logging in, Gnome starts itself up. On the guide I followed, it asked me to reinstall ubuntu-desktop which I have tried doing but to no  luck. To try to reinstall I open up terminal and type:
> sudo apt-get install gdm ubuntu-desktop
but it does not install. Below I have pasted a log of the processes that go on.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  visualboyadvance libfltk1.1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fast-user-switch-applet
Suggested packages:
  xnest uswsusp
Recommended packages:
  gdm-themes
The following NEW packages will be installed:
  fast-user-switch-applet gdm ubuntu-desktop
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1891kB/2227kB of archives.
After this operation, 19.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main gdm 2.20.6-0ubuntu2
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.20.6-0ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.20.6-0ubuntu2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

The sad thing about this situation is that my sound issue was not rectified. Ubuntu is still outputting mono only.:(

Thanks in advance,
C. Anderson

---

### Post by Vadi on 2008-08-04
Can you please go to System - Administration - Software Sources, and select "Main Server" as your mirror. Then try the "sudo apt-get install gdm ubuntu-desktop" command again.

---

### Post by Thesuperchang on 2008-08-05
Problem resolved. Thank you very much.

---

### Post by Vadi on 2008-08-05
You're welcome! Please click on 'Thread Tools' and 'Mark as solved' :)

---

