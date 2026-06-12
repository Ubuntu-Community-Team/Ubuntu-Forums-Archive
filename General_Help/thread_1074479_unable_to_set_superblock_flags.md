---
title: "unable to set superblock flags"
date: 2009-02-19
forum: General Help
---

### Post by doctorltd on 2009-02-19
Hi all!
Please help me to rescue my flash drive! I have xubuntu installed on it and today it refuse to load =( I can mount my flash-drive, but some files disappeared and i can't get write access even with root privileges. 
I tried this:
```

ubuntu@ubuntu:~$ fdisk -l
Disk /dev/sdc: 4016 MB, 4016046080 bytes
128 heads, 63 sectors/track, 972 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Disk identifier: 0x000651ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         896     3612640+  83  Linux
/dev/sdc2             897         972      306432    5  Extended


ubuntu@ubuntu:~$ fsck.ext3 /dev/sdc1
e2fsck 1.41.3 (12-Oct-2008)
/dev/sdc1: recovering journal
fsck.ext3: unable to set superblock flags on /dev/sdc1


ubuntu@ubuntu:~$ e2fsck -b 32768 /dev/sdc1
e2fsck 1.41.3 (12-Oct-2008)
ext3 recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
/dev/sdc1: recovering journal
ext3 recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
e2fsck: unable to set superblock flags on /dev/sdc1

```

What i can do to fix this?

---

### Post by Bachstelze on 2009-02-19
You need to run [font="monospace"]fsck[/font] as root, i.e.:

```
sudo fsck /dev/sdc1
```

---

### Post by doctorltd on 2009-02-19
> **HymnToLife said:**
> You need to run [font="monospace"]fsck[/font] as root, i.e.:

```
sudo fsck /dev/sdc1
```

I tried to do this, but effect was the same =(

I've decided to erase all data from flash. But i can't do it from linux! 
I tried to erase all data with ```
sudo dd if=/dev/zero of=/dev/sdc bs=1M
```. It finishes with no errors, but all data on flash left unchanged. Then i tried to use gparted, it stopes with error. With fdisk after several runs i, thanks God, erase partition information.
Then i tried to format created partition with sudo mkfs.ext3 /dev/sdc1.
I can't remember what was the error, but i can't format flash-drive.

As the last possible variant i run my old rescue cd with dos-utilities. I tried at least 10 different utilities, anything wont work. And when i was ready to broke this flash, i found tool that helped me to make logical partition and erase all other data from flash. Then i rebooted in Windows, it found my flash and ask to format it. After that everything works. 

It is very pity, that i cant do it from linux =( Sorry for my English, bye!

---

