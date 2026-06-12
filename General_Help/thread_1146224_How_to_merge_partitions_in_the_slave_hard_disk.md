---
title: "How to merge partitions in the slave hard disk?"
date: 2009-05-02
forum: General Help
---

### Post by badaveil on 2009-05-02
I am doing some spring cleaning to my hard disk. My master hard disk contains only my operating system (OS). My slave hard disk along the way, now, has 3 partitions and contains my work files in one partition while duplicates of the OS are in the other two partitions.

Q: I want to delete all the files in the slave hard disk and merge all 3 partitions into 1 partition but even as sudo I cannot seem to delete the the OS folders or OS files and I don't know how to merge all 3 partitions. Any advice?

---

### Post by taurus on 2009-05-02
Install gparted and use it to delete all the partitions on the second drive.  Then, create a new partition that takes up the whole harddrive and format it to whatever filesystem you want.  Don't forget to unmount the partitions first before you can delete them.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

---

### Post by badaveil on 2009-05-02
[IMG]http://lh6.ggpht.com/_yJ5Rhn3UxL4/Sfyl5Q-gK7I/AAAAAAAACEU/JfMzL9uGdTo/s400/Screenshot-1.png[/IMG]

[IMG]http://lh3.ggpht.com/_yJ5Rhn3UxL4/Sfyl5RAFKEI/AAAAAAAACEc/OtFy5xtm5Mk/s400/Screenshot-2.png[/IMG]

[IMG]http://lh6.ggpht.com/_yJ5Rhn3UxL4/Sfyl5qFr8oI/AAAAAAAACEk/zGicwrKWHnE/s400/Screenshot-3.png[/IMG]

[IMG]http://lh3.ggpht.com/_yJ5Rhn3UxL4/Sfyl5zlLgoI/AAAAAAAACEs/a0XQL-J1_0E/s400/Screenshot-4.png[/IMG]

[IMG]http://lh5.ggpht.com/_yJ5Rhn3UxL4/Sfyl5-Kx88I/AAAAAAAACE0/ZtAwpG9zcBE/s400/Screenshot-5.png[/IMG]

Firstly, thanks for your help. I copied/pasted the script on the terminal later typed gparted in the terminal coz I didn't know where to find it and got the result below. I realized that there was a Gnome Partition Editor in the Main Menu and after gparted was installed it became Partition Editor. I activated it and saw gparted in its menu. I instinctively selected the partitions one by one and deleted until there was only one (I didn't delete coz my work files were there and were still intact after being gparted) then used gparted to stretch the partition, did an apply and Hey Presto it works!

Cool! Thanks again, Taurus. You're a real pal.
___________________________

badaveil@pc:~$ gparted 
The program 'gparted' is currently not installed.  You can install it by typing: 
sudo apt-get install gparted 
bash: gparted: command not found 
badaveil@pc:~$ sudo apt-get install gparted 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 

Suggested packages: 
  jfsutils ntfsprogs reiser4progs xfsprogs 
The following NEW packages will be installed: 
  gparted 

0 upgraded, 1 newly installed, 0 to remove and 357 not upgraded. 
Need to get 348kB of archives. 
After this operation, 2150kB of additional disk space will be used. 
Get:1 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) hardy/main gparted 0.3.5-1ubuntu3 [348kB] 
Fetched 348kB in 15s (22.9kB/s)                                                
Selecting previously deselected package gparted. 
(Reading database ... 97266 files and directories currently installed.) 
Unpacking gparted (from .../gparted_0.3.5-1ubuntu3_i386.deb) ... 
Setting up gparted (0.3.5-1ubuntu3) ... 

badaveil@pc:~$

---

