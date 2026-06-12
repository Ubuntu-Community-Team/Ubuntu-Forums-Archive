---
title: "Doom3 Throws Segmentation Fault and Won't Launch"
date: 2012-02-14
forum: Gaming &amp; Leisure
---

### Post by drmrgd on 2012-02-14
I just followed the community directions to install Doom 3 on my Kubuntu partition.  Been running it fine on Windows for a while now, and thought I'd try on the Linux side.  I'm running Kubuntu 32-bit with an Nvidia GeForce 6800 using nvidia_173 drivers.  

After copying all of the files to the correct locations and running "doom3", I'm getting the following:

```
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.1.3/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /usr/local/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/dave/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak008.pk4 (3 files)
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
WARNING: file sound/lights.sndshd, line 866: Expecting '{' but found '30'
WARNING: file sound/lights.sndshd, line 867: Expecting '{' but found '220'
WARNING: file sound/lights.sndshd, line 867: Expecting '{' but found '15'
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
idRenderSystem::Shutdown()
```

I searched the web for a while and found that most of the other people having problems usually get past this step and are having problems with their graphics drivers.  I'm not sure I'm even getting that far, though.  I can't seem to see what I'm missing here, and I can't find this specific error on the web anywhere.  It's a long shot, but does anyone have any idea why I'm getting a segmentation fault before it starts loading the graphics components?  Maybe I'm missing a library somewhere?

I can't find the file that throwing the warning and I'm wondering if it's part of one of the .pk4 files.  Checksum seems OK.  But maybe there's a corrupt file in there somewhere?

---

### Post by drmrgd on 2012-02-15
Well.....I think I "fixed" this.  Despite there being a good checksum on all of the .pk4 files (at least compared to the output I've seen from others), pak003.pk4 is likely to be corrupt.  This archive is where the sounds are, including the lights.sndshd file that seems to be throwing the error.  If I manually extract the archive, I find that lights.sndshd is actually empty, although it's not supposed to be.  Actually removing that whole .pk4 file from the base directory will allow me to run the game fine - but without any sounds!  

After more digging I found that this file is on Disc 3, which I remember was giving me some problems when I was copying it over.  So, it looks like I might have to get a new copy of the game since my Disc 3 might be mucked up.  Oh well.

Solved!

---

