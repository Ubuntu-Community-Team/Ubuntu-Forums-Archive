---
title: "Repartition - a help needed"
date: 2010-01-23
forum: Desktop Environments
---

### Post by superthin on 2010-01-23
Hi everybody,

I've installed Ubuntu Karmic Koala into a Laptop HP DV4. Everything seems to OK.

But when I view my HDD in Gparted, I socked. The status like:

[IMG]http://img503.imageshack.us/img503/3434/20100124001213.png[/IMG]

I think I installed my Ubuntu in a wrong way. Please help me fix the problem. I don't want to have any existence of FAT, FAT32 or NTFS (which get involved with Windows - I hate Windows).

How do I live without Windows. I think the perspective like:

[IMG]http://img94.imageshack.us/img94/9921/20100124003236.png[/IMG]

I am ready with a LiveCD [Parted Magic]("http://partedmagic.com/").

I am not an experience Linux user. I could use Parted Magic to repartition my HDD. But I may not config GRUB to boot correctly. And I wonder "*Does Parted Magic ( version 4.8 ) work smoothly with ext4 or wipe every data beautifully?*".

Could you tell me (step by step) what should I do?

I greatly appreciate your support.

Thank you very much.

---

### Post by XubuRoxMySox on 2010-01-23
Just title the root partition "**/**" instead of "**/boot**."

Should be fine using the Live CD

-Robin

---

### Post by 2hot6ft2 on 2010-01-23
If you don't want or need any FAT, FAT32 or NTFS on your drive then what I would do if it were me.

I would boot from the live cd/dvd (I use Ubuntu Ultimate Edition myself ver. 2.5 so it would be the dvd for me).

Go to System > Adminstration > Gparted
Select the swap partition, right click on it and select swapoff.
(Since the live cd/dvd will automatically mount it you have to turn it off to make any changes to it).

Then I would delete every partition.
(Because you currently have sda5, sda6 and sda7 inside one extended partition which is sda2).

Apply

That would leave me with a blank drive with NO partitions.

Then I would create a primary partition at the beginning of the drive for my OS and make it the size and format of my choice such as ext4.

Next I would create a swap partition of the size I choose right after the OS's partition.

Then I would create a storage partition (for files like mp3's and other misc. files) which would use the rest of the drive (primary or logical it really wont matter) and format it to ext3 or ext4.

Apply

Close gparted when it finishes.

Start the install "choosing MANUALLY SELECT PARTITIONING during the partitioning part of the install and direct it to install to the first partition".
Once the manual partitioner starts select the first partition (should be sda1) > click on change > then file system type (ext4) tick the format box and mountpoint as /

And go thu the rest of the install.

Then I would have a nice clean install and only have 3 partitions on the drive.

That's what I would do if it were me and I was only going to have the 1 OS on the computer but personally I triple boot so mine is a bit more involved.

---

### Post by superthin on 2010-01-24
Thanks **dixiedancer** and **2hot6ft2**. I have some information from you. But I don't want to remove all partition and reinstall -> it cost me many hours.

After more than 2 hours playing with Parted Magic I am having a HDD like:

[IMG]http://img709.imageshack.us/img709/3738/partitionubuntu.gif[/IMG]

Primary & Extended are ext4 system file.

Who help me?

---

