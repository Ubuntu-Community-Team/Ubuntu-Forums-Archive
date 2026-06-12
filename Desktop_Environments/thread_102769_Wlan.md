---
title: "Wlan"
date: 2005-12-12
forum: Desktop Environments
---

### Post by satbunny on 2005-12-12
I need to be able to scan for WiFi networks, to find the SSID. How do I do this? Is there an application in Ubuntu or do I need to install something.

---

### Post by gw90se on 2005-12-12
Open Synaptic and do a search for "wireless". You might find what you need.

---

### Post by stevea1210 on 2005-12-12
If the network is broadcasting the essid, you can find it via

```
iwlist ath0 scan
```

Of course replace ath0 with the name of your wireless nic.  

you may get this message after the command:
Interface doesn't support scanning.

If you get that, then your card / driver doesn't support scanning, and you'll have to look elsewhere.  I got that message when I was using ndiswrapper with a Linksys card.  I now have a Netgear and a Belkin card, both of which had drivers out of the box, both of which can scan.

If you're trying to grab the essid of networks that aren't broadcasting, the above won't help.  Sorry.

---

### Post by soulestream on 2005-12-13
wifi-radar

soule

---

