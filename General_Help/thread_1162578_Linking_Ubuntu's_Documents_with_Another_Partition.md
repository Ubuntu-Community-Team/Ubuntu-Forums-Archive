---
title: "Linking Ubuntu's Documents with Another Partition"
date: 2009-05-17
forum: General Help
---

### Post by fiveacez on 2009-05-17
I dual booted my computer, so now I have a partitions for Windows, for my data, and for all my Ubuntu stuff.

On my windows partition, I was able to move the link for my documents, video, and pictures from my Windows partition to my data partition (That way I wouldn't have to move through my data partition to get to it, I would just need to hit "My Documents" or "Pictures").

Is there a way to do the same thing on Ubuntu?  I would rather just hit Places => Pictures than Places=>Data=>User=>Pictures.

---

### Post by taurus on 2009-05-17
What you need is to create a link.  In other words, ~/Pictures (~/ stands for your $HOME) would be pointing to /media/share/Pictures (assuming you have mounted the other partition to /media/share and there is a Pictures directory on it).

```
rmdir ~/Pictures  # You need to remove it first before you can link it.
ln -s /media/share/Pictures ~/Pictures
```

---

### Post by fiveacez on 2009-05-17
2 Questions:
1) Will I need to mount the partition before I use the link?
2) If I do this, it will show up in places, as if I hadn't done anything to it?

---

### Post by taurus on 2009-05-17
1.  You should mount it; otherwise, you won't be able to access it.

2.  Once you've created the link, clicking on Pictures will put you in /media/share/Pictures instead of ~/Pictures (currently).

---

### Post by fiveacez on 2009-05-17
Can I automatically mount a partition when I log in, or is that not advised?

---

### Post by taurus on 2009-05-17
If you want it to mount automatically each time you boot Ubuntu, then you need to edit /etc/fstab and add an entry for that partition in there.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by fiveacez on 2009-05-17
Ok I'm new to Linux, so did I do that by typing that code into the Terminal?  Or was that just listing out the information that I need to do that?

---

### Post by taurus on 2009-05-17
You can either run those commands from a terminal, one line at a time, and post the outputs here and somebody will walk you through editing /etc/fstab.

Otherwise, here is a guide for doing it, [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab).

---

### Post by fiveacez on 2009-05-17
Ok, here ya go.

```
user@user-ubuntu:~$ sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14131413

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5978    48010752    7  HPFS/NTFS
/dev/sda2            5978       26226   162648064    7  HPFS/NTFS
/dev/sda3           26227       28982    22137570    5  Extended
/dev/sda4           28983       30401    11390976    7  HPFS/NTFS
/dev/sda5           26227       26886     5301418+  83  Linux
/dev/sda6           26887       28193    10498446   83  Linux
/dev/sda7           28194       28982     6337611   82  Linux swap / Solaris
user@user-ubuntu:~$ sudo blkid
/dev/sda1: UUID="DCEECCD4EECCA85A" LABEL="Windows Vista" TYPE="ntfs" 
/dev/sda2: UUID="D0D860EAD860CFF0" LABEL="Data" TYPE="ntfs" 
/dev/sda4: UUID="3CD0CEC5D0CE849C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="70c7bc2b-1a2d-458d-8c04-2c7912c1be81" TYPE="ext3" 
/dev/sda6: UUID="19e8f996-fc53-457d-8fcf-81a871c9d7fb" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="43e4aa7b-9f96-41c2-b068-05c76b525136" 
user@user-ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=19e8f996-fc53-457d-8fcf-81a871c9d7fb /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=70c7bc2b-1a2d-458d-8c04-2c7912c1be81 /home           ext3    relatime        0       2
# swap was on /dev/sda7 during installation
UUID=43e4aa7b-9f96-41c2-b068-05c76b525136 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
user@user-ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.9G  2.7G  6.8G  29% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  184K  1.5G   1% /dev
tmpfs                 1.5G   84K  1.5G   1% /dev/shm
lrm                   1.5G  2.7M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda5             5.0G  585M  4.2G  13% /home
/dev/sda2             156G   34G  122G  22% /media/Data

```

---

### Post by taurus on 2009-05-17
I assume /dev/sda4 is the one you want to mount so you can share stuff between Ubuntu and windows.  Since it's ntfs, install ntfs-config and use it to configure it.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by fiveacez on 2009-05-17
Actually, it's sda2. sda4 is my HP Recovery Partition, but it's NTFS also.

---

### Post by taurus on 2009-05-17
/dev/sda2 is already mounted to /media/Data.  If you want to use ntfs-config to add an entry in /etc/fstab for /dev/sda2 so you don't have to click it to mount it after you log in, then you first need to unmount it before you run the gksudo ntfs-config command.

```
sudo umount /dev/sda2
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by fiveacez on 2009-05-17
Once I run the ap, what do I do?

---

### Post by fiveacez on 2009-05-17
Ah, nm I figured it out (the checkboxes were confusing me a bit).

Thanks.:D

---

