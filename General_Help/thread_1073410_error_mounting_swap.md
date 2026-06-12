---
title: "error mounting swap"
date: 2009-02-18
forum: General Help
---

### Post by alfonz19 on 2009-02-18
Hi, 

my swap does not get mounted and I do not know why. Everything was all-right, but then I moved swap partition. I've already corrected /etc/fstab entry (uuid value), but problem is still here.

this is my entry in /etc/fstab
UUID=2031d8bb-b7b8-48f7-abc3-315968a263b0 none swap sw 0 0
and uuid is coherent to one found in /dev/disk/by-uuid

do you have any hints what could be wrong?
thanks in advance 
alfonz.

---

### Post by geirha on 2009-02-18
Do you get any messages if you run the following? ```
sudo swapon -a
```

---

### Post by albandy on 2009-02-18
if you moved your swap partition this UUID=2031d8bb-b7b8-48f7-abc3-315968a263b0 is not valid.

type blkid in terminal
then a list of uuid will appear
search for swap and edit /etc/fstab with the correct uuid

---

### Post by alexh3791 on 2009-02-18
> **albandy said:**
> if you moved your swap partition this UUID=2031d8bb-b7b8-48f7-abc3-315968a263b0 is not valid.

type blkid in terminal
then a list of uuid will appear
search for swap and edit /etc/fstab with the correct uuid

This worked right away for me using Ubuntu 8.10.

This problem has frustrated me ever since I put in a new hard drive.

-Thanks a lot!

---

### Post by drs305 on 2009-02-18
> **alfonz19 said:**
> my swap does not get mounted and I do not know why. Everything was all-right, but then I moved swap partition. I've already corrected /etc/fstab entry (uuid value), but problem is still here.

this is my entry in /etc/fstab
UUID=2031d8bb-b7b8-48f7-abc3-315968a263b0 none swap sw 0 0
and uuid is coherent to one found in /dev/disk/by-uuid

Run this to ensure the swap uuid you are getting is current and not cached:
```
sudo blkid -c /dev/null
```

---

### Post by caljohnsmith on 2009-02-18
Alfonz19, how about posting the output of the following:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```
Also, do you get the Ubuntu splash screen on start up OK?

EDIT: Dave, we posted at the same time. :)

---

### Post by alfonz19 on 2009-02-19
> **geirha said:**
> Do you get any messages if you run the following? ```
sudo swapon -a
```

that's ok.

> **albandy said:**
> if you moved your swap partition this UUID=2031d8bb-b7b8-48f7-abc3-315968a263b0 is not valid.

type blkid in terminal
then a list of uuid will appear
search for swap and edit /etc/fstab with the correct uuid

AND

> **drs305 said:**
> Run this to ensure the swap uuid you are getting is current and not cached:
```
sudo blkid -c /dev/null
```

That helped. Thanks a lot. Question. How actually /dev/disk/by-uuid/ works? I mean, I thought that it shows current uuid of some partition, but that's turns out to be wrong. So it reflects just some information store somewhere in cache or what? 

> **caljohnsmith said:**
> Alfonz19, how about posting the output of the following:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```
Also, do you get the Ubuntu splash screen on start up OK?

EDIT: Dave, we posted at the same time. :)

Thanks for trying to help me, I appretiate it.

---

### Post by alfonz19 on 2009-02-19
one more question. This problem always really sucks me on windows, but I'm convinced that it can be solved in linux (on windows I've never found solution). Right now I've tested whether the swap is working. I've to launch few really hungry applications to run out of memory. Swap works, but now I've got 0.5GB in swap and can shut down most of those applications (since I do not need them). Doing so I end up with empty physical memory and partially filled swap and with some applications running slower than it can run(since their data has to be fetched from swap). Is there a command forcing to empty swap back to primary memory(i.e. try to move as much data as possible back to prim. memory)?

---

