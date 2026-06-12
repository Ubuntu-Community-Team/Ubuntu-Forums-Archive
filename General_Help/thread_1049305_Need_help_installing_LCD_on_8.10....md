---
title: "Need help installing LCD on 8.10..."
date: 2009-01-24
forum: General Help
---

### Post by tiger.woods on 2009-01-24
The error is as follows:

$:/etc/init.d# LCDd
imonlcd: ERROR opening /dev/lcd0 (No such file or directory).
imonlcd: Did you load the iMON VFD kernel module?
imonlcd: More info in lcdproc/docs/README.imon
Driver [imonlcd] init failed, return code < 0
Could not load driver imonlcd
There is no output driver
Critical error while initializing, abort.

I was following this guide ([http://wiki.foxmediasystems.com/index.php/Antec_Fusion_v2_Black_LCD](http://wiki.foxmediasystems.com/index.php/Antec_Fusion_v2_Black_LCD)) and all went well except the LCD doesn't work.

I looked for the /dev/lcd0 and it doesn't exist so I'm confused on what was supposed to create that device, lcdproc or lirc?

Any help would be appreciated.

TW,

---

### Post by tiger.woods on 2009-01-24
Anyone who is getting the error message like I did needs to re-install LIRC as it wasn't installed correctly. 

I ran the setup.sh as was instructed in the README with LIRC.

TW,

---

