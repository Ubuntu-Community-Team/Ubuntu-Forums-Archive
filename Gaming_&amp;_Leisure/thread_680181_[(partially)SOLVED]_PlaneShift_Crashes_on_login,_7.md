---
title: "[(partially)SOLVED] PlaneShift Crashes on login, 7.10 Gutsy on 1420n"
date: 2008-01-27
forum: Gaming &amp; Leisure
---

### Post by supermikey on 2008-01-27
On the RPG PlaneShift if you are having a crash on login problem with 7.10 or have a dell 1420n, try this solution:

[http://hydlaa.com/smf/index.php?topic=31373.0](http://hydlaa.com/smf/index.php?topic=31373.0)

[http://hydlaa.com/smf/index.php?topic=31133.0](http://hydlaa.com/smf/index.php?topic=31133.0)

Make sure you have libcal3d12 installed as well as the xserver-xorg-video driver that is appropriate (intel for 1420n, NOT i810). Install fglrx.

Code

 sudo apt-get install xorg-driver-fglrx

In the ./pssetup select VGA texture buffering to ON.

Do NOT install to /opt, instead do something on your /home.
(chmod wont run on /opt it'll say you don't have permission, it's just harder to troubleshoot there)

If any anyone has a solution for the overheating my laptop just about does, I'm all ears.

Does anyone else have any ideas or tricks to get it to run?

Most of the people with crash errors on the PlaneShift website are Ubuntu Gutsy Users. I wonder if that's because there more of us, or if Gutsy is missing some stuff (as some of the Gentoo/OpenSUSE/Linspire fanboys so condescendingly accused on the threads there)?

---

### Post by dtgolder on 2008-03-08
I installed it to /opt, but had to put a symbolic link to there from my home directory:

ln -s /opt ./opt

---

