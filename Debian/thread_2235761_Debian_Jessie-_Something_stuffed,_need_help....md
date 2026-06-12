---
title: "Debian Jessie- Something stuffed, need help..."
date: 2014-07-22
forum: Debian
---

### Post by leezer32 on 2014-07-22
So, apologies if this seems like a ramble.

The basic setup is as follows:
Debian Jessie server, various disks in several LVMs etc.
Root is on /dev/sdc1 (This sometimes varies if booted from USB, it's set via UUID in FSTAB)

The problems all started when I upgraded Wheezy to Jessie. Seemed like a good idea at the time.....
The first sign that something was wrong is that my Netbios name resolution keeps stopping working. Never had a problem with it before, but it's randomly dropping out. That's irritating, but restarting SAMBA or the box usually fixes it, so I'd been ignoring it.
Two weeks ago I then discovered that I was out of space on the root partition (20gb). This was traced back to a seriously oversize apt package list directory- I found several old bugs on the subject, deleted the files and decided that it was probably an artifact of the upgrade and so left alone.

The primary problem is now. I rebooted today in an attempt to get Netbios working, and discovered I was dumped into a rescue shell with RO root filesystem.
I then booted from a livecd & ran a FSCK on the root and /home partitions, which both came up clean.
Rebooted again, and was dropped straight back into the rescue shell....

At the moment, I've removed the RO on errors from my fstab, which gives me a perfectly working system, but I'm concerned there is something more fundamental up.
This is the current fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=3fd325b7-e9c1-4f3d-8bff-df62cd3f3a8f /               ext4 noatime   0       1
# /home was on /dev/sdd5 during installation
UUID=7aa21c46-b667-4a13-b358-8f21026a02a9 /home           ext4    defaults,noatime        0       2
# swap was on /dev/sdd6 during installation
UUID=fceb3cf6-3fba-4ece-b2f7-52c7ca9343b0 none            swap    sw              0       0

#Media Drive 1 ( LVM )
UUID=5331dca6-c790-4aa1-8b0c-908fe2d8eae6 /mnt/media xfs defaults,noatime,nodiratime 0 2
#Media Drive 2
UUID=35773233-3c4d-4b2c-bcfe-209f5b85c500 /mnt/media2 xfs defaults,noatime,nodiratime 0 2
#Media Drive 3
UUID=9ab5de7b-95db-497d-bc88-29c07d34fcae /mnt/media3 xfs defaults,noatime,nodiratime 0 2
#Downloads Drive
UUID=ae0a526c-d7e2-4010-8cf0-21c00f54d00d /mnt/downloads xfs defaults,noatime,nodiratime 0 2
#Media Drive 4
UUID=fc8528a8-2452-4e2b-a4ec-4e329f32839b /mnt/media4 xfs defaults,noatime,nodiratime 0 2
```

Thoughts? :)

---

### Post by Tadaen_Sylvermane on 2014-07-27
Only thought I have is you should never use a testing / experimental distro on something like a server. Am curious for an update else bumping to find out other ideas.

---

