---
title: "Onboard Mic Inspiron 1526 Not working"
date: 2010-08-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Moofknock on 2010-08-21
I just installed Ubuntu 10.04 which I'm usining for the first time - never used Linux before. I can't get the onboard mic going. I tried to use a fix I saw in the forum using linux-backports-modules-2.6.22-14-generic_2.6.22-14.50_i386 file but it gave me this notice.

Ubuntu supplied Linux modules for version 2.6.22 on x86/x86_64
This package contains modules supplied by Ubuntu for Linux kernel 2.6.22 on x86/x86_64.
You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed. 

I need to know what I have to do, I'm still new to this operating system so I'm not sure what I'm doing here yet.

---

### Post by mikewhatever on 2010-08-21
The package you should install is linux-backports-modules-alsa-lucid-generic. It will pull in the correct version for your latest kernel. I'd also suggest updating the system, as the latest kernel version in Lucid is 2.6.32-24.

---

### Post by Moofknock on 2010-08-22
Ok I got them both installed (gotta love Synaptic) but what do I do next?

---

### Post by mikewhatever on 2010-08-23
Well, check if the microphone works after a reboot.
Also, open Sound Preferences, the Input tab, and make sure microphone is not muted, which it is by default.

---

### Post by Moofknock on 2010-08-23
Tried that but no luck :(

---

