---
title: "hal daemon problem"
date: 2006-12-20
forum: Desktop Environments
---

### Post by Ubsl on 2006-12-20
Hi,

following problem: I use xubuntu 6.10 with the laptop Dell XPS m1210.  If I haven't plugged in my card reader (hama USB 2.0 Card Reader 19 in 1), I can't see the icons for this device and for the cd-rom. Mounting the card reader manually and cdrom works fine. I have done a search in the Internet for this kind of problem but it seams there are many people having similar problems. I have tried to run the command  ```
lshal
``` from the terminal but it says ```
Could not initialize connection to hald...
``` Obviously the hald daemon doesn't runs. If I start with ```
sudo hald
``` the hal daemon manually and log off and in. The icons of the plugged in card reader and cdrom is shown on the xfce desktop. Whats going wrong here?

Note that, if I have plugged in the card reader at the boot process the hal daemon is loaded properly and the icons for the card reader / cdroms appears.

Cheers,
Ubsl

---

