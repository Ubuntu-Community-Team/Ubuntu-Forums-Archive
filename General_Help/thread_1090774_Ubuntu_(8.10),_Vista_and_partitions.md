---
title: "Ubuntu (8.10), Vista and partitions"
date: 2009-03-08
forum: General Help
---

### Post by edlondon on 2009-03-08
Hi

This post is in two parts. Firstly to describe my (highly positive) experience installing Ubuntu and, secondly, to pose a few general questions. 

So, a friend has given me a spare Compaq C700 notebook (as a sort of payment to recover his data from the notebook, he has since migrated to Apple).  Well anyway data recovered, via a usb caddy, and portable recovered to Vista factory default (via recovery partition).   Since then I installed Ubuntu (8.10) into a free partition created with the Vista partition manager. Install this morning went just fine. I was slightly worried my wireless client would not be seen. I should not have fretted, it took about 90 seconds for the driver (broadcom) to be found, installed and a strong internet connection to be made. Then it was off to the races!  Fully updated install (about 400 patches), migrated firefox settings and everything 'just works'. So a big 'high five' to all the developers and people behind Ubuntu. I have never installed a Linux OS before, I'm simply blown away as to the ease and speed of this OS. 

So much so, I think I will just dump Vista on this machine and go with Ubuntu 100% (forget about partitions etc).  

So, now, the questions ;)

How do I just get rid of the Vista partition and use that space for ubuntu? I see various comments recommending GParted etc, but these solutions seem to be resizing partitions rather than just getting rid of the vista (or other OS) partition. There also seems to be an issue of not being able to move the start of the ubuntu partition. If this is the case then it seems that if I did a resize there would be vacant holes on the drive. Thoughts?

Given that this machine does not hold any live data (only Vista, its recovery partition and the ubuntu partitions, all on a 160gb drive), maybe the way forward is to just go the whole way by doing a full fresh install of ubuntu and use the whole disc?  If this is the way I should go then how can I back up the hidden Vista recovery partition?  Is there a utility that I can use to dump that hidden partition to a DVD and if required at a later date to be able to restore that hidden partition?

Once I have ubuntu installed such that it takes the whole disc I plan on installing Sun Virtualbox and then XP (in Virtualbox). This is so I can then install much needed apps such as Photoshop, Adobe Premiere and other Windows apps that I own. Or there a better way of doing this?  I have not tried Wine yet, but I read that, for some windows apps, Wine is not the solution.  What the pros and cons of Virtualbox vs. Wine?  Or maybe there is a better way of doing VM? 

Oops, this post if too long! :lolflag:  Especially for a first post. #-o

thanks
Ed

---

### Post by miegiel on 2009-03-08
Gparted also lets you delete partitions (and resize the remaining ones to use the full disk). However you can't do anything on mounted partitions. If you can't unmount a partition, your best option usually is the Gparted live CD. It boots to a minimal linux with gui and gparted.

The remaining vista boot option is just some lines in your /boot/grub/menu.lst, in mine they go like:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

BTW you can run into some troubles if the windows partition is the "active" partition on your disk and/or the 1st partition (sometimes the active "flag" is called boot).

ps I always have a backup OS on my PCs, just in case I break it and fixing it needs to wait. You could just make windows use less of your disk and keep it, or as I do, put a backup linux on the partition.

---

### Post by edlondon on 2009-03-08
miegiel

Thanks for the response, much appreciated.

Good news on GParted (in boot mode) being able to delete partitions and resize the rest.

What problems may I run into if the Vista partition is the first partition?  Which it is.

Any ideas of how I may be able to backup the Vista Recovery Partition? If I can do this and be confident that I can restore it then i think i will do that and then just delete all partitions and install Ubuntu to occupy the whole disc. (deleting every partition before I do).

Ed

---

### Post by miegiel on 2009-03-08
Maybe partimage is what you need, it is in the ubuntu repros. I've got no experience using it though. [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

Oh ... almost forgot :)
If the windows partition is the active partition the disk might not boot after you delete it. Marking your linux partition as active should fix this in most cases I think, but I've avoided having to mess with it for a long time now. Sometimes "active" is also called a boot flag/lable)

edit (again)
[Backup and Restore Linux Partitions Using Partimage]("http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html") looks good :)

---

### Post by edlondon on 2009-03-09
Hi miegiel

Thanks for the useful suggestion.  I'm now running partimage in the back ground and am waiting to see how things work out. Partimage says that NTFS support is experimental, mostly depending on how fragmented the NTFS partition may be. 

Anyway, I'll come back and report sucess, failure or otherwise ..... :)

Ed

---

### Post by 3Miro on 2009-03-09
Partitioning is tricky business. Make sure you have all relevant data in a backup.

Experimental NTFS would mean that resizing NTFS partition might not work well. If you delete NTFS (which any partition manager can do), you should be able to simply resize the Linux partition with no NTFS interference. I have never done resizing of a partition so except for the backup, all of my advice could be incorrect.

For wine vs VB. VB cannot play DirectX games, not all apps wrok on wine. I use wine for games and VB for regular apps (very few). I don't know about photoshop, they say that CS2 works well with wine, depending on what you need this might work for you:
[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

---

### Post by edlondon on 2009-03-10
Thanks 3miro. Yeah last night I was playing around with Wine and tried various windoze apps (not PS yet) and although they all seemed to install correctly, not one of them ran correctly. I tried a variety of apps such as file utilities, ftp clients, photo browsers etc. I'm probably doing something wrong somewhere. Also I can't seem to uninstall these apps. I run the uninstall routine (via Wine) and it 'looks' like the uninstall occured in fact the apps are still there.  Oh well, something else to sort out when I get time.

Have not played with VB yet. Maybe I will later tonight, assuming I'm not on dinner cooking duties. :D

Meantime, as I mentioned earlier, I ran partimage and that apparently ran to conclusion. However when I try to move the two resultant files (000 and 001, each 2gb, which itself is strange) to a dvd+r the DVD writer software (forget which it was as I'm not on that machine now) says that the two files are invalid. So another puzzle.

The main thing I want to achieve for now is to backup the recovery partition and be sure that I can restore it. Then I will simply just do a fresh Ubuntu install using the whole disc. For the partition backup and restore tools maybe I should use something from the Windoze world - like Norton Ghost? :eek: :)

Ed

---

