---
title: "Recommended partition sizes/types for my Computer?"
date: 2012-06-25
forum: Desktop Environments
---

### Post by Learn2Troll on 2012-06-25
Hi, i'm new on the forum and i know absolutely NOTHING about linux but ill learn.  I know nothing about partitions and how big or small they need to be.  I was wondering if anybody could give me a good partition setup based on my system specs.
Windows 7 (used to be installed)
3gb RAM
320.1 gb of Space
Laptop not a desktop

Thank you guys and please tell me the type : primary or logical
the partition size
the Type ( Ext2, swap, etc)
and the mount point
if you cant thats fine! i just really need my computer to work again
Thanks!!!!!!11:popcorn:

---

### Post by carl4926 on 2012-06-25
It could be easier if you let Ubuntu installer do it all for you.
Just choose the option to erase disk and install ubuntu
[https://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10_go_advanced_partit.png](https://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_11.10_go_advanced_partit.png)

---

### Post by Max Blyss on 2012-06-25
If your intention is to Dual - Boot with Windows, re-install Windows FIRST!  Just run through the installer the default way...  When it's done and set up, insert the Ubuntu disc and run through its installer. Choose the 'Install Ubuntu alongside Windows' option, and a graphical partition manager will pop up and allow you to drag a bar with your mouse that will let you apportion your desired amount of space to both OS's.  It will do everything else for you automatically (formatting, swapspace, etc...).

As far as I know, any fancy partitioning is preference - based, although some pros out there may have backup or security related partitioning schemes they use for their occult pro reasons...

If you just want a clean Ubuntu install, the installer ought to walk you right through.

If there's some reason you need particular partitioning, and I misread your question, I apologize in advance.

---

### Post by Learn2Troll on 2012-06-25
Sorry  i just now seen the beginner section of the forum but since i already posted here i guess ill stay.  Sorry for the bother.  Alright what i did was like i got tons of viruses on windows so i just made a live cd for ubuntu on my desktop.  I got to this one screen and it said more options i clicked new preference table and it deleted all of my recent ones i guess occupied by windows 7.  I dont know what i need to do with the boot home options to make the partitions make my computer run smoothly because i read somewhere if you only have one partition doing RAM and storage it isnt efficient.

---

### Post by Learn2Troll on 2012-06-25
> **Learn2Troll said:**
> Sorry  i just now seen the beginner section of the forum but since i already posted here i guess ill stay.  Sorry for the bother.  Alright what i did was like i got tons of viruses on windows so i just made a live cd for ubuntu on my desktop.  I got to this one screen and it said more options i clicked new preference table and it deleted all of my recent ones i guess occupied by windows 7.  I dont know what i need to do with the boot home options to make the partitions make my computer run smoothly because i read somewhere if you only have one partition doing RAM and storage it isnt efficient.
Also, im just single booting i got rid of windows 7.  So i guess its alright to use all of the harddrive space on linux?

---

### Post by carl4926 on 2012-06-25
> **Learn2Troll said:**
> Also, im just single booting i got rid of windows 7.  So i guess its alright to use all of the harddrive space on linux?
Yes

If you don't have at least 1GB RAM you willbe better not running the install from the live desktop.
Instead, reboot and as the cd boots, press esc, and you should first see a language selector and from there the 2 option to TRY or INSTALL, choose Install
Then as I showed you to use the entire HD

---

### Post by Learn2Troll on 2012-06-25
I know but it doesnt give me that option i deleted it something and it told me on the 'something else' tab (the dropbox picture in your prev. post) that i needed like a Root partition and all this other stuff.  Oh and i have 3gb of RAM so i can live desktop right?

---

### Post by zombifier25 on 2012-06-25
3GB of RAM is more than enough.

If you are still a beginner, just chose to erase disk and let Ubuntu do the job. "Something else" should be used only if you have a rather exotic set up of operating systems and you need to partition manualy, but since your requirement is simple (use entire disk for Ubuntu) choose the automated option.

---

### Post by carl4926 on 2012-06-25
If you use 'Something else'
It will start the partitioner but it's confusing for some. There you can create/delete partitions.
Personally I would advise the following:

swap 3GB
ext4 for /(root) of 20GB
ext4 for /home all the remaining space

If you get stuck using this partitioner try Gparted.....

So go to a live desktop and start gparted
Here is a video, just to give you the idea
[http://www.su2root.ukfsn.org/files/all_videos/create-partitions.mpeg](http://www.su2root.ukfsn.org/files/all_videos/create-partitions.mpeg)

---

### Post by Seb71 on 2012-06-25
I would also use "Something else" option during install and make 3 partitions:

1. Primary, ext4, Mount point /, Size 10-20GB (depending in how many programs are you planning to install).
2. Primary, Swap, Size 3222 GB (to be able o use Hibernation). 
3. Primary, ext4, Mount point /home, Size - rest of the disk.

I would put the / partition first because with 3GB of RAM you will rarely use the swap partition (it will mostly be used for hibernation). On a hard disk, the first partition (beginning of the disk) is faster so this is why it matters what you put there.

If you want to use hibernation, the swap partition must be at least equal to RAM. For some reason, the partitioner counts [in 1000 instead of 1024]("http://en.wikipedia.org/wiki/Megabyte"), so for 3 GB RAM you need to set the swap partition at 3222 GB (or more). Sometimes the partition will not have exactly the entered size. If the partitioner rounds down to say 3020, then delete the partition and try a slightly larger value, like 3224 GB.

In Ubuntu 12.04 you have to manually enable hibernation (search the forum on how to do that).

If you do not want to use hibernation, then with 3GB of RAM, you could use a smaller swap partition - something like 1GB.

On a laptop that had Windows, it is possible to have a hidden recovery partition. If you do not want to keep Windows (and even if you do), you can delete that partition (if exists). In that case you will need the installation disk to reinstall Windows (the actual installation disk, not some recovery disk).

The number of partitions on a hard disk can be maximum 4 primary or maximum 3 primary and one extended partition. If you need more than 4 partitions on a disk, then one of the partitions must be extended (and you will make logical partitions inside this extended partition).

---

### Post by Seb71 on 2012-06-26
I just noticed a typing error in my post:
> **Seb71 said:**
> 
2. Primary, Swap, _Size 3222 GB_ (to be able o use Hibernation). 

That should be 3222 MB (not GB).

---

