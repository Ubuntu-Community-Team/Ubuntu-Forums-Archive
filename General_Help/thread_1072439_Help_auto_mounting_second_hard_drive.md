---
title: "Help auto mounting second hard drive"
date: 2009-02-17
forum: General Help
---

### Post by alejobar on 2009-02-17
Hi guys!

I need some help, I'm fixing my nephew's computer... again, so this time I'm going with Ubuntu 8.10 because I think its the only way he will be away from virus, adware, spyware and all the know windows related problems. 

The computer its running perfect now, but he have two hd with 40gb each and I want to auto mount the second hd at boot and if there's any way that Ubunut will use the second hd as part of the file system in order to have more space for music, games, pics etc..

I found these links:
[http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+ext3]("http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+ext3") 
[http://ubuntuforums.org/showthread.php?t=175761]("http://ubuntuforums.org/showthread.php?t=175761")and follow them step by step, but for some reason I had no luck :(, because after reboot I still have to go to Places and click on the second hd to mount it and open it

---

### Post by taurus on 2009-02-17
Open a terminal and post the outputs of these commands here to see what have you done to the second harddrive so far?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
id
```

---

### Post by drs305 on 2009-02-17
Run these commands and post the results so we can put the drive into fstab.

If it isnt' obvious, tell us which device you want mounted that isn't, and where you want it mounted.

```

sudo blkid -c /dev/nul
cat /etc/fstab
df -Th

```

---

### Post by alejobar on 2009-02-17
Oh my! thanks for the quick response! that's why i love this forum! :p, I'll run those commands as soon I get home and post the results.

Thanks again!

---

### Post by alejobar on 2009-02-17
> **taurus said:**
> Open a terminal and post the outputs of these commands here to see what have you done to the second harddrive so far?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
id
```



Hi Guys here are the results:

fdisk -l

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb28fb28f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4683    37616166   83  Linux
/dev/sda2            4684        4870     1502077+   5  Extended
/dev/sda5            4684        4870     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00013c44

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4870    39118243+  83  Linux


blkid:

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="e1ebabd5-fcfb-4b62-b44a-e608d060e275" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="56407821-45e9-4dfe-95f9-2f2596e6c284" 
/dev/sdb5: UUID="95B3A032AC4808AC" LABEL="Games" TYPE="ntfs" 
/dev/sdb1: UUID="891b3213-a38a-48a6-9627-50f4c127504d" SEC_TYPE="ext2" TYPE="ext3" 

fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e1ebabd5-fcfb-4b62-b44a-e608d060e275 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=56407821-45e9-4dfe-95f9-2f2596e6c284 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda2 /second_drive ext3 auto defaults 0 0


df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  4.2G   30G  13% /
tmpfs                 252M     0  252M   0% /lib/init/rw
varrun                252M  100K  251M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  2.7M  249M   2% /dev
tmpfs                 252M  608K  251M   1% /dev/shm
lrm                   252M  2.0M  250M   1% /lib/modules/2.6.27-11-generic/volatile

id:

uid=1000(ale) gid=1000(ale) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(ale)

---

### Post by jms1989 on 2009-02-17
Well, you almost had it. :)

Change 

```
/dev/sda2 /second_drive ext3 auto defaults 0 0
```

 in your fstab file to 

```

/dev/sdb1 /media/HDD1 ext3 auto,defaults 0 1

```

Commands:
```

sudo nano /etc/fstab

```

Change last line to what I suggested and press Ctrl + o to save and Ctrl + x to exit nano. 

Run mount -a to have ubuntu automatically mount it and it should mount a boot up too.

EDIT: Almost forgot, it is recommended to create a folder corresponding to the mount directory. In this case, you can run (mkdir /media/HDD1). That will create a directory in your media folder for the extra disk.

P.S.: If it were me, I'd use the UUID of the partition so it will still mount even if you changed the master/slave jumpers around in the two hard drives but if you happen to reformat the disk in the future or replace it, you'd need to update the UUID for the new file system.

Cheers.

---

### Post by alejobar on 2009-02-18
> **jms1989 said:**
> Well, you almost had it. :)

Change 

