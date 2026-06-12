---
title: "ext4 support on Windows XP"
date: 2009-06-08
forum: General Help
---

### Post by munishvit on 2009-06-08
Hi, ):P
I have installed Windows XP as an alternate Operating System. I use to keep all my Important data on partitions formatted with ext4/ext3. I want to access those drives within Windows XP too, preferably in Read-Only mode. What is the best tool which can be installed in XP for this and from where to get it?

Thanks in advance.

---

### Post by Bucky Ball on 2009-06-08
I would be interested to know. To my knowledge, Windows understands neither and I don't know of any software that can make this happen.

---

### Post by Sef on 2009-06-08
I know there is a way to get Windows to access ext2 and by extention ext3, but not sure if it will work with ext4.

---

### Post by anaconda on 2009-06-08
You need to install ext3 driver for your windows. Here is the link.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Ps. I THINK that this will also work for ext4 because it is downward compatible with ext3.. But haven't tried it myself.

But this definetely works for ext2 and ext3, I used this when I still used windows...

---

### Post by Idefix82 on 2009-06-08
For ext3 I am using this: [http://www.fs-driver.org/]("http://www.fs-driver.org/")

It works very well. You can see your ext3 drives in all the windows apps, so the integration is transparent for the user. However, the driver is actually written for ext2 and doesn't support journaling.

I would strongly recommend only ever mounting partitions as read-only, which you can tell the driver to always do by default.

I don't know if this works for ext4.

---

### Post by Bucky Ball on 2009-06-08
I stand (sit comfortably) corrected. :)

---

### Post by sedawk on 2009-06-08
Warning!

The driver is limited to file system where the inode size is 128.
Newer versions of Ubuntu might use inode size of 256 when
formatting file systems (during installation process), so
check what inode size you use !

---

