---
title: "ET: Sound but no video FIX!!!!"
date: 2005-11-24
forum: Gaming &amp; Leisure
---

### Post by Buddy DarDar on 2005-11-24
It's pretty simple, actually.  If you have you copy of ET freeze after the intro screen with an ATI card, it may be the ATI video drivers to blame.  If you installed the ATI drivers from the ATI website, follow these steps: 

1) uninstall ATI driver
"sudo apt-get remove xorg-driver-fglrx"

2) follow the steps here:
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

And that's really all these is to it.  Good luck, see you online!

---

