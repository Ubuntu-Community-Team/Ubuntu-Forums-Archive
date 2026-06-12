---
title: "Script edit fstab ?"
date: 2011-12-07
forum: Development CD/DVD Image Testing
---

### Post by caka2604 on 2011-12-07
I want to run the script edit content of fstab file and run at boot time, i want to delete these text  "errors = remount-ro" where UUID, instead of "ro" and add some line to the bottom , ex: "tmpfs / home tmpfs defaults, siz = xyz 0 0 ". The reason that I created iso file setup ubuntu running on ramdisk by remastersys, however it is not saved fstab file, so I want to write script to edit it, but i dont's master script , so can someone help me?

---

### Post by oldfred on 2011-12-08
I use separate data partitions and install/reinstall often to test. # are my own comments on planned improvements or old versions of stuff. You will als

This is my script as my data partitions UUIDs do not change even though the installs UUID is new. The mounts I have already created.

```

#!/bin/bash
# make mount points for other partitions
echo $USER
mkdir /mnt/cdrive
#mkdir /mnt/backup

# windows shared NTFS
mkdir /mnt/shared
chown $USER:$USER /mnt/shared
chmod 777 /mnt/shared
mkdir /mnt/data
chown $USER:$USER /mnt/data
chmod 777 /mnt/data
#The big "X" will also not make files executable unless they were executable to begin with.Morbius1
#sudo chmod -R a+rwX /mnt/data

# edit fstab to add mounts, UUIDs of data partitions do not change
cp /etc/fstab /etc/fstab.backup
#Edit fstab first Need to change from UUID to labels, so it works on both portable & DT
str1="# Entry for /dev/sdc6 :"
str2="UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext3         auto,users,rw,relatime               0  2  "
str3="# Entry for /dev/sda1 :"
str4="UUID=04B05B70B05B6768                      /mnt/cdrive           ntfs-3g   defaults,uid=1000,nls=utf8,windows_names   0  0  "
str5="# Entry for /dev/sdc2 :"
str6="UUID=44332FD360AA9657                      /mnt/shared  ntfs-3g   defaults,uid=1000,nls=utf8,windows_names   0  0  "
fname=/etc/fstab
echo $str1 >> $fname
echo $str2 >> $fname
echo $str3 >> $fname
echo $str4 >> $fname
echo $str5 >> $fname
echo $str6 >> $fname

# Verify no errors in fstab & remount with new mounts
mount -a


```

---

### Post by caka2604 on 2011-12-08
I've been edited fstab susessfull **(echo "tmpfs /home tmpfs defaults,siz=xyz 0 0" | sudo tee -a /etc/fstab)**. The next step i want to run it auto when the first time boot after install. But how can i run script before fstab load??? it's so difficult :(

---

### Post by oldfred on 2011-12-08
You just need to run it, even after fstab loads as the mount -a reloads the fstab file.
I am not familiar with where in the startup process you have to put it, but have seen several posts discussing that issue.

Looks like: /etc/rc.local 
[http://ubuntuforums.org/showthread.php?t=1531030](http://ubuntuforums.org/showthread.php?t=1531030)
[http://ubuntuforums.org/showthread.php?t=1046139](http://ubuntuforums.org/showthread.php?t=1046139)

---

