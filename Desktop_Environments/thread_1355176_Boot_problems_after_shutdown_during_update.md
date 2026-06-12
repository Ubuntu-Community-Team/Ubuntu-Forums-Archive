---
title: "Boot problems after shutdown during update"
date: 2009-12-14
forum: Desktop Environments
---

### Post by IrrationalIntellect on 2009-12-14
I'm using LTS Hardy on a i386 machine.

I was updating when a friend who thought she was being funny shut my machine off.

Now when I reboot there is no sound, the mouse, power manager and internet wireless do not work. I was able to figure out how to boot into safe mode and the console, but I don't know what to do when I get in there.

I have a recovery disk made, but as I just moved I can't find it. Any advise on what I should do? I am posting this from  a library computer and will check back here thru that.

Thanks.

---

### Post by bryonak on 2009-12-14
If you have wired internet connectivity, boot into recovery ("single user") mode. In case you have no IP (the 'ifconfig' command tells), run```
dhclient eth0
```
To repair the broken packages, your best bet is:```
aptitude update && aptitude upgrade
```
After that, reboot into the normal system, run ```
sudo aptitude
```and look for corrupt packages there. If there are any, report back.


Without internet access, the system'd be back running easily if you have a separate partition for your home folder, so you can reinstall without losing your data and settings. It's common practice, but most people new to Ubuntu sadly don't do that.


Without internet connection and just one partition for the whole system... well, the simplest way is to back up what is possible (usb should work fine, just ask if you need instructions) and reinstall from scratch (this time with a separate home partition ;) ).
The obvious alternative is walking through every defunct package and manually repairing it. Not fun.
Another option might be installing a fresh system over the current one without formatting, but I don't think that's a good idea...

---

### Post by IrrationalIntellect on 2009-12-15
Thanks so much bryonak, will give it a go round and see...

---

