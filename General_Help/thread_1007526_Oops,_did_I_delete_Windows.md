---
title: "Oops, did I delete Windows?"
date: 2008-12-10
forum: General Help
---

### Post by Minuet on 2008-12-10
I thought I partitioned the drives so I would have Windows XP and Ubuntu on the same computer. How do I get to Windows? :| How do I know if I really did get rid of Windows completely?

---

### Post by barisurum on 2008-12-10
You should be able to see and browse the ntfs partition with windooz installed in the Places menu

---

### Post by taurus on 2008-12-10
Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Minuet on 2008-12-10
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37825   303829281   83  Linux
/dev/sda2           37826       38913     8739360    5  Extended
/dev/sda5           37826       38913     8739328+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb27a8cb

   Device Boot      Start         End      Blocks   Id  System

```

Thanks.

---

### Post by taurus on 2008-12-10
Well, you have only Ubuntu on the first harddrive and your second harddrive doesn't have a partition yet so you can't use it for now.  When you installed Ubuntu, did you tell the installer to use the whole disk because I don't see windows partition anywhere on the first harddrive?

---

### Post by oldos2er on 2008-12-10
No Windows there, just Linux.

---

### Post by Minuet on 2008-12-10
> **taurus said:**
> Well, you have only Ubuntu on the first harddrive and your second harddrive doesn't have a partition yet so you can't use it for now.  When you installed Ubuntu, did you tell the installer to use the whole disk because I don't see windows partition anywhere on the first harddrive?

I partitioned the drive 50/50, but my computer kinda froze in that step so I restarted it and I think it just partitioned the entire thing the second time.:confused:

And I didn't understand "your second harddrive doesn't have a partition yet so you can't use it for *now*". What do you mean? Can I install Windows on it or what? 

Sorry, I'm such a noob with this. I only need Windows for *one* program, and it doesn't work with wine.

---

### Post by TeXtonyx on 2008-12-10
> **Minuet said:**
> ```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37825   303829281   83  Linux
/dev/sda2           37826       38913     8739360    5  Extended
/dev/sda5           37826       38913     8739328+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb27a8cb

   Device Boot      Start         End      Blocks   Id  System

```

Thanks.

It certainly looks like you deleted Windows if it was installed
on your first drive which is sda, you didn't report about sdb.

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS
/dev/sda2            9730       19012    74565697+  83  Linux 
/dev/sda3         19013       19457     3574462+  82  Linux swap

Since most people start with Windows it is installed on the first
drive on the first partition, sda1 (1 is the partition number).

Unless you have a very old Windows OS, which might be System fat32
the System is NTFS which is Windows XP or Vista. Your fdisk report
doesn't display any ntfs partition unlike my example which shows
you how it should look if you still had Windows. 

So there are some partition recovery tools which sometimes work.
But if I were you, it's quicker just to restore Windows from
your backup. Speaking of which, I came across a nice backup tool
for Linux just today. [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by Minuet on 2008-12-10
Thank you. I guess I'll just reinstall Windows XP. I installed it myself last time but I feel it's a little different this time. Do I insert the XP cd, restart, then what? I don't want to overwrite the Ubuntu installation.

---

### Post by Atzu on 2008-12-10
You can try this: 
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by Minuet on 2008-12-10
> **Atzu said:**
> You can try this: 
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Thanks, that worked perfectly! I just wish it would automatically give me the option to boot in Ubuntu or XP. I have to press 'esc' when GRUB is loading.

---

### Post by PocketDog on 2008-12-10
Odd, have you enabled hiddenmenu? Either way, could you paste the contents of your grub menu? ```
gksudo gedit /boot/grub/menu.lst
``` and we'll fix that for you

---

### Post by Minuet on 2008-12-10
Ah, I forgot to add that. I just added the "#" so it's probably fixed. Thank you.

---

### Post by Atzu on 2008-12-10
> **Minuet said:**
> Thanks, that worked perfectly! I just wish it would automatically give me the option to boot in Ubuntu or XP. I have to press 'esc' when GRUB is loading.

Go terminal and type:
gksudo gedit /boot/grub/menu.lst

If you don't want to press ESC then search for the line with "hiddenmenu" and add a "#" in front of it, if you want more time for selecting the OS then search for the "timeout" line and change the number to a number(in seconds) you like or if you don't want to have timeout just add "#" in front of that line.

---

### Post by dragos_iliescu_2005 on 2008-12-10
I had this problem several time in the past. At that time I solve this by following way:
- first, prepare the installation. Using Live CD, delete everything you will not need on the new installation. Only files, do not delete partitions.
-second, start to install Windows. You can select to format or keep format as you decide for the windows partition. Clean install is better.
-last, install Ubuntu, do not format partition. In this way you will keep pre-existent files. (Generaly, better way is to keep important files on a different partition than the OS)

In my case this way worked. But today I pay much more attention to my back-up. Is more rapid and convenient.

---

