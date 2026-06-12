---
title: "Storage Device Manager reads two partitions as one"
date: 2009-06-08
forum: General Help
---

### Post by Randypan on 2009-06-08
Hello

I don't really know i this problem can raise serious issues with my system, other than small annoyances with folder management (as i posted in another thread of mine, it apparently prevented me from setting individual custom folder icons)

What happens is that when I run SDM, it tells me that my sda1 partition IS actually my sdb2 partition.( this means that it can be found as sda1 in the Partition List sidebar, but when I open it, it appears as sdb2 with all the default options of that last drive)
What's worse now, is that if I try to change the mountpoint and the name of the partition ( the one listed as sda1) in order to fix it , the changes really affect sdb2.

Except for the minor folder trouble i mentioned above, this mix-up prevents me from turning sda1' s automount option off. Other than that, all files are readable and all executables are... executable in both partitions.

Not only are sda1 and sdb2 existing and separate partitions, they also belong to different physical drives!...

Notes: 
-sda1 is NTFS and sdb2 is ext3
-sda1' s mountpoint: /media/drv0, it's my Windows partition
-sdb2' s mountpoint: /media/sdb2  

What's happening?

---

### Post by 123456789123456789123456 on 2009-06-08
> **Randypan said:**
> Hello

I don't really know i this problem can raise serious issues with my system, other than small annoyances with folder management (as i posted in another thread of mine, it apparently prevented me from setting individual custom folder icons)

What happens is that when I run SDM, it tells me that my sda1 partition IS actually my sdb2 partition.( this means that it can be found as sda1 in the Partition List sidebar, but when I open it, it appears as sdb2 with all the default options of that last drive)
What's worse now, is that if I try to change the mountpoint and the name of the partition ( the one listed as sda1) in order to fix it , the changes really affect sdb2.

Except for the minor folder trouble i mentioned above, this mix-up prevents me from turning sda1' s automount option off. Other than that, all files are readable and all executables are... executable in both partitions.

Not only are sda1 and sdb2 existing and separate partitions, they also belong to different physical drives!...

Notes: 
-sda1 is NTFS and sdb2 is ext3
-sda1' s mountpoint: /media/drv0, it's my Windows partition
-sdb2' s mountpoint: /media/sdb2  

What's happening?
the physical hard disk hd1,0 is your Ubuntu drive then, where hd0,0 is your windows drive.
the partition sdb would be what GRUB reads as hd1,0 as being the second physical disk
I am confused, why is your Ubuntu machine installed on the second partiton of that disk, where is the swap partiton installed on, sdb1, or sdb3?
I am not sure why the confusion is taking place, other than that the swap partion should be sdb2, and the main Ubuntu partition should be sdb1, just as the windows partition is sda1.
it is possible that the partitions for some reason was not set up properly by the partition manager upon installation of the system, though I can't think of why what would accure.  I suggest backing up data, possibly even making a clone of the ubuntu partiton and resinstalling, but this time, go to manual, and set up sdb1 as the Ubuntu partiton and sdb2 as the swap partition.
that could fix the problem.

---

### Post by Randypan on 2009-06-09
(hd0,0) is my windows partition [sda1]
(hd0,4) is my swap partition [sda5]
(hd0,5) is my Ubuntu partition [sda6]
And the sdb2 partition is holding random files in a folder (mp3s, videos etc, it's even on a different physical drive) and it didn't really have anything to do with the installation of Ubuntu. ...and that's what's really odd

_Anyway I managed to solve the issue_ in some strange and vague way. Amongst other things, I tried to manually change sda1' s mountpoint, couldn't do it, then I unmounted it and when I run Storage D. Manager  where everything looked normal...

I doesn' make mutch sense- Anyway thanks for the attention

---

### Post by Randypan on 2009-06-09
Ok, I found somewhere around this forum a thread about fstab. It said that a usb drive (in this case my sdb2 partition of my external drive) may automatically mount on an sda1 mountpoint and that this has to do whith what order the devices are pluged-in and even with which usb slot you use. Here's the link to this thread:  [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) 

My question now is how to prevent the external drive from mounting /media/sda1, since this mountpoint is reserved for the actual dev/sda1 partition and that greedy external drive allready has its own mountpoint...

---

