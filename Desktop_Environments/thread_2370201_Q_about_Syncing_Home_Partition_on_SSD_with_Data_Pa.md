---
title: "Q about Syncing Home Partition on SSD with Data Partition on HDD"
date: 2017-08-31
forum: Desktop Environments
---

### Post by dswaugh on 2017-08-31
Have Ubuntu 17.04 installed on an SSD drive with separate root and home partitions. Have also linked the home folder to a separate HDD labeled "data" so that all of my "home" data writes to the HDD rather than the SSD. Created this set-up so I wouldn't have to erase all the existing data on the HDD by assigning my home folder to it during installation. Well, all works fine except for one little glitch. Whenever I boot the OS, the links to the data drive (which are inside the home folder on the SSD) aren't automatically active. I first have to click the HDD icon BEFORE opening the home folder. Just wondering if anyone can recommend an easy fix to eliminate this additional step. Essentially, I want my links within the home folder to be active automatically when I boot Ubuntu, rather than having first to open the data drive before I can use the links in the home folder. Thoughts?

---

### Post by oldfred on 2017-08-31
You must have set up the links using the default mount that Naulitus or your file browser creates.
Better to create your own mounts, give yourself ownership & permissions in data partition and add entry to auto mount with fstab so when you reboot it is there.

I prefer to use /mnt/data, as then it does not show twice in Nautilus. (not sure if still an issue or not.
You probably have /media/$USER as mount. If you labeled partition it uses label. If not labeled you have a very long UUID as default mount.

Since I have all data in my /mnt/data partition on HDD, and then /home is tiny with only the hidden files & folders. I do also move some larger normally hidden folders like Firefox & Thunderbird as I can edit profile.ini in each to another folder in my data partition.

Post this to see current mounts (after you have mounted it)
sudo mount

I have this in my mount:
/dev/sdb4 on /mnt/data type ext4 (rw,relatime,data=ordered)

cat /etc/fstab
I have this which created the above mount.
```
# Entry for /dev/sdb4 :
UUID=a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5 /mnt/data ext4 relatime 0 2

```

to see your UUIDs:
       sudo blkid -c /dev/null -o list 

You can copy my example but use your UUID. If you want your current mount point use the /media/$USER that you found from mount command. 
If you use /mnt/data, you will have to remove current links & create new ones.

If starting from scratch. & more examples.
      
 The actual user settings are small. My /home is 2GB with most of that as .wine' Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home in my typical 25GB / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

Another example with more explanation of editing fstab:

 Seems like a better way as you have more control over what is executable. Isee post #8 & 10 by morbius1.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)

Set ownership & permissions if Linux formatted partition. Cannot be done on NTFS as Windows does not support Linux ownership & permissions.
sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data
#where $USER should be your login name

---

