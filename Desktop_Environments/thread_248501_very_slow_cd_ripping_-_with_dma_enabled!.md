---
title: "very slow cd ripping - with dma enabled!"
date: 2006-09-01
forum: Desktop Environments
---

### Post by amagee on 2006-09-01
I've been struggling to get Dapper to rip CDs at a reasonable speed for some time now.  I've read various threads which invariably point to DMA being the problem, however hdparm claims it is enabled:

bob@bob:~$ sudo hdparm /dev/cdrom

/dev/cdrom:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

Is the final line relevant to the problem?  If not, what else can I do to improve the speed?  It takes 10 minutes to rip a CD to flac in Dapper (using whatever program: KAudioCreator, grip, even dbPowerAmp running under XP on vmware), but it takes 2 minutes on Windows XP on the same machine.  Thanks in advance for any help.

---

### Post by capnrick on 2006-10-01
I am having the same problem, although I am using AMD64.  I had gentoo before and it ripped songs about 5x faster.  The encoding part is about the same speed.  I also have dma turned on, and that HDIO_GETGEO failed argument shows up on my hdparm too.  Any clues anyone?

---

### Post by offramp13 on 2006-10-01
I am experiencing the same thing, i am running an AMD64 processor, but not 64 bit ubuntu.

---

### Post by amagee on 2006-10-02
I'm also on an AMD64, running the 32-bit version of ubuntu.  This seems to be a common theme...?

---

### Post by StefanoCole on 2006-10-02
HDIO_GETGEO refers to the device geometry and it makes sense only in the case of hard discs. So, in the case of cdroms it does not apply and you get the 
> HDIO_GETGEO failed: Invalid argument

message.

Stefano

---

