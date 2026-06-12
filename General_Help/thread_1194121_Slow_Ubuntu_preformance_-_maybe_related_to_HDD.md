---
title: "Slow Ubuntu preformance - maybe related to HDD"
date: 2009-06-22
forum: General Help
---

### Post by GingersK on 2009-06-22
Hello guys

Basically, I switched to linux a few months ago using fedora core. However the other week I decided to give Ubuntu a try. The installation was very problematic and involved me installing 8.10 (which had to be run in safe graphics mode and with the additional parameter "all_generic_ide") from which I then had to upgrade to Ubuntu 9.04. Now to get ubuntu 9.04 to run I have to add "all_generic_ide" to the kernel parameters. 

Generally speaking, the system works. However I'm having performance issues. The computer can pretty much only handle one thing at once. Basically, when the hard disk is been accessed (like Vuze, or file transfer between hard disks) every thing lags up completely. For instance the mouse starts to jump around and watching or listening to any media is made impossible. It is even causing problems with typing this post.

It seems to me the issue is with the hard disk (which coincidently works with windows and fedora without issue), At the moment, I'm moving a 13Gb media file from one hard disk to another and the transfer rate is only 1.5MB/sec. When the hard drive is in use and the system begins to lag, the system resource use is still low with CPU less then 20% and only 300Mb of the RAM been utilized. However I'm no expert, so I can't say for sure that it is the hard drives. 

Also, maybe related to this problem. My installation will not start using "Ubuntu 9.04, kernel 2.6.28-11-generic" with or without the addition of "all_generic_ide". So I have to boot into ubuntu with "Ubuntu 9.04, kernel 2.6.27-14-generic" but only with adding "all_generic_ide" to the parameters.

Any help on this problem would be really appreciated.

Thank You 

Kurt 


System Specs:

AMD Athlon 64 Processor 3500+
A8V-XE Motherboard
2GB DDR333 RAM
Ati Radon x550 *Propriety drivers can't be installed on 9.04
2x 250GA samsung SATA HDD *Ubuntu installed on this
1TB MAXTOR HDD
SATA Samsung DVD-Drive
2x Samsung 22" Monitors

---

### Post by salvachn on 2009-06-22
Might it be the hard disk is heavily fragmented due to access from Windows, and performance takes a hit? So defrag it in Windows and try it again. Or if you find a bug, post it in Launchpad.

---

### Post by geirha on 2009-06-22
Are you using ext4? If so, it may be related to this: [Lock-ups when deleting files from ext4 filesystems]("http://www.ubuntu.com/getubuntu/releasenotes/904#Lock-ups when deleting files from ext4 filesystems")

---

### Post by lovinglinux on 2009-06-22
I guess the fact that you can't install proprietary graphics driver could also contribute for system low performance, but it seems the hard drive is really slowing you down.

Test you hard drive speeds with the command below and post your results:

```
sudo hdparm -tT /dev/[color=#CC0000]sda1[/color]
```

Replace the part in red for each partition accordingly.

You could also try [these tweaks](http://ubuntuforums.org/showthread.php?t=1152095), including formatting the drive as ext4.

> **salvachn said:**
> Might it be the hard disk is heavily fragmented due to access from Windows, and performance takes a hit? So defrag it in Windows and try it again. Or if you find a bug, post it in Launchpad.

When you install Linux you need to format a partition for it, which would erase any previous Windows fragmentation. Additionally, Windows cannot access Linux partitions. 

I don't know if Windows fragmentation could influence a Wubi installation, but it doesn't seems to be the case here.

---

### Post by GingersK on 2009-07-01
Sorry for the late reply, I've been without the net for a week.

Actually the computer is a dual boot with windows 7, completely forgot to mention that in the first post, my apologies. 

Since this problem I have downgraded to Ubuntu 8.10 and installed the propriety drivers for the ati graphics card.

However the problems still persist and the read time off the hard disks is extremely slow.

One thing I have considered is that since only the primary hard disk on which ubuntu is installed is formatted ext3, all other hard disks are formatted NTFS (I should have mentioned initally, it just didn't occur to me). With this in mind are there any ideas that can speed up the hard disks?

Cheers

Kurt

---

### Post by lovinglinux on 2009-07-01
> **GingersK said:**
> Since this problem I have downgraded to Ubuntu 8.10 and installed the propriety drivers for the ati graphics card.

However the problems still persist and the read time off the hard disks is extremely slow.

One thing I have considered is that since only the primary hard disk on which ubuntu is installed is formatted ext3, all other hard disks are formatted NTFS (I should have mentioned initally, it just didn't occur to me). With this in mind are there any ideas that can speed up the hard disks?

Cheers

Kurt

So I think we can discard the graphics card issue.

Having NTFS partitions mixed with ext3 shouldn't have any effect. Did you mounted the NTFS Windows partition on Ubuntu? I'm not sure, but if the NTFS partition is extremely fragmented, then it might be possible that Ubuntu is slowing down while trying to read it. I'm just guessing.

How many partitions you have on the ext3 disk? If Ubuntu installed as the last partition, you might experience reduction in performance because the [disk is slower at the end](http://ubuntuforums.org/showthread.php?p=7391830), but I think your speeds are considerably low. I get those speeds when transferring files with ssh over lan.

---

### Post by GingersK on 2009-07-01
I defragmented the drive but it didn't help the sitation at all.

To my knowlage the hard disk should have three partions (windows, ubuntu and linux swap). I'm not sure what order theyre in but I would still be suprised if it was causing these kinds of slowdowns.

---

### Post by lovinglinux on 2009-07-01
> **GingersK said:**
> I defragmented the drive but it didn't help the sitation at all.

To my knowlage the hard disk should have three partions (windows, ubuntu and linux swap). I'm not sure what order theyre in but I would still be suprised if it was causing these kinds of slowdowns.

Try to test the speed of the Windows partition and compare with the Ubuntu partition. I don't know if the command I provided a few posts back will work on NTFS, but you could try.

---

### Post by HavocXphere on 2009-07-01
There are two modes of accessing IDE drives. Can't remember the abbreviation. The fast one is DMA...DMA5 I think. That would result in 1.5mb/s. And I have no idea how linux handles this...but the dma thing isn't OS specific.

The fact that you had to add "all_generic_ide" suggests that ubuntu is not coping with your gear.

I'd definitely also check CPU utilization. That part about it being slow while typing the post does not sound like hdd issues.

Also, if the mouse is on USB then switch it to another USB port.

And finally, bad sectors could also cause a slow-down...but I don't think this is the cause here.

> fedora without issue
On the same hdd as this?

> The installation was very problematic
Details?

Updating mobo firmware *might* help, but its a long shot.

---

### Post by GingersK on 2009-07-01
Just a quick reply, the CPU utilization is very low (5%) and only 30% ram used aswell..

I'll reply properly to the other parts tomorrow.


Cheers 

Kurt

---

### Post by GingersK on 2009-07-02
Think I'm going to leave the problem here for the time been. I'm getting a new computer next week so hopefully Ubuntu will be more appreciating to that system. 

Thanks for all your help guys, its appreciated. 

Kurt

---

