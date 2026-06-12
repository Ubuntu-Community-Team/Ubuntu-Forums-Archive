---
title: "What defrag utilites can i use in Ubuntu?"
date: 2009-01-31
forum: General Help
---

### Post by Macfunky on 2009-01-31
I have looked everywhere for a defrag utility and can't seem to find one. All I keep getting is "you don't need to defrag Linux". I understand that it uses a different file system but that doesn't completely stop fragmenting of files. I heard that Linux uses a different name for defragging. Maybe that has been my problem in finding a utility?

Also theres similar response when searching regarding virus protection. I would still prefer to have protection even if Linux is not as prone to virus'

Any help would be appreciated :D

---

### Post by DeMus on 2009-01-31
> **Macfunky said:**
> I have looked everywhere for a defrag utility and can't seem to find one. All I keep getting is "you don't need to defrag Linux". I understand that it uses a different file system but that doesn't completely stop fragmenting of files. I heard that Linux uses a different name for defragging. Maybe that has been my problem in finding a utility?

Also theres similar response when searching regarding virus protection. I would still prefer to have protection even if Linux is not as prone to virus'

Any help would be appreciated :D

I don't know where you heart it, but:

**Linux does not need a defragmenting tool because files are not defragmented**

The Ext3 filesystem prefends files from becoming defragmented.

Just accept and enjoy that.

There are anti-virus programs running in Linux but all they do is look for Windows viruses. So they are of no use. Don't let your CPU lose power because you have a useless anti-virus program running.

---

