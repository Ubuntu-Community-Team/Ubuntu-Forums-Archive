---
title: "fglrx is crashing Xorg server"
date: 2008-10-22
forum: Desktop Environments
---

### Post by theluddite on 2008-10-22
Hello all,
      At least once a day Xorg restarts on its own for no consistent reason.  The Citrix ICA client will crash it every time and I think npviewer is also one of the culprits.  The problem started when I installed a second monitor with the "Big Desktop" method (I'm using the ATI binary driver).  It's probably also relevant that I'm using Compiz, which I'd rather not do without.  Is there anything I can do?  I've attached my xorg.conf and output of dmesg.

---

### Post by theluddite on 2008-11-27
Bueller?

---

### Post by r m h on 2008-12-12
The problem may well be the fglrx proprietary drivers you have installed.  I had big problems getting X to even run, let alone run stable until I removed the proprietary AMD/ATI FGLRX drivers.

Yeah, that means, I'm stuck with way less than optimal graphics - I'd like to run dual or quad monitors, plus Compiz advanced features, but until fglrx gets updated and fixed, I can't even install the proprietary fglrx drivers since X won't even run on my system when I 'upgrade' to them....

---

### Post by r m h on 2008-12-13
After lots of research on my own fglrx problem, your problem **may** also have to do with your hardware configuration.  If you have 4+GB of RAM, there are some combinations of 64-bit Linux, ATI video cards and mainboards where the MTRRs are not being properly configured.  

This thread may help:  
[http://ubuntuforums.org/showthread.php?p=6363604#post6363604](http://ubuntuforums.org/showthread.php?p=6363604#post6363604)

---

### Post by theluddite on 2008-12-15
Thanks for responding, but I doubt that solution will work for me.  I'm running 2Gb of RAM and I updated to Intrepid so our situations are a bit different.  I'm sure your response may help someone else though. Anyone else have any suggestions?

---

