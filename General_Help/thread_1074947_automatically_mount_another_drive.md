---
title: "automatically mount another drive"
date: 2009-02-19
forum: General Help
---

### Post by barraymian on 2009-02-19
hi all,

I've two drives. driveA has Ubuntu(8.10) installed and driveB has other stuff. 

I want to have driveB mounted automatically so that the icon for this drive on my desktop stays there after i restart and i don't have to go in "Places" to open the drive.

Secondly, Ubuntu calls this driveB "New Volume", is there a way i can change this name?

thank you

---

### Post by taurus on 2009-02-19
If you want to mount a second drive automatically each time you boot Ubuntu, you could add an entry in /etc/fstab for it.

Open a terminal and post the outputs of these commands.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
id
```

---

### Post by barraymian on 2009-02-21
Hello, here is the output of the commands. I ran these commands as root

**_sudo fdisk -l_**
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x83115876

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69e469e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30139   242091486   83  Linux
/dev/sdb2           30140       30515     3020220    5  Extended
/dev/sdb5           30140       30515     3020188+  82  Linux swap / Solaris

**_sudo blkid_**
/dev/sda1: UUID="DC20DEC620DEA734" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb1: UUID="44c94d69-65fa-4cd0-82f4-a9cbe708b340" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="781192ad-4cd6-4c98-8bcb-30face73f504" 


**_cat /etc/fstab_**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=44c94d69-65fa-4cd0-82f4-a9cbe708b340 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=781192ad-4cd6-4c98-8bcb-30face73f504 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

**_df -h_**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             228G  5.2G  211G   3% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  124K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  104K  505M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-11-generic/volatile

**_id_**
uid=0(root) gid=0(root) groups=0(root)

---

### Post by taurus on 2009-02-21
When you said driveB, I assume you mean /dev/sda1 since is your ntfs drive.  Install ntfs-config and use it to configure your /dev/sda1, by adding an entry in /etc/fstab so it would be mounted automatically each time you boot.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```
It's highly recommended you run those commands as regular user instead of logging in as root.

---

### Post by barraymian on 2009-02-21
alright so i ran all those commands and ran ntfs-config and this is what i got which doesn't look right. I was reading somewhere that if it can't see the drives then thats a problem but no solution was provided.

[[IMG]http://img150.imageshack.us/img150/1462/ntfsconfigcopy.th.jpg[/IMG]](http://img150.imageshack.us/my.php?image=ntfsconfigcopy.jpg)

and when i press OK, nothing really happens and this window closes

---

### Post by barraymian on 2009-02-23
nevermind the above message. It works fine, i guess i had to restart the machine? but now "NTFS Configuration Tool" appears in my Applications/System Tools menu

thank you very much

---

