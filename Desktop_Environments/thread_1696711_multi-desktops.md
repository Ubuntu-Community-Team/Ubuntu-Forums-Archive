---
title: "multi-desktops?"
date: 2011-02-27
forum: Desktop Environments
---

### Post by roblikeschocolatecake on 2011-02-27
hello i have an hp laptop with windows xp and ubuntu 10.10 installed. i searched for a bit and couldnt find an answer to my problem. i was wondering if i would be able to have multiple desktops that i could boot into? for example: right now i have the gnome version of ubuntu installed but i would like to install the kde version as well and also the compiz version. is there a way to do this so that i would be able to choose which one i want when booting up? either this or i would like to triple boot from xp, ubuntu 10.10, and linux ultimate edition 2.8

thanks in advance for any help that may be given

---

### Post by ankspo71 on 2011-02-27
Hi,
Here is a link that contains a section dedicated to installing different desktop environments on Ubuntu, and also has top notch advice on how to remove them. See the section called "Playing Around" on this page:[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Triple booting, Quadruple booting and so on can be done too, but it requires more work on the users part, such as creating new partitions or resizing existing partitions, making sure to have the same grub bootloader version to avoid additional work (like seen here [http://www.dedoimedo.com/computers/grub-2.html#mozTocId982259](http://www.dedoimedo.com/computers/grub-2.html#mozTocId982259)), and so on.

I don't think there is a real need for anyone to install Ultimate Edition along side Ubuntu, because Ultimate Edition is based on Ubuntu. But, of course, anyone can if they wanted to. They also have a repository that Ubuntu users are welcome to use too. [http://ultimateedition.info/ultimate-edition-repository/](http://ultimateedition.info/ultimate-edition-repository/) . I believe installing "ultimate-edition" from that repository is what is needed to convert Ubuntu into Ultimate Edition. The major differences between Ultimate Edition and Ubuntu is: Ultimatix?, extra games and applications already installed, themes/artwork/branding, and other goodies.  

Welcome to Ubuntu. :)

---

### Post by ankspo71 on 2011-02-27
I'm sorry, I forgot to answer something....
To switch to another desktop after installing it, all you need to do is log out, then click on your username, then select the new desktop in the menu below, enter your password and log back in. 
Hope this helps.

---

### Post by roblikeschocolatecake on 2011-02-27
> **ankspo71 said:**
> I'm sorry, I forgot to answer something....
To switch to another desktop after installing it, all you need to do is log out, then click on your username, then select the new desktop in the menu below, enter your password and log back in. 
Hope this helps.

thank you sooo much. one more question though. is it possible, and if so how, to have multiple types of linux installed at once? for example: multi boot xp, ubuntu 10.10, and linux mint, and fedora?

---

### Post by ankspo71 on 2011-02-28
Hi, and Yes
Setting up a triple boot (or greater) is like how you already installed Ubuntu along side Windows (dual boot), except you will need to use manual partitioning with the installer (or partition editor) so you can create room for other distributions, and then finally create their own partitions to install them on. Creating room normally involves shrinking and moving existing partitions.

The most difficult part of it all is deciding on which partitioning scheme you want to create, because there are some limitations... 

Hard drives are only limited to 4 primary partitions, so that is important to remember. If you already have 3 used primary partitions, you will need to make the 4th partition Extended. If you are already using 4 primary partitions, then reinstall Ubuntu using an extended partition containing logical partitions. 'Extendend' partitions are counted as 'primary' partitions too, but they are used to contain as many 'logical' partitions as you think you need (max of 24 total partitions per hard drive (or system?)). Some partitioners automatically create the extended partitions for you as you create your logical partitions. Also, it is only necessary to have one swap partition because swap can be shared by all Linux distributions. Reference to partition limits: [http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

Here is some more info on manual partitioning. [http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)
And here is a video: (dual boot on 2 drives, worth watching though) [http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning](http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning)

So one partitioning layout might be:
A primary NTFS partition for windows, 50gb
An extended 154gb partition to contain the following logical partitions:
A logical ext4 patition for Ubuntu, 50gb, mountpoint=/
A logical ext4 partition for Mint, 50gb, mountpoint=/
A logical ext4 partition for Fedora, 50gb, mountpoint=/
A logical swap partition, 4gb

If you prefer to have a separate home partition then your layout might be:
A primary NTFS partition for windows, 50gb
An extended 154gb partition to contain the following logical partitions:
A logical ext4 patition for Ubuntu, 15gb, mountpoint=/
A logical ext4 patition for Ubuntu, 35gb, mountpoint=/home
A logical ext4 partition for Mint, 15gb, mountpoint=/
A logical ext4 partition for Mint, 35gb, mountpoint=/home
A logical ext4 partition for Fedora, 15gb, mountpoint=/
A logical ext4 partition for Fedora, 35gb, mountpoint=/home
A logical swap partition, 4gb

Hope this helps.

---

### Post by false truths on 2011-02-28
Just a suggestion when you have more then one desktop environment, have a different user account for each one. That way, one's settings doesn't mess with any other's settings.

---

### Post by roblikeschocolatecake on 2011-02-28
i see. would i be able to use me portable 500 gb drive to run one of the linux operationg systems? or is it not enough space?

---

