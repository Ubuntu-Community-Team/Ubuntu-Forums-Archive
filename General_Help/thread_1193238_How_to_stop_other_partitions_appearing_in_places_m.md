---
title: "How to stop other partitions appearing in places menu"
date: 2009-06-21
forum: General Help
---

### Post by jonboy99 on 2009-06-21
Hi folks, just installed a copy of ubuntu ibex on a comp with several other partitions, for a family member's use.
I don't want them to be able to access and potentially mess up the other partitions, so when installing ubuntu I told the installer not to mount other partitions. 
My fstab makes mention only of my / and /home partions and nothing else.

Yet when I go to the places menu, all the other partitions (including the windows ones) are listed, and accessible just by clicking on them. 

How do I remove them from this menu?  They are not in the nautilus bookmarks menu.  I do not need to make them particularly secure, just not have them so easily accessible.

Thanks

Jon

---

### Post by paperplate9 on 2009-06-21
Just make a dummy entry in /etc/fstab for the partition...won't show up.

Note: just discovered by accident so can't really explain the rules that govern it.

---

### Post by Gen2ly on 2009-06-21
Possibly using gparted, selecting the partition, right click > Properties then selecting "hidden" will do?

---

### Post by jonboy99 on 2009-06-21
Tried the dummy entry thing - it appears anything with a mount point in the /media directory will show up in the places menu, so setting any other mount point than there does the trick.
Cheers folks.
Jon

---

### Post by paperplate9 on 2009-06-21
> **jonboy99 said:**
> Tried the dummy entry thing - it appears anything with a mount point in the /media directory will show up in the places menu, so setting any other mount point than there does the trick.
Cheers folks.
Jon

Ok. Yeah I was using /mnt as my mount point, guess that's rule #1 - don't mount in /media.

---

### Post by egalvan on 2009-06-21
Anything in **/media** show up in "Places", and mounted, if possible.

Anything in **/mnt** does not automatically show up anywhere,. unless the "automount" option is set.

A savvy user can still navigate to **/mnt** and click on the devices, though.


I have my internal Windows NTFS partitions mounted this way,
in **/mnt** without automount

---

### Post by paperplate9 on 2009-06-21
> **egalvan said:**
> Anything in **/mnt** does not automatically show up anywhere,. unless the "automount" option is set.

Ah, another thing I forgot.

---

