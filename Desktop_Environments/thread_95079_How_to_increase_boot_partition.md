---
title: "How to increase /boot partition"
date: 2005-11-25
forum: Desktop Environments
---

### Post by baraider on 2005-11-25
Look like my /boot partition is too small (around 10M) so when i install linux-686 kernel, it doesn't install properly due to the space.

 How do i increase my boot partition to like 100M?

Thanks

---

### Post by psusi on 2005-11-25
You can try using gparted to resize partitions.  You will need to do this from the livecd so it can write to the disk while it is not otherwise in use.  Also 50 MB should be quite sufficient, that's the size I use and I have 3 or 4 kernels on there.  

Then again, you might just forget about having a seperate /boot partition at all and install grub to your root partition.  

[QUOTE=baraider]Look like my /boot partition is too small (around 10M) so when i install linux-686 kernel, it doesn't install properly due to the space.

 How do i increase my boot partition to like 100M?

Thanks[/QUOTE]

---

### Post by baraider on 2005-11-26
Can you please help with what steps i should follow

I download the live cd, boot into the desktop, opened the gparted program, click on the HD but i can't rezise that /boot only...i can only increase the whole ext3 partition


Or i should type something at the boot prompt to get to the command line qparted thing?

---

### Post by psusi on 2005-11-29
[QUOTE=baraider]Can you please help with what steps i should follow

I download the live cd, boot into the desktop, opened the gparted program, click on the HD but i can't rezise that /boot only...i can only increase the whole ext3 partition

[/QUOTE]


This does not make sense to me.  I thought your problem was that /boot was on its own partition, which was too small?

---

