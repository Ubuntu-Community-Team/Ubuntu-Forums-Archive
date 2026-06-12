---
title: "Xine can't play DVDs"
date: 2005-09-07
forum: Desktop Environments
---

### Post by filemanager on 2005-09-07
With any DVD I put in, I get the following error message upon clicking the "DVD" button:

> 
The source seems encrypted, and can't be read.
Your DVD is probably crypted. According to your country laws
you can or can't install/use libdvdcss to be able to read this
disc, which you bought (Media stream scrambled/encrypted)


When I go into Synaptic, libdvdcss cannot be found, and neither can libdvdcss2. I did an apt-get update, but it it doesn't come up. I'm running an amd64 system.

If I try to play the DVD using Totem, I get this error message:

> 
Totem could not start up.

ALSA device "default" is already in use by another program.


---

### Post by amohanty on 2005-09-07
Have you enabled universe in your repos?
Also (I am not sure of this - writing from a win2K box) add backports to your repos list and look for it again.

Instructions to add repos can be found on the forums and int he official wiki (link on top right).

HTH
AM

---

### Post by arnieboy on 2005-09-07
[QUOTE=filemanager]With any DVD I put in, I get the following error message upon clicking the "DVD" button:



When I go into Synaptic, libdvdcss cannot be found, and neither can libdvdcss2. I did an apt-get update, but it it doesn't come up. I'm running an amd64 system.

If I try to play the DVD using Totem, I get this error message:[/QUOTE]
[http://ubuntuguide.org#repositories](http://ubuntuguide.org#repositories)
make ur /etc/apt/sources.list look like the one shown at that site. then:
```
sudo apt-get update
sudo apt-get install  libdvdcss2
```

---

### Post by filemanager on 2005-09-07
Here's my sources.list file, is it right?

> 
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


---

### Post by arnieboy on 2005-09-07
[QUOTE=filemanager]Here's my sources.list file, is it right?[/QUOTE]
these guys keep moving apps in and out of backports. try changing all ca.archive.ubuntu.com  to archive.ubuntu.com and then do a:
```
sudo apt-get update
```

---

### Post by filemanager on 2005-09-07
Ok, I copied and pasted the sources.list file from that page, and did an sudo apt-get update, and still no libdvdcss package =\

---

### Post by sandmanfvr on 2005-09-07
[QUOTE=filemanager]Ok, I copied and pasted the sources.list file from that page, and did an sudo apt-get update, and still now libdvdcss package =\[/QUOTE]
 What I did was I copied and pasted the ENTIRE file on that guide into the file, didn't want to risk typing one thing wrong.  Try that, then do the update.

---

### Post by filemanager on 2005-09-07
Ok I did that but still no workie.
when I type "sudo apt-get install libdvdcss2" I get this error message:

> 
Package libdvdcss2 is not availble, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


---

### Post by filemanager on 2005-09-07
Fixed it! Thanks all.

[http://ubuntuforums.org/showthread.php?t=60014&page=2&pp=10&](http://ubuntuforums.org/showthread.php?t=60014&page=2&pp=10&)

---

### Post by LongTooth on 2005-09-07
I might as well jump in on this topic. I too can't play DVDs. I've checked to see if I have the two libs in question installed and I do. 

Inserting a DVD, opening Totem and selecting "play Disc 'CD-ROM/DVD-ROM DRIVE'" I get this error message: Failed to play Audio/Video Disc. Please check that a disk is present in the drive. Of course there is one in the drive. 

my /etc/fstab information if this will help solve my problem. 

--------------------------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

-----------------------------------------------------------------------------------------------------

Thanks.

---

### Post by arnieboy on 2005-09-07
[QUOTE=LongTooth]I might as well jump in on this topic. I too can't play DVDs. I've checked to see if I have the two libs in question installed and I do. 

Inserting a DVD, opening Totem and selecting "play Disc 'CD-ROM/DVD-ROM DRIVE'" I get this error message: Failed to play Audio/Video Disc. Please check that a disk is present in the drive. Of course there is one in the drive. 

my /etc/fstab information if this will help solve my problem. 

--------------------------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

-----------------------------------------------------------------------------------------------------

Thanks.[/QUOTE]
the error happens because u have 2 cd/dvd drives and the player checks in the wrong one. u have to point it to the correct drive.

---

### Post by LongTooth on 2005-09-07
From Arnieboy:" ...u have to point it to the correct drive." Just how do I do this?

Thanks.

---

### Post by ricesteam on 2005-09-12
Followed the solution, installed libdvdcss2, but DVDs still don't play. 

Anyone else having issues?

---

