---
title: "xtightvncviewer 1.3.9-4 + ultravnc SC no display"
date: 2008-12-28
forum: General Help
---

### Post by seamuso on 2008-12-28
Worked with the previous version of xtightvncviewer (hardy 1.2.9-22), no longer works with the current 1.3.9-4 version that is installing in intrepid.

I currently am being forced to have to reboot into Vista to be able to offer the same support that I was previously able to offer from both operating systems, which leaves me less likely to be booted into linux for much of anything now.

Has anyone else run into this? Have you resolved it? if you have resolved it, what did you do?

Is my only option to have this working correctly a wipe of my system and a reversion to Hardy?

---

### Post by seamuso on 2008-12-28
Fixed by reverting to the previous version

files -
vnc-common_3.3.7-14 (get your arch)
[http://archive.ubuntu.com/ubuntu/pool/universe/v/vnc](http://archive.ubuntu.com/ubuntu/pool/universe/v/vnc)

tightvncserver_1.2.9-22 (get your arch)
xtightvncviewer_1.2.9-22 (get your arch)
[http://archive.ubuntu.com/ubuntu/pool/universe/t/tightvnc/](http://archive.ubuntu.com/ubuntu/pool/universe/t/tightvnc/)


```

sudo apt-get remove tightvncserver
sudo apt-get remove xtightvncviewer
sudo apt-get remove vnc4-common
sudo dpkg -i vnc-common_3.3.7-14_<your_arch>.deb
sudo dpkg -i tightvncserver_1.2.9-22_<your_arch>.deb
sudo dpkg -i xtightvncviewer_1.2.9-22_<your_arch>.deb

```

do this after wards to keep update manager from trying to upgrade to the 1.3.9-4 version .. [http://ubuntuforums.org/showthread.php?t=821902&highlight=disable+updates+specific+packages](http://ubuntuforums.org/showthread.php?t=821902&highlight=disable+updates+specific+packages)

Still looking for a way to get this working with the intrepid version too.

---

### Post by BelJoost on 2009-10-28
I can confirm this solves the problem in 9.04 (Jaunty) as well.

Unfortunately I couldn't find the common files at the Ubuntu repository mentioned in the post by seamuso. Fortunately they were available at Debian. Also I did not need the server package to be able to receive VNC-SC (single click) requests. 

The following script gets the packages and installs it for i386:

```

wget http://ftp.nl.debian.org/debian/pool/main/v/vnc/vnc-common_3.3.7-14_i386.deb
sudo dpkg -i vnc-common_3.3.7-14_i386.deb

wget http://archive.ubuntu.com/ubuntu/pool/universe/t/tightvnc/xtightvncviewer_1.2.9-22_i386.deb
sudo dpkg -i xtightvncviewer_1.2.9-22_i386.deb

```

You may delete the downloaded deb files after installation.

---

### Post by c0mp13371331337 on 2009-12-27
Are there any plans to fix whatever bug broke SC-VNC in the newer versions of xtightvncviewer?  I know SC-VNC is not the most widely used application, but it's essential to those that do use it to support clients/friends/family.

---

