---
title: "Unable to connect to webcam after modprobe ueagle-atm"
date: 2008-11-11
forum: Desktop Environments
---

### Post by lores on 2008-11-11
Hi, all!

I've just run into an issue with Ubu, more precisely - Xubuntu 8.04. I'm connecting to the Inet via an USB ADSL modem with ueagle-atm.

Whenever I modprobe ueagle-atm (preferably during the boot-time), I am unable to connect to /dev/video0, which is a still existent entry of my webcam (working o-o-t-box without ueagle).

Whenever I either disconnect the modem or rmmod ueagle-atm, I can use the cam again. Besides, other mods' states don't change when I modprobe ueagle-atm, i. e. all other mods remain inserted, e. g. gspca and zc, which are necessary for the cam.

How can I use them both simultaneously for vid-calls?

---

