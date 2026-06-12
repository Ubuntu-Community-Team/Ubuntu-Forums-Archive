---
title: "Can't find new hard drive"
date: 2008-12-15
forum: General Help
---

### Post by BobSutan on 2008-12-15
I installed a 1.5TB drive tonight, partitioned it and formated it with EXT3, but I can't find it anywhere in my Places. Is there a trick to getting the drive to show up in the GUI? I think I may still have to mount it. Does anyone know if partion manager does that for you? If not, is there a specific way I should do it?

---

### Post by cdtech on 2008-12-15
can you post the output of:
```
sudo fdisk -l
```
and the output of:
```
cat /etc/fstab
```
You just probably need to mount the drive, but you'll need to know the device name using the fdisk output above.

**UPDATE::.**
If this is a USB device it should automount and be listed within the /media/devicename folder.

---

### Post by BobSutan on 2008-12-15
sudo fdisk -l
> Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ba09b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      182401  1465136001   83  Linux

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36907918

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8666    69609613+  83  Linux
/dev/sdb2            8667        9039     2996122+   5  Extended
/dev/sdb5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22c222c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sdc2            3825       38912   281844360    f  W95 Ext'd (LBA)
/dev/sdc5            3825       38912   281844328+   7  HPFS/NTFS




cat /etc/fstab


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8565da94-444f-4650-98ad-5435dc123e1c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0a532e73-649d-4331-ae44-2c675265e2c3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0




FYI, It's not a USB drive. This is the drive: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148337](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148337)




blkid

> /dev/sda1: UUID="a82d8e80-27be-4e81-b633-87404049be72" TYPE="ext3" LABEL="Storage" SEC_TYPE="ext2" 
/dev/sda5: UUID="0a532e73-649d-4331-ae44-2c675265e2c3" TYPE="swap" 
/dev/sdb1: UUID="8565da94-444f-4650-98ad-5435dc123e1c" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="0a532e73-649d-4331-ae44-2c675265e2c3" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdc1: UUID="BEC0F2A1C0F25F59" TYPE="ntfs" 
/dev/sdc5: UUID="FCC4E45BC4E41A22" TYPE="ntfs" 


---

### Post by cdtech on 2008-12-15
You need to find the block id for the drive by using:
```
blkid
```
This will give you the device id to put along with the fstab entry:
```
# Entry for /dev/sda1 :
UUID=**41d95d32-e6bf-418b-b3fe-278d0c7ba5e1** /mnt/**newdirectory** ext3 defaults 0 1
```
The bolds are created by you....

sudo mkdir /mnt/**yournewdirectory**

After you edit the "fstab" file and creat a directory to mount to within the /mnt directory, just issue the command "mount -a" to mount it.

---

### Post by BobSutan on 2008-12-15
Here's what I did based on where the mount points are already at:

sudo mkdir /media/storage
sudo chmod 777 /media/storage
sudo gedit /etc/fstab

In fstab I input these lines at the bottom:

```
# /dev/sda1
UUID=a82d8e80-27be-4e81-b633-87404049be72 /media/storage ext3 defaults 0 1 
```


All good?


**EDIT**
Apparently not. I did a "sudo mount -a" and got the following error:

mount: special device /dev/disk/by-uuid/a82d8e80-27be-4e81-b633-87404049be72 does not exist

---

### Post by cdtech on 2008-12-15
Try replacing the UUID with just the /dev/sda1.

---

### Post by BobSutan on 2008-12-15
Weird. I was able to mount it with the following, but I can't write or change it:

sudo mount /dev/sda1 /media/storage

---

### Post by BobSutan on 2008-12-16
> **cdtech said:**
> Try replacing the UUID with just the /dev/sda1.

Did just that, but the drive is already sorta mounted (not writable). 

I made the changes you mentioned though and tried to mount again. This is what I got:

sudo mount -a

mount: special device /dev/disk/by-uuid/\x2fdev\x2fsda1 does not exist




I changed it back to the a82d8e80-27be-4e81-b633-87404049be72 uuid and got this again:

sudo mount -a
mount: special device /dev/disk/by-uuid/a82d8e80-27be-4e81-b633-87404049be72 does not exist

---

### Post by cdtech on 2008-12-16
> **BobSutan said:**
> Weird. I was able to mount it with the following, but I can't write or change it:

sudo mount /dev/sda1 /media/storage

Try to un mount using the "sudo umount /dev/sda1" and with the changes you made to the fstab try the "mount -a" agian.

---

### Post by BobSutan on 2008-12-16
> **cdtech said:**
> Try to un mount using the "sudo umount /dev/sda1" and with the changes you made to the fstab try the "mount -a" agian.

Will do. FYI, I did a chown to my account and was able to edit the folder finally. But that's just a quick fix. I want it writable from when it boots. Thoughts on how to fix that as well?




Uh...


sudo unmount /dev/sda1 /media/storage
sudo: unmount: command not found



EDIT

I'm an idiot. It's umount, NOT unmount. My bad.

---

### Post by BobSutan on 2008-12-16
[https://help.ubuntu.com/community/InstallingANewHardDrive#Automatic%20Mount%20At%20Boot](https://help.ubuntu.com/community/InstallingANewHardDrive#Automatic%20Mount%20At%20Boot)

We were close with getting rid of the UUID. Just adding the /dev/sda1 and the rest to the fstab did the trick. 

Thanks for all the help! This has been a good learning experience :)

---

### Post by cdtech on 2008-12-16
umount

Your welcome.........

---

### Post by scouser73 on 2008-12-16
To have full access to your files you need to log in as root. Firstly open a Terminal, then type **gksudo nautilus**, you'll then be prompted for your password, enter it, once you've done that, you'll be logged in as root, make your way to the partition/HDD/file or folder of your choice and then right click, select the **Properties** tab, then the **Permissions** tab, from here select the **Owner drop-down menu**, then the **Group drop-down menu** find your name in the list, select and click close. You will now have full access rights.

---

### Post by BobSutan on 2008-12-16
Well ain't this a kick in the nuts. I rebooted and lost the drive. Just great. 

I tried doing what scouser mentioend, but in order to get access I had to go back into a terminal and chown and chmod 777 the /media/storage mount point. 

Regardless, it's still not mounting automagically.

---

### Post by BobSutan on 2008-12-16
> **BobSutan said:**
> Well ain't this a kick in the nuts. I rebooted and lost the drive. Just great. 

I tried doing what scouser mentioend, but in order to get access I had to go back into a terminal and chown and chmod 777 the /media/storage mount point. 

Regardless, it's still not mounting automagically.

And that would be because I moved the drives around in the system this morning and forgot to update the fstab to reflect the drives new place. Updated the fstab file, did a 'sudo mount -a' and all is fine, even on a reboot. 

Thank you all for your help!

---

### Post by cdtech on 2008-12-17
> **BobSutan said:**
> Well ain't this a kick in the nuts. I rebooted and lost the drive. Just great. 

I tried doing what scouser mentioend, but in order to get access I had to go back into a terminal and chown and chmod 777 the /media/storage mount point. 

Regardless, it's still not mounting automagically.

Thats too funny. :lolflag:

---

