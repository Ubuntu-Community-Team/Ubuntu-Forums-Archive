---
title: "Removing Swap file/making swap partition permanent"
date: 2009-06-20
forum: General Help
---

### Post by cybrosh on 2009-06-20
Hi,

My Laptop is a dual boot system,4GB ram, primary vista, secondary Ubuntu Jaunty. 

I've had a 1 GB swap file, and I couldn't hibernate or suspend propertly, so eventually I've decided to create a permanent 4GB swap linux partition.

I need to edit the fstab file to make the swap partition permanent and get rid of the swap file.

Here's the fstab : 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
```

blkid : 
```
/dev/loop0: UUID="1c825e8c-5016-4547-90e7-76419d71b217" TYPE="ext3" 
/dev/sda1: UUID="E282E86F82E8499D" LABEL="ServiceV002" TYPE="ntfs" 
/dev/sda2: UUID="907E56E27E56C0A0" LABEL="SW_Preload" TYPE="ntfs" 
/dev/sda3: UUID="5CF81535F8150F40" LABEL="Ubuntu" TYPE="ntfs" 
/dev/sda4: UUID="a16a0b3e-5042-4dc5-918a-7682b2543870" TYPE="swap"
```

Help, anyone? I'm kind of confused as to writing the last line in the fstab....

*also, would I need to do something for hibernation? (Set it to the new swap partition?)

Cheers

---

### Post by cybrosh on 2009-06-20
added 

```
/dev/sda4       none            swap    sw              0
```

As the last line instead of the swap file line, and I can see it as activated, but I'm not sure if I'm doing it all right? Anyone?

Cheers

---

