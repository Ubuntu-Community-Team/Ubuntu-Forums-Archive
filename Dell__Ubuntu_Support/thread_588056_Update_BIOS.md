---
title: "Update BIOS"
date: 2007-10-23
forum: Dell  Ubuntu Support
---

### Post by trondhuso on 2007-10-23
Does anyone know if Dell has released a BIOS upgrade utility? Both D630 and D420 has a BIOS upgrade available.

**UPDATE:**
This is what you have to do to update your BIOS for your Dell D420 (will probably also work under D630 and other D-series Dell laptops):
```
$ wget -q -O - http://linux.dell.com/repo/firmware/bootstrap.cgi >  bootstrap.sh
$ sudo  bash bootstrap.sh
$ sudo aptitude install firmware-addon-dell
$ sudo aptitude install firmware-tools
$ sudo aptitude install $(sudo bootstrap_firmware -a)
$ sudo update_firmware --yes
```

As of today the latest BIOS for D420 is A06. For D620/D630 it is A10.

my kernel:
```
$ uname -r
2.6.24-16-generic
```

---

### Post by bwakkie on 2007-10-23
latest version is A03

---

### Post by trondhuso on 2007-10-23
> **bwakkie said:**
> latest version is A03

I'm running d420 and it has d03, but here the latest is d04 (I got another D420 with D04-Bios that's how I know). On D630 it is d03, but some shipped Dells has d02...
Anyway the problem still remains, how do we upgrade the BIOS on Dell Latitude computers.

-t-

---

### Post by Skweek on 2007-10-23
I had to do this recently on my 1720 - It wasn't that straight forward though as I do not have access to a windows box.  What I did...

I downloaded the BIOS from Dell support.
Installed a quick Virtualbox Win2k.
In win2k did the following;
Installed Nero
Downloaded a win98 bootdisk image from Bootdisk.com
Downloaded VFD (Virtual Floppy drive program)
mounted the 98 Bootdisk image using VFD and removed everything except command.com
Copied the BIOS file to the floppy.
Created an image of the floppy using VFD
Used Nero to create a bootable CD using the Newly created floppy image.
Plopped CD into drive.
Reboot
Got an A:> prompt
Ran the BIOS program.

Job done.

Phew.

---

### Post by trondhuso on 2008-05-27
I have managed to update my bios under Linux. I'll post the description later.

---

