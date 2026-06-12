---
title: "On which partition, or where, did my Ubuntu 7.04 get  installed???"
date: 2007-05-09
forum: Desktop Environments
---

### Post by john3333 on 2007-05-09
Obviously, I'm a Ubuntu newbie, so hope someone can help with the following.
I just installed Ubuntu 7.04 on a 20GB disc, which I previously partitioned into one 10GB NTFS partition, and one 10GB FAT32 partition. 
The 10GB NTFS partition holds Windows2000 (which is working).
I intended to install Ubuntu 7.04 on the other 10GB partition (FAT32).
But during the installation process, I stumbled around so much in the 'partitioning' section (first tried to do everything 'manually' which may have caused my problem) that I'm not sure how the installation succeeded.
Finally, however, I did get Ubuntu installed, and it's working okay.
BUT . . . 
I have no idea where (on which partition) it is installed. 
Now, when I look at this disc using Windows2000, it shows two partitions, but the second (the FAT32) partition shows only 477MB of space, of which 8kb is used.
I assume I created this 477MB of space inadvertentlly when I was stumbling around in the Ubuntu install process, and was trying to create a 500MB swap file, which I thought it was demanding that I do.
When I look at the disc using Ubuntu 7.04, it shows one partition holding Windows2000, another partition holding this 477MB of space, and also a third icon which looks like a HD icon, but is called File System, which is where I assume maybe my Ubuntu 7.04 is installed.
My question is this:
If, in fact, Ubuntu is installed in this File System, on which partition is this File System residing???? 
Clicking on Properties in Ubuntu does not tell me. And, of course, I can't see this File System icon at all using Windows2000.
Thanks for any light anyone can shed on this.

---

### Post by Kevanx on 2007-05-09
I deal well with things graphically, so I believe that if you install Gparted sudo apt-get install gparted that it should tell you what and where your partitions have been placed. You can look it up in a text file somewhere in the root system (I can't remember the name of it), but it's messy and difficult to read. Gparted is nice and clear, and can help you to resize the partitions as you need it.

Also, the 477 Mb partition might very well be the appropriate 500 Mb partition, because of the base 2 vs. base 10 confusion that computers suffer - took me a lot of trial and error to get my partitions. I can't do the math, but this is a good explanation of why that partition might be the size you requested:
[http://mathforum.org/library/drmath/view/54359.html](http://mathforum.org/library/drmath/view/54359.html)


> If, in fact, Ubuntu is installed in this File System, on which partition is this File System residing????
Clicking on Properties in Ubuntu does not tell me. And, of course, I can't see this File System icon at all using Windows2000.


Linux is probably on the HDA1 partition, but not necessarily. Can you boot up with ubuntu, or are you running off of the CD? If you can boot up, then yes it is installed. Also, windows (using the NTFS file system) and Linux (Using the EXT3 file system) don't talk too well. To get windows to see any of Ubuntu's files in the windows network, you need to share stuff with Samba (plenty to find in the forums) and also I think, install an NTFS-EXT3 translator, but I think that might have been automatic in Feisty Fawn. Regardless, a search for windows networking should provide plenty of tutorials. But I may be misunderstanding your question.
I hope this helps!

---

### Post by merlinus on 2007-05-10
Entering the following in a terminal will perhaps give you the information:

sudo fdisk -lu

hth...

-merlin

---

