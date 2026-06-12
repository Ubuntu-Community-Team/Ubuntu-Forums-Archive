---
title: "Problem with IDE drives"
date: 2011-07-27
forum: Desktop Environments
---

### Post by ilikefpgas on 2011-07-27
Greetings, I am new here. I just built a new PC with a brand new, but modest motherboard I got from tiger-direct, it is an MSI GF615M-31 with SATA and IDE connectors. When I put the machine together a few days ago, the Ubuntu 10.04 and windows 7 both recognized my IDE drives, cd and HDD. Ubuntu 11.04 does not. The hardware setup screen does recognize the controller for IDE as if nothing was attached to it, recognizes the SATA Drive no problem. Booting from windows 7 does give me access to those drives.

---

### Post by iustus on 2011-07-28
Well 
1) In the SETUP OF BIOS you must indicate  IDE and SATA to be used enhanced . ¿Did You? 

2) Than you must indicate in the BIOS which will be the order of 
boot-devices and if the BIOS is quite new you will have confirm  the first boot-device  

If the error is laying in the SETUP - I guess - Than it should be now functioning . 

If not revise the connections of your HDD IDE  and eventually look if it apprears in gparted  (install it if not installed ) 

If there can be a problem of 32 or 64 bits un this context, well I do not know

---

### Post by ilikefpgas on 2011-07-28
All my drives work now, Ubuntu ran some updates, that's all, not sure problem or fix was.

---

