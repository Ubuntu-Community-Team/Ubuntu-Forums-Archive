---
title: "Running app from console error"
date: 2006-11-29
forum: Desktop Environments
---

### Post by SteveF on 2006-11-29
I just installed edgy Kubuntu.  Whenever I run a graphical app from the console, I get the following output in the console (the app seems to run correctly though):

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Any ideas why I get this and how it can be fixed?

Thanks,

Steve

---

### Post by drphilngood on 2006-11-29
See this thread:

[kubuntu error]("http://www.ubuntuforums.org/showthread.php?t=185930")

and this post in the thread:

[post # 12]("http://www.ubuntuforums.org/showpost.php?p=1101754&postcount=12").

Good luck!

---

### Post by SteveF on 2006-11-29
> **drphilngood said:**
> See this thread:

[kubuntu error]("http://www.ubuntuforums.org/showthread.php?t=185930")

and this post in the thread:

[post # 12]("http://www.ubuntuforums.org/showpost.php?p=1101754&postcount=12").

Good luck!

Thanks.  I do have a Wacom tablet so that is probably the issue.  I'm not going to remove the lines because I do use the tablet at times.  I didn't have this problem with Dapper so is this something between Wacom drivers and newer libs used by Edgy?

Steve

---

### Post by drphilngood on 2006-11-29
What are your system specs?

---

### Post by SteveF on 2006-11-29
> **drphilngood said:**
> What are your system specs?
I'm running a Dell 8100
Intel Pentium 4 1.4 mhz
512MB RAM
2 Hard drives
HDA has Windows 2000 on it
HDB is partitioned to 6 drives
1 - FAT32 mounted by default
2 - NTFS not mounted by default
3 - EXT3 with Kubuntu 10 GB
4 - EXT3 with Ubuntu not mounted by default 10GB
5 - EXT3 shared by Ubuntu and Kubuntu mounted by default 80GB
6 - Swap 1 GB

Graphics:
nVidia geForce2 MX
Dell M991

Connected I have:
1 SCSI card connected to film scanner (not on usually)
1 Multi-card reader connected USB
1 HP Printer connected USB
1 Flatbed scanner connected USB
1 Wacom tablet if connected (which is not usually) it would be USB

Steve

---

