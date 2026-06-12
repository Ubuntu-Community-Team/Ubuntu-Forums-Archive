---
title: "Second Harddrive Auto Mount"
date: 2009-04-24
forum: General Help
---

### Post by nadazip on 2009-04-24
Just switched back to Ubuntu 9.04 from Fedora and having a little problem getting my second drive to auto mount. When i reboot my computer my second drive is not mounted until i click on it. I have all my media on that second HD and if you do not click on it first and open rhythmbox it is unable to find the media. 

I did take a look around the forum and was unable to find what i needed. I did have a simalar problem in Fedora but do not recal how i fixed it. 

PS the latest release is awesome my fastest install ever. This is the only issue i have.

---

### Post by Monotoko on 2009-04-24
You will need to edit your /etc/fstab file

can you run ```
sudo fdisk -l
``` and i can tell you what you need to put in fstab

---

### Post by nadazip on 2009-04-24
I am at work at the moment. I will be home in a a few hours.

---

### Post by Mistoffeles on 2009-04-24
Did you make it a part of your filesystem when you installed 9.04?

Otherwise you will have to manually add it to fstab as Montoko recommended.

---

### Post by nadazip on 2009-04-24
No i after installation.

---

### Post by nadazip on 2009-04-24
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d4a6d4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38156   306488038+  83  Linux
/dev/sda2           38157       38913     6080602+   5  Extended
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c47162d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6994    56179273+  83  Linux
/dev/sdb2            6995        7297     2433847+   5  Extended
/dev/sdb5            6995        7297     2433816   82  Linux swap / Solaris


What do i need to do next? the 60 gig is my os.

---

### Post by x001 on 2009-04-24
Check out: [http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")

Helped me auto mount my HDs.

---

### Post by dcstar on 2009-04-24
> **nadazip said:**
> Just switched back to Ubuntu 9.04 from Fedora and having a little problem getting my second drive to auto mount. When i reboot my computer my second drive is not mounted until i click on it. I have all my media on that second HD and if you do not click on it first and open rhythmbox it is unable to find the media. 

I did take a look around the forum and was unable to find what i needed. I did have a simalar problem in Fedora but do not recal how i fixed it. 

PS the latest release is awesome my fastest install ever. This is the only issue i have.

Install the **pysdm** tool.

---

### Post by nadazip on 2009-04-25
Thanks, that worked perfect.

---

### Post by holmesy999 on 2010-06-03
I think I have followed all the steps on the help page [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

My problem is the write permissions for this mounted hard drive. I have been doing various options (I think) in my fstab file to say that I can write, but for some reason it is still only letting root (with sudo commands) do the writing (ie deleting, moving files etc)

I've used the pysdm tool, and edited the fstab file with a few options but it still seems to only let the root do anything with it and won't give me any permissions

I've got the new hard drive /dev/sdb1, and it is pointing to /media/sdb1.

I put this line in my fstab (using gksu gedit /etc/fstab):
/dev/sdb1      /media/sdb1      vfat       rw,users      0      0

I have then run sudo mount -a
then have run sudo chown -R myusername:myusername /media/sdb1, but I get a list of error messages saying change of ownership not permitted.

The drive is mounted, but I can;t make  directory on it.

So I am assuming that the fstab file is missing an option to mount it so ANYONE can delete / move / copy files on the drive.

Help please!

---

### Post by sisco311 on 2010-06-03
> **holmesy999 said:**
> I think I have followed all the steps on the help page [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

My problem is the write permissions for this mounted hard drive. I have been doing various options (I think) in my fstab file to say that I can write, but for some reason it is still only letting root (with sudo commands) do the writing (ie deleting, moving files etc)

I've used the pysdm tool, and edited the fstab file with a few options but it still seems to only let the root do anything with it and won't give me any permissions

I've got the new hard drive /dev/sdb1, and it is pointing to /media/sdb1.

I put this line in my fstab (using gksu gedit /etc/fstab):
/dev/sdb1      /media/sdb1      vfat       rw,users      0      0

I have then run sudo mount -a
then have run sudo chown -R myusername:myusername /media/sdb1, but I get a list of error messages saying change of ownership not permitted.

The drive is mounted, but I can;t make  directory on it.

So I am assuming that the fstab file is missing an option to mount it so ANYONE can delete / move / copy files on the drive.

Help please!

FAT and NTFS partitions do not support unix/linux permissions. You have to set the permissions at mount time:
```
UUID=**uuid-here**    /media/sdb1   vfat    defaults,users,gid=plugdev,dmask=0002,fmask=0113    0    0
```

This sets read/write permissions for the group plugdev and read permissions for others.

To get the UUID of the partition run:
```
sudo blkid /dev/sdb1
```

Directly using /dev/hd*# or /dev/sd*# is no longer preferred since these device assignments can change between system boots. [uhelp]community/UsingUUID[/uhelp]

[thread=283131]Understanding fstab[/thread]

---

### Post by holmesy999 on 2010-06-04
> **sisco311 said:**
> FAT and NTFS partitions do not support unix/linux permissions. You have to set the permissions at mount time:
```
UUID=**uuid-here**    /media/sdb1   vfat    defaults,users,gid=plugdev,dmask=0002,fmask=0113    0    0
```

This sets read/write permissions for the group plugdev and read permissions for others.

To get the UUID of the partition run:
```
sudo blkid /dev/sdb1
```

Directly using /dev/hd*# or /dev/sd*# is no longer preferred since these device assignments can change between system boots. [uhelp]community/UsingUUID[/uhelp]

[thread=283131]Understanding fstab[/thread]

Thanks - the UUID= line in the fstab file did the trick and it is all working now

---

