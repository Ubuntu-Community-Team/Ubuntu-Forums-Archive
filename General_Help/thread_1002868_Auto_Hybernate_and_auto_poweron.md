---
title: "Auto Hybernate and auto poweron"
date: 2008-12-05
forum: General Help
---

### Post by usamahashimi on 2008-12-05
edited

---

### Post by snova on 2008-12-05
Automatically going into Hibernation should be easy, but coming back out wouldn't. Hibernation *turns off* the computer.

I'm pretty sure there is a way, though.

---

### Post by usamahashimi on 2008-12-06
edited

---

### Post by gTinker on 2008-12-06
WOL is something that has to be supported by the MB and powersupply, but probably is by yours. In order for WOL to work your NIC has to be still 'awake' when the system is powered down. If your NIC is a separate card there usually needs to be a jumper from the MB to the card. If you pull the mains cord or use a shutoff switch on the atx power supply, this can't work.

It works by waking up the computer from the power off state when the system receives a network request for connection. I believe you should be able to see the network connection led on after you have shutdown.

---

