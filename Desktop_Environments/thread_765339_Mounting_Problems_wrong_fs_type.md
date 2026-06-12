---
title: "Mounting Problems wrong fs type"
date: 2008-04-24
forum: Desktop Environments
---

### Post by acrane1 on 2008-04-24
I recently installed another Hard drive on my computer. I am running Ubuntu Gusty. the hard drive was working fine except for the fact that it would not auto mount after reboot and mount have to remount. The hard drive is an internal 500gb western digital formated to extended ext3 with a single partition. My friend who is much more knowledgeable with linux than me tried to fix the auto mount problem. what i think he did was mount it using the command mount -a -o auto. now after restart i am getting this warning message when i try to mount the drive since it is still not auto mounting. 
The waring i got was cannot mount volume.

details
mount:wrong fs type, bad option, bad superblock on /dev/sdb5,   missing codepage or header program, or other error. In some cases useful info is found in syslog -try dmesg | tail or so

I typed in dmesg | tail and got
[   33.200000] hda-intel: Invalid position buffer, using LPIB read method instead.
[   46.496000] eth0: no IPv6 routers present
[   74.540000] JBD: Clearing recovery information on journal
[   77.796000] kjournald starting.  Commit interval 5 seconds
[   77.796000] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[   77.800000] EXT3 FS on sdd1, internal journal
[   77.800000] EXT3-fs: mounted filesystem with ordered data mode.
[  107.664000] EXT2-fs: sdb5: couldn't mount because of unsupported optional features (4).
[  147.380000] EXT2-fs: sdb5: couldn't mount because of unsupported optional features (4).
[  538.704000] EXT2-fs: sdb5: couldn't mount because of unsupported optional features (4).



I've got no idea how to fix it any ideas???

---

### Post by adamitj on 2008-04-24
You have created the partition, but have you formatted it?

mkfs.ext3 /dev/sdb5

If did it already, I really don't know what it could be. I had problems with SCSI disks when the SCSI controller card wasn't so updated as the HD. The only way I could fix was buy a new Adaptec Scsi card.

---

### Post by acrane1 on 2008-04-25
yeah the drive is formatted and there is data on the drive. I have been using the drive on the machine for about a week now and it worked fine except for having to mount it every time I booted up the computer. We remounted the drive but did so using the permissions and classifications listed above and now it wont mount

---

### Post by logos34 on 2008-04-25
> **acrane1 said:**
> 
[   77.796000] EXT3-fs warning: mounting fs with errors, [COLOR="Red"]running e2fsck is recommended[/COLOR]

I've got no idea how to fix it any ideas???

Did you run fsck?

---

### Post by acrane1 on 2008-04-25
no i didn't I missed that line when i was looking at it. I fixed the problem though, it was trying to mount the drive under the wrong filesystem type. So i just had to change the mount options to specify that it was an ext3

---

