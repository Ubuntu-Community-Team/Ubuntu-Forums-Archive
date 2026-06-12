---
title: "Erased 512 Bytes from Disk, HELP!"
date: 2008-12-04
forum: General Help
---

### Post by jorl17 on 2008-12-04
I am in such a mess, sorry if I sound completely stupid but I am extremely stressed.

While testing around some operating system development I had to write a hello world bootsector to a floppy drive. It's ok, I've done this around 1000 times, but this time, I misspelled it and, instead of /dev/sde, I wrote /dev/sda.

This means that I just wrote a bootsector (512 bytes) which probably will say Hello World (if it will even do that) to my harddisk.

I'm still on this computer with it on and am only planning to shut it down when I know there is nothing I can do to get everything I have back.

I checked Gparted and it reports that there is no partition table in /dev/sda, obvious...

Yet, I am still able to write to the filesystems as long as I stay on with my PC. This means that if I manage to find on which sectors each partition starts, I only have to recreate the partition table, that is, write to the disk the partition table, without actually deleting anything there is in there.

After that, I'd be able to install GRUB again and all would be OK (I think, or am I wrong?).

**So, could you please URGENTLY help me? I need help on how to, keeping my data, recover the 512 beginning bytes. Please help me and give me suggestions and instructions on how to do this.**

---

### Post by jorl17 on 2008-12-04
I installed testdisk, found my partition table and wrote it. Now with gparted it seems to find it. I'm just too scared I might have lost the MBR. Anyway I think I'm gonna have a go at rebooting unless you have any suggestions, backup stuff or anything.

---

### Post by jorl17 on 2008-12-04
Ok testdisk fixed it and I also rewrote the MBR after that using dd. Thanks for any help you thought of providing. You may now close this topic.

Thanks.

---