```
/dev/sda2 /second_drive ext3 auto defaults 0 0
```

 in your fstab file to 

```

/dev/sdb1 /media/HDD1 ext3 auto,defaults 0 1

```

Commands:
```

sudo nano /etc/fstab

```

Change last line to what I suggested and press Ctrl + o to save and Ctrl + x to exit nano. 

Run mount -a to have ubuntu automatically mount it and it should mount a boot up too.

EDIT: Almost forgot, it is recommended to create a folder corresponding to the mount directory. In this case, you can run (mkdir /media/HDD1). That will create a directory in your media folder for the extra disk.

P.S.: If it were me, I'd use the UUID of the partition so it will still mount even if you changed the master/slave jumpers around in the two hard drives but if you happen to reformat the disk in the future or replace it, you'd need to update the UUID for the new file system.

Cheers.


Thanks Jms1989! I will try that when I get home, hope it work this time ;)

---

### Post by tombott on 2009-02-18
I'm sure jms1989's suggestions will get this sorted for you, but just in case it doesn't here's a link to a guide I wrote on automounting:

[http://tombott.com/Automatically_Mount_Additional_HD_in_Ubuntu_8.10](http://tombott.com/Automatically_Mount_Additional_HD_in_Ubuntu_8.10)

Tom.

---

### Post by alejobar on 2009-02-19
Good news guys! I finally made it!!! Thanks to all for your help! ;), now I can reboot and see the drive mounted in my desktop and it appears as HDD1 in my media, but only one thing I cant create folders on the drive, that's normal? or I did something wrong?

---

### Post by drs305 on 2009-02-19
> **alejobar said:**
> Good news guys! I finally made it!!! Thanks to all for your help! ;), now I can reboot and see the drive mounted in my desktop and it appears as HDD1 in my media, but only one thing I cant create folders on the drive, that's normal? or I did something wrong?

If this is an ext3 partition, you must make yourself the owner of the mount point:
```

sudo chown -R *[COLOR="DarkRed"]yourusername:[/COLOR]* /media/HDD1
chmod -R 755 /media/HDD1

```
If you didn't use "/media/HDD1" change it to the correct mount point.
The 'chmod' command gives you read/write/execute, group and others read/execute

---

### Post by alejobar on 2009-02-19
> **drs305 said:**
> If this is an ext3 partition, you must make yourself the owner of the mount point:
```

sudo chown -R *[COLOR="DarkRed"]yourusername:[/COLOR]* /media/HDD1
chmod -R 755 /media/HDD1

```
If you didn't use "/media/HDD1" change it to the correct mount point.
The 'chmod' command gives you read/write/execute, group and others read/execute

Thank you Drs305, I run the commands in terminal, using sudo chown -R ale: /media/HDD1 and chmod -R 755 /media/HDD1 and still I cant create a folder :( here is my fstab in case you need more info:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e1ebabd5-fcfb-4b62-b44a-e608d060e275 /               ext3    relatime,erro$
# /dev/sda5
UUID=56407821-45e9-4dfe-95f9-2f2596e6c284 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /media/HDD1     ext3    defaults        0       0

---

### Post by drs305 on 2009-02-19
Please run these:
```

sudo umount /dev/sdb1
sudo mount /dev/sdb1
ls -la /media/HDD1  # lists permissions and owers
mkdir /media/HDD1/test

```
If the second command doesn't let you make the folder, post the error message.

---

### Post by jms1989 on 2009-02-20
I've always gave my media the 777 permissions. One more thing you could try is replacing the "defaults" part in your /etc/fstab file for sdb1 to "user,auto".

That will allow the user to freely mount it and it will be auto mounted at startup. Also you can chmod it to 777. (sudo chmod 777 /media/HDD1) It has always worked for me with linux partitions. :)

Cheers!

---

### Post by alejobar on 2009-02-20
I finally fixed, first I had to go to System > Administration > User and Groups, then unlock root, then Properties, User Privileges, mark all, then go to Ale account, same thing as root.

Finally went to File System > Media > HDD1 right click Properties > Share > create Share point, close

Now I can create folders in the drive :p

Thank you all guys for your help and pacience :D

---

