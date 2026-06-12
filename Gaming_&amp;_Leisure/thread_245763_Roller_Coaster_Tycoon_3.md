---
title: "Roller Coaster Tycoon 3"
date: 2006-08-28
forum: Gaming &amp; Leisure
---

### Post by mikesena on 2006-08-28
I want to try and install RCT3 using cvscedega.  I have installed it, but i don't know if im configured correctly.```
[Drive C]
"Path" = "/home/meo/.cvscedega/drive_c"
"Type" = "hd"
"Label" = "Dos Drive"
"Filesystem" = "win95"
 
 [Drive D]
 "Path" = "/media/cdrom"
 "Type" = "cdrom"
 "Label" = "CD-ROM"
 "Filesystem" = "win95"
 "Device" = "/dev/hdc"
 
[Drive E]
"Path" = "/tmp"
"Type" = "hd"
"Label" = "tmp"
"Filesystem" = "win95"
 
[Drive G]
"Path" = "/"
"Type" = "hd"
"Label" = "root"
"Filesystem" = "win95"
```

I don't know how to access my D:.  I type in:```
cvscedega D:
```and it returns this:```
meo@meo-laptop:~$ cvscedega D:
fixme:cdrom:CDROM_GetIdeInterface not implemented for true scsi drives
/usr/lib/cvscedega/bin/wine: cannot open 'D:\'
```How do I fix this problem?  Also, how do I then install things?  Im used to the wine, winecfg, winefile etc. of wine.  i don't know how cvscedega works.

Also, I've heard cedega is better for games.  RCT3 got a silver wine cert. back in kubuntu 5, but ubuntu 6.06 it is garbage.  I would like to try in cvscedega anyway.

Someone help! :)

---

### Post by mikesena on 2006-08-29
anyone?

---

### Post by mikesena on 2006-08-30
please?

---

### Post by Astinsan on 2009-04-20
Install PlayOnLinux. It has a front end to setting up most games... It also has the ability to use many different versions of wine on the same machine. 

To answer your question (be it late) You can access the cdrom via the normal automounts.. IE: drives that automount in the /media directory off your root.

To change this you need to run cedagas version of winecfg. (which is what you can used with normal wine.

As far as setting up rct3.. it doesn't work with wine yet.. Soon it may. This is because the authors used lame direct calls to extra dlls dealing with sound and graphics. If I get it running on my system I'll let ya know

---