### Post by munishvit on 2009-06-08
Friends I tried [http://www.fs-driver.org/](http://www.fs-driver.org/), but this driver is not supporting ext4. After installation and assigning drive letters to the drive, I get the following error :(
[IMG]http://ubuntuforums.org/picture.php?albumid=1059&pictureid=4216[/IMG]

---

### Post by Dilligaf on 2009-06-08
This driver works on 256 bytr inodes:
[]("http://ext2.yeah.net")[http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)
it shows directorys in ext4 but not files, works good in ext3.

Mike

---

### Post by zika on 2009-06-08
> **munishvit said:**
> friends i tried [http://www.fs-driver.org/](http://www.fs-driver.org/), but this driver is not supporting ext4. After installation and assigning drive letters to the drive, i get the following error :(
[img]http://ubuntuforums.org/picture.php?albumid=1059&pictureid=4216[/img]
+1

---

### Post by munishvit on 2009-06-09
So.. nothing can help me on ext4??

---

### Post by GrfyGrumpyBear on 2009-06-26
If you have 'extents' enabled on ext4, this breaks ext3 backwards compatibility and means that ext3 Windows drivers (or at the very least, the EXT2 Windows driver found at [http://www.fs-driver.org/]("http://www.fs-driver.org/")) won't work until 'real' ext4 support is added.

The worst part is that as far as I know, no Windows ext4 driver exists yet.... if anyone could find one, it would be very nice to mention it here.

---

### Post by munishvit on 2009-06-27
> **GrfyGrumpyBear said:**
> If you have 'extents' enabled on ext4, this breaks ext3 backwards compatibility and means that ext3 Windows drivers (or at the very least, the EXT2 Windows driver found at [http://www.fs-driver.org/]("http://www.fs-driver.org/")) won't work until 'real' ext4 support is added.

The worst part is that as far as I know, no Windows ext4 driver exists yet.... if anyone could find one, it would be very nice to mention it here.

Thanks for the reply dude :P. For Windows, now I have started using VirtualBox (was not aware this package before #-o). I found it much more convenient than otherwise separate installation. Even ext4 partitions can be easily shared with Windows...

---

### Post by GrfyGrumpyBear on 2009-06-27
Hey, it's no problem. It's just annoying for me when it comes to dual-booting, you know? All my stuff is on my EXT4 partitions. So when I want to rock out to some music I have to reboot and wait about 20 seconds for Ubuntu to come up and be ready to use.

On second thought, it's not all that bad....

---

### Post by Ubuntist on 2009-06-28
About the alternative driver mentioned by Dilligaf, has anyone tried [Ext2fsd]("http://ext2fsd.sourceforge.net/")?

BTW, what is an I-node, and why would I care that Ext2fsd supports longer ones than does Ext-fs?

---

### Post by jerome1232 on 2009-06-28
If memory serves Inodes are where directory and file information is stored.

Longer inodes means more possible directories, and more possible files per directory.

That and a couple releases ago Ubuntu began giving a default of 256 byte (or are they bit?) inodes, some drivers ONLY worked with 128 and couldn't work with filesystems that were using the larger inodes.

---

### Post by Ubuntist on 2009-07-03
Thanks for the explanation. After reading the above posts, I decided to install [ext-fs]("http://www.fs-driver.org/") but couldn't get it to work.  Running the mountdiag.exe diagnostics program (in a terminal window) that can be downloaded from the same site, I found out that, lo and behold, the very I-node issue that I asked about was causing the problem: my ext3 partition was using 256-byte I-nodes. The recommended solution, re-formatting to 128-byte I-nodes looked painful so I decided to go for the less-well-known ext3 driver, [Ext2fsd]("http://ext2fsd.sourceforge.net/"). FWIW, after a week, I've had no problems with it, although I didn't manage to designate my ext3 drive as **L:** instead of the default **D:**. I also I can't say that I often boot to Windows XP.

---

### Post by ajoliveira on 2009-07-28
Hello

I just installed Ext2Fsd 0.48 on XP, tried it on a ext4 partition, extents enabled, and so far it works :P. Used the registry mount method.

---

### Post by Zorael on 2009-07-28
At least on my Acer laptop, installing that ext2fs driver makes XP bluescreen when I try to mount truecrypt images. I've seen a blog where it happened to at least another guy, so chances are they're simply incompatible.

edit: Minor googling turns up;
[http://linuxnewb.wordpress.com/2008/10/03/getting-a-bluescreen-with-truecrypt/](http://linuxnewb.wordpress.com/2008/10/03/getting-a-bluescreen-with-truecrypt/)
[http://www.edugeek.net/forums/windows/25377-mount-ext2-3-windows-truecrypt-installed.html](http://www.edugeek.net/forums/windows/25377-mount-ext2-3-windows-truecrypt-installed.html)
[http://www.softblog.com/2008-02/the-hunt-for-blue-screen/](http://www.softblog.com/2008-02/the-hunt-for-blue-screen/)
[http://xlshadow.livejournal.com/78729.html](http://xlshadow.livejournal.com/78729.html)
[http://www.wilderssecurity.com/showthread.php?t=209269](http://www.wilderssecurity.com/showthread.php?t=209269)


The [Ext2 IFS changelog](http://www.fs-driver.org/extendeddl.html) suggests it's fixed now though.
> [list][*]Bug fixed that caused a blue screen when the Ext2 IFS 1.11 software was used together with the Truecrypt disk encryption software.[/list]

---

### Post by hessiess on 2009-07-28
Mounting Linux partitions in windows, especially XP is a bad idea as it has no concept whatsoever for folder permissions, meaning you can very easily mess up your system. If you have to mount Linux file systems in windows, make sure that they are mounted read only.

---

### Post by ajoliveira on 2009-07-28
No, I was not referring to that one, click [here]("http://sourceforge.net/projects/ext2fsd") instead...I hope it works for you too... ):P

---

### Post by johny_ on 2009-08-06
> **Dilligaf said:**
> This driver works on 256 bytr inodes:
[]("http://ext2.yeah.net")[http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)
it shows directorys in ext4 but not files, works good in ext3.

Mike

Ah... Yes, that's the pain. Jaunty support ext4 (I'm not sure if by default). I use Windows for videochatting and sometimes love to be able to access Linux partition, without switching.
Unfortunately, I'm on ext4. My partition mounts but I can access any files and I see only main directories, no subfolders or files..

Have any idea if there is a way to get around this?

P.S Ajoliveira - Did you have to to make any special setup in extfsd?

---

### Post by Bucky Ball on 2009-08-07
johny- a good reason to set up a shared partition, FAT or NTFS when dual booting.

---

### Post by johny_ on 2009-08-07
> **Bucky Ball said:**
> johny- a good reason to set up a shared partition, FAT or NTFS when dual booting.

Sorry. Can you please explain your point. I'm not getting this.
You mean I should set a shared partition?

---

### Post by Bucky Ball on 2009-08-07
Yes, one that can be read easily from both your Linux boot and your MS boot. Linux can read/write NTFS or FAT fine but Windows has no idea about EXT3 therefore ... a lot of folk create a partition that can be used by both, a 'shared' partition on the local machine that can be shared between both OSs.

I set one up on my uni laptop over a year ago but find I can do everything in Ubuntu and it is kinda redundant as I never use Windows on it anymore!

---

### Post by garikaib on 2009-08-07
Will be interested in the solution.

---

### Post by johny_ on 2009-08-07
> **Bucky Ball said:**
> Yes, one that can be read easily from both your Linux boot and your MS boot. Linux can read/write NTFS or FAT fine but Windows has no idea about EXT3 therefore ... a lot of folk create a partition that can be used by both, a 'shared' partition on the local machine that can be shared between both OSs.

I set one up on my uni laptop over a year ago but find I can do everything in Ubuntu and it is kinda redundant as I never use Windows on it anymore!

Thanks for this :).

There is a little problem though; I need to access an existing Ubuntu partition, on ext4 from Windows.
If I'm not wrong, If I create a shared one I'll have to move all the data I want to read there, right?
I can't do this, as all my HDD space is used, and, at the moment I've got no external disks to attach.

Have any idea?

---

### Post by martinbaselier on 2009-08-07
Is your partition full? If not, you can shrink it from a jaunty live cd with gparted (aka partition editor). This could give some troubles with grub though. 

Why don't you do it the other way around and just copy the file from ubuntu to the windows partition?

---

### Post by johny_ on 2009-08-07
> 
Why don't you do it the other way around and just copy the file from ubuntu to the windows partition?


Well, I can't do that. My goal was to have access to some photo archives and movies and music stored on the Ubuntu partition. The Windows one is way more smaller and so there wouldn't be enough space.

---

### Post by Bucky Ball on 2009-08-07
Yep, see if you can shrink one of the partitions using a Live CD. It must be done this way (if you are manipulating the partition Ubuntu OS is on) as the partition needs to be UNmounted to manipulate it. What partitions have you got in Ubuntu and what size (ignoring Windows for now)?

* Right click the folder you want to access from Windows (Pics?) and check Properties. Note how big it is (data size, not folder size). You will find that under heading 'Contents'.

* Go to System->Admin->Partition Editor (Gparted) and have a look at your partitions. Is there enough unused space on any of them to make a partition to fit them on (for the moment)? 

Sometimes you can change things around until it is the way you like it, but takes a few moves, a bit like planning ahead in chess if you follow me! It takes a bit of data copying and deleting, a few shrinks and grows to get it right.

(Enough room for half your pics? Shrink/Create 'Shared' Partition/Move half the Pics to New Partition/Shrink Old Partition/Grow New Partition/Move other half of Pics!)

* Could you burn them to DVD? Compress them with a backup app, burn to DVD, delete them from the partition then shrink and grow etc ... ?

Hope that makes some sense and hope it helps. Without another storage device these are the only options I can think of. :)

(Online storage/Manipulate Partitions/Download again? ... bit time consuming.)

---

### Post by johny_ on 2009-08-08
Thank you Bucky for all this useful info. I wasn't aware that Gparted had such an option.

This is how my partitions are located

> 
                      Size  Used Avail Use% Mounted on

            105G   98G  1.9G  99% /home

             28G  9.2G   19G  33% /windows


I guess shrinking it is a bit of work :) As you can see, my home is 105 Gb and Windows only 20; yahoo! hurrah! ;).
I'm going to digg for more info about [exd2fsd]("http://sourceforge.net/projects/ext2fsd/"),, the whole thing of ext3 and ext4 is interesting and I will to find out if that an usual to ex2fsd not to support ext4 either it's something regarding the partitions.

Can anyone who made it to on XP with a Jaunty ext4 partition tell me their experience please?

Of course; Shrinking is always a solution, but, for now, I'll try out something different just to play with that excellent OS as Ubuntu is:D

---

### Post by CydeSwype on 2009-10-22
Hey Guys,

There is no Ext4 support for Windows yet.  I've spoken with Stephan of fs-driver.org (the developer of the Ext2 IFS for Windows software discussed in this thread).  He is actively working on support for Ext4 but is only available to work on it in his off hours.  He has a day job.  Curious about what it would take to sponsor his full time development of the project, he said roughly 4 months of full time work (which would equate to roughly $48-72K euros).

Is anyone interested in helping with a fundraising campaign?

-Ian

---

### Post by pwrcul on 2009-11-09
I reinstalled Kubuntu netbook 9.10 after not being able to access the prior install's ext4 filesystem using Ext2Fsd.  

On installing the 2nd time I specified Manual disk partitioning and selected ext3 journaling filesystem.

Back on XP I had to do a fresh install of Ext2Fsd 0.48, but it works great.

I found the following on the features page for Ext2Fsd (note it explicitly states no support for ext4):

From [http://www.ext2fsd.com/?page_id=25](http://www.ext2fsd.com/?page_id=25)

Features Ext2Fsd supports:

   1. ext2/ext3 volume reading & writing
   2. ext3 journal replay when mounting
   3. various codepage: utf8, cp936, cp950 …
   4. mountpoint automatical assignment
   5. large inode size: 128, 256, …
   6. large file size bigger than 4G
   7. OS: 2k, xp, vista, server 2008 (i386/amd64)

Features Ext2Fsd doesn’t support:

   1. ext3 journal support
   2. htree for directory entry management
   3. ext4 extent support
   4. LVM and Linux raid (md)
   5. NT4 is no longer supported.
   6. Win7 or server 2008 r2 support are uncertain.

---

### Post by eddiedotnet on 2010-04-15
Careful there Pwrcul. What the notes say is that the 'extent' feature in ext4 is not supported. ext2fsd can access ext4 with some limitations. I think the latest test version sets the 'hidden' bit for files that have been written using the new extent feature.
One option is to disable the extent option when creating the ext4 filesystem. The extent feature optimizes large files so the performance penalty depends on the partition's use. Still better than ext3.

Here's an example of someone getting WIN7 to see ext4:
[http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)

---

### Post by Ubuntist on 2010-05-27
> **pwrcul said:**
> Features Ext2Fsd doesn’t support:

   1. ext3 journal support
   2. htree for directory entry management
   3. ext4 extent support
   4. LVM and Linux raid (md)

What's the practical impact of ExtFsd not supporting the features above?  In other words, if I'm Joe Average user, how much should I worry about these things and when might they bite me?

---

### Post by Bucky Ball on 2010-05-27
I run 8.04 LTS. Need stability and use, for the moment, EXT3. If you have the hours to tweak and learn, which I don't dissuade, load the bleeding edge 10.04 release (rather than an update) with default EXT4.

Bit like Hardy being defaulted to IPV6. Who's dumb idea was that? Maybe 2% of the population t have IPV6 capable routers. Oh, great thinking. Don't get me wrong, love Ubuntu, but last update killed the wife's ATI graphics driver and last thing you need when preparing for presentation and final essay yourself and your wife is not a problem solving nerd. 

Good luck in future endeavours. Thought I'd throw that in.
In six months 10.04 LTS might come close. I'm looking for functional, reliable, production. Not experimental. That's fine. 8.04 has been solid as a rock until that last update, which is the last thing you would expect from an LTS release that has been on the planet since April 2008 ...

---

