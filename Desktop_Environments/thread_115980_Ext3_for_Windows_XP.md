---
title: "Ext3 for Windows XP"
date: 2006-01-11
forum: Desktop Environments
---

### Post by EnderTheThird on 2006-01-11
I've been googling and I found software ("[Ext2 Installable File System for Windows]("http://www.fs-driver.org/index.html")") that will let Windows read/write Ext2 and Ext3 file systems.  I was wondering if any of you have had experience with this program.  I'm thinking about reformatting my (currently NTFS) HDD that houses all of my music, movies, school, and other personal documents to Ext3, assuming I have enough room on my other 2 drives to temporarily store everything while I reformat the disk.

Do any of you know how reliable/stable the software is when used with Ext3 in Windows?  I've never had any problems with Ext3 in Ubuntu, but I've also never had to have files stored on there for nearly as long because I usually end up trying a fresh install after I mess something up.  :)  I'd love to be able to read/write to that disk in both Windows and Ubuntu, but I also need to make sure that my files are going to survive both OS's reading/writing without getting corrupted.  I know that NTFS write access in Linux is iffy, so I figured using Ext3 with Windows might be better if it's "safe" to use.  Thanks for your input.

P.S.  I know how to mount disks/partitions separately, as with a Home partition if I wanted it to survive fresh installs.  But I've never used my Ubuntu HDD for storing anything that can't be replaced because I use Windows most of the time, which is because I can use Windows to read/write to my HDD with all of my files on it.  And I haven't had any luck with getting WoW to run well with Cedega at the correct resolution and with working sound.  Stupid ATI video card, heh.

---

### Post by hillbilly on 2006-01-11
whoa !! I thnk you have to hold on here. I dont thnk windows applications can be installed on ext2 file system. So go easy before you format your entire windows filesystems to ext2. And of course post back your results ;) !

But yeah you would be able to read linux partitions and write onto them and that I guess is certainly tempting, if you use windows a lot more than linux.

---

### Post by EnderTheThird on 2006-01-11
Oh, sorry, I guess I didn't make this clear.  If I formatted the HDD with Ext3, it would be used for file storage ONLY (just as it is now).  No programs would be installed on it, in Windows or in Linux.  Neither would it serve as a Home folder in Linux.  I would just mount it as /home/user/Documents (which it is now, but with read only access) or something like that, so that it wouldn't host any configuration files for Linux (from what I've read, that Windows software has trouble with files/folders beginning with ".").  It would just be used to store all of my music, movies, school documents, downloads, etc. that I would need frequent read/write access to in both operating systems.  Better?  ;)

---

### Post by hillbilly on 2006-01-12
oh yeah that rocks all right :D

---

### Post by rubengs on 2006-01-12
I use this small program and is transparent to windows, the ext3 drives are mounted as letters [C-Z:] and you can use them as any other drive, even for installing applications. All my drives are now ext3, except for a small partition (15GB) for windows. I don't use windows too much so I don't need that ntfs partitions anymore.

---

### Post by patrickfromspain on 2006-01-12
You could also use FAT32.. both OS will be able to read and write to it without any trouble.

---

### Post by Harleen on 2006-01-12
I'm using that program and it works quite well for accessing my Ext3-Linux Partition. It should work for your purpose. But I'd prefer a FAT partition for data exchange, because that ext3 driver has some disadvantages:

- Windows always creates a Trash folder when you delete files. 
That shouldn't matter in your case, but If you delete files on your partition mounted as / you may find that /RECYCLED-folder  quite annoying...

- files written with windows get the ownership 'root'

- you can create filenames with Linux, that cannot be read with Windows
That happened to me sometimes when I ripped CDs, which album names contained backslashes or apostrophes, which aren't allowed in Windows file names. And I think (not shure at the moment) that there were some problems with Ubuntu writing file names in Unicode, while Windows expected some ISO charset. But is only a problem if you use characters not represented in the ASCII charset like German Umlauts.

---

### Post by Rackerz on 2006-01-12
I use that program, works pretty well. I hesitated to install it at first but it all worked out in the end. It says for use with Ext2 but it works in just the same way with Ext3.

---

### Post by MetalMusicAddict on 2006-01-12
I talked about this a little while ago. Give it a read.

[Wanna read/write to your Ext2/3 drive from windows? ]("http://www.ubuntuforums.org/showthread.php?t=107311")

Gets heated but still good info. I have noticed that when writing LARGE files to the drive it didnt like it in **my** case. Other than that it was fine.

---

### Post by Nrvnqsr on 2006-01-12
[QUOTE=patrickfromspain]You could also use FAT32.. both OS will be able to read and write to it without any trouble.[/QUOTE]

but the problem is that files that are larger than 4GB will not be recognized by FAT while ext2/3 does and when you got DVD ISOs and any large files its an issue.

so far my EXT3 partition in my laptop is doing so far so good at the moment, I been heavily writing in the partition in Windows. **But** you can't defragment the filesystem with windows.

---

### Post by becatlibra on 2007-09-17
> **rubengs said:**
> I use this small program and is transparent to windows, the ext3 drives are mounted as letters [C-Z:] and you can use them as any other drive, even for installing applications. All my drives are now ext3, except for a small partition (15GB) for windows. I don't use windows too much so I don't need that ntfs partitions anymore.


um - what program is that?

---

### Post by checho4 on 2007-09-21
Hi, I have all of my music files saved onto an ext3 partition that is read from and written to in both Windows and Kubuntu Feisty [64bit].  There was no problem with this until about 3 days ago.  I started getting an error upon startup that told me that the trash protocol could not be started.

At the same time, I couldn't access my music partition.  If any application tried to get to it, the application would hang.  Amarok won't even OPEN.  I'm not sure if it's this program or Windows that did something.

---

### Post by PmDematagoda on 2007-09-21
Run fsck on the affected hard drives except the main one. I assume you know how to run an fsck?

Usually the integrity of the hard drives can be compromised by the program itself, because my program I use to read my ext3 file systems causes the journal file to be out of date, as given in the first post, it's for ext2 file systems, so everytime I use XP and need to go back to Linux(Ubuntu), Linux automatically performs fsck on the root file system. So don't use those programs unless you really need to.

You can have a look at this thread:-

[http://ubuntuforums.org/showthread.php?t=529321&page=3](http://ubuntuforums.org/showthread.php?t=529321&page=3)

---

