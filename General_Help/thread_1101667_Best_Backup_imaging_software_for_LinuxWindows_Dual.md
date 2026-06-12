---
title: "Best Backup imaging software for Linux/Windows Dual Boot HDD ?"
date: 2009-03-20
forum: General Help
---

### Post by 1ronlung on 2009-03-20
Hi.  I really need to get a backup image of my HDD - it's taken me ages to get my configuration just right.  Now, my laptop HD consists of a NTFS part, ext3 part and Linux swap part.

I want to image the whole lot to an external hard disk.

I was looking at a Linux freeware app earlier that seemed to tick all the boxes.  Sorry - the name of it evades me right now.  However, there was a glitch with it where you couldn't transfer from a bigger HD than the one you were writing to.

Obviously, freeware is far preferable.

Looking at commercial software, ghost for windows will now image ext3 partitions and swaps.  However, I've used Ghost on Windows and ever since they've started running it within W2K, in my experience, the images have been unreliable when written back.  Random reboots, that sort of thing.

I'm currently looking at Terabyte Unlimited Image for either Windows or Linux.  Linux us a tenner cheaper, so I'll probably side with that.  Also figure they're would be less hassle with file shares while imaging.

If anyone has any sage advice or experience to add, please do !

ironlung

---

### Post by dusan.saiko on 2009-03-21
I have never found a reason to look at any commercial software for backup.

For Linux partition you could just archive your files with tar utility (this is sufficient), or if you would like to have complete disk/partition image, I would just use the dd command to backup the partition, or whole harddisk. 

I would boot to any liveCD distribution (I use Trinity Rescue Kit which has automatic networking) then plug your USB storage and then copy and zip the partition into file.

PLEASE do not just try to execute any of following commands, you have to be sure first what the commands are doing and you have to change the parameters relevant to your system. dd command is very dangerous and you can destroy your data if you use it incorrectly !

- to backup whole harddisk:
dd if=/dev/sda bs=1M | gzip -c > /media/STORAGE/harddisk.img.gz

- to backup different partitions:
-- first backup a MBR (Master Boot Record - info about partitions)
dd if=/dev/sda of=/media/STORAGE/mbr.img bs=512 count=1 
-- to backup partition sda1
dd if=/dev/sda1 bs=1M | gzip -c > /media/STORAGE/windows.img.gz

---

### Post by 1ronlung on 2009-03-24
I know it's cheating 'cos it's Windows, but I found  [http://www.macrium.com/default.asp](http://www.macrium.com/default.asp) which will do an image of a windows or windows & Linux dual boot PC

Haven't tried restoring yet, so will hold off my opinion until I do.

At the time of my first post, they had a free version available that would do the job.  Upon checking now, it doesn't appear to be available now.  Dunno if they'll put it up again ...

---

### Post by uidb4056 on 2009-03-24
You can have a look at Clonezilla ( [http://www.clonezilla.org]("http://www.clonezilla.org/") ) it can solve your needs.

---

### Post by 1ronlung on 2009-03-25
Cheers dude, but that's the sofware I was refering to when I said 
"I was looking at a Linux freeware app earlier that seemed to tick all the boxes. Sorry - the name of it evades me right now. However, there was a glitch with it where you couldn't transfer from a bigger HD than the one you were writing to."

The name just rang a bell :)

---

