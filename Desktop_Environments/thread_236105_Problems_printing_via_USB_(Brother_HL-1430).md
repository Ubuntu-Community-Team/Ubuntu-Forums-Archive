---
title: "Problems printing via USB (Brother HL-1430)"
date: 2006-08-14
forum: Desktop Environments
---

### Post by amadeus_z on 2006-08-14
Hello,

I'm having problems printing via USB on a relatively new Ubuntu install.

The problems arise when I print from OpenOffice. I think it is something to do with the spooler:

a) Printing from Firefox is fine (cups)
b) Printing one document from OO is fine (cups)
c) Printing a second document is no good. The document is queued.
d) Sending a test page sometimes works, sometimes it sends the document that was queued! 
e) Switching the printer on, off makes it print everything in the queue.
f) Restarting hplip and cupsys does not help

I've converted this desktop for my parents, so obviously I need printing to work without these problems!

Does this sound familiar to anyone? Any idea why this is going on?

THanks

Amadeus

---

### Post by AlterEgo on 2006-08-27
You have the same issue as described here:
[http://ubuntuforums.org/showthread.php?t=240549&highlight=brother+print](http://ubuntuforums.org/showthread.php?t=240549&highlight=brother+print)
(and so do I). No Fix however. 

Bugreport: [https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/57050](https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/57050)

---

### Post by amadeus_z on 2006-08-28
Thanks; it seems the "fix" is to switch to a parallel port cable, which I'll do.

Amadeus

---

