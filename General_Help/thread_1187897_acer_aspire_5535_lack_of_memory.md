---
title: "acer aspire 5535 lack of memory"
date: 2009-06-15
forum: General Help
---

### Post by searover on 2009-06-15
I installed 9.04 a few days ago, I followed the prompts and installed as default there appeared to be 2 drives both 67gig I left vista on the machine, the default said that each operating system would have 67gig. the drives are acer and data, I though it strange that nether were mounted when the system was running, today the update manager would not install the updates because it thinks there is not enough memory. how can I get around this, I got ubuntu on my other computer but am no computer buff,

---

### Post by nothingspecial on 2009-06-15
Open a terminal (in your menu acessories > terminal) and post the output of ```
sudo fdisk -l
```

---

### Post by searover on 2009-06-15
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
dave@dave-laptop:~$

---

### Post by nothingspecial on 2009-06-15
It`s a little L not number 1

```
sudo fdisk -l
```

---

### Post by searover on 2009-06-15
sorry not used to command lines
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40a4e3e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275       10367    73028608    7  HPFS/NTFS
/dev/sda3           10367       19132    70401880    7  HPFS/NTFS
/dev/sda4           19133       19457     2610562+   5  Extended
/dev/sda5           19133       19435     2433816   83  Linux
/dev/sda6           19436       19457      176683+  82  Linux swap / Solaris
dave@dave-laptop:~$

---

### Post by nothingspecial on 2009-06-15
I should have done this together -

Now ```
df -h
```

---

### Post by searover on 2009-06-15
dave@dave-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   29M  99% /
tmpfs                 1.4G     0  1.4G   0% /lib/init/rw
varrun                1.4G  104K  1.4G   1% /var/run
varlock               1.4G     0  1.4G   0% /var/lock
udev                  1.4G  172K  1.4G   1% /dev
tmpfs                 1.4G  488K  1.4G   1% /dev/shm
lrm                   1.4G  2.4M  1.4G   1% /lib/modules/2.6.28-11-generic/volatile
dave@dave-laptop:~$

---

### Post by nothingspecial on 2009-06-15
> **searover said:**
> dave@dave-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
[COLOR="Red"]/dev/sda5             2.3G  2.2G   29M  99% /[/COLOR]
tmpfs                 1.4G     0  1.4G   0% /lib/init/rw
varrun                1.4G  104K  1.4G   1% /var/run
varlock               1.4G     0  1.4G   0% /var/lock
udev                  1.4G  172K  1.4G   1% /dev
tmpfs                 1.4G  488K  1.4G   1% /dev/shm
lrm                   1.4G  2.4M  1.4G   1% /lib/modules/2.6.28-11-generic/volatile
dave@dave-laptop:~$

That`s your problem. Ubuntu is full because it`s only 2.3gigs. You really need a minimum of 5 gigs.

Is your windows full of important files or is this a new box?

---

### Post by searover on 2009-06-15
I only have windows to operate things like my g3 dongle, blackberry backup and my tom tom updater and such like, things that don't self load ect

---

### Post by nothingspecial on 2009-06-15
What you need to do is boot into windows and defrag it.

Then back up anything you don`t want to loose.

Then boot your live cd and go to system > administration > partition editor.

You need to delete /dev/sda5. That is your tiny Ubuntu partition.

/dev/sda2 is windows.

Do you know what /dev/sda1 /dev/sda3 and /dev/sda4 are?

I suspect that /dev/sda1 is a recovery partition but what about the other 2.

If they have nothing of value on them then I would delete /dev/sda4 aswell then grow /dev/sda3 into the free space. Then install ubuntu to that new larger partition.

To do this during the install select manual partitioning (advanced). When the partition editor fires up leave sda1 and sda2 alone.
Make /dev/sda6 2gigs and allocate it to swap.
The select your new partition /dev/sda3 and asign it a mountpoint of / and select format to ext3.
[COLOR="Red"][SIZE="3"]
This will completely erase anything that was on those 3 partitions[/SIZE][/COLOR]

This advice is based on my experience of dual booting different linux distros. I have never dual booted windows. You may want to wait for more advice.

Read all you can about manually partitioning for a dual boot before you do this.
[COLOR="Red"][SIZE="5"]
Do not get it wrong or you could destroy windows[/SIZE][/COLOR]

If you don`t understand what you are doing, don`t do it untill you do.

Good luck.

---

### Post by searover on 2009-06-15
I did notice that on bootup there are 2 lots of windows on offer the one on reboot wants to recover, the other just boots as normal, thanks for your assistance and patience, I'll have a little potter.

---

