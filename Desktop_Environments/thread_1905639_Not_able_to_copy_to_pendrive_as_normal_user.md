---
title: "Not able to copy to pendrive as normal user"
date: 2012-01-07
forum: Desktop Environments
---

### Post by chaitanyakumar on 2012-01-07
Hi,

I am not able to copy any files to my pendrive as normal user. Everytime I need to login as root and copy files to pendrive. I tried to change the owner of the pendrive to the user(non root) by which I am logging in now. I used the command chown currentusername /media/sdc1 .But I got an error saying " chown: changing ownership of `/media/sdc1/': Operation not permitted". Please help...

---

### Post by ajgreeny on 2012-01-07
How is the pendrive formatted?

If it is fat32, as most are by default, it should normally mount when inserted and the mount folder in /media would be yours automatically.  Perhaps you have formatted it as ntfs, or even one of the Linux filesystems?

---

### Post by chaitanyakumar on 2012-01-08
Hi,

I have formatted the pendrive in ubuntu and I hope it is in fat32 only. I was not prompted to choose fat32 or ntfs while formatting.And in the normal user, if I insert pendrive, it says only root can mount the media under /media/sdc1. I need to remove the pendrive and insert in root login. Then it gets mounted. And after that I can see the data in my login. Here, I am not able to delete anything or add data to the pendrive. This is my problem.

---

### Post by ajgreeny on 2012-01-08
Can you attach the drive and then run command ```
sudo fdisk -l
``` lower case L at the end, please.  That will tell us the format type of the partition on the pendrive.  You say you formatted it in ubuntu;  how did you do that?  Did you use **gparted** or in command line with **mkfs**?

---

### Post by chaitanyakumar on 2012-01-08
Hii,

sudo fdisk -l gave me the result:


Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    15636303     7818120+   b  W95 FAT32

And regarding the formatting, I logged in as root user and if I right click on my pendrive in my computer, there is an option called format. I select it thats it.. and the formatting is done.

---

### Post by ajgreeny on 2012-01-08
You logged in as root?

I think that is why the partition mountpoint is now owned by root, but it is not what I would expect with a fat32 partition.

I think you will need to login as a user with admin rights and use the command ```
sudo chown user:user /media/mountpoint
``` replacing "user:user" with your username in both places, and replacing "mountpoint" with wherever the pendrive mounts in /media.  It may be worth labeling the partition with gparted to ensure that it always mounts at the same folder, /media/*label*, as it is possible that /media/sdc1 could become /media/sdd1 if other disks are attached before the pendrive.

---

### Post by chaitanyakumar on 2012-01-09
Hi,

When I used the command you gave, it gave me the following output:

chown: changing ownership of `/media/DHARMA/': Operation not permitted

FYI, I have logged in root user and tried this cmd, but still it is not able to change the permissions. I have removed the pendrive, unmounted the folder and changed the permissions of the folder. And after that, I have inserted the pendrive but the permissions what I have changed, are overwritten. 

Previously, /dev/sdc1 is mounted on /media/sdc1 folder. I have removed the /media/sdc1 folder and created new folder /media/pendrive and created an entry in fstab file. Now even in non root user, it is getting mounted. One problem  is solved. Now my only problem is I am not able to write(copy or delete) to the pendrive. 

Thanks,
Chaitanya.

---

### Post by Blackbird_13 on 2012-01-09
I had a similar problem with a ntfs partition and this worked for me. My options entry in fstab was:

> defaults,uid=1000,gid=1000
This changed root access to my user access.

---

### Post by ajgreeny on 2012-01-09
You should not need any entry in fstab for a fat32 pendrive.  I am now lost with this problem, I'm afraid, so will leave it to others.

---

### Post by chaitanyakumar on 2012-01-09
Blackbird_13: can you pls give me the complete fstab entry so that I ll try to modify mine as urs. In my fstab, I have the entry as below for my pendrive(/dev/sdc1)


/dev/sdc1   /media/DHARMA  vfat  defaults    0  0  


ajgreeny: I have installed storage device manager to automatically mount the partitions in my drives. I have total 6 partitions. Everytime I have to open them atleast once after I login to the machine. So I have installed this software. This software mounts the partitions automatically while booting up. I have seen sdc1 also there, which is my pendirve. So I created a folder in /media and pointed to that folder. Now mounting is fine,as I told before. Only the copying/deleting problem is there now.

---

### Post by Blackbird_13 on 2012-01-09
I would try the following:

>  /dev/sdc1   /media/DHARMA  vfat defaults,uid=1000,gid=1000     0  0  where uid = your user id number
           gid = your home group id number (ignore this if you want)

---

### Post by Blackbird_13 on 2012-01-09
I should have added, if you are not sure what your user id is enter the following in a terminal.

> id -u USERNAMEwhere USERNAME is your username

---

