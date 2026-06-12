---
title: "Create some partition for Linux space"
date: 2009-06-07
forum: General Help
---

### Post by Magnificence on 2009-06-07
So, I heard that Windows handles slow with a Linux filesystem and Linux slow with a Windows filesystem. So I want to make some space for Ubuntu. I have a harddisk with 3 partitions that the factory decided to be funny to do :P. 1 NTFS that in windows is considered as C: with 30GB of total space, 1 hidden FAT32 with the instalation of winXP and 7.8GB of total space, and another NTFS partition wich in windows is considered as D: with  160GB of total space.
Now I installed Ubuntu on D: through winXP, and chose for 30GB. I still don't know were that's for, but I'm still a newbie :P.

So my questions are:
- How can I change to third partition of 160GB into 2 partitions, 1 with 100GB NTFS and 1 with 60GB ext2?
- Can I do that without losing the files from the original partition?
- Can I manage to let the files held on the NTFS partition? What I actually want to do is shrink the NTFS partition to have some space to create a new one,
- How about ubuntu installed on that partition, should I reïnstall it when I've created a new ext2 partition?
And some other questions: :P
- What is that 30GB for that I chose when I installed ubuntu?
- I tried some games on ubuntu through Wine, but they run really slow. Like Starcraft, that's a 10 years old game so very low graphic but even that game runs slow in ubuntu. Is that because it is on a NTFS filesystem?

---

### Post by stretch427 on 2009-06-07
Gnome Partitioner has always worked for me 
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754)

Create a boot CD or live USB and just follow the instructions. Configure however you like.
As you probably know, you have the risk of losing data. I suggest backing up your data. Especially if your going to modify an existing partition with data on it. 
Cheers!

---

### Post by Tipped OuT on 2009-06-07
If you're using Windows then try Partition Magic. It's the easiest, and best way to make, resize, and split partitions. You do not have to burn a CD to use it, you install it, apply your changes, restart, and done.

---

### Post by Magnificence on 2009-06-07
And ubuntu will have no problems at all moving to another partition?

---

### Post by Tipped OuT on 2009-06-07
> **Magnificence said:**
> And ubuntu will have no problems at all moving to another partition?

Oh, I have no idea, that's not the easiest thing to do (move an entire operating system to another partition). I would suggest, backing up your stuff from Ubuntu, and starting fresh on that new partition.

By the way, Ubuntu doesn't use NTFS and Windows can't use ext3. As a dual boot, they each use there own file system. Completely separate, hope that answers your other questions.

---

### Post by DeMus on 2009-06-07
You have to do a couple of things:

[LIST=1]
[*]Enter Windows and defragment your D-drive to have all the files at the beginning of the drive. This is to keep your files there once you make it smaller.
[*]If you have a windows program to manage partitions you can use it to make the D-drive (or better, the D partition) smaller. Continue with step 5.
[*]If not, boot into your Ubuntu Live-CD and use Gparted to do that for you.
[*]Make sure when using Gparted your Windows D-drive is unmounted otherwise it won't work.
[*]Now you have free disc space to use to install Ubuntu.
[*]When reaching step 4 out of 7 (partition step) make absolutely sure you don't choose the complete disc otherwise your Windows setup is gone.
[*]Choose manual setup and create a / (root) partition which is 20-30GB, a swap partition which is 2 times your Ram memory size and a /home partition which covers the rest of the free space. Both "/" and "/home" can be EXT2, EXT3 or when installing Jaunty EXT4 for extra speed.
[*]Continue with the installation and just before things are really installed choose advanced to have Grub installed on the MBR of your disk.
[*]Let Ubuntu install, take out your disc and reboot. Now you will see the Grub menu with item 1 being your new Ubuntu installation. Press Enter or wait 10 seconds to have it booted.
[*]Have fun.
[/LIST]

---

### Post by Magnificence on 2009-06-07
Thanks, I'll do that when I have time.

And Tipped OuT, maybe I was not completly clear, but here is the information of my partitions:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=116704&stc=1&d=1244362943[/IMG]

And now everything seems to work.

---

### Post by -kg- on 2009-06-07
A bit more complex than the two replies you have received.  I would suggest that you read "How To Partition" at the link in my signature block.

First:

