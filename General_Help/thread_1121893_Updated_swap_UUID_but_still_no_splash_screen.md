---
title: "Updated swap UUID but still no splash screen"
date: 2009-04-10
forum: General Help
---

### Post by aheckler on 2009-04-10
I recently moved some partitions around on my drive. I knew it would change the UUID of my swap partition, so I updated /etc/fstab and /etc/initramfs-tools/conf.d/resume to reflect the new UUID, but my Ubuntu splash screen still dumps me back into a "text only" boot. The relevant info is below. Halp!

**sudo blkid:**
```
/dev/sda1: UUID="2f7d56bf-b413-4994-b71d-98155d0f474d" TYPE="ext3" 
/dev/sda2: UUID="4fecd27d-ba21-4be4-9d50-6f8000957478" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda3: TYPE="swap" UUID="[COLOR="Red"]df374ac6-6b44-4c1b-8b85-4a5dbfa4e1c3[/COLOR]" 
```

**cat /etc/fstab:**
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2f7d56bf-b413-4994-b71d-98155d0f474d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=4fecd27d-ba21-4be4-9d50-6f8000957478 /home           ext3    relatime        0       2
# /dev/sda3
UUID=[COLOR="Red"]df374ac6-6b44-4c1b-8b85-4a5dbfa4e1c3[/COLOR] none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# For security reasons, as per: https://help.ubuntu.com/community/StricterDefaults
tmpfs     /dev/shm     tmpfs     defaults,ro     0     0
```

**cat /etc/initramfs-tools/conf.d/resume:**
```
RESUME=UUID=[COLOR="Red"]df374ac6-6b44-4c1b-8b85-4a5dbfa4e1c3[/COLOR]
```

EDIT: If it matters, I'm running a 64-bit installation of Intrepid.

---

### Post by plucky on 2009-04-10
I think you have to also update the initramfs using the command ```
sudo update-initramfs -u -k all
```

Good luck

---

### Post by aheckler on 2009-04-10
That did it, thanks!

---

