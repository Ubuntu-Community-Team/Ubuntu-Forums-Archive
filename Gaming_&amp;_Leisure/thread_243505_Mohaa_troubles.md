---
title: "Mohaa troubles"
date: 2006-08-25
forum: Gaming &amp; Leisure
---

### Post by shunkk on 2006-08-25
Hello, i see this thread [http://www.ubuntuforums.org/showthread.php?t=213945&highlight=MOHAA](http://www.ubuntuforums.org/showthread.php?t=213945&highlight=MOHAA) but i still having trouble with this...

I install mohaa everything goes well, but when the installation finish and I try to start the game, the terminal show me this.

```
dk-WARNING **: locale not supported by C library

Copying file from Disc 2


Extracting files from Disc 1

--- Common Initialization ---
Medal of Honor Allied Assault 1.11 linux-i386 Sep  3 2004
----- FS_Startup -----
Current search path:
/root/.mohaa/main
/usr/local/games/mohaa/main
/usr/local/games/mohaa/main/pak7es.pk3 (102 files)
/usr/local/games/mohaa/main/pak6es.pk3 (471 files)
/usr/local/games/mohaa/main/pak5.pk3 (259 files)
/usr/local/games/mohaa/main/pak4.pk3 (593 files)
/usr/local/games/mohaa/main/pak3.pk3 (669 files)
/usr/local/games/mohaa/main/pak2.pk3 (4722 files)
/usr/local/games/mohaa/main/pak1.pk3 (396 files)
/usr/local/games/mohaa/main/pak0.pk3 (11174 files)
/media/cdrom0/main

----------------------
18386 files in pk3 files
execing default.cfg
execing menu.cfg
couldn't exec newconfig.cfg
Config: unnamedsoldier.cfg
STUB: wtf in unix/linux_general_extras.c line 95.
STUB: wtf in unix/linux_general_extras.c line 101.
couldn't exec configs/unnamedsoldier.cfg
couldn't exec localized.cfg
execing autoexec.cfg
Unknown command "fov"
couldn't exec custom.cfg
You are now setup for easy mode.
----- Client Initialization -----
Called FadeSound with: 0.000000
----- Initializing Renderer ----
----- R_Init -----
...loading libGL.so: Initializing SDL OpenGL display
...setting mode 3: 640 480
Attempting 4/4/4 Color bits, 24 depth, 0 stencil display...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17
```

I need a patch? or something else?    By the way, i have a Sapphire ati radeon x550, Athlon 64 +3000@2400, 1024 MB of ram. I install this driver [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300) (i can't found one for my especific hardware). Maybe this is getting me troubles, but i don't know where find a driver for my video card :/.    My apologies for my english, I'm complete newbie at this, please don't assume to much please :).

Thanks for your time.

Regards.

---

### Post by shunkk on 2006-08-26
This problem fix with the install the ati software and this first step [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

just for the records :).

---