### Post by Rinzwind on 2009-01-31
Degfragmentation: forget about it. I shall repeat it: forget about it.
Read this part: [http://dataexpedition.com/~sbnoble/Tips/filesystems.html#Optimization](http://dataexpedition.com/~sbnoble/Tips/filesystems.html#Optimization)
and this
[http://www.whylinuxisbetter.net/items/defragment/index.php?lang=](http://www.whylinuxisbetter.net/items/defragment/index.php?lang=)
> Does your digital life seem fragmented ?

If you already know what fragmentation is, and are already used to defragmenting your disk every month or so, here is the short version : Linux doesn't need defragmenting.

Now imagine your hard disk is a huge file cabinet, with millions of drawers (thanks to Roberto Di Cosmo for this comparison). Each drawer can only contain a fixed amount of data. Therefore, files that are larger than what such a drawer can contain need to be split up. Some files are so large that they need thousands of drawers. And of course, accessing these files is much easier when the drawers they occupy are close to one another in the file cabinet.

Now imagine you're the owner of this file cabinet, but you don't have time to take care of it, and you want to hire someone to take care of it for you. Two people come for the job, a woman and a man.

    * The man has the following strategy : he just empties the drawers when a file is removed, splits up any new file into smaller pieces the size of a drawer, and randomly stuffs each piece into the first available empty drawer. When you mention that this makes it rather difficult to find all the pieces of a particular file, the response is that a dozen boys must be hired every weekend to put the chest back in order.
    * The woman has a different technique : she keeps track, on a piece of paper, of contiguous empty drawers. When a new file arrives, she searches this list for a sufficiently long row of empty drawers, and this is where the file is placed. In this way, provided there is enough activity, the file cabinet is always tidy.

Without a doubt, you should hire the woman (you should have known it, women are much better organized :) ). Well, Windows uses the first method ; Linux uses the second one. The more you use Windows, the slower it is to access files ; the more you use Linux, the faster it is. The choice is up to you!

Linux uses a journaling system so it does not matter where the files are stored.

If you want to you can check out fsck and the -a option
[http://linux.die.net/man/8/fsck](http://linux.die.net/man/8/fsck)
> fsck(8) - Linux man page
Name
fsck - check and repair a Linux file system
Synopsis
fsck [ -sAVRTNP ] [ -C [ fd ] ] [ -t fstype ] [filesys ... ] [--] [ fs-specific-options ]
Description
fsck is used to check and optionally repair one or more Linux file systems. filesys can be a device name (e.g. /dev/hdc1, /dev/sdb2), a mount point (e.g. /, /usr, /home), or an ext2 label or UUID specifier (e.g. UUID=8868abf6-88c5-4a83-98b8-bfc24057f7bd or LABEL=root). Normally, the fsck program will try to handle filesystems on different physical disk drives in parallel to reduce the total amount of time needed to check all of the filesystems. 


fsck is used to repair your filesystem, If Linux would needed a defrag tool this command would have an option for it.

Virussen: read this please 
[http://www.whylinuxisbetter.net/items/viruses/index.php?lang=](http://www.whylinuxisbetter.net/items/viruses/index.php?lang=)

> Forget about viruses.

If your computer shuts itself down without asking you, if strange windows with text you don't understand and all kinds of advertisements appear when you don't ask for them, if emails get sent to all your contacts without your knowing it, then your computer probably has a virus. The main reason for this is because it runs Windows.

Linux hardly has any viruses. And that's not like "Oh well, not very often, you know". That's like "If you've ever heard of a real Linux virus, please tell me". Of course, a Linux virus is not impossible to get. However, Linux makes it very hard for this to happen, for several reasons:

    * Most people use Microsoft Windows, and pirates want to do as much damage (or control) as possible: therefore, they target Windows. But that's not the only reason; the Apache web server (a web server is a program located on a remote computer that sends web pages to your browser when you ask for them), which is open source software, has the biggest market share (against Microsoft's IIS server), but it still suffers from much fewer attacks/flaws than the Microsoft one.
    * Linux uses smart authorization management. In Windows you (and any program you install) usually have the right to do pretty much anything to the system. If you feel like punishing your PC because it just let your precious work disappear, you can go inside the system folder and delete whatever you want: Windows won't complain. Of course, the next time you reboot, trouble begins. But imagine that if you can delete this system stuff, other programs can, too, or just mess it up. Linux doesn't allow that. Every time you request to do something that has to do with the system, an administrator password is required (and if you're not an administrator on this system, you simply can't do it). Viruses can't just go around and delete or modify what they want in the system; they don't have the authorization for that.
    * More eyes make fewer security flaws. Linux is Open source software, which means that any programmer in the world can have a look at the code (the "recipe" of any program), and help out, or just tell other developers "Hey, what if blah blah, isn't this a security flaw?".



The only reason for a virusscanner in Linux is to scan incomming emails that are forwarded into your network where you have Windows PC's.
There is an AVG version for Linux [http://free.avg.com/4040](http://free.avg.com/4040)  
and there is also CLAM AV: [http://www.clamav.net/](http://www.clamav.net/)
There are also 3 packages inside add/remove when you search for virus: virus scanner (GUI for CLAMAV) Stepbill and XBill.


When using Linux free your mind. Stop thinking the Windows way because that way if flawed; Linux != defragging. Linux != virusses.
Yes there are virusses for Linux but these do not run wild and as long as you stick to the regulare sources for installing software you will never ever get a virus (yes I am certain about that).

---

### Post by mb_webguy on 2009-01-31
Bravo, Rinzwind!  That's one of the best-written posts on the subject I've read lately.  I would just like to make one clarification, though.  When Rinzwind says "Yes there are virusses for Linux but these do not run wild", what he means is that the Linux viruses known to exist are technical curiosities which you're not likely to encounter except on an old, dusty disk on a shelf in some university's computer science department.  There has *never* been a computer virus "epidemic" on Unix-based systems like the ones that *continually* spread through the Windows world.  Linux viruses simply don't exist "in the wild".

[Here]("http://librenix.com/?inode=21") is a very interesing article that explains why viruses don't fare well on Linux, comparing them to biological viruses.  (Do please read the footnote on the Bliss "virus" -- which is polite enough to uninfect your system for you -- and keep in mind that you still have to manually run the program for it to infect your system in the first place.)

And no, you don't have to defragment Linux file systems because they do not get fragmented.

---

### Post by Rinzwind on 2009-01-31
mb_webguy: I just type a basic post and try to find some websites where someone else did all the work so I can copy/paste it to add to my own comments ;) Nothing fancy :+
LOL

Thanks for the addition on my post.

---

### Post by Vince4Amy on 2009-01-31
> Linux does not need a defragmenting tool because files are not defragmented

The Ext3 filesystem prefends files from becoming defragmented.


ext3 is **NOT** immune to fragmentation.

---

### Post by em4r1z on 2009-01-31
While it's not as important as it is within Windows, there's fragmentation within a Linux file system and there are different ways of dealing with it depending on your file system. As far as I know, only XFS provides online defragmentation. I use JFS and I have to move my files to a different location before a defragmentation.

Regarding the anti-virus, if you share documents with Windows systems, you'll need one, for even though your Linux system won't be affected, you can spread a virus because you won't know if a file is infected. Try Avast!

---

### Post by Rinzwind on 2009-01-31
> **Vince4Amy said:**
> ext3 is **NOT** immune to fragmentation.

Correct. 
The difference between Linux and Windows is that Windows gets slower when defragmented. The journaling system Linux uses knows where all parts are and therefor locating them costs 'no' time.
To all: please read the 2nd quote in my 1st post for an analogy :+

---

### Post by em4r1z on 2009-01-31
> **Rinzwind said:**
> Correct. 
The difference between Linux and Windows is that Windows gets slower when defragmented. The journaling system Linux uses knows where all parts are and therefor locating them costs 'no' time.
To all: please read the 2nd quote in my 1st post for an analogyWindows has been using quite a decent journaling file system for the last decade. Linux file systems fragment, no matter what analogy you use.

---

### Post by Rinzwind on 2009-01-31
> **em4r1z said:**
> Windows has been using quite a decent journaling file system for the last decade. Linux file systems fragment, no matter what analogy you use.

Oh is that way Vista had a defrag scheduled by default to run in the background on wednesdays?

---

### Post by Cresho on 2009-01-31
> **Macfunky said:**
> I have looked everywhere for a defrag utility and can't seem to find one. All I keep getting is "you don't need to defrag Linux". I understand that it uses a different file system but that doesn't completely stop fragmenting of files. I heard that Linux uses a different name for defragging. Maybe that has been my problem in finding a utility?

Also theres similar response when searching regarding virus protection. I would still prefer to have protection even if Linux is not as prone to virus'

Any help would be appreciated :D

no defregger needed
no virus scanner needed.  OHH WAIT!  I have a worm but it cant run out of my folder.  I keep double clicking on it but it wont execute.  I also executed it in wine....but i removed association from it.  so my worm requires me to let it run.

---

### Post by em4r1z on 2009-01-31
> **Rinzwind said:**
> Oh is that way Vista had a defrag scheduled by default to run in the background on wednesdays?I guess you confuse journaling with fragmentation. Read about it and you'll see. They're different advantages of modern file systems.
The fact that Vista schedules a defragmentation every week (I didn't know it did for I've never used it) only means that its file system is more prone to fragmentation than the ones currently used in Linux. It doesn't mean that the Linux file systems don't fragment. They do and they give you various options to deal with it, depending on the file system you use.

---

### Post by hyper_ch on 2009-01-31
The Linux Document Pages:
> 
5.10.11. Fighting fragmentation?

When a file is written to disk, it can't always be written in consecutive blocks. A file that is not stored in consecutive blocks is fragmented. It takes longer to read a fragmented file, since the disk's read-write head will have to move more. It is desirable to avoid fragmentation, although it is less of a problem in a system with a good buffer cache with read-ahead.

Modern Linux filesystem keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system.

In the earlier days of the ext2 filesystem, there was a concern over file fragmentation that lead to the development of a defragmentation program called, defrag. A copy of it can still be downloaded at [http://www.go.dlr.de/linux/src/defrag-0.73.tar.gz](http://www.go.dlr.de/linux/src/defrag-0.73.tar.gz). However, it is HIGHLY recommended that you NOT use it. It was designed for and older version of ext2, and has not bee updated since 1998! I only mention it here for references purposes.

There are many MS-DOS defragmentation programs that move blocks around in the filesystem to remove fragmentation. For other filesystems, defragmentation must be done by backing up the filesystem, re-creating it, and restoring the files from backups. Backing up a filesystem before defragmenting is a good idea for all filesystems, since many things can go wrong during the defragmentation.

[http://tldp.org/LDP/sag/html/filesystems.html](http://tldp.org/LDP/sag/html/filesystems.html)

---

### Post by Rinzwind on 2009-01-31
> **em4r1z said:**
> I guess you confuse journaling with fragmentation. Read about it and you'll see. They're different advantages of modern file systems.
The fact that Vista schedules a defragmentation every week (I didn't know it did for I've never used it) only means that its file system is more prone to fragmentation than the ones currently used in Linux. It doesn't mean that the Linux file systems don't fragment. They do and they give you various options to deal with it, depending on the file system you use.

No I don't confuse them.
Read my 1st lengthy post and you shall see I said:
Linux uses a journaling system so defragging is not an issue: windows (the Windows '95/XP/Vista' branche) needed defragging to speed up your system. That's not an issue with a journaling system.

---

### Post by heindsight on 2009-01-31
Filesystem journaling does not prevent fragmentation. The purpose of journaling is to enable a fast recovery if the filesystem was not unmounted properly. 

ext2 and ext3 do get fragmented (in fact if you do an fsck on an ext3 or ext2 filesystem you'll get some output at the end indicating the degree of fragmentation on the filesystem). These filesystems are however designed to keep fragmentation to a minimum - after about 3 years of use the ext2 filesystems on my previous computer were all less than 5% fragmented.

---

