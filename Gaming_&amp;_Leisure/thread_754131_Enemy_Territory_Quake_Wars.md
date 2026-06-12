---
title: "Enemy Territory Quake Wars"
date: 2008-04-13
forum: Gaming &amp; Leisure
---

### Post by chrispche on 2008-04-13
How do you install this game? Sorry if this is a stupid question, I downloaded the ETQW-client-1.4-full.x86.run file. Then followed this guide. 

[http://community.enemyterritory.com/forums/showthread.php?t=14144&highlight=Installing+Quake+Wars+on+Linux](http://community.enemyterritory.com/forums/showthread.php?t=14144&highlight=Installing+Quake+Wars+on+Linux)

Then when attempting to run got the following:

chrispche@chrispche-desktop:~$ /home/chrispche/ETQW/etqw
ETQW 1.4.12247.12247  linux-x86 Jan  4 2008 13:52:05
found interface lo - loopback
found interface ppp0 - 41.208.197.184/255.255.255.255
found interface vmnet1 - 172.16.194.1/255.255.255.0
found interface vmnet8 - 172.16.88.1/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
ETQW using generic code for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Loaded pk4 /home/chrispche/ETQW/base/game000.pk4 with checksum 0x1eefa237
Loaded pk4 /home/chrispche/ETQW/base/game002.pk4 with checksum 0x5f707685
Loaded pk4 /home/chrispche/ETQW/base/pak005.pk4 with checksum 0x5ccc7213
Loaded pk4 /home/chrispche/ETQW/base/pak006.pk4 with checksum 0x9edf1b7d
Loaded pk4 /home/chrispche/ETQW/base/pak007.pk4 with checksum 0x74a1a2f
Loaded pk4 /home/chrispche/ETQW/base/zpak_english001.pk4 with checksum 0x6583cd8
Loaded pk4 /home/chrispche/ETQW/base/zpak_english002.pk4 with checksum 0x8dc70e3d
Loaded pk4 /home/chrispche/ETQW/base/zpak_french001.pk4 with checksum 0x3bd7a062
Loaded pk4 /home/chrispche/ETQW/base/zpak_french002.pk4 with checksum 0x79287190
Loaded pk4 /home/chrispche/ETQW/base/zpak_german001.pk4 with checksum 0xa694c3f1
Loaded pk4 /home/chrispche/ETQW/base/zpak_german002.pk4 with checksum 0x64bee731
Loaded pk4 /home/chrispche/ETQW/base/zpak_korean000.pk4 with checksum 0xd42c084
Loaded pk4 /home/chrispche/ETQW/base/zpak_korean001.pk4 with checksum 0x4de6a4e7
Loaded pk4 /home/chrispche/ETQW/base/zpak_korean002.pk4 with checksum 0x15d2c9af
Loaded pk4 /home/chrispche/ETQW/base/zpak_polish001.pk4 with checksum 0x2575ff8e
Loaded pk4 /home/chrispche/ETQW/base/zpak_polish002.pk4 with checksum 0x3ab92dd6
Loaded pk4 /home/chrispche/ETQW/base/zpak_russian001.pk4 with checksum 0xf3e91581
Loaded pk4 /home/chrispche/ETQW/base/zpak_russian002.pk4 with checksum 0x38b1a37c
Loaded pk4 /home/chrispche/ETQW/base/zpak_spanish001.pk4 with checksum 0xd609566c
Loaded pk4 /home/chrispche/ETQW/base/zpak_spanish002.pk4 with checksum 0xcf994ada
Current search path:
/home/chrispche/.etqwcl/base
/home/chrispche/ETQW/base
/home/chrispche/ETQW/base/zpak_spanish002.pk4 (119 files)
/home/chrispche/ETQW/base/zpak_spanish001.pk4 (13 files)
/home/chrispche/ETQW/base/zpak_russian002.pk4 (119 files)
/home/chrispche/ETQW/base/zpak_russian001.pk4 (13 files)
/home/chrispche/ETQW/base/zpak_polish002.pk4 (119 files)
/home/chrispche/ETQW/base/zpak_polish001.pk4 (13 files)
/home/chrispche/ETQW/base/zpak_korean002.pk4 (12 files)
/home/chrispche/ETQW/base/zpak_korean001.pk4 (12 files)
/home/chrispche/ETQW/base/zpak_korean000.pk4 (6 files)
/home/chrispche/ETQW/base/zpak_german002.pk4 (119 files)
/home/chrispche/ETQW/base/zpak_german001.pk4 (13 files)
/home/chrispche/ETQW/base/zpak_french002.pk4 (119 files)
/home/chrispche/ETQW/base/zpak_french001.pk4 (13 files)
/home/chrispche/ETQW/base/zpak_english002.pk4 (117 files)
/home/chrispche/ETQW/base/zpak_english001.pk4 (9 files)
/home/chrispche/ETQW/base/pak007.pk4 (1510 files)
/home/chrispche/ETQW/base/pak006.pk4 (3 files)
/home/chrispche/ETQW/base/pak005.pk4 (2172 files)
/home/chrispche/ETQW/base/game002.pk4 (3 files)
/home/chrispche/ETQW/base/game000.pk4 (3 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
fs_basepath = /home/chrispche/ETQW
fs_savepath = /home/chrispche/.etqwcl
fs_userpath = /home/chrispche/.etqwcl
fs_cdpath = /home/chrispche/ETQW
fs_devpath = /home/chrispche/.etqwcl
0x0
[0x082e7e71]
[0x0819b5f9]
[0x0819e912]
[0x0819f242]
[0x0819f41e]
[0x083dcd6e]
[0xb7b69050]
[0x0804ca61]
********************
FATAL ERROR: Couldn't load fs.chk
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()
Sys_Error: Couldn't load fs.chk
chrispche@chrispche-desktop:~$ 

What is fs.chk?

Is there a simple way to install this? Because with Doom 3 and Quake 4 all you had to do was copy some .pak files and run the Linux patch.

Surely the same can be done here?

Thanks in advance for any advice.

---

### Post by chrispche on 2008-04-13
Ok I searched the Ubuntu Forums and found this guide. Which I followed and seemed more familiar to the installs of Quake 4 and Doom3:

[http://gaming.gwos.org/doku.php/guides:32bit:etqw?s=quake%20wars](http://gaming.gwos.org/doku.php/guides:32bit:etqw?s=quake%20wars)

I still get the:

********************
FATAL ERROR: Couldn't load fs.chk
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()
Sys_Error: Couldn't load fs.chk
chrispche@chrispche-desktop:~/Desktop$ 

Error.

Any ideas?

Cheers!

---

### Post by Perfect Storm on 2008-04-13
Try re-download the installer - it might be faulty. Get it via bittorent to avoid faulty downloads.

Also make sure you downloaded the right file.

---

### Post by Ideastone on 2008-04-13
Did you download the instlaller from the official site? Sometimes third party sites don't download properly.

---

### Post by chrispche on 2008-04-14
No I did not. I'll download it from ID now. Just to ask a question. Does it matter if the DVD is in the drive or not, because I just copied the contents of the DVD to my Desktop under ETQWDVD folder. The installer seem to find the files correctly.

---

### Post by Perfect Storm on 2008-04-14
I don't know but you could try from the DVD. No harm to try it.

---

### Post by chrispche on 2008-04-17
Yes that worked. However how do I backup the DVD. It's bigger than a normal DVD. I suppose I could make an ISO of it and back is up onto my external hard drive.

---

### Post by Perfect Storm on 2008-04-17
Well, why would you back it up, you have your ETQW DVD you bought.

---

