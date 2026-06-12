---
title: "Doom3 installer fails!"
date: 2006-10-22
forum: Gaming &amp; Leisure
---

### Post by horgh on 2006-10-22
I downloaded installer for doom3, I run it and get this:

root@horgh-desktop:/home/horgh# sh doom3-linux-1.3.1302.x86.run 
Verifying archive integrity... All good.
Uncompressing DOOM III............................................................................................
./setup.sh: 279: /root/.setup3335: not found
./setup.sh: 290: /root/.setup3335: not found

No matter if I run it as root or normal user? I googled, but it seems that no-one has ever had this problem? So could anyone help me?

---

### Post by Episteme on 2006-10-22
Just finished having this problem myself... I had to install the dev files that go with libc, and that seemed to do it. I don remember exactly which file it is that did it... but here's my package history from that session.

(I just searched for libc6 on my Edgy system and clicked on any dev file that appeared logical to me)

Hope it helps.

Commit Log for Sun Oct 22 11:32:51 2006


Installed the following packages:
lib32gcc1 (1:4.1.1-13ubuntu5)
libc6-dev (2.4-1ubuntu12)
libc6-dev-i386 (2.4-1ubuntu12)
libc6-i386 (2.4-1ubuntu12)
linux-libc-dev (2.6.17-10.33)
libice-dev (2:1.0.1-1ubuntu1)
libsm-dev (2:1.0.1-1ubuntu1)
libx11-dev (2:1.0.3-0ubuntu4)
libxau-dev (1:1.0.1-1)
libxdmcp-dev (1:1.0.1-1)
libxext-dev (2:1.0.1-1ubuntu1)
libxi-dev (2:1.0.1-0ubuntu1)
libxmu-dev (2:1.0.2-1ubuntu1)
libxmu-headers (2:1.0.2-1ubuntu1)
libxmuu-dev (2:1.0.2-1ubuntu1)
libxpm-dev (1:3.5.5-1)
libxrandr-dev (2:1.1.1-0ubuntu1)
libxt-dev (1:1.0.2-1ubuntu1)
libxtrap-dev (2:1.0.0-3build1)
libxtst-dev (2:1.0.1-3build1)
libxv-dev (2:1.0.1-3ubuntu1)
x-dev (7.0.7-1)
x11proto-core-dev (7.0.7-1)
x11proto-input-dev (1.3.2-3ubuntu1)
x11proto-kb-dev (1.0.3-0ubuntu1)
x11proto-randr-dev (1.1.2-3ubuntu1)
x11proto-record-dev (1.13.2-3ubuntu1)
x11proto-trap-dev (3.4.3-3ubuntu1)
x11proto-video-dev (2.2.2-3ubuntu1)
x11proto-xext-dev (7.0.2-4ubuntu1)
xlibs-dev (1:7.1.1ubuntu6)
xtrans-dev (1.0.1-1)
zlib1g-dev (1:1.2.3-13ubuntu2)

---

### Post by horgh on 2006-10-23
Thanks! That did the trick, actually I only had to install libc6-i386, lib32gcc1 and libc6-dev-i386. :)

---