### Post by geirha on 2009-02-19
> **alfonz19 said:**
> 
That helped. Thanks a lot. Question. How actually /dev/disk/by-uuid/ works? I mean, I thought that it shows current uuid of some partition, but that's turns out to be wrong. So it reflects just some information store somewhere in cache or what? 


They are created by udev. So to be certain they are up to date, either reboot or just restart udev. ```
sudo /etc/init.d/udev restart
```

---

### Post by geirha on 2009-02-19
> **alfonz19 said:**
> one more question. This problem always really sucks me on windows, but I'm convinced that it can be solved in linux (on windows I've never found solution). Right now I've tested whether the swap is working. I've to launch few really hungry applications to run out of memory. Swap works, but now I've got 0.5GB in swap and can shut down most of those applications (since I do not need them). Doing so I end up with empty physical memory and partially filled swap and with some applications running slower than it can run(since their data has to be fetched from swap). Is there a command forcing to empty swap back to primary memory(i.e. try to move as much data as possible back to prim. memory)?

If data in swap is needeed, it will be moved to physical memory. I don't think you lose much performance from it. However, if you unmount the swap, it will copy everything from swap to physical memory. Just make sure you have enough physical memory :)

```

sudo swapoff -a # unmount all currently mounted swap partitions
# Check that the status is as expected
swapon -s
free
sudo swapon -a  # mount all swap partitions listed in fstab again.

```

---

### Post by alfonz19 on 2009-02-19
> **geirha said:**
> They are created by udev. So to be certain they are up to date, either reboot or just restart udev. ```
sudo /etc/init.d/udev restart
```

I write it in longer way, just to be sure I understand it right.

After I moved partition, swap stops working. I ignored it, since I did not need to use ALL my physical memory. So few poweroffs&system starts occured until I wanted to solve it and realized that it's probably caused by wrong uuid. So assume that /dev/disk/by-uuid are up-to-date after restart, then my approach by copying this uuid into /etc/fstab should work, but it didn't. So I presume, these files (in /dev/disk/by-uuid) are created not on basis of scanning partitions and their attributes, but are build from informations stored in /etc/fstab. Right?

---

### Post by albandy on 2009-02-19
We can solve it using the old way.

First  make a list of your partitions in all your disk:

sudo fdisk -l /dev/sda (for first disk)
sudo fdisk -l /dev/sdb (for second disk)

then type the result here.
After doing it we will modify /etc/fstab without using UUID

---

### Post by alfonz19 on 2009-02-19
> **geirha said:**
> If data in swap is needeed, it will be moved to physical memory. I don't think you lose much performance from it. However, if you unmount the swap, it will copy everything from swap to physical memory. Just make sure you have enough physical memory :)

```

sudo swapoff -a # unmount all currently mounted swap partitions
# Check that the status is as expected
swapon -s
free
sudo swapon -a  # mount all swap partitions listed in fstab again.

```


Yep, I know, that when they're needed they will be swapped back to primary. But when you have large application(moreover composed from many small modules) which get swapped out then you can suffer from that quite a long time since each module is swapped back only when it's needed.

