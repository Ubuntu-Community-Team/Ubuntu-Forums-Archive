---
title: "error: not enough space"
date: 2005-10-22
forum: Desktop Environments
---

### Post by jbergfel on 2005-10-22
I have bought a new harddisk 250GB. I created a partition of 50GB for Ubuntu and 190GB for my documents etc. This harddisk I mount directly in my home folder. The last 10GB is swap.

I try to copy my old harddisk of 80GB to my second partition of 190GB. I have mount the hardisk with:

/dev/hda1	/windowsxp	ntfs	umask=000	0	0

Ubuntu mounts the harddisk ok, but when I copy the files with the command 

cd /windowsxp
cp -R * ~/windowsxp

But after copying some time ubuntu gives a message not enough space. When I check properties of ~/windowsxp it says 142GB of free space. Now I can't copy any files any more to my home folder because of the not enough space message. It also fails with nautilus' copy and paste commands. 

Why can't I copy any files and how do I know for sure that linux copy's the files to the right partition?

---

### Post by tehwa on 2005-10-22
Just a thought, but try using rsync instead of cp:```
man rsync
```
Have a butcher's at the manual for the options. Much more verbose than cp. There are easy command line options to preserve permissions, time, groups...etc.

---

### Post by bryan986 on 2005-10-22
A 10gb swap file? Damn...I thought my 2gb one was overly large....

---

### Post by jbergfel on 2005-10-23
After I shut down I couldn't log into ubuntu again, because of an unknow error. So I decided to reformat the harddisk and reinstall ubuntu. This solved my problem, so it was probably an error in the harddisk.

I had a 10GB swap area because I don't know how much swap area is normal. Because of your reply I decided to change it to 5 GB.

---

### Post by afonic on 2005-10-23
Swap file twice as big as your RAM should be more than enough.

Ex. You have 512MB RAM -> 1 GB Swap

That space problem is weird, maybe you can post your /etc/fstab file, it may help to see how your partitions are configured.

---

### Post by jbergfel on 2005-10-24
With reformat I meant I deleted all partitions and created new partitions, so I can't give you fstab from my old configuration anymore.

I believe my drives were configured as:
hda1 pri               ext3          50 GB
hda4 extended                     200 GB
hda5 log              ext3          190 GB
hda 6 log             swap         10 GB

hda1 was mounted automatically into /
hda5 was mounted automatically into /home with defaults
hda6 was mounted as swap

I changed my partition scheme a little:

hda1 pri                ext2       50 MB       /boot
hda2 pri                swap      2 GB         
hda3 pri                ext3       23 GB       /
hda4 extended
hda5 log               ext3       20 GB       (not used)
hda6 log               ext3       200 GB     /home

But the problem is solved by repartition, so it is not so important anymore.

---

### Post by kozimodo on 2005-10-24
[QUOTE=jbergfel]I have bought a new harddisk 250GB. I created a partition of 50GB for Ubuntu and 190GB for my documents etc. This harddisk I mount directly in my home folder. The last 10GB is swap.

I try to copy my old harddisk of 80GB to my second partition of 190GB. I have mount the hardisk with:

/dev/hda1	/windowsxp	ntfs	umask=000	0	0

Ubuntu mounts the harddisk ok, but when I copy the files with the command 

cd /windowsxp
cp -R * ~/windowsxp

But after copying some time ubuntu gives a message not enough space. When I check properties of ~/windowsxp it says 142GB of free space. Now I can't copy any files any more to my home folder because of the not enough space message. It also fails with nautilus' copy and paste commands. 

Why can't I copy any files and how do I know for sure that linux copy's the files to the right partition?[/QUOTE]
I ran into the same issue once and I believe it is a problem with the journaling filesystem you're using -- the journaling is taking up all the space with the cp command.  As suggested by another reader, you might want to try rsync instead.

---

