---
title: "Jaunty Network Related Freezes -- New Bug Report Launch"
date: 2009-05-13
forum: General Help
---

### Post by brntoki on 2009-05-13
OK!  User Madomac has made a fresh bug report to launchpad concerning Jaunty freezes that are network related.  I'll link to it below.  The reason for the new report is that the old one seems it may be somewhat diluted due to people with slightly dissimilar problems reporting as well.

THIS NEW BUG REPORT is for those who have narrowed their issue down to networking ONLY!  We are hopeful to get the developers headed in the right direction on this and make their job a little easier.

Therefore, if you wish--and you really should wish--to subscribe to the bug and help towards a fix, please verify the following:

[INDENT]1. Can you work on the machine without freezing if you have disabled networking?  If you are stable without networking, and then upon re-enabling it the freeze returns, you are a good candidate for this bug report.
2. When your computer freezes, are you able to get out of the freeze with Ctrl+Alt+SysRQ, and after releasing only SysRq key, slowly typing R-E-I-S-U-B?  If not, you are a good candidate for this bug report.[/INDENT]

If this is you, please help with a fix by visiting this launchpad bug report and submitting your logs (submitting logs is easy... even I learned how).  Here is the new bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375986](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375986)

Thanks everyone.  And thanks to Madomac for taking the initiative on this.

---

### Post by madomac on 2009-05-13
Thanks for opening this new thread. I hope we can deliver more accurate information to the developers by opening a network specific bug and thread.

Cheers,
Marc

> **brntoki said:**
> OK!  User Madomac has made a fresh bug report to launchpad concerning Jaunty freezes that are network related.  I'll link to it below.  The reason for the new report is that the old one seems it may be somewhat diluted due to people with slightly dissimilar problems reporting as well.

THIS NEW BUG REPORT is for those who have narrowed their issue down to networking ONLY!  We are hopeful to get the developers headed in the right direction on this and make their job a little easier.

Therefore, if you wish--and you really should wish--to subscribe to the bug and help towards a fix, please verify the following:
[INDENT]1. Can you work on the machine without freezing if you have disabled networking.  If you are stable without networking, and then upon re-enabling it the freeze returns, you are a good candidate for this bug report.
2. When your computer freezes, are you able to get out of the freeze with Ctrl+Alt+SysRQ, and after releasing only SysRq key, slowly typing R-E-I-S-U-B[/INDENT]If this is you, please help with a fix by visiting this launchpad bug report and submitting your logs (submitting logs is easy... even I learned how).  Here is the new bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375986](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375986)

Thanks everyone.  And thanks to Madomac for taking the initiative on this.

---

### Post by madomac on 2009-05-14
I am testing an "ralink rt73" based USB WiFi adapter now. Reception and throughput are worse, so far... ;) Let's see if the system will freeze in the next hours.

---

### Post by madomac on 2009-05-15
I stress-tested my system with the external WiFi adapter for nearly 24 hours now, transferred some 6 GiB via WiFi. Listened to Shoutcast radio via Songbird. Downloaded and provided Ubuntu images via Transmission. Copied disk images from local systems. Jaunty is rock-solid. So I think I can pinpoint *my* problems to the "iwlagn" driver.

---

### Post by alexv75 on 2009-05-16
I'm experiencing freezes too, and it seems that they are related to which version of the driver is in use. I have no problem with Jaunty's default version supplied by the 2.6.28 kernel (ver. 2.2.1), but as soon as i try newer kernel (2.6.29 or 2.6.30), the backports package or the compat-wireless package the lockups begin. I've found something that all three share - they all use version 2.3.0 of the ralink drivers. I have RT2561/RT61-based card using the rt61pci driver in ad-hoc mode. There is also a thread on the rt2x00 project forums about this - [http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5247]("http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5247"). I hope this gets fixed soon as i was eager to play around with Karmic :frown: .

---

