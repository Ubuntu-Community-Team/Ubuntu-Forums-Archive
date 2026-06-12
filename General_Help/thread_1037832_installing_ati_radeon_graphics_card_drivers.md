---
title: "installing ati radeon graphics card drivers"
date: 2009-01-12
forum: General Help
---

### Post by chris3966 on 2009-01-12
I'm having a bit of troube installing my ATI Radeon 9200 graphics card. I've got the drivers from ATI and I run them in the terminal as instructed by ATI but they always fail, they say that the x86 cannot be found. I have gone to ATI and got their x86 drivers and thay install bu the same problem still occures. 
If any one has encountered the same problem and knows what to do please help!

Many Thanks,

Chris

---

### Post by cros13 on 2009-01-12
Hi Chris,

Are you using a 64-bit or 32-bit version of Ubuntu?

The easiest way to install these drivers is by using
the driver package provided by ubuntu:

1. Launch the &#8220;Restricted Devices Manager&#8221; program from the menu System &#8594; Administration &#8594; Restricted Devices Manager

2. Enable the &#8220;ATI accelerated graphics driver&#8221; driver

3. Reboot

Simple as that.

---

### Post by Tim Sharitt on 2009-01-12
Have you tried to install xorg-driver-fglrx from the repositories? I believe it provides the same driver as the installer provided by ATI.

---

