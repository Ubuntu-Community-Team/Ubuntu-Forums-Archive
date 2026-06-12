---
title: "X and/or Gnome won't start and boots to tty1"
date: 2009-09-23
forum: Desktop Environments
---

### Post by hakko on 2009-09-23
Hi

I' tried to get dual monitor working on Ub 8.10. via my onboard intel graphics (VGA and DVI ports)  Then I got an Nvidia Quadro NVS290 with two VGA.  I now wanted QUAD monitor setup but driver installs failed.  Tried to go back to intel setup removing Nvidia card and setting onboard graphics only in the bios, but still no gnome/X.

When I boot up the PC it goes to tty1 and says normal boot, after resume image is not found - which is ok from what I read.

I log in as root and try starting gdm, it says already started.

If I do startx it says :
```
Saw signal 11.  Server aborting.
giving up.
xinit: Connection refused (errno 111):  unable to connect to X server
xinit: No such process (errno 3): Server error.

```

I was hoping for a system restore facility a la XP, but it turns out there is no actual "rescue" mode on the Ubuntu CD.

I have Ubuntu 8.10 64bit.

I've searched up the erros I've found and so far have:
resintalled xserver-xorg, ubuntu-desktop, restored xorg.conf files. After restarting it would go back to "tty1... resume image not found, normal boot, etc."

---

### Post by hakko on 2009-09-24
Help!:confused:

---

### Post by hakko on 2009-09-24
Aha, I see a line on startup:
* nvidia (180.11)  [fail]

I thought I did an ap-get remove xserver-xorg-video-nvidia*

---

### Post by hakko on 2009-10-06
In the end I put the quadro card back in. Flipped between nvidia 180 and 185 drivers until got back to my original 2 screen setup.

---

