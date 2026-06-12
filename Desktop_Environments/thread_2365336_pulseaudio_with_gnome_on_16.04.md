---
title: "pulseaudio with gnome on 16.04"
date: 2017-07-05
forum: Desktop Environments
---

### Post by kmand on 2017-07-05
I'm running 16.04 with gnome and gdm. When I login to the desktop I get two pulseaudios, one owned by gdm the other by me. The gdm one interferes with mine. What is the right way to avoid this?

---

### Post by mc4man on 2017-07-07
Maybe take a look at this - 
[https://www.debuntu.org/how-to-disable-pulseaudio-and-sound-in-gdm/](https://www.debuntu.org/how-to-disable-pulseaudio-and-sound-in-gdm/)
and or 1st. section here under troubleshooting, "disable pulseaudio in gdm"
[https://wiki.debian.org/BluetoothUser/a2dp](https://wiki.debian.org/BluetoothUser/a2dp)

Noting that it may be gdm or gdm3 depending on what you have in 16.04 & the chown command in 2nd link wouldn't be correct for Ubuntu (chown Debian-gdm, ect.

---

### Post by kmand on 2017-07-17
Thanks. As suggested in the links, this did the trick: 

Another solution is to simply tell GDM not to use the sound. This can be done by editing /var/lib/gdm/.pulse/client.conf and add:

autospawn = no
daemon-binary = /bin/true

(its /var/lib/gdm3/.config/pulse/client.conf in gdm3)

---

