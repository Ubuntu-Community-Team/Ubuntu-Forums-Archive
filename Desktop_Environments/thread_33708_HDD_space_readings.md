---
title: "HDD space readings?"
date: 2005-05-11
forum: Desktop Environments
---

### Post by -TayloR- on 2005-05-11
Just wondering how, or what ways are best, to find out your space used, free and overall with your hdds.. command or program wise, preferably easy to read etc :).. anyone have any suggestions?

---

### Post by Xian on 2005-05-11
Open a terminal and type this at the command prompt:

$ df -h

My output:

```
xian@linux:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             9.4G  2.8G  6.6G  30% /
tmpfs                 221M     0  221M   0% /dev/shm
/dev/hda1              26G  9.7G   16G  39% /ntfs
/dev/hda3              12G   33M   12G   1% /bsd
/dev/hda6             4.7G  1.3G  3.4G  28% /home
/dev/hda7              12G   33M   12G   1% /slack
/dev/hda8              19G  4.5G   15G  25% /gentoo
/dev/hda9              89M   23M   62M  27% /genboot
/dev/hda10             28G  7.9G   21G  29% /storage
/dev/hda11            9.4G  3.7G  5.7G  40% /arch
</snip>

```

---

### Post by Buntu on 2005-05-11
Launch a terminal and type:

df -h

[diskfree -human] shows the amount of disk space that's used and available in a human readable format.

To see how much memory you have, type:

free -m

(or free -k to show the result in kilobytes).

For more information, type:

man df

and

man free

---

### Post by -TayloR- on 2005-05-11
hey df -h is just what i was looking for, thanks :) 

:: Edit ::

Ok a few more questions, how would i go about formatting my other HDD in my computer, currently its in NTFS and as i dont have windows installed that drives rendered pretty useless right now... so how would i go about formatting it and to what format would be best just for file storage? also how would i get it to auto mount on boot afer formatting?

---

### Post by F for Fragging on 2005-05-12
To view partition information, including free/used disk space, open KInfoCenter, which can be found in "System" in the K Menu.

To format partitions you could use the software your harddisk manufacturer has available. But I don't know how you could convert it to a Linux partition, for example a partition with ext2, after that. To auto mount partitions you have to edit etc/fstab.

---

