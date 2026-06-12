---
title: "Latest updates stuffed cdrw/dvdrw and Xorg in Kubuntu"
date: 2006-07-20
forum: Desktop Environments
---

### Post by master_b on 2006-07-20
Have 2 pcs running Kubuntu Dapper.

Latest updates have stuffed up both pcs in different ways.

1 pc has GForce 440mx - no longer loads KDE - ran sudo dpkg-reconfigure xserver-xorg but doesn't fix it. NO graphical mode at all.

2nd PC now has problems with DVDRW (dual layer) LG ( 2610b I think).

can't see dvd-r's. Changed /etc/fstab for cdrom0 to dvd and suid to nosuid but still have problems

Help please. Until now Kubuntu Dapper has been problem free.

Bill

---

### Post by OU812 on 2006-07-20
Do you mean that you start in text mode? If so, enter startx at the prompt. If this gets kde up and running, then do sudo gedit /etc/inittab.conf (I think). Look for something about runlevels. Change the 3 to 4. Next reboot should be in graphics mode.

As for the dvd - I don't know. But changing /dev/cdrom0 to /dev/dvd won't help. It's still /dev/hdc to linux - the master device on your secondary ide cable. Do you have the latest firmware installed on that device?

john

---

### Post by master_b on 2006-07-24
Thanks for the reply John.

The DVD problem somehow solved itself - seems to take longer to automount than on other pcs.

As for problem with xorg.conf, just put brain in gear and renamed the auto-backup copy - now it works - is set to "vesa".

Bill

---

