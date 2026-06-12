---
title: "doom3-demo noobie question"
date: 2006-11-26
forum: Gaming &amp; Leisure
---

### Post by tedrampart on 2006-11-26
so bear with me,.. I'm a linux noob..

I just installed doom3-demo on here.. (amd64 on an X2 with 1gb ram, and an nvidia geforce 6150).. and everytime I run it, it crashes and I'm thrown back into the login manager.  I've tried the oss method and no esd and such.. but it does the same thing everytime.  I don't know how to check the log files to  post here, or decipher other log files on the same issue.. I've searched but haven't found anything..

also, if this can be fixed, is it possible to use the windows retail version to install on linux..or is that just a pipe dream?

---

### Post by tedrampart on 2006-11-27
so here's the output of the startup... although I don't know what it all means.. I figure its something to do with the "can't find" sorta parts near the end.. 

DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 192.168.0.101/255.255.255.0
------ Initializing File System ------
Loaded pk4 /home/manimal/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /home/manimal/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /home/manimal/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /home/manimal/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /home/manimal/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /home/manimal/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /home/manimal/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /home/manimal/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /home/manimal/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /home/manimal/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /home/manimal/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /home/manimal/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/manimal/.doom3/base
/home/manimal/doom3/base
/home/manimal/doom3/base/pak007.pk4 (38 files)
/home/manimal/doom3/base/pak006.pk4 (48 files)
/home/manimal/doom3/base/pak005.pk4 (63 files)
/home/manimal/doom3/base/pak004.pk4 (5137 files)
/home/manimal/doom3/base/pak003.pk4 (4676 files)
/home/manimal/doom3/base/pak002.pk4 (6120 files)
/home/manimal/doom3/base/pak001.pk4 (8972 files)
/home/manimal/doom3/base/pak000.pk4 (2698 files)
/home/manimal/doom3/base/game03.pk4 (2 files)
/home/manimal/doom3/base/game02.pk4 (2 files)
/home/manimal/doom3/base/game01.pk4 (2 files)
/home/manimal/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480

also output to errors.txt and got this...

X connection to :0.0 broken (explicit kill or server shutdown).

---

### Post by tedrampart on 2006-11-27
oh, and I forgot to add, that I decided to try it using the retail version of doom3 I had.. I didn't know you could just copy the pk4 files off the disc and use an installer.. (which is cool if I can get it to work...)

---

### Post by tedrampart on 2006-11-28
just updated to the new beta drivers, and it fixed my problem.. now I just have to get sound working....back to the search I go...

---

