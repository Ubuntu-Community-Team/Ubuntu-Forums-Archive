---
title: "Odd issue with Doom 3 Native Client"
date: 2006-11-03
forum: Gaming &amp; Leisure
---

### Post by Echo35 on 2006-11-03
I attempted to install and run the Doom 3 client, and I get an odd error message from the terminal when I do:

$ ./doom3
DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 192.168.0.103/255.255.255.0
------ Initializing File System ------
Loaded pk4 /home/echo35/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /home/echo35/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /home/echo35/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /home/echo35/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /home/echo35/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /home/echo35/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/echo35/.doom3/base
/home/echo35/doom3/base
/home/echo35/doom3/base/pak007.pk4 (38 files)
/home/echo35/doom3/base/pak006.pk4 (48 files)
/home/echo35/doom3/base/pak005.pk4 (63 files)
/home/echo35/doom3/base/game03.pk4 (2 files)
/home/echo35/doom3/base/game02.pk4 (2 files)
/home/echo35/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg

What exactly does that error mean and how can I fix it?

---

### Post by Iarwain ben-adar on 2006-11-04
Hi,
it means that you should copy the "default.cfg" file from your cd-rom to your /base folder :D

If you don't have it,
i can post mine..

EDIT: lookie [here](http://ubuntuforums.org/showpost.php?p=1692141&postcount=10)


Iarwain

---

### Post by Echo35 on 2006-11-04
I can't seem to find mine so I'll use that one, thanks!

EDIT: Nice Naruto Tux!

---

### Post by Echo35 on 2006-11-04
Grr...

$ ./doom3
DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 192.168.0.103/255.255.255.0
------ Initializing File System ------
Loaded pk4 /home/echo35/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /home/echo35/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /home/echo35/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /home/echo35/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /home/echo35/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /home/echo35/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/echo35/.doom3/base
/home/echo35/doom3/base
/home/echo35/doom3/base/pak007.pk4 (38 files)
/home/echo35/doom3/base/pak006.pk4 (48 files)
/home/echo35/doom3/base/pak005.pk4 (63 files)
/home/echo35/doom3/base/game03.pk4 (2 files)
/home/echo35/doom3/base/game02.pk4 (2 files)
/home/echo35/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
/proc/cpuinfo CPU frequency: 2400.17 MHz
guessing video ram ( use +set sys_videoRam to force ) ..
Setup X display connection
found XNVCtrl extension 1.10
Detected
        2.40 GHz CPU
        2048 MB of System memory
        1024 MB of Video memory on an optimal video architecture

This system qualifies for High quality!
------- Initializing renderSystem --------
idRenderSystem::Shutdown()
signal caught: Segmentation fault
si_code 1
Was in fatal error shutdown: _default material not found
Trying to exit gracefully..

---

### Post by Echo35 on 2006-11-04
Got it working, but now the sound is crap, and I tried getting OSS to work, but I don't have OSS and it won't seem to install right.

---

### Post by Iarwain ben-adar on 2006-11-05
Hi,
did you try this?
```
sudo aptitude install alsa-oss
```
and to start doom3 with aoss
```
doom3 +set s_driver aoss
```


Iarwain

---

### Post by Echo35 on 2006-11-05
Ah, no, havent tried that yet. I'll attempt that once I figure out my other issue. I tried installing oss but it screwed my package managers, so I'll need to get that working before I can install aoss.

---

### Post by Echo35 on 2006-11-08
Nope, I still get choppy sound.

---

### Post by Iarwain ben-adar on 2006-11-09
Maybe [this](http://ubuntuforums.org/showpost.php?p=1063104&postcount=6) can help.
[This](http://ubuntuforums.org/showpost.php?p=1318308&postcount=3) could help aswell.

Hope you get it solved :D


Iarwain

---

### Post by Echo35 on 2006-11-09
Thanks. I'll try those when I get home. This is so annoying, and I have to get it up soon because Microsoft won't send me an updated key, so the copy of XP I bought a few years ago now no longer belongs to me apparantly ](*,)

---

### Post by dmn_clown on 2006-11-09
> **Echo35 said:**
> Thanks. I'll try those when I get home. This is so annoying, and I have to get it up soon because Microsoft won't send me an updated key, so the copy of XP I bought a few years ago now no longer belongs to me apparantly ](*,)

That copy of XP never belonged to you, you only bought the right to use it.  Try reading the licenses before you click through them ;)

Is your problem solved?

---

### Post by Echo35 on 2006-11-09
Oh, right. And now I'm no longer privileged enough to use their product? Sounds like a bunch of crap to me.

---

