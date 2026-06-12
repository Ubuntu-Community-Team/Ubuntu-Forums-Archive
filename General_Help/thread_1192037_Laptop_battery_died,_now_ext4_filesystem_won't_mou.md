---
title: "Laptop battery died, now ext4 filesystem won't mount for boot"
date: 2009-06-19
forum: General Help
---

### Post by Frem on 2009-06-19
So, I'm using the 64-bit version of Ubuntu 9.04 on a laptop. The filesystem is ext4.

Now, the Gnome power manager is set to automatically turn my computer off if battery life is critical. It didn't, and the system was not turned off properly. I was using Firefox and OpenOffice at the time.

When I got to a wall outlet and plugged the laptop back in, there were a lot of boot errors saying things about mpage_da_map_block, block allocation failed, bad manager magic in super-block, io manager magic bad, there will be data loss, etc.

I tried to run the disk checking program, and it said that there would be data loss, and failed.

I rebooted. When it came up again, it just couldn't mount the partition and dumped me into a busybox shell. I was unable to find the disk check command like before.

Help!

---

### Post by salemboot on 2009-06-20
Boot with a live-disc and go to a Terminal
Applications // Accessories // Terminal

figure out what your partitions look like
sudo fdisk -l /dev/sda

usually sda1 is the primary if you did the default install.

sudo fsck.ext4 /dev/sda1

Be careful about the choices you make.  But in general it's safe to accept the actions, hit Y and relax.

If that don't work.  ...

---

