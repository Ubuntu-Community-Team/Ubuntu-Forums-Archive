---
title: "XFS destroys files"
date: 2008-12-30
forum: General Help
---

### Post by Grumbel on 2008-12-30
Since my graphic card driver (Nvidia 7600 LE) is currently a bit buggy I get regular crashes with OpenGL applications, mostly when exiting OpenGL applications. These crashes themselves are a little annoying, but not really a big problem by themselves, due to them happening only on existing an application not while using them.

What however is a big problem is XFS, on almost every crash I lose files (they end up with a 0 byte size), everything from the whole Gconf tree, Gnome configuration to Wine registry files has been eaten by XFS. After browsing a bit around I found out that disabling write cache was supposed to fix this, but it doesn't. I disabled it via /etc/hdparm.conf and checked that it gets properly set on reboot. But even with that XFS still is destroying files on a regular basis. 

Is there anything beside dumping XFS and replacing it with something better that I can do to fix this?

Are there possible other causes for this behavior? 

I am using a Seagate ST3500320AS, my filesystems are on a LVM volume and I am running a vanila Ubuntu 8.10.

---

### Post by scorp123 on 2008-12-30
> **Grumbel said:**
>  What however is a big problem is XFS, on almost every crash I lose files (they end up with a 0 byte size) Yes, this is unfortunately a "known feature" of XFS. The problem here is that XFS default **"maximum write-cache time"** is **30 seconds**, whereas on e.g.** Ext3** it's **5 seconds**. So if you have a crash during those 30 seconds that XFS has not yet written its files from the cache onto the disk you will get those corrupted files with zero bytes length.

Why is XFS designed like that?