I've tried your code and have few questions. 
1. what actually happens when I turn it off and do not have enough memory (I'm not going to try it). Will I lose data or command will fail?
2. when checking whether I have enough of space I've notice, that space has priority -1. That's contradicting with man, since there is said that priority is between 0 and 32767. But ok, I assume that -1 means priority is not set. Right. But after unmounting and mounting again (in way you've mentioned) the priority changed to -2. What's that?

---

### Post by geirha on 2009-02-19
udev's job is to scan all hardware and create device nodes for it under /dev. When it does the first harddrive, it creates /dev/sda, then scans all the partitions. For each partition, it creates a corresponding /dev/sdaX and also adds a link in /dev/disk/by-uuid/ for the uuid of the filesystem, and in /dev/disk/by-label if the filesystem has a label. So, the UUIDs in /dev/disk/by-uuid/ really should be up-to-date after a reboot. The file /etc/udev/rules.d/60-persistent-storage.rules contains the rules for udev to do this.

Don't know why this wasn't the case for you ... perhaps I'm just wrong about how udev works.

Did you run mkswapfs after the last reboot? that would've changed the UUID at least ...

---

### Post by alfonz19 on 2009-02-19
> **albandy said:**
> We can solve it using the old way.

First  make a list of your partitions in all your disk:

sudo fdisk -l /dev/sda (for first disk)
sudo fdisk -l /dev/sdb (for second disk)

then type the result here.
After doing it we will modify /etc/fstab without using UUID

no, no. You did not understand me. Everything's working fine now(swap's working). I'm just trying to understand how thing works, especially why my first attempt failed.

---

### Post by alfonz19 on 2009-02-19
> **geirha said:**
> udev's job is to scan all hardware and create device nodes for it under /dev. When it does the first harddrive, it creates /dev/sda, then scans all the partitions. For each partition, it creates a corresponding /dev/sdaX and also adds a link in /dev/disk/by-uuid/ for the uuid of the filesystem, and in /dev/disk/by-label if the filesystem has a label. So, the UUIDs in /dev/disk/by-uuid/ really should be up-to-date after a reboot. The file /etc/udev/rules.d/60-persistent-storage.rules contains the rules for udev to do this.

Don't know why this wasn't the case for you ... perhaps I'm just wrong about how udev works.

Did you run mkswapfs after the last reboot? that would've changed the UUID at least ...

no I did not run mkswapfs ever. I do not even know what this command  does (I've get come guesses, of course, but since I did not find man for this, I'm not running it).

---

### Post by geirha on 2009-02-19
> **alfonz19 said:**
> 
I've tried your code and have few questions. 
1. what actually happens when I turn it off and do not have enough memory (I'm not going to try it). Will I lose data or command will fail?


Haven't tried that either, but I think either, the kernel detects that you are out of memory and the oomkiller starts killing off random processes, or swapoff fails to unmount the swap. If the first thing happens, it will probably end badly. Would be a fun thing to try in a virtual machine :)
> **alfonz19 said:**
> 
2. when checking whether I have enough of space I've notice, that space has priority -1. That's contradicting with man, since there is said that priority is between 0 and 32767. But ok, I assume that -1 means priority is not set. Right. But after unmounting and mounting again (in way you've mentioned) the priority changed to -2. What's that?

From what I understand, if you set the priority yourself, it must be 0 or higher. If you don't set the priority, it will use a lower priority than any of the other swap partitions. I'm guessing that's why your new swap partition got an even lower priority than your previous.

---

### Post by geirha on 2009-02-19
> **alfonz19 said:**
> no I did not run mkswapfs ever. I do not even know what this command  does (I've get come guesses, of course, but since I did not find man for this, I'm not running it).

My bad. The command I meant was mkswap. It formats the swap partition, creating a new swap filesystem (with a new UUID).

---

### Post by alfonz19 on 2009-02-19
> **geirha said:**
> Haven't tried that either, but I think either, the kernel detects that you are out of memory and the oomkiller starts killing off random processes, or swapoff fails to unmount the swap. If the first thing happens, it will probably end badly. Would be a fun thing to try in a virtual machine :)


From what I understand, if you set the priority yourself, it must be 0 or higher. If you don't set the priority, it will use a lower priority than any of the other swap partitions. I'm guessing that's why your new swap partition got an even lower priority than your previous.

sounds sensible, thanks for explaining.

> **geirha said:**
> My bad. The command I meant was mkswap. It formats the swap partition, creating a new swap filesystem (with a new UUID).

no, I did not do that, so that (maybe) weird behavior isn't lurking from this corner. Moreover I can't see why creaing a new swapspace should change uuid of existing partition, but maybe I'm just shortsighted since I'm REALLY new to linux administration.

---

