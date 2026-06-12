---
title: "Where is my swap ?"
date: 2010-08-26
forum: Desktop Environments
---

### Post by dargaud on 2010-08-26
Hello all,
I noticed today that I don't have a swap space anymore. And the partition seems gone too also the PC seems to work fine:

```
# swapon -s
Filename                                Type            Size    Used    Priority

# fdisk -l /dev/sda
Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x281a2819

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801   83  Linux

# swapon -a
swapon: cannot find the device for UUID=cf16708e-d584-43b5-8a14-6e36ae8afc66
```
That leaves 54 Gb unused, which is strange (too much IMHO). Any idea what happened. I originally installed that PC with Ubuntu 8 or 9 and went through the upgrades.

---

### Post by dabl on 2010-08-26
Modern Linux distributions will run OK without swap space, as long as you don't run out of memory.  But it's better to have some swap space (partition or file), for safety.

Hard to say what happened -- a "disappearing" partition is kinda scary, since that is not the type of thing that should happen without you deliberately removing it with a partitioning tool.  Could be corruption in the hard drive partition table -- a very bad thing.

You could boot a Parted Magic Live CD (or GParted or a hundred others), and make a swap partition, and then edit /etc/fstab to mount it at boot time.

---

### Post by dargaud on 2010-08-27
Thanks for the reply. I'm sure I had a swap partition before because I did a 'dd' backup at the device level of the entire disk, I still have it and can see the swap partition on it.
The only thing I can think of is that a couple days ago I mounted some disk with the command "mount /dev/whatever /tmp" instead of "mount /dev/whatever /mnt" Yeah, I know, my mind skipped a beat or something. After a few seconds I got a kernel crash. After that reboot I noticed the missing swap, but it may have been a lot older.

Indeed, I still have "UUID=cf16708e-d584-43b5-8a14-6e36ae8afc66 none swap sw 0 0" in my fstab

If I don't have particular problems I'll probably wait for the next Ubuntu and do a clean reinstall. I don't like to do that because I have a lot of servers running and time consuming to reconfigure.

---

