---
title: "Fix wrong partition mount at book"
date: 2010-11-04
forum: Desktop Environments
---

### Post by Tarrasque on 2010-11-04
Hello everybody.

I have an installed and completeli functioning Kubuntu 10.10 distro. During installation I chose to bind a couple of existing partitions on the disk to /mnt/shareddisk and /mnt/fat32disk.

Then, I installed another Linux distro, and I resized the "shareddisk" partition in order to make room for it.

Now Kubuntu doesn't recognize the partition and fires an error at boot, where it asks me to (S)kip the auto mount or (M)anually fix the problem.

Skipping the mount brings up Kubuntu normally. I can access the partition from Dolphin by clicking on the drive icons on the left, but it's not automatically mounted anymore.

How can I fix the problem and "mount again" the shareddisk partition at boot time?

Thank you very much.

---

### Post by Zorael on 2010-11-04
When you resized the partition it probably assumed a new UUID, which is (in most cases) used as an identifier when mounting filesystems at boot. If so, it's trying to mount your old UUID and failing.

So make sure that the partition's entry in **/etc/fstab** refers to the correct UUID. You can list UUIDs of available parititons with '**sudo blkid**'.

For instance;
```
$ **sudo blkid**
/dev/sda1: LABEL="RECOVERY" UUID="A05E-0310" TYPE="vfat" 
/dev/sda6: LABEL="swap" UUID="271467da-45c3-4047-b445-19929c58ab91" TYPE="swap" 
/dev/sda2: LABEL="XP" UUID="02F840B6F840A9AD" TYPE="ntfs" 
/dev/sda4: UUID="bfe2926e-f8bf-41dd-a237-690b609cafe6" TYPE="ext4" 
/dev/sda5: LABEL="**[COLOR="Green"]home[/COLOR]**" UUID="**[COLOR="Green"]92905906-f227-49fb-ac5a-72e7bff3a796[/COLOR]**" TYPE="ext4" 
/dev/sdc1: LABEL="PLEIADES" UUID="9637-7E77" TYPE="vfat"

$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                                 <mount point>   <type>  <options> <dump> <pass>
proc                                            /proc           proc    defaults,noatime 0 0
UUID=bfe2926e-f8bf-41dd-a237-690b609cafe6       /               ext4    errors=remount-ro,noatime,nobarrier,commit=60 0 1
UUID=**[COLOR="Green"]92905906-f227-49fb-ac5a-72e7bff3a796       /home[/COLOR]**           ext4    defaults,noatime,nobarrier,commit=60 0 2
UUID=02F840B6F840A9AD                           /main           ntfs    defaults,fmask=113,dmask=002,gid=999,uid=999 0 0
UUID=271467da-45c3-4047-b445-19929c58ab91       none            swap    sw 0 0
```

---

### Post by Tarrasque on 2010-11-04
Thank you very much.

Just to know, is there a tool in KDE Settings I might have overlooked to do the same thing?

Not that I fear editing the fstab file, but adding new disks is such a common thing nowadays that I'd be perplexed if the Desktop Environment didn't provide a graphical tool for this.

Thanks again!!

---

### Post by Zorael on 2010-11-04
I don't think there is.

fstab is in one of those grey zones, seeing as it's *technically* not part of the desktop environment (instead part of the linux platform), so it's *technically* outside of KDE's juristiction. Then again they named the configuration center "System Settings" and not "KDE Settings", so it's a bit vague where the multiplatform KDE stops and the platform-specific linux bits begin.

---

