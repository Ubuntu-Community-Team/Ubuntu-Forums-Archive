---
title: "Heron and Dell Latitude D830 Truemobile 1505 Wireless Working and Link to how"
date: 2008-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Merrickk on 2008-05-09
Heron 
Dell Latitude D830
Truemobile 1505 Wireless, detected as: 
Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

Working great, per first page instructions found here:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

I used step 2d period per link to original help thread from Mazza558.

Step 2d: R151517 Driver Download/Extraction
wget [http://myspamb8.googlepages.com/R151517-pruned.zip](http://myspamb8.googlepages.com/R151517-pruned.zip)
unzip R151517-pruned.zip

Thank you Alex, Mazza, and everyone.  I'm breaking away, and this was my first roadblock into the new open source world.  Wish me luck, and thanks again.

---

### Post by Myxb on 2008-05-12
Yes, the workaround works but its performance is ... well... unstable.

It is not always possible to connect after resume or after the wireless switch is toggled ON. Sometimes it is requiered to run the script manually. Also when kNM connects automatically to the last used AP mostly it is unsuccessful until you select and click the AP from the list manually.

The workaround script is the runlevel 2 and also (for resume) in the usr/lib/pm-utils/sleep.d.

I am looking into running the script when the wireless switch on turned ON. Hopefully this should eliminate any sharp edged still there. It specifically concerns our D630 and that's why I write here.

Has anybody tried to tie the script to the switch?

BTW it is better to use the script which uses output of the lsmod (somewhere in that thread) rather then the original script

---

