---
title: "Error: Unable to create io-slave: Read-only file system"
date: 2007-03-13
forum: Desktop Environments
---

### Post by utkjamie on 2007-03-13
I'm getting the error: "Could not start process. Unable to create io-slave: Read-only file system."

The error seems to occur randomly and I only notice it when I need to save something to the hard drive. The error seems to affect my entire filesystem, including external drives. I cannot save nor navigate directories without receiving this error.

I can navigate directories from the command line without problem. I tried creating a file on the desktop from the command line. The file shows up using the ls command but does not show up on the desktop.

Rebooting makes everything work normally again but I'd like to find out what the culprit is and fix it. Any idea what is going on?

---

### Post by utkjamie on 2007-03-13
Not sure if it is related to the above problem, but after rebooting I was faced with errors telling me that I needed to manually run fsck. When I run fsck -n I get "zero dtime" and "multiply-claimed blocks" errors.

The last time I had this problem was following a system freeze at shutdown. Other than the "unable to create io-slave" error, the system seemed to go through a normal reboot last time -- so I'm not sure what caused these errors. Fortunately I'm on a dual-boot system and was able to run hard drive diagnostics from WinXP, which showed nothing wrong with the hard drive.

If the fsck fixes are as catastrophic as last time, I'll be reinstalling Ubuntu again. I've only been a Linux user since late January so installing Linux for a third time in that short of a period isn't promising. Any idea what the problem might be so I can avoid it in the future?

---

### Post by markoloka on 2007-06-13
Tell me what happened and how you fixed it... i just had same problem. 
Now my kubuntu: read-only files system and will not boot.

---

