---
title: "Recover Win XP??"
date: 2009-02-04
forum: General Help
---

### Post by Red Sonja on 2009-02-04
I made a fatal mistake.  I first failed to backup my XP Pro system and files before attempting to do an Ubuntu dual boot.  Then worse, I let my friend rush me to install Ubuntu before changing BIOS   boot sequence. :(

Get the picture...  Ubuntu loaded over my XP Pro system.  I almost immediately realized what had happened and pulled that disk OUT and rebooted Ubuntu to a reformatted 320GB drive.

Now the problem...  Is the old corrupted XP boot disk recoverable????  I do have an XP "recovery CD" and a complete XP SP2 system CD.  However, I am worried about the purchased XP software and personal data (docs, pics, etc).

Bottom line, i can remake an XP boot drive, but how do I recover the other stuff on that drive??  I did install this drive (SATA) to MY computer (VISTA) and it doesn't even recognize the drive!!! :(

HELP,
Red Sonja

---

### Post by mb_webguy on 2009-02-04
How far did you get into the installation before you stopped it?  I'm assuming after the partitioner started.  But was it before Ubuntu was installed?  If the drive has been partitioned but *not yet written to*, then it may be possible to recover the data.  Otherwise, you're pretty much out of luck.

---

### Post by niteshifter on 2009-02-04
Hi,

First thing: Stop using the drive. 

Second thing: With another computer get the testdisk / photorec Live CD ISO and burn it (get from [here]("http://www.cgsecurity.org/wiki/TestDisk_Download")). Use that to recover what can be recovered.

Almost certainly you will lose some stuff.

---

### Post by linux_tech on 2009-02-04
If you formatted the drive during reinstall and had data files you wish to recover, then data recovery software is your best bet. You cab download testdisk and run it.  There is very good step by step documentation on their site.

Here are some guides for setting up dual boot-
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

