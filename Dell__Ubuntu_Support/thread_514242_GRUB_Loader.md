---
title: "GRUB Loader"
date: 2007-07-31
forum: Dell  Ubuntu Support
---

### Post by wtfdop0987 on 2007-07-31
So here's the problem:

I had Ubuntu and XP Home dual-booting with 2 separate partitions. I didn't use Ubuntu so I formatted the partition it was on in XP. There is nothing on the new partition (F:). I had to restart my computer because I installed something and now when I boot my computer up it reads:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 17

Please help. XP is still installed in (C:)

---

### Post by kebes on 2007-07-31
If you have erased Ubuntu, and don't need GRUB anymore, then you can use Windows XP to replace the master-boot record (MBR).

There is a command called "fixmbr" that is available in Windows recovery mode. I think if you boot off a Windows floppy disk or Windows install CD, and get to the command prompt, you can run that command.

Quoting from [this thread]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9921-uninstalling-linux.html"):

> 
Boot off the Windows XP CD and after windows loads type **r** to get to the Recovery Console. ... Now were in recovery console all we have to do is type:

fixmbr

this command will re-write the Master Boot Record, therefore removing Grub.


Hope that helps.

---

