---
title: "Dropping into BusyBox - disk controller issue?"
date: 2009-02-27
forum: General Help
---

### Post by gr8dogs on 2009-02-27
For a while now, I have had issues with Ubuntu failing to boot/reboot.  While the problem does not always occur, it usually does.  The system starts to boot, and then drops me into BusyBox. The issue has persisted through several kernel upgrades, so it's not associated with any particular kernel.(Currently, I'm on 2.6.24-23-generic.)  Trying to boot using recovery mode fails as well, but perhaps the messages I'm seeing will shed some light on the problem.  Everything seems to go fine until I see the following on the console.

Begin: Running /scripts/init-bottom
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
Done: Target filesystem doesn't have /sbin/init.

Then it drops me into BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) ...

Based on the messages, I thought perhaps it might be some kind of disk
controller initialization issue.  Completely powering the machine off and back on doesn't seem to help; however, if, after it fails, I boot from a CD, I CAN see the file systems just fine; and if I then shutdown/reboot from the CD, it has (so far) then been able to boot from the disk just fine.  

Anybody got any ideas on what the problem might be, or better, how to fix it??!

Thanks!

---

### Post by ozPATT on 2009-03-02
Hey there, I have been having the same issues for the last few days also, I am hoping that my files are still on the system, and from the sounds of it they are so thats a good thing.. but it just wont boot at all. no matter how many times I try, it does the same thing after the running scripts/init-bottom line... 

sorry i can't help with the solution, but just thought i would mention that you are not the only one...

---

