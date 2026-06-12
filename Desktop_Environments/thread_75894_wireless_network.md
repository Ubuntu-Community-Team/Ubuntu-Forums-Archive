---
title: "wireless network"
date: 2005-10-14
forum: Desktop Environments
---

### Post by acrobat on 2005-10-14
my system (ubuntu 5.10) detects my wireless card , everything seems to be ok but it can't detect any wireless network..   in my shool i there is wireless everywhere but my pc doesn't see it... what could be the problem?

---

### Post by acrobat on 2005-10-14
anyone?

---

### Post by anders.ostling on 2005-10-14
card model?

have you tried "iwlist scan"? That should report available networks.

Anders

---

### Post by freakazoid on 2005-10-15
Hello I am having the same problem. connection properties just shows the loopback device and the wifi light on my thinkpad(r50) blinks in accordance. the wifi chipset is a Atheros comm. AR5212 802.11abg. Also i cant find "iwlist" do you need to launch a shell or is it available on gnome? Thanks

---

### Post by bionnaki on 2005-10-15
what nic do you have? perhaps you need to use ndiswrapper?

---

### Post by JLB on 2005-10-15
do a search for gtkwifi and grab version 1.09. it works a treat and picks up new wifi AP's nicely. just select the one you want and click on connect. the wifi discovery part works quite well for me.

---

