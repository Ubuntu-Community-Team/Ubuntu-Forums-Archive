---
title: "Ubuntu breaks Windows 7"
date: 2009-01-11
forum: General Help
---

### Post by Moptop650 on 2009-01-11
Hey,
I've been working on setting up an OsX/Ubuntu/Windows 7 tri boot. It works, but: After I install Windows 7, I can reboot to OsX then back to 7 just fine. But, after I boot to Ubuntu then try to use Windows 7 again, it cannot boot, "BOOTMGR is missing, press CTRL+ALT+DEL to reboot.

So the way I see it, Ubuntu is doing something that BREAKS Windows 7. Any ideas?

---

### Post by jonabyte on 2009-01-11
Well it is still beta...normally I would install Windows first, then add other OS's for booting.

---

### Post by melojo on 2009-01-11
> **Moptop650 said:**
> Hey,
I've been working on setting up an OsX/Ubuntu/Windows 7 tri boot. It works, but: After I install Windows 7, I can reboot to OsX then back to 7 just fine. But, after I boot to Ubuntu then try to use Windows 7 again, it cannot boot, "BOOTMGR is missing, press CTRL+ALT+DEL to reboot.

So the way I see it, Ubuntu is doing something that BREAKS Windows 7. Any ideas?

Since windows 7 is still in beta I would think that it has something to do with windows 7.  I have not had any issues with xp or vista booting after being in Ubuntu.  It may be MS way of saying hey you have linux on your system and I don't want to play nice with a free operating system because it doesn't allow me to take complete control of your computer!!! :p

---

### Post by teddks on 2009-01-11
This is not a bug, it is a feature.

---

### Post by destructaball on 2009-01-11
I installed 7 just fine only problem im having is moving between the OS's part from the basic MBR bug which can be fixed by booting in a live disc.

---

### Post by Moptop650 on 2009-01-11
I mounted the windows partition in ubuntu, and I noticed, that IT HAS BEEN WIPED! 

So after booting Ubuntu, It got wiped?! Everything except the "Temp" folder is gone!

So I did an experiment. I installed windows 7, then booted ubuntu, shut it down, then booted ubuntu. The windows partition was WIPED again.

This isn't windows 7 fault. Ubuntu is killing it.

Could this be a ntfs-3g bug?

---

### Post by hikaricore on 2009-01-11
Are you 100% sure that ***dows7 is using a standard NTFS filesystem and not some kind of weird hybrid?

If this is the case it may not be a bug persay but an incompatibility.

---

### Post by hikaricore on 2009-01-11
Are you 100% sure that ***dows7 is using a standard NTFS filesystem and not some kind of weird hybrid?

If this is the case it may not be a bug persay but an incompatibility.

---

### Post by Moptop650 on 2009-01-11
I don't remember where, but somewhere listed it as HTFS/NTFS (Possibly HPFS/NTFS?).

Would uninstalling NTFS-3g remedy this?

---

### Post by hikaricore on 2009-01-11
Yea if you have any doubts about the filesystem DO NOT mount it.

Take it out of your fstab, no reason to uninstall ntfs-3g.

---

### Post by Moptop650 on 2009-01-11
That sounds good, but I'm not sure how to do that.

Here's my /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=81ba08cc-f85b-4ed8-8514-983d915b50d7 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

From my inexperienced view, it doesn't seem to be in there. (I don't have it set to mount at boot), I don't think its in there. But I could be wrong, I've never messed with fstab before.

Edit: /dev/sda4 would be the windows partition.

---

### Post by Moptop650 on 2009-01-12
Bump: I tried reinstalling NTFS-3g anyways. 

Same issue.

:/

---

### Post by Moptop650 on 2009-01-12
Bump

---

### Post by cariboo on 2009-01-12
Instead of reinstalling, you should have taken some time to investigate further. You won't see Windows7 in fstab, unless you specifically put it there. To check which patition it is installed on you can use:

```
sudo fdisk -l
```

This will list all your partitions and you should see the NTFS/HPFS partition listed there. To mount it type:

[CODE]sudo mount /dev/<partition> /mnt/CODE]

where <partition> is the partition windows7 is installed on.

I'm not exactly sure, but if Windoiws7 is the same as all the rest of the Windows versions, the bootloader has to be on the first partition of the first hard disk.

Jim

---

### Post by Moptop650 on 2009-01-12
That would put it on my EFI partition.. Which it SHOULDN'T/CAN'T be...

And that's what I did when I noticed the 7 partition had been wiped...

---

### Post by Moptop650 on 2009-02-04
Bump..

---

