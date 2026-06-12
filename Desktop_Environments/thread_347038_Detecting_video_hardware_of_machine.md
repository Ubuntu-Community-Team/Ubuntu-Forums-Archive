---
title: "Detecting video hardware of machine"
date: 2007-01-26
forum: Desktop Environments
---

### Post by banzera on 2007-01-26
Hello all,

I've got edgy installed on an external USB HDD. It is successfully working in every aspect when connected and booting at my office machine.

I can also connect to and boot to my laptop, however the hardware configuration is quite different. 

The office machine has an NVIDIA graphics card, but the laptop has ATI mobility 9200.

I'd like the setup to detect which hardware is present and load the appropriate video drivers. Currently I have a 3D accelerated environment while plugged in at the office. If I want to boot to the laptop (or another machine for that matter) I have to switch out the Xorg.conf file to use the VESA driver before shutting down to reboot.

My question is this: how can I determine (at boot time) which hardware is in the system so that I can script the use of an appropriate xorg.conf file?

TIA

-Bryan

---