> If you're using Windows then try Partition Magic. The easiest, and best way to make, resize, and split partitions. You do not have to burn a CD to use it, you install it, apply your changes, restart, and done. 

Yes, except that Partition Magic costs money, while GPartEd is free.

That being said, it will not work to just download the GPartEd Live CD and perform the operations, as you will read at the link.  There are already 3 Primary partitions on your hard drive, and there is a limit of 4 Primary partitions on a physical hard drive.  But you're in luck...one of the Primary partition can be an Extended partition, in which you can create plenty of Logical partitions to do the job.

What you have done is installed Ubuntu using Wubi, which installs it under Windows and on a Windows (ntfs) partition.  And though you can boot directly into Ubuntu from the boot menu, yes...running it under (and from) a Windows partition will make it run slower than if it's on a native Linux partition.  So on to your questions:

> Now I installed Ubuntu on D: through winXP, and chose for 30GB. I still don't know were that's for...

That space was created on the Windows partition, where ever Windows decided to install it.  That is the space that the Ubuntu directory takes on the Windows partition.

> How can I change to third partition of 160GB into 2 partitions, 1 with 100GB NTFS and 1 with 60GB ext2?

This will be addressed in "How To Partition."  You will need to shrink your 160 GB partition to 100 GB.  Then you want to create an Extended partition in the space that you freed up.  The reason you need to do this is you will need a minimum of 2 more partitions (one swap and one or more for your installation), and considering that you already have 3 Primary partitions, and considering the "4 Primary partitions" limit, you will need the Extended partition in which to create the extra (or more) partitions.

> Can I do that without losing the files from the original partition?

Yes, but you should back up your installations and data anyway.  There is always a possibility of data loss, even if you aren't performing partitioning operations.  You should always make frequent backups of your data, just in case.

> Can I manage to let the files held on the NTFS partition? What I actually want to do is shrink the NTFS partition to have some space to create a new one,

You can leave files on the partition when performing the operation, but do back it up.  You can leave the data on the partition and access it from Ubuntu also, as Ubuntu will access ntfs partitions.

> How about ubuntu installed on that partition, should I reïnstall it when I've created a new ext2 partition?

Yes, you're pretty much going to have to.  And I would suggest ext3, which the installer is going to default to anyway.  Any critical files (such as Firefox bookmarks, etc.) will still be in your Wubi installation (the one under Windows) in your installation folder.

> What is that 30GB for that I chose when I installed ubuntu?

That is the space you allocated when you installed to your Windows partition with Wubi.  It didn't change anything on your hard drive, other than taking up space in the Windows partition.  Once you have installed Ubuntu in it's own partitions and copied over your critical files, you can uninstall it from Windows.

> I tried some games on ubuntu through Wine, but they run really slow. Like Starcraft, that's a 10 years old game so very low graphic but even that game runs slow in ubuntu. Is that because it is on a NTFS filesystem?

It's basically because you have it installed under Windows.  If Starcraft is a Windows game, it will continue to run slow because you must run it under Wine or some other emulator, but if it's a native Linux game, then yes, it will run faster once you start running Linux in it's native format.

This all probably sounds complicated, but if you really study "How To Partition" and read more about Ubuntu and how it works, it will become much clearer to you over time.  It threw me for a loop at first, but now I much prefer Linux to Windows.  It becomes much easier.

Enjoy! ):P

---

### Post by -kg- on 2009-06-07
> **Tipped OuT said:**
> 
By the way, Ubuntu doesn't use NTFS and Windows can't use ext3. As a dual boot, they each use there own file system. Completely separate, hope that answers your other questions.

Oh, Ubuntu *certainly does* use NTFS!  With little or no problem.  I haven't even had to use the "ntfs-3g" drivers in fstab to do it.  Piece of cake.

---

### Post by Magnificence on 2009-06-07
Thank you -kg-! Once again, I'll work on it when I've time.

>   It threw me for a loop at first, but now I much prefer Linux to Windows.  It becomes much easier.
Yes I know! I'm learning and sometimes I just see things in linux, or the distro Ubuntu, wich I find better than WIndows. One thing I'm really happy with is that the DE is really customable.

---

### Post by Magnificence on 2009-06-11
So I had time, created a 2 partitions in 1 extended, one root (/) with ext4 and 1 with swap-linux. Installed Ubuntu normally and it whas pretty easy. Thanks for your times guys! ^^

---

