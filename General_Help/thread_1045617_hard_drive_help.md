---
title: "hard drive help"
date: 2009-01-20
forum: General Help
---

### Post by coops351 on 2009-01-20
hey im a new ubuntu 8.10 user. i recently changed from windows xp to ubuntu and i backed up all my music and documents to my portable hard drive. so once i set my system up with linux i started to transfer my music over to the linux file system but it says it can't mount my hard drive.
has anyone got and tips or solutions to my problem?

cheers

Luke

---

### Post by 67GTA on 2009-01-20
Open a terminal and post the output of ```
sudo fdisk -l
``` with the hard drive plugged in.

---

### Post by coops351 on 2009-01-20
still says unable to mount

---

### Post by dabl on 2009-01-20
If it is a USB drive, you should be able to open the "Media" icon, then right-click on it and choose "mount".

---

### Post by coops351 on 2009-01-20
still nothing? lol

---

### Post by BrandonBan6 on 2009-01-20
when you typed fdisk -l as stated above, it only returned a message cannot mount?

---

### Post by coops351 on 2009-01-20
when i typed in the console all that happens is a list of all the partitions and thats it

---

### Post by 67GTA on 2009-01-20
I need to see that list.

---

### Post by coops351 on 2009-01-20
> **67GTA said:**
> I need to see that list.
luke@luke-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97659103+  83  Linux
/dev/sda2           12159       29179   136721182+   5  Extended
/dev/sda3           29180       30401     9815715   82  Linux swap / Solaris
/dev/sda5           12159       29179   136721151   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xffdf5c44

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60952    30719776+   7  HPFS/NTFS
/dev/sdb2           60953      484520   213478272    f  W95 Ext'd (LBA)
/dev/sdb5           60953      162539    51199816+   7  HPFS/NTFS
/dev/sdb6          162540      264126    51199816+   7  HPFS/NTFS
/dev/sdb7          264127      375872    56319952+   7  HPFS/NTFS
/dev/sdb8          375873      484520    54758560+   7  HPFS/NTFS

---

### Post by BrandonBan6 on 2009-01-20
Oh great, well it should see a partition for your external drive.

something like 
```
 Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

```

so in the terminal type:
```

sudo mount -af /dev/sdc1 /media/extdrive

```

Where "/dev/sdc1" is your actual device path, and "/media/extdrive" is the mount point or folder you want the drive to be stored at. 

Paste the code here if you get stuck.

---

### Post by BrandonBan6 on 2009-01-20
> **coops351 said:**
> luke@luke-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97659103+  83  Linux
/dev/sda2           12159       29179   136721182+   5  Extended
/dev/sda3           29180       30401     9815715   82  Linux swap / Solaris
/dev/sda5           12159       29179   136721151   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xffdf5c44

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60952    30719776+   7  HPFS/NTFS
/dev/sdb2           60953      484520   213478272    f  W95 Ext'd (LBA)
/dev/sdb5           60953      162539    51199816+   7  HPFS/NTFS
/dev/sdb6          162540      264126    51199816+   7  HPFS/NTFS
/dev/sdb7          264127      375872    56319952+   7  HPFS/NTFS
/dev/sdb8          375873      484520    54758560+   7  HPFS/NTFS

hehe, this got posted before I got my post submitted. 

It looks like your external drive has a several partitions, are you wanting to mount them all?

---

### Post by coops351 on 2009-01-20
sudo mount -af /dev/sdb6 /media/Music

would that work?

---

### Post by 67GTA on 2009-01-20
You need to create the directory your going to mount to. ```
sudo mkdir /media/Music
``` then ```
sudo mount /dev/sdb6 /media/Music
```

---

### Post by coops351 on 2009-01-20
what would you recommend? lol


luke@luke-desktop:~$ sudo mkdir /media/Music
luke@luke-desktop:~$ sudo mount /dev/sdb6 /media/Music
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb6': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb6 /media/Music -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb6 /media/Music ntfs-3g force 0 0

---

### Post by 67GTA on 2009-01-20
Is this just a storage partition, or is there an operating system installed on sda6? If it is just storage, then you can just force it: ```
sudo mount -t ntfs-3g /dev/sdb6 /media/Music -o force
``` If it is an operating system, then do a clean boot/shutdown and try again.

---

### Post by coops351 on 2009-01-20
thank you very much guys for your help :D

---

### Post by coops351 on 2009-01-20
so if i want to mount the rest of the partitions just repeat the steps jsut with the relevent partition?

---

### Post by 67GTA on 2009-01-20
You could do that. If this is something you will occasionally mount, it might be easier to mount the whole hard drive. Create a directory for it such as /media/External and then you can access every partition on the drive. 

sudo mount -t ntfs-3g /dev/sdb /media/External -o force

---

### Post by coops351 on 2009-01-20
all the partions are mounted thanks for the help guys :D

---

### Post by 67GTA on 2009-01-20
If you look in /etc/mtab while it is mounted, there will be a temporary mount option. Copy it and add it to your fstab file. Then you can mount it next time by clicking on the hard drive icon.

---

