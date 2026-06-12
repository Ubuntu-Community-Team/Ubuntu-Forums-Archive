---
title: "R210 w/PERC H200 USB Install Hangs on Boot"
date: 2010-10-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by asmosk on 2010-10-26
I just installed 10.04.1 to a R210 with PERC H200 via USB disk.  The install worked great.  Upon reboot the system just hung on a black screen after the diagnostic menu.

It took me a while but here is the problem:  the PERC H200 card takes about 7 seconds to initialize.  During this time the USB disk sneaks in and gets mounted as /dev/sda.  Then PERC comes to life as /dev/sdb.  Now this should not be a problem as Grub2 these days uses drive UUID for mounting purposes.  HOWEVER the Ubuntu installer ALWAYS seems to install GRUB on /dev/sda.  Thus at the end of my 10.04.1 install GRUB went onto my flash drive!!!

So here is how I fixed it:
1. Following the install reboot with USB key still plugged in
2. Set BIOS to boot from USB key
3. Machine should then boot normally as GRUB with proper parameters is on USB key
4. sudo grub-install /dev/sdb
5. unplug USB key
6. reboot

Hopefully this will save someone some time.

---

### Post by stfnfrnr on 2011-05-16
Thanks! You definitely made my day!

---

