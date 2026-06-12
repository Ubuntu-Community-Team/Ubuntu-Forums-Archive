---
title: "kernel updates keep messing up grub!"
date: 2006-09-16
forum: Desktop Environments
---

### Post by dguido on 2006-09-16
Every time I encounter a kernel update, Ubuntu takes it upon itself to move the root=/dev/hda3 in my menu.lst to root=/dev/sda3!  Why in the world would it do something like that?  I have no OS installed on /dev/sda3 and the entire sda disk has no bootable partitions.  What is going on?

---

### Post by llamakc on 2006-09-16
So after you do boot up, do you edit /boot/grub/menu.lst to the way it should be?

If so, be sure to run: sudo update-grub

---

### Post by lenticular on 2006-09-16
Same prob here.  After the last update, menu.lst was rewritten so grub decided that my XP lived on some other partition.  Why would the update do that?  There must be some intelligence to the way it handles menu.lst since it kept my custom grub colors, yet the partition options seem to get blown away or mangled.

At least it would be nice if the update made a backup copy of menu.lst before digging in.  This is the kind of prob that would really freak out newbies.

-John

---

### Post by llamakc on 2006-09-16
Where are you defining your partition options at in the file?

---

### Post by konst88 on 2006-09-16
menu.lst has a section named:AUTOMAGIC KERNELS LIST, and there you should specify the kernel options.
for example:
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

in this example hda6 is the kernel partition. there you should write your partiton, so the automatic menu.lst will be correct.

---

### Post by dguido on 2006-09-17
> **llamakc said:**
> So after you do boot up, do you edit /boot/grub/menu.lst to the way it should be?

If so, be sure to run: sudo update-grub

Yes, every time I update grub (99% of the time through a kernel update) I edit menu.lst and switch back all the sda3's to hda3's.

I ran sudo update-grub and it just switched everything back to sda3 again!  ARGGG.

---

### Post by dguido on 2006-09-17
> **konst88 said:**
> menu.lst has a section named:AUTOMAGIC KERNELS LIST, and there you should specify the kernel options.
for example:
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

in this example hda6 is the kernel partition. there you should write your partiton, so the automatic menu.lst will be correct.

I changed kopt=/dev/sda3 to kopt=/dev/hda3 (not groot).  After running update-grub it kept hda3 as the root device :-).  Thank you!

---

### Post by lha on 2006-09-17
> **konst88 said:**
> menu.lst has a section named:AUTOMAGIC KERNELS LIST, and there you should specify the kernel options.
for example:
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

in this example hda6 is the kernel partition. there you should write your partiton, so the automatic menu.lst will be correct.

Grub starts numbering from zero, so (hd0,6) refers to hda7.

---

