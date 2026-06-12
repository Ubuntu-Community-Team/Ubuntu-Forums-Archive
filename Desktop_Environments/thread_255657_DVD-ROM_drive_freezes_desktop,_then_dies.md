---
title: "DVD-ROM drive freezes desktop, then dies"
date: 2006-09-11
forum: Desktop Environments
---

### Post by youspeakmylanguage on 2006-09-11
I have been using Ubuntu now for almost a year and a half, but this is only my second post on these forums. Please forgive my noobieness.

I have experienced my first major problem with an Ubuntu release, in this case Ubuntu (w/GNOME) 6.06 LTS. Also, this is the first time I have had a problem that I haven't found a quick fix for in these forums. I hope someone can help. To start - I am familiar with basic use of Ubuntu and Linux functions but I am not familiar with advanced Linux administration or any sort of real programming.

My DVD-ROM drive will not read CDs or DVDs. The drive will open when requested, and will initially seem to read the disc. Then the computer will freeze for approximately 30 seconds. This message appears in the syslog:

> Sep 11 19:21:21 localhost kernel: [XXXXXXXX.xxxxxx] hdc: DMA timeout retry

the computer will resume normal activity, and then approximately 30 seconds later it will repeat the above action:

> Sep 11 19:22:22 localhost kernel: [XXXXXXXX.xxxxxx] hdc: DMA timeout retry
Sep 11 19:36:56 localhost kernel: [XXXXXXXX.xxxxxx] ide-cd: cmd 0x28 timed out

When I attempt to mount the drive from the command line I get this:

> Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: block device /dev/hdc is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdc,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so

Here is my fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I'm positive this is NOT a hardware issue, unless the drive has just malfunctioned in some way in the past week. The DVD-ROM drive has worked with the last two Ubuntu releases and with Windows XP before that. The drive is powered and is spinning the discs.

I'm also pretty sure that this is not a singular or unique incident, even though I have not found a solution on these forums. Other users are experiencing similar problems, although they seem to be related to a DVD burner drive instead of a DVD-ROM.

Any assistance that can be provided will be greatly appreciated.

---

### Post by youspeakmylanguage on 2006-09-11
help!

---

### Post by youspeakmylanguage on 2006-09-12
PLEASE help! This will be my last bump.

---

