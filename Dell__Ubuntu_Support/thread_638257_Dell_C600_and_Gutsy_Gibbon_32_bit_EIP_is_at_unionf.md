---
title: "Dell C600 and Gutsy Gibbon 32 bit EIP is at unionfs_rename error on install"
date: 2007-12-11
forum: Dell  Ubuntu Support
---

### Post by ookboo on 2007-12-11
I have an older C600 that I am very excited about revitalizing wth UBUNTU.  I have installed 64 bit versions on both my desktop and laptop systems and love it.  Trying to get my 6 year old a laptop up and running and get this awful mess on screen during install.

The boot CD I am using is created from ISO image as the ISO image file will not even show the install screen.  I burned them from UBUNTU on my desktop.
UBUNTU install options screen comes up on C600, I choose basic install.  There is much delay, then...
(Each line followed by 365.076000 in brackets)

EIP is at unionfs_rename+0x4fd/0x9f0 [unionfs]
eax:  00008000   ebx: 00000002   ecx: 00000000  edx: c0e0ba18
esi:  00000000  edi:  ffffffff ebp:  00000001  esp:  c2b21e24
ds:  007b  es:  007b  fs:00d8  gs:  0033  ss:  0068
Process debconf-set-sel (pid: 5081, ti=c2b20000 task=c7a0e000 task.ti=c2b20000
Stack:  00000000  00000000  00763b78  00000000  c6160c30  c0e0ba18 c6160c30  ffffffe4
00000001  c789d120  00000001  00000000  00000002  c43a9d48  00000000  00000000
00000000 00000001  00000000 00000000 00000001 00000000 c896e3c0 c0e0ba18
Call Trace:
[<c0188cde>]  vfs_rename+0x3de/0x480
[<c018abf6>]  sys_renameat+0x1e6/0x220
[<c0183cbe>]  sys_stat64+0x1e/0x30
[<c018ac57>]  sys_rename+0x27/0x30
[<c01041d2>]  sysenter_past_esp+0x6b/0xa
=======================
Code:  40 00 00 0f 84 f4 02 00 00 8b 4c 24 44 39 4c 24 50 0f 84 b9 02 00 00 8b 4c 24 54 85 c9 74 0c 81 f9 00 f0 ff ff 0f 86 34 02 00 00 <0f> 0b eb fe 8b 44 24 14 31 d2 e8 22 f3 ff ff 83 f8 d9 89 44 24
EIP:  [[<c896439f>]  unionfs_rename+0x4df/0x9f0 [unionfs]  SS:ESP 0068:c2b21e24

If nothing else, I got good practice typing numbers in on a laptop.

thanks for any assistance.


o ok boo

---

### Post by ocr14a on 2007-12-21
I have this exact problem on the exact machine model. 
No response yet, eh?

---

### Post by Kontar on 2007-12-22
I have the same problem on a Desktop PC (Intel Pentium III 700Mhz, 512MB RAM, also a bit older)

Here are additional informations (ubuntu support request): [https://answers.launchpad.net/ubuntu/+question/20542]("https://answers.launchpad.net/ubuntu/+question/20542")

With the SimplyMEPIS Distribution Live-CD (6.5.02) I was able to start KDE without problems...

---

### Post by ookboo on 2007-12-24
I installed Xubuntu alternate CD and used text install (gutsy i think) on the machine and seems to be running fine.

I only have 128 mb of memory, so I think that is the problem with the ubuntu.  I plan on getting more memory for it anyway and will try the ubuntu setup again.

---

### Post by Kontar on 2007-12-27
I found out, that my CD-drive was the problem.

Above the unionfs error were some SQUASHFS errors and this points to CD integrity issues (said google).

---

