---
title: "BCM4312 problem after 9.10 install"
date: 2009-11-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by colinireland on 2009-11-17
Hey,

I have a strange (read: infuriating!) problem with my wireless card after a second installation of karmic. First installation went flawlessly. Then, I decided to completely format my hard-drive to create a separate /home partition and a small encrypted partition.

However I wasn't able to install the propriety driver that I need. The strange thing is that when I boot from the CD everything works fine. I can install the driver with no problem.

I tried reinstalling karmic twice after that. Once with the partitioned hard-drive and then using the entire drive. One noticeable difference when I try to install the driver when booting from the hard-disk I am only given the option to install the STA driver. The B43 driver doesn't appear in the Systems >> Administration >> Hardware Drivers menu whereas it does when I boot from the CD. 


Boot from Hard-disk & CD: lspci gives

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Does anybody know what I need to do to sort this out? Is this broadcom card just crap? I had some problems with it running 9.04.

Sorry about the essay!

Colin

---

### Post by msvf on 2009-11-17
I had the same problem, my 1397 wireless card worked in the "live cd" mode but not in the after full install. This worked for me  [http://ubuntuforums.org/showthread.php?t=1318452&highlight=dell+fix]("http://ubuntuforums.org/showthread.php?t=1318452&highlight=dell+fix") Hope it helped :)

---

### Post by mikewhatever on 2009-11-17
> **msvf said:**
> I had the same problem, my 1397 wireless card worked in the "live cd" mode but not in the after full install. This worked for me  [http://ubuntuforums.org/showthread.php?t=1318452&highlight=dell+fix]("http://ubuntuforums.org/showthread.php?t=1318452&highlight=dell+fix") Hope it helped :)

Bad idea. Apparently, Karmic has a problem with Jockey, the hardware drivers installer, but you can install the wireless driver manually, if available. 
Check out how -> [http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by colinireland on 2009-11-18
Hey,

I just tried both methods listed above and still nothing worked. The exact same problem occured. How can it be working no problem once and not the next?

I just hope a fresh install of jaunty will still work!!!!!

Thanks for your help lads

---

### Post by mikewhatever on 2009-11-18
Just to clarify, if you have a restricted wireless driver available and want to use it, the solution is [-->here<--.]("http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html") Do not install ndiswrapper and the Windows driver as suggested in post #2.

---

### Post by colinireland on 2009-11-19
Hey,

The method above worked. Thanks for you help

Colin

---

### Post by Rifester on 2009-11-19
What I don't understand is why was the final release issued without the appropriate drivers?   It does not make any sense and I have found any explanation for it.

---

