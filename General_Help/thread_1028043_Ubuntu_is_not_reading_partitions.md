---
title: "Ubuntu is not reading partitions"
date: 2009-01-02
forum: General Help
---

### Post by Liliitha on 2009-01-02
Back in Fiesty Fawn and Gutsy Gibbon I could read the C: drive partition on my computer.  But now in Intrepid Ibex I cannot see my windows filesystem.  How can I fix this?

---

### Post by dcstar on 2009-01-02
> **Liliitha said:**
> Back in Fiesty Fawn and Gutsy Gibbon I could read the C: drive partition on my computer.  But now in Intrepid Ibex I cannot see my windows filesystem.  How can I fix this?

What doesn't "see" it?, is it in Places-Computer?

---

### Post by Liliitha on 2009-01-02
> **dcstar said:**
> What doesn't "see" it?, is it in Places-Computer?

Yeah, I went to computer and the only thing listed now is the filesystem which belongs to Ubuntu.  C: is not listed. :(

---

### Post by dcstar on 2009-01-02
> **Liliitha said:**
> Yeah, I went to computer and the only thing listed now is the filesystem which belongs to Ubuntu.  C: is not listed. :(

Install gparted and see what it says about the partitions on your PC.

---

### Post by kgas on 2009-01-02
can you check the mounted devices ?  (df -h)

check also all the file system using sudo fdisk -l  and see the listing for your NTFS file system.

---

### Post by Schok on 2009-01-02
hey im having the same problem too.gparted says it is unable to read the contents of this filesystem.

gomez@MAHA617:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             9.4G  4.1G  4.9G  46% /
tmpfs                 878M     0  878M   0% /lib/init/rw
varrun                878M  216K  878M   1% /var/run
varlock               878M     0  878M   0% /var/lock
udev                  878M  2.8M  876M   1% /dev
tmpfs                 878M  120K  878M   1% /dev/shm
/dev/sda1             7.9G  5.3G  2.6G  68% /media/PQSERVICE
/dev/sda3              23G  765M   21G   4% /home
gomez@MAHA617:~$ sudo fdisk -l
[sudo] password for gomez: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f34aae7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   12  Compaq diagnostics
/dev/sda2   *        1020        5394    35142187+   7  HPFS/NTFS
/dev/sda3            5395        8422    24322410   83  Linux
/dev/sda4            8423        9729    10498477+   5  Extended
/dev/sda5            8423        9667    10000431   83  Linux
/dev/sda6            9668        9729      497983+  82  Linux swap / Solaris

sorry, im not really good in this so ill just paste what it says..

---

### Post by Liliitha on 2009-01-02
It says something about a partition type being 0xc0 or something like that.  The file system is fat.  It says this in the start up of Ubuntu on the black screen.

---

### Post by kgas on 2009-01-04
You can try to mount the file system in the following way. Try this,

First unmount the ntfs volume (check this with sudo fdisk -l)

# sudo umount /dev/sdbX (X is the number you have)

#sudo mount -t ntfs-3g /dev/sdbX /media/<mount point> -o rw,users,auto

<mount point> is the directory name where you want to mount. If not then create one. 

you should have the ntfs file utility installed to use this.

---

