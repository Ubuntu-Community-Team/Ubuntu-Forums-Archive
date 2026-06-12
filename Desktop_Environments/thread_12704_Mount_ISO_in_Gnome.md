---
title: "Mount ISO in Gnome?"
date: 2005-01-26
forum: Desktop Environments
---

### Post by ScruffyEU on 2005-01-26
Why can't I mount iso files when I try this code:

$ sudo modprobe loop 
$ sudo mount -t iso9660 -o loop file.iso /mnt/iso
($) umount /mnt/iso

At second, will this message show up:

"mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       or too many mounted file systems
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)"

What am I doing wrong?

---

### Post by AndersAA on 2005-01-26
personally I generally losetup /dev/loop1 file.iso then mount -t iso9660 /dev/loop1 /mnt/cdrom.

If it still fails try : [http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/) :)

---

### Post by ScruffyEU on 2005-01-26
CDemu looks nice, how do I install it don't really under stand this line 

# you need the source of your current running kernel.
/lib/modules/$(shell uname -r)/build/include needs to point at it.

Thanks for the answer.  :)

---

### Post by AndersAA on 2005-01-26
[QUOTE=ScruffyEU]CDemu looks nice, how do I install it don't really under stand this line 

# you need the source of your current running kernel.
/lib/modules/$(shell uname -r)/build/include needs to point at it.

Thanks for the answer.  :)[/QUOTE]

write uname -r :)

if you install kernel headers (should be in synaptic, try searching for header) it should compile and install fine :)

---

### Post by ScruffyEU on 2005-01-26
Thanks, got it working  \\:D/

---

