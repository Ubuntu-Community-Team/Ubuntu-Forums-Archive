---
title: "Grub problem, cant do anything"
date: 2010-06-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mokal on 2010-06-09
Hi,

I have a problem because of a mistake I did today. I have a Mini 10, with windows xp on it. I made a 20gb partition and installed Ubuntu Netbook Remix 10.04 on it.
I ran into some problems with ubuntu, then I just formatted the partition to NTFS using windows. Then when I restarted I got "error: unknown filesystem" and then "grub rescue>".
I dont know what to do now, is there anyway to boot into windows?
There is no recovery drive, no CD drive, Im stuck and would really appreciate the help.
Thanks

---

### Post by oldfred on 2010-06-09
You need to reinstall a windows boot loader to the MBR. Grub is still in the MBR and looking for the partition you deleted to continue to boot. 

The official is to use the windows Cd:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But the windows boot loader just looks for the active partition (boot flag *) in linux and jumps to the windows partitions. There is a generic boot loader that does the same thing. This will not install lilo (which is another boot loader) but just installs the lilo MBR part that will then boot windows. Use the linux install USB flash drive you have. Boot to live system and in terminal:

Restore basic windows boot loader - universe enabled
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

It may give messages about the rest of the boot loader is missing, ignore them.

---

### Post by mokal on 2010-06-11
Thanks oldfred,

My laptop is up and running again.

---

