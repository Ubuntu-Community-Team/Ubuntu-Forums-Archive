---
title: "newbie question: Ubuntu / XP and file system"
date: 2005-07-27
forum: Desktop Environments
---

### Post by ad noiseam on 2005-07-27
Hello,

Just installed Unbuntu today, after having played a bit with the live CD. The installation went fine, so far so good.

However, I have a question regarding how files and hard drives are handled with Ubuntu.
Here is the situation:
-I have installed Ubuntu on a system that already have XP, and have a dual boot with GRUB. 

-I have partitionned my hard drive this way:
HD1:
   -part 1. NTFS - with XP
   -part 2. - Ubuntu (created during install)
   -part 3. - swap (created during install)
   -part 4. NTFS, with data on it
HD2:
   -part 5: FAT32, with data
   -part 6: FAT32, with data

When I run XP, I can see everything except partitions 2 and 3, so I can neither see nor access the Ubuntu files
When I run Ubuntu, I can see only what I believe is part 2. I have no access to any file from XP, or even to my second HD. When I go to "Places" and go up as much as possibe, it seems I have only one HD, and with one partition on it.

Interestingly, when I start Partition Magic on XP, it tells me that my firsrt HD is "BAD" (yes, all capital letters :) ). It says that there is an error 116 on a partition on disk 1. The LBA and CHS values are no equal. It also says that it could fix this problem.

I don't know if both problems are related, but here are my questions:

**1. how can I do something so that I can access all the partitions from both OS? I have files that I want to access from both Ubuntu and XP.**

**2. should I fix this problem that Partition Magic is reporting? What will happen if I do, what will happen if I don't?**

I hope I can fix at least the first problem, it doesn't make sense not to have access to all my files.

Otherwise, congratulations to the Ubuntu team, the installation was really easy, and all seems to work ok.

Nicolas

---

### Post by ad noiseam on 2005-07-27
Actually, I forgot something, I don't know if it has something to do with the rest:
in GRUB, I have two entries for XP. When I click the first, I get a command line with "grub>", and nothing happens. When I click the second, XP starts fine...
How could I remove the first entry?

---

### Post by OzPhoenix on 2005-07-27
Hey dude,

You simply have to mount the two file systems at a mount point of your chosing. You do this via a terminal with the mount command.

Say you create some directories called /mnt/XP1, /mnt/XP2, /mnt/FAT32-1 and /mnt/FAT32-2. You could then do:

mount -t ntfs /dev/hda1 /mnt/XP1
mount -t ntfs /dev/hda4 /mnt/XP1
mount -t fat32 /dev/hdb1 /mnt/FAT32-1
mount -t fat32 /dev/hdb2 /mnt/FAT32-2

Something like that anyway. Once you get that working, then you can look at making it automatic by adding it to your /etc/fstab.

The thing that could trip you up above is the -t xxx and the /dev/hdxx. As in I'm not sure if there is a fat32 or you're just meant to use msdos, and your drives (and partitions) might be named differently). But above all use this command:

man mount

As for grub configuration, start with:

man grub

Good luck, ope that helps,
OP.

---

### Post by ad noiseam on 2005-07-27
Thanks for your very quick answer.

[QUOTE=OzPhoenix]
Say you create some directories called /mnt/XP1, /mnt/XP2, /mnt/FAT32-1 and /mnt/FAT32-2. You could then do:

mount -t ntfs /dev/hda1 /mnt/XP1
mount -t ntfs /dev/hda4 /mnt/XP1
mount -t fat32 /dev/hdb1 /mnt/FAT32-1
mount -t fat32 /dev/hdb2 /mnt/FAT32-2[/QUOTE]

Ok, I am going to try this, thanks.

[QUOTE=OzPhoenix]
The thing that could trip you up above is the -t xxx and the /dev/hdxx. As in I'm not sure if there is a fat32 or you're just meant to use msdos, and your drives (and partitions) might be named differently). But above all use this command:

man mount

As for grub configuration, start with:

man grub[/QUOTE]

I am not so sure about this. Should I type

man mount

and

man grub

in the terminal after having typed the above?

[QUOTE=OzPhoenix]
Something like that anyway. Once you get that working, then you can look at making it automatic by adding it to your /etc/fstab.[/QUOTE]

Er, where? Does it mean that I need to add these "mount" lines to a file in order to have the partitions / drive mounted every time I start Ubuntu?

---

### Post by shakin on 2005-07-27
It'd be easier if you read the how-to in the Ubuntu Guide: [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

Once you get that working you'll notice that you can't write to the NTFS partitions, only read. If you want to write, look into CaptiveNTFS... there may be a how-to somewhere on this forum, but if not don't worry because it's easy to use. You'll just need to install it and then make a small change to your entry in /etc/fstab that you made for the read-only NTFS partition. The CaptiveNTFS documentation is easy to understand.

---

### Post by karl_kashofer on 2005-07-27
Hi !

After following the (stalled) development of the ntfs driver for linux for a while and having a go at Captive I found a solution that works for me.

