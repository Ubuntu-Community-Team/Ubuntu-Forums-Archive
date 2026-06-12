---
title: "Xserver messed up after editing xorg"
date: 2007-01-29
forum: Desktop Environments
---

### Post by cgrado on 2007-01-29
So I tried to edit the xorg file to make my G7 work ([http://ubuntuforums.org/showthread.php?t=125752](http://ubuntuforums.org/showthread.php?t=125752))  and i logged out, then nothing happened. i got a blank screen and something said the xserver was messed up. so i'm stuck with a command line.

How can i make it normal again???

---

### Post by meng on 2007-01-29
Did you back up your xorg.conf file before editing? If so, restorethe old file with
sudo mv /etc/X11/xorg.conf~ /etc/X11/xorg.conf
(assuming the name of your backup file is xorg.conf~)

Otherwise:
sudo dpkg-reconfigure xserver-xorg

---

### Post by cgrado on 2007-01-29
Alright thanks, i'll give it a go.

all fixed. thanks!

---

