---
title: "wg111 monitor mode"
date: 2005-12-31
forum: General Help
---

### Post by blull on 2005-12-31
I finally was able to get my wg111v2 usb ethernet card installed.  I am trying to get the card to go into monitor mode, but when I run iwconfig wlan0 mode monitor, i get:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not permitted.

I am using the 1.7 ndiswrapper and the driver that came on my cd.  Any suggestions?

---

### Post by Lambert on 2005-12-31
ndiswrapper doesn't support monitor mode.

> No! NDIS doesn't support Master/Repeater/Monitor modes. The only modes supported are Ad-Hoc and Managed

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ](http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ)

---

