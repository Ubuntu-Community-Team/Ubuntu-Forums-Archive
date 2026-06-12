---
title: "Strange Live CD issue"
date: 2006-08-16
forum: Desktop Environments
---

### Post by crag277 on 2006-08-16
I've been running Ubuntu on my laptop for a while now and have now decided to bring it to the desktop as well.  My system is a strange one, MSI MEGA 865, and has had one fatal flaw that has prevented me form installing linux on it.  The fans ALWAYS spun at full speed in linux.  Finally, after searching some of the MSI forums, I found that if I downgrade the BIOS thermal control will once again be handled by the BIOS, not a windows driver.

So I flashed the BIOS and popped in my Ubuntu CD.  Sure enough, once the Kernel was loaded the fans quieted down.  But as soon as it got the the "Loading restricted drivers" step the startup process immedietaly switched to the shutdown process.  All modules were unloaded and the computer shut down.  First I thought it was a bad cd, so I tried another one, this one was one of the official ones that you get in the mail.  Same problem.  Then I tried a Kubuntu live cd.  This time it got to the desktop, but then there was a beep from the PC speaker and the computer turned off.

Any ideas, or is this system just not linux friendly?

Here's a more detailed hardware description:
MSI MEGA 865 BIOS 1.2
Intel 865 / ICH5 chipset
Pentium 4 3.2GHz Northwood
1GB Corsair DDR-400 RAM
ATI Radeon 9700 Pro AGP

---

### Post by arkham on 2006-08-16
This previous post indicates that a downgrade to 1.1 sorted out his issues:

[http://ubuntuforums.org/showthread.php?t=200319](http://ubuntuforums.org/showthread.php?t=200319)

Adam

---

### Post by crag277 on 2006-08-16
Thanks, but there's somethig screwed up with my system.  I've tried BIOS 1.2 and 1.1, and neither one works.  I can tolerate Windows until it's time to upgrade...

At least the laptop runs Ubuntu

---

