---
title: "[SOLVED] New /home for super user. Old one gone"
date: 2007-10-12
forum: Desktop Environments
---

### Post by tipp98 on 2007-10-12
So I was trying to move the installer/superuser account to a new drive using tar. I was able to get it over a couple of times, using both superuser and root, but not without errors upon login. So I would delete folders and try again. Well, you guessed it, I deleted /home.

I don't care about recovering the data, it was a fresh install. I just want to be able to log in with a profile on the new drive. I do have a tar backup of the original /home folder before it was deleted, but when I try to extract it I get a lot of cannot change ownership and cannot create symlink errors. Any guidance would be much appreciated.

---

### Post by phansiizwe on 2007-10-12
How are you trying to extract the tar file?

Try to prefix your tar command with "sudo" e.g.:

```
sudo tar ...etc.
```

---

### Post by tipp98 on 2007-10-12
Yes, I've tried ```
cd /mnt/hda2
sudo tar -xvf /mnt/hda2/home.tar
``` I've also tried the same, sans sudo, logged in under root. I am fairly certain I created the tar archive I currently have under the root account using ```
cd /
tar -cf home.tar home
``` but am not certain as I had tried several different time, several different ways.


I currently get the following error while trying to log in
```
Could not start kstartupconfig. Check your installation.
``` and get booted back to the login screen.

---

### Post by tipp98 on 2007-10-12
Ok, so silly thought. ```
cd /
tar -xvf /mnt/hda2/home.tar
``` and BAM! I can log in

I am guessing this is a problem with the fs type, no? It is fat32. I was hoping to share this partition with a windows OS and have it as the personal files/profiles catch all partition. The following is how I was trying to set up my fstab.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2b7a513d-2186-488b-b016-9101c649e4d8 /               ext3    noatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8f0ea2d0-1682-4a3e-ac86-0c43a8fe3c2e none            swap    sw              0       0
/dev/hda2	/mnt/hda2	vfat	noatime		0	0
#/mnt/hda2/home	/home		none	rbind		0	0
#/mnt/hda2/files	/home/files	none	rbind		0	0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```
Files is to be a samba/windows share with miscillaneous files, accessable over the network when either OS is loaded. Then, I was also planning on having a "Documents and Settings" folder on this drive. Any suggestions?

---

### Post by tipp98 on 2007-10-12
Well, I played with the permissions some for the fat32 patition and got it to where any user could read/write to the drive, but upon untar I still received symbolic link errors. I remembered seeing ext2 drivers for windows so I am going to go that route. I had trouble with my standalone Gparted liveCD not creating the ext2 partition but my KNOPPIX disk worked fine. I don't know what that was all about. So, I've got my home directory over to the new drive happily and all that is left is to install windows. blah.

It would still be nice to know how to recover from a missing /home directory without a backup in case anyone else is unlucky enough to be not quite as lucky as me. I found that /etc/skel is suppose to hold a blank profile but it does not look like it holds any gui data so I'm not sure if that would help any.

---

### Post by phansiizwe on 2007-10-13
I'm glad you've got your system backup up and running. I figure that the symbolic link problem is caused by the FAT32 filesystem as it does not support these.

I always thought that if your home directory is gone and you do a

```
mkdir /home/USERNAME
```

that all applications will put their default configuration files back to where they would expect them. Looks like that is not the case...

---

### Post by tipp98 on 2007-10-13
Ohh. Yeah, your right. followed by
```
sudo chown USERNAME /home/USERNAME
```

Thanks for the help by the way.

---