I gave up on Captive, as it will get very slow with big files, and you can not access files > 2GB. (or was it 4 ?) Also full writing support for the linux ntfs driver seems far away, and with microsoft changing ntfs all the time it may well never get stable.

Anyway, I found this: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

Its a windows driver for accessing ext2 and ext3 file systems. It works very reliably, and I have just put all my data on the ubuntu drive now. 
I have even moved the "my documents" folder to point to /etc/home/myhome
Its a pity its not open source, maybe some ubuntu users could ask the guy to give it to the community ? 

This is again a demonstration that open standards are more powerful than proprietory software. I am sure if microsoft would publish the specs for their ntfs system it could be supported by the linux crowd.

I am inclined to think that in the long run ntfs will get abandoned, as its not accessible from linux. Unfortunately that driver does not (yet) allow booting windows from ext3, if it ever does I will remove the major p.i.t.a. NTFS from my computer. 

Well, maybe until then I have no need for windows any more anyway.

Cheers,
Karl

---

### Post by jones_jj on 2005-07-27
Ad-  Just as a side note.  If you are in XP you will not be able to see your Ubuntu partitions at all.  Windows does not really play well with Linux, so you will not be able to see any files that you have saved to those partitions.  Hopefully MS will get on the ball and start to play nicely with other file systems, like ext2, ext3, reiserfs, etc.

---

### Post by Hamman on 2005-07-27
[QUOTE=jones_jj]Ad-  Just as a side note.  If you are in XP you will not be able to see your Ubuntu partitions at all.  Windows does not really play well with Linux, so you will not be able to see any files that you have saved to those partitions.  Hopefully MS will get on the ball and start to play nicely with other file systems, like ext2, ext3, reiserfs, etc.[/QUOTE]
 [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

---

### Post by OzPhoenix on 2005-07-27
To clarify what I meant by:
man mount
and
man grub

'man' is a command that access a documentation system called the '**man**ual pages'. If you type man followed by the command name, it will be up the man page for that command (if the page exists). These pages will tell you all about the command.

It's basically similar to pressing F1 in windows.

So what I was saying, is that if you have issues then type 'man mount' to get more information. And if you want to figure out grub a good start point is 'man grub'.

---

### Post by jones_jj on 2005-07-27
[QUOTE=Hamman][http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)[/QUOTE]


Oh hey that's pretty awsome that someone is working on a way for Windows to finally see Linux partitions.   As I said before, maybe one day MS will finally allow Windows to play nicely with others   :grin:

---

### Post by Hamman on 2005-07-28
[QUOTE=jones_jj]Oh hey that's pretty awsome that someone is working on a way for Windows to finally see Linux partitions.   As I said before, maybe one day MS will finally allow Windows to play nicely with others   :grin:[/QUOTE]
 Yeah, when we reached like 50% marketshare ;-)
Wouldn't take them long, as the standards are open, as opposed to NTFS.

---

### Post by coosa on 2005-08-03
Regarding Partition Magic; yes you should let Partition magic fix and there would be no problem after that.
Partition magic will include all linux partitions including the swap partition under an extended one.
I had experienced that problem with mandrake and ubuntu and made partition magic fix the problem and had no problem by booting or accessing after that.

Coosa

---

### Post by frodon on 2005-08-04
[QUOTE=jones_jj]Oh hey that's pretty awsome that someone is working on a way for Windows to finally see Linux partitions.   As I said before, maybe one day MS will finally allow Windows to play nicely with others   :grin:[/QUOTE]I think it will be possible very soon because with windows I can already make a ghost image of my linux partition using norton ghost which see ext2 and ext3 format.

---

### Post by eyolf on 2005-09-29
I'll jump in here with some questions:

Background: new to linux, tried a live CD, wants to install linux on a machine with WinXP, 40 Gb harddisk, only one partition, c. 25 Gb filled with data already.

Questions:
1. I would like to be able to access all my data files both from linux and from Windows. Have I understood it correctly, that I can/should set up three partitions: one for Windows (10Gb?), one for Linux (10Gb?) and one shared (20Gb)?
2. How do I set up the partitions, given the amount of data on the hd at the moment? Do I do it in several steps? First set up one of, say 13 Gb (there is currently 14 Gb free space on the hd), then move the to-be-shared files to that one, then split off the space that is now freed into another partition - the one to which I will install Ubuntu - and then, perhaps, adjust the sizes to 10-20-10? Or is there an easier way? 
3. Is there a risk of data loss in any of these procedures? E.g., if I make a new partition now, with 20 Gb, what will happen to the 5Gb of data that would not fit on the old partition?
4. The shared partition, should that use FAT32? 

I'm sorry if these questions have been asked a milllion times already (which I'm sure they have).

---

### Post by karl_kashofer on 2005-11-24
Hi !

Try [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

Its a driver for Windows which gives you full read and write access to linux ext2 volumes, so you can keep all your data on the linux partition.

It also works for ext3 but messes up the journaling, so you will get a disk check every time you change something on the ext3 disk. You can disable journaling, but then you basically have a ext2 partition.

The only gripe i have with it is that its not open source.

Cheers,
Karl

---

