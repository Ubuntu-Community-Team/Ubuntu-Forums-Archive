---
title: "strange wifi problems, broadcom 4727 works then stops"
date: 2011-01-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by thesupergame on 2011-01-11
I have a broadcom 4727 network device. 'rfkill list' says that it is soft enabled but not hard enabled, and nm-applet will not connect to anything over wireless because the "enable wireless" button is permanently grayed out.

I have tried using the fn-f2 function call to turn the wireless card on, but it switches the soft enabled part on or off. I have checked the bios and it definitely is controlling the internal wlan properly.

'sudo lshw -C network' confirms that the card is not disabled.

Interestingly enough, 'sudo iwlist eth1 scan' lists the available wireless networks properly, and the program Wifi Radar detects them too. Also, networking used to work, then, after a long time of using windows 7 (ubuntu is a wubi install), the wireless does not work anymore.

I have tried reinstalling the drivers, 'sudo ifconfig eth1 up', ifup, etc, and nothing works. I have rebooted many times, in combination with many of the things mentioned - it does not help.

modifying the /etc/modules file to add "wl" and has no effect. My computer is fully updated (and is a wubi install)

any advice is appreciated, thanks

---

