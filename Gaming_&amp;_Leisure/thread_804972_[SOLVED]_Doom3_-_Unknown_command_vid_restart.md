---
title: "[SOLVED] Doom3 - Unknown command vid_restart"
date: 2008-05-23
forum: Gaming &amp; Leisure
---

### Post by Kevbert on 2008-05-23
Hi. I'm trying to run Doom3 in native linux mode on an AMD2 x64 +3800 PC with  a 256Mb nVidia GeoForce 7600GS display card and 4 Gb RAM.  I've loaded the PAK files from CD onto my PC, installed the 32 bit libraries (via Getlibs), edited my ld.so.conf, and run ldconfig. When I run doom3 from the command line I get a load of checksums and eventually this...

/home/kevin/dosgames/Doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg

What do I need to do next ?

---

### Post by Barasuishou on 2008-05-23
hi, i'm sorry i don't know what your problem is, i am trying to run quake 4(which installation is the same that doom 3), but i can't run it, because i can't install de 32 bits libraries, can you help me?, i'm a linux noob :(

---

### Post by Sleaka J on 2008-05-23
Have you copied over all 5 PAK files from all 3 CD's to the doom3/base directory yet? You need all 5.

---

### Post by Barasuishou on 2008-05-24
yes i have copied all :S, it seems to me that the problem is with the library libsdl1.2debian ......

---

### Post by Kevbert on 2008-05-24
You need to use getlibs which can be found on one of my previous posts here: [http://ubuntuforums.org/showthread.php?t=804847]("http://ubuntuforums.org/showthread.php?t=804847")

---

### Post by Sleaka J on 2008-05-25
Actually, I was asking Kevbert if he'd copied over all 5 PAK files. PAK000.PK4 & PAK001.PK4 are on Disc Two. PAK003.PK4 & PAK004.PK4 are on Disc Three. PAK002.PK4 is on Disc One.

I had 2 of the 3 CD's in storage (Disc One is the only disc needed to play in Windows) and was only able to copy over PAK002.PK4 to the HDD and I got that exact message. Only when I got the other 2 CD's out of storage and copied the files across did I get into the game. Next problem: finding the manual with the CD-key, which is also in storage. I'll then be able to play.

---

### Post by Kevbert on 2008-05-26
Yes all pak files are on the hard disk in my /home/kevin/dosgames/Doom3 directory.  Doom3 install has also put a shortcut under Applications-Other, but when I click on it nothing happens.  I can only (start to) run from the terminal command line where I get the vid-restart error.
I may try to install again under WinXP and try to fathom out what's going wrong from there.  I haven't used XP in weeks, so I hope its still working !
Well it works fine in XP so it's not a hardware problem, but a configuration/software problem.

---

### Post by Kevbert on 2008-05-26
Yippee... let's kill some mutants.  The game now works.  For some reason some of the pak files were in the wrong directory - I copied them across and success.  There's actually 9 Pak files and 3 gamexx.pk4 files.

---

### Post by Sleaka J on 2008-05-26
Yeah, they shouldn't be in the doom3 directory, but in the doom3/base directory (along with the other .PK4 files), but it looks like you figured that out.

---

### Post by linuxciting on 2010-08-30
i have exact same problem and i am very very new in ubuntu.
i navigated to my base folder and found these 3 files. game00.pk4,game01.pk4,game05.pk4
what exactly i need to do to get this game running? 
btw, i dont have windows ,runinng machine with Ubuntu 10.04

---

### Post by linuxciting on 2010-08-30
solved it myself...yeyyyyyy

---

