---
title: "Sharing files between multiple computers and OSes"
date: 2005-12-09
forum: General Help
---

### Post by SimonJW on 2005-12-09
Ok, so as a bit of a geek, I have (and regularly use) three computers - a Windows laptop, an Ubuntu desktop and a Mac mini. The problem is, I have certain files (mp3's, photos) that I'll always want to have access to, no matter what computer I'm on at the time. Let's say around 60 gig of files, total.

The ideal solution is obviously to set up a file server, but as I'm a uni student I take my computers around the country, and don't want to have to carry a file server around with me too. Plus, I won't necessarily take *all* those computers with me to uni (typically only one, sometimes two), so the ones I leave behind would be unusable for my parents as there would be errors about the missing file server.

So, here's the question - how to keep these files accessible from all the computers? At the moment, I have a physical copy of the data on each computer, but this means that keeping them all up-to-date is a tedious process at best. Everytime I change something, I have to remember what it is and then copy the new files across manually. The way I see it, I have two possibilites:


**External drive** - this has the benefit of being low-cost (I have the drives, I'd just need to buy enclosures) and low-tech. On the other hand, I already use one external drive for non-essential files, and adding more would be noisey, take up space and plug sockets, and be bulky. Also, I couldn't access the data on both computers at the same time.

**Server at home** - I could set up a server at my home that has my files on it. Because I would not always be in the same place as my server, I would keep a physical copy of my files on each computer, and set each computer to rsync with the server once a day. This would keep bandwidth low, which is important as these syncs would be happening across the internet. It is not really a problem for me to keep a seperate physically copy of the data on each computer. 
This method has the disadvantage of having to build a server (I have the parts, but not necessarily the know-how) that could run 24-7 for the 8 weeks I am at Uni, without any attention(short of ssh access). It would also have to be secure, as I will need to access the files on it from across the internet, but keep my data private and my server un-hacked.
This is an ideal solution, but sounds very complicated for me to implement...


Does anyone else have any better ideas, or anything to say for or against my two methods? How does everyone else keep track of all their files? This must be quite a common thing for many geeks - how do you make sure you  have your music files available when you're surfing the web in Starbucks, away from the home network? :)[LIST]
[/LIST][INDENT][/INDENT][INDENT][/INDENT][INDENT][/INDENT][INDENT][/INDENT]

---

### Post by MetalMusicAddict on 2005-12-09
If you go the external route 1 option that would fit all 3 woult be a FAT32 drive. Then you are limited to a 4gig filesize and a partition size limit. I do forget what this is though. I thought it was 32 but I think there is a way around that.

I know of a windows driver you could use to read/write Ext2/3 drives. [Ext2 IFS]("http://www.fs-driver.org/"). Im not sure if macs can use ext2/3.

I have a 60gig laptop drive in a USB2 case in Ext3 I use.

---

### Post by SimonJW on 2005-12-09
Thanks for the advice **MetalMusicAddict**!

My problem isn't so much the setting up of the external hard disk. As I say I already use one external HDD (which is 160 GB in a single FAT32 partition) to share less 'essential' data between the computers - all three systems can access this drive perfectly.

*[Incidentally, the theoretical limit for a FAT32 drive is 2 terbytes - to use Microsoft Scandisk you need a drive of less that 120 GB, and Windows 2000/XP imposes a limit of 32 GB - it'll read bigger drives, but won't create them. So I formatted the drive in good ole' Ubuntu :) Info [here!]("http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32")]*

With the external drive, I'm more concerned about the size, noise, power consumption and most of all, the fact that it is accessible from only one machine at a time.

To be honest, I'm leaning towards the second set-up, but it sounds **really** complicated. It'll be a good geek project, at least!

---

### Post by ninotob on 2005-12-09
[QUOTE=SimonJW]With the external drive, I'm more concerned about the size, noise, power consumption and most of all, the fact that it is accessible from only one machine at a time.[/QUOTE]

You probably don't have a laptop drive hanging around, but an **external laptop drive **is the way to go.  I have usb/firewire shell on an 80gb laptop drive.  It's powered by a single firewire port or when using usb, two usb ports (one data one power).  It's practically silent, as in I have to get my ear within inches of it to hear it.  There is no extra power cord and it's really quite small -- it fits in a regular shirt pocket just fine, too loosely in fact.  It would definitely fall out if I bent over with it in my pocket.

Anyway, a laptop drive in a small enclosure is quiet, power friendly, and extrememly portable.  It would probably run you about $120-150, but that's cheaper than a 4th system.  As for accessing it from all at once, I'm sure you could manage that easily if attached to the linux or mac box.

---

