---
title: "can't access my windows partition"
date: 2005-12-02
forum: Desktop Environments
---

### Post by tazzik on 2005-12-02
I have my windows partition (ntfs) at /dev/hda1, it seems to mount ok and can only be SEEN by root and me only by sudo. I want to be able to write and delete files to and from it from my user within nautilus (im new to linux, if im confusing please try to understand). So my /etc/fstab is:```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    rw,user         0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
please try and help, I have tried putting "rw,user" into the options on /dev/hda1
cheers
tazzik

---

### Post by teaker1s on 2005-12-02
take a look [here]("http://ubuntuguide.org/#mountunmountntfs")

---

### Post by mrmcctt on 2005-12-02
I believe this is what it should look like. ```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```

Check your /media folder and make sure the drive is named 'hda1' like in your fstab.  Mine is named windows but yours may be different.

I got my drive to automount using [this link]("http://ubuntuguide.org/#automountntfs") in the Ubuntu Guide.

---

### Post by tazzik on 2005-12-03
it has all the options there except ntfs read write
can someone tell me how to do this please
tazzik

---

### Post by towsonu2003 on 2005-12-03
you cannot write to ntfs partition... it's just not possible (and not safe at all). sorry...

also, try to use your ntfs as infrequently as possible if you are not using something like clamav (antivirus) under linux so that you won't transfer viruses from your linux to your windows...

you may wanna plan for a fat32 partition as a transfer area between windows and linux. I am using one, 1GB, works nicely...

PS. or, better yet, buy a small (256MB?) flash usb drive thing.

---

### Post by tazzik on 2005-12-03
ok ill reinstall windows on a fat partition
(can i re-format the windows partition even after ive installed ubuntu) will the windows bootloader get rid of the grub one.
I tried doing windows after ubuntu before and if broke my ubuntu. couldnt get the grub bootloader and couldn't see the hdd etc...
tazzik

---

### Post by towsonu2003 on 2005-12-03
you can format the windows partition after installing ubuntu... ** always do backup** as this will erase everything under windows partition (and under ubuntu partition as well if you make a mistake)...

I forgot the details though :) you'll need a howto for partitioning & a live cd...

installing windows will screw grub, but it's easy to recover! check out this link which uses the ubuntu install cd in rescue mode to reinstall grub:

try this: [http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

It says:
-------
Q: How to restore GRUB menu after Windows installation?

   1. Read General Notes
   2. Read How to use Ubuntu Installation CD, to gain root user access? (boot:rescue)
   3.

      e.g. Assumed that /dev/hda is the location of /boot partition

   4.

      # grub-install /dev/hda

I believe your case is /dev/hda as well...

---

### Post by tazzik on 2005-12-03
which of the hdas is my boot partition?

---

### Post by tazzik on 2005-12-03
some help please

---

### Post by mrmcctt on 2005-12-03
[QUOTE=tazzik]which of the hdas is my boot partition?[/QUOTE]

In looking at your /etc/fstab I am assuming that you have one hard drive in your system.  If that's the case, your /dev/hda is your boot partition.

---

### Post by tazzik on 2005-12-03
but in /etc/fstab there is no /dev/hda 
which hda# is it

---

### Post by mrmcctt on 2005-12-03
[QUOTE=tazzik]but in /etc/fstab there is no /dev/hda 
which hda# is it[/QUOTE]

What I used for my set up was to put the 'boot flag' on /dev/hda1 (my ntfs partition).

---