You have to bear in mind where XFS is coming from ... From SGI and their graphics workstations and super-computers which used IRIX (SGI's own UNIX variation) as operating system. Those machines were supposed to run 24 hours per day and to be constantly under extremely high load, rendering movies and special effects and generating gigabytes and gigabytes of graphical data ...

That's where XFS inherited its default behaviour from, because under above scenario it made a lot of sense to keep data so long in the cache and avoid slowing down the system by constantly causing I/O traffic to the disks.

Long talk short ... I'd suggest to play with the XFS mount options. They are explained in the manual page:
```
man 8 mount
``` ... scroll down until you find **"Mount options for xfs ..."**

Another place to find answers is the Linux kernel itself: there is a file in the "Documentation" sub-folder which explains a few things. If you have the kernel sources installed (e.g. "apt-get install build-essential") you'd find the file on your own system - if you don't, well here is an online copy of the file:
[http://www.mjmwired.net/kernel/Documentation/filesystems/xfs.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/xfs.txt)

It too explains the XFS mount options. I suggest you take a close look at the options.

SGI also has a FAQ where they discuss the problem - take a look here:
[http://www.xfs.org/index.php/XFS_FAQ#Q:_How_can_I_address_the_problem_with_the_write_cache.3F](http://www.xfs.org/index.php/XFS_FAQ#Q:_How_can_I_address_the_problem_with_the_write_cache.3F)

---

### Post by Grumbel on 2008-12-30
> **scorp123 said:**
> So if you have a crash during those 30 seconds that XFS has not yet written its files from the cache onto the disk you will get those corrupted files with zero bytes length.
Thats the thing I don't get. I could totally accept new files not getting written to disk, but what good is *destroying* old files that are already on the disk? What's the point of a journaling filesystem when you have to restore from backup after each crash or even worse when you end up with a machine that is no longer bootable because critical files have disappeared?

As far as I understand the XFS FAQ and other docu on this, this all is an artifact from a harddisk write cache, not intended behavior, yet even so I already disabled the write cache it still happens on basically every single crash, disabling the write cache had absolutely no notifiable effect. 

Which leaves me with only two possible answers, either XFS is really that broken and completly unusable on any real world machine, which would made me wonder how that ever ended up in the stable kernel, or my harddisk is somehow lying about the write cache and its still active even so hdparm says its off. Or there is something else that I am completly missing.

None of the XFS mount options seem to address my problem.

---

### Post by dcstar on 2008-12-31
> **Grumbel said:**
> 
.......
Which leaves me with only two possible answers, either XFS is really that broken and completly unusable on any real world machine, which would made me wonder how that ever ended up in the stable kernel, or my harddisk is somehow lying about the write cache and its still active even so hdparm says its off. Or there is something else that I am completly missing.


No filesystem is designed to work when a system crashes and all sorts of random events can occur, they are designed to minimise data loss when a power outage occurs and the whole system stops - not bumbles along as some faulty hardware/software corrupts the way the O/S is trying to function.

Some work better than others, which is why EXT3 is used as the default filesystem in Ubuntu.

---

### Post by scorp123 on 2008-12-31
> **Grumbel said:**
> Thats the thing I don't get. I could totally accept new files not getting written to disk, but what good is *destroying* old files that are already on the disk? If I had to guess I'd say you had a program open that was accessing and possibly modifying those files. Voila!

> **Grumbel said:**
>  What's the point of a journaling filesystem when you have to restore from backup after each crash Truth be told I haven't had the "zero bytes" problem in ages. But then again my machines hardly ever crash.

> **Grumbel said:**
>  or even worse when you end up with a machine that is no longer bootable because critical files have disappeared?  I keep /boot as Ext3 ... ;)

> **Grumbel said:**
>  which leaves me with only two possible answers, either XFS is really that broken and completly unusable on any real world machine Can't agree to that. I use XFS on my servers, and there it performs tip top.

Maybe you'd give IBM's JFS a try? JFS is the default filesystem on IBM's AIX (that's IBM's commercial UNIX distro) and it is widely used there. Performance-wise it's identical to XFS as far as I can tell. I am not sure though how JFS reacts to crashes. You might want to google that.

> **Grumbel said:**
>  which would made me wonder how that ever ended up in the stable kernel Well, XFS is stable. It's sad that it does not seem to work for you, but you can't assume that just because it does strange things in your case that it does strange things to everyone.

---

### Post by adamlau on 2008-12-31
Exactly why I only use XFS under my storage partition (music, videos) and nothing more. That said, XFS takes up 90% of my filesystem space and so to be safe, I run sync after performing major file operations within XFS.

---

### Post by scorp123 on 2008-12-31
> **adamlau said:**
> I run sync after performing major file operations within XFS. One of my paranoid friends has a cron job that performs "sync" every few seconds ... 8-[  

A bit of an overkill IMHO and not really helpful for the performance #-o ... but it works for him and he's happy. 

But then again I'd rather use Ext2 (not having a journal at all can make sense too under certain scenarios) or Ext3 in such a case.

---

### Post by Grumbel on 2008-12-31
> **scorp123 said:**
> Well, XFS is stable. It's sad that it does not seem to work for you, but you can't assume that just because it does strange things in your case that it does strange things to everyone.
I consider a filesystem that does strange things to be broken. A crash is not something that should destroy files. I used reiserfs for a long long while and while that did destroy files  in the very very early version (back then before Ubuntu even existed), that got fixed and it hasn't destroyed a single file in half a decade after that. XFS on the other side destroys files on basically every single crash and I had problems with it on the very first day of usage, it just took me a while to realize that XFS was killing my files, not some fluke in a Gnome app.

Just for the record, files I lost:

~/.gtk-bookmarks
~/.recently-used.xbel
~/.gconf/%gconf-tree.xml
~/.wine/user.reg
~/.wine/userdef.reg
~/.wine/system.reg
~/.gnome2/rhythmbox/rhythmdb.xml

Anyway, whatever, now going to try ext3 and then maybe ext4 whenever Ubuntu offers 2.6.28.

---

### Post by scorp123 on 2008-12-31
> **Grumbel said:**
> A crash is not something that should destroy files.  Au contraire! A crash may very well destroy or corrupt files.

> **Grumbel said:**
>  I used reiserfs ...   I once lost 500 GB of data thanks to ReiserFS ... since then it's "taboo" on my machines. :)

> **Grumbel said:**
>  XFS on the other side destroys files on basically every single crash   And what if you tried to improve your system's stability? Because if it's crashing all the time then I'd say you have a few more important issues to worry about ...

> **Grumbel said:**
>  Anyway, whatever, now going to try ext3  Ext3 might serve you better in your case. Did you ever give JFS a try?

---

### Post by Grumbel on 2008-12-31
> **scorp123 said:**
> And what if you tried to improve your system's stability?
My system is rock solid, it only crashes sometimes in a single well defined case: exiting an OpenGL application, annoying, but really no big deal and there is nothing I can do about that anyway, other then buying a new graphics card or hoping that a new driver might fix it one day.

> Did you ever give JFS a try?
Nope, I think I had enough experiment with filesystems for the moment, going back to mainstream Ext3.

Still fail to see the point of a filesystem where you have to recover from backup after every crash.

---

### Post by scorp123 on 2008-12-31
> **Grumbel said:**
>  Still fail to see the point of a filesystem where you have to recover from backup after every crash. But at least you have backups ;)

---

### Post by MisterFlibble84 on 2008-12-31
> **dcstar said:**
> No filesystem is designed to work when a system crashes and all sorts of random events can occur, they are designed to minimise data loss when a power outage occurs and the whole system stops - not bumbles along as some faulty hardware/software corrupts the way the O/S is trying to function.

Some work better than others, which is why EXT3 is used as the default filesystem in Ubuntu.

Yes, but since ext3 has a much more extensive journal (XFS is writeback only), it also loses performance and uses up disk space.

No matter what file system you use, there are pro's and con's, I use XFS.

I would probably switch to Ext4 in Jaunty but I have so many hundreds of gigs of files to back up and restore, I may just stick with XFS. (uggghhhhhh)

---

