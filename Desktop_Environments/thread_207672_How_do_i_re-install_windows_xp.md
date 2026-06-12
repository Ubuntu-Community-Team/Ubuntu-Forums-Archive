---
title: "How do i re-install windows xp?"
date: 2006-07-02
forum: Desktop Environments
---

### Post by boyes on 2006-07-02
Hello all,
The other day i installed ubuntu and thought it was ok untill i realized that nearly all programs are designed for microsoft so i then decided to unistall ubuntu and re-install windows xp and then later attempt to create a dual boot system, so i deleted all the partitions on my hard drive to completely remove ubuntu (using gparted) and then i inserted my xp disc into the cd tray and restarted, when the text came up i pressed ESC and selected to boot from my xp disk. It then sounds like it is running the disk and initializing set up, but then it tries to boot from the hard disk (whih has no data on) and so grub error appears and i come to a dead end. How can i install xp? my disk runs in linux using wine and then when i select install an error comes up. Any suggestions?

---

### Post by dpaint4 on 2006-07-02
That's a pretty unhip sentiment, but I think I know where you're coming from. I've been back and forth a few times myself (though I hate to admit it).

A lot of your post dosen't make sense though. What do you mean you're running linux using Wine? 

Are you trying to install Windows XP through Wine in Linux???  (!!!)

No no no. Insert the Windows XP install disc, restart your computer, and boot from the disc, like you did when you installed Linux. When you get to the part where you chose your disc, delete all the partitions and install over the entire disc.

Now for the part that I can tell you from experience... You'll be back to Ubuntu one day soon! You'll discover tons of gorgeous open source applications that you weren't aware of and you'll wonder why you were ever using the commercial versions. And you'll miss how pretty it is and how fast and responsive it is. Or at least, that's my story.

---

### Post by nickpaton on 2006-07-02
Hi Boyes & welcome to Ubuntu! 

As Dpaint says, you need to clean the disk and start from scratch, by installing XP first, and then Ubuntu.  Don't try to use Wine to install XP &#8211; it doesn't work!

To partition the HDD:

Search for and download a Linux recovery disk which will include Qtparted and burn it as an .iso CD.

I have an 80Gb disk which is partitioned as follows:

XP NTFS 50Gb and is installed first.
Linux Ext3 25Gb.  Note that when you come to format this partition it is set up as root and set up as '/' without (' ').
Swap to be about twice the size of your memory.
Finally create a 1Gb FAT32 partition where you can store stuff which you may want to swap between XP and Linux.

Some people also create another partition for their /home folder.  This is the equivalent of the My Documents folder in XP, and by having it separate means that if you need to reinstall Ubuntu then you do not lose any of your saved data.

Any problems get back and let us know how you get on.

---

