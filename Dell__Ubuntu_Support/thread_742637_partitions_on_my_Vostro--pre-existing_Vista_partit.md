---
title: "partitions on my Vostro--pre-existing Vista partitions and allocating new"
date: 2008-04-01
forum: Dell  Ubuntu Support
---

### Post by elfchick on 2008-04-01
Im about to add linux to my new Vostro 1700.  I'd actually be happiest with linux only (my old computer was) but I'm also paranoid about making sure that it *works*.  I also was not the primary administrator for my old computer, so I'm not entirely a newbie, but not anything approaching expert.  So I will keep Vista for now, at least.

I went to get started today and got hung up before I could accomplish anything.  I have four partitions, and I don't know why.  I've looked at other threads regarding partitioning, and just want to see if anyone can reassure me before I get started.  I have:
* 78 MB partition with no label and appears to be 100% free
* 2.5 GB partition with no label, also appears to be 100% free
* Vista partition (C), 
* Recovery partition (D)

So I see that other threads mention Dell utilities in their own partition, so I thought that might be the 78 MB partition, but Vista's disk management also says it's empty.  

QUESTION: Why do I seem to have two small empty partitions?  If they're empty, does it matter if I get rid of them?  

I saw the discussions of Dell Media Direct and its hidden partition, but I am guessing that I won't be able to see that with Windows disk management, so it's probably not one of these.  I did find a program that apparently ought to be able to remove the HPA: [http://www.hdat2.com/](http://www.hdat2.com/) (SET MAX ADDRESS).   Those discussions were very informative and I really appreciate them. 

gtspaulding's post was fantastic, where he said:
> The (undocumented) fix for the self-destruct button is found in a program called RMBR found on the Media Direct Reinstall CD. It's best run in a DOS environment (boot up from the MD CD and then quit).

Syntax: RMBR DELL [partition to use for power button] [partition to use for Media Direct button]

Ah...

QUESTION: how do I get Vista disk management to tell me partition numbers?  They're listed in different orders above and below.  

I want to be able to access almost all my files from both Vista and linux.    I've never had a dual boot machine before--I don't play games, just browse web, edit images, work on docs, etc.  I'll likely be using the same programs no matter which OS I'm using (OpenOff, GIMP, Scribus, Firefox/Thunderbird), but I'm happier in the linux environment.

QUESTION: Is there any reason not to make a large FAT32 partition for photos/images (a large part of my work), videos, OpenOffice files, etc?

Thanks so much.

---

### Post by cousinavi on 2008-04-04
Hi elfchick,

Answers to questions:
I wouldn't remove any small partitions, the ~100 MB one is probably the dell utility drive, and I would never remove that.
 
When I installed Ubuntu on my Vostro I used the partitioning tool on the 'Gusty' Live CD. Using it will require some research before you start.

Storing your data on a FAT32 partition is certainly an option, it all depends on what you need to do and how often you need to do it.
<---->

Here is a quick walkthrough on how to use the "custom" partioning tool in 'Gusty'. It has advantage that you can see all your drives, partitions with numbers. You may also shrink your vista partition as small as you like (I heard some people having problems with vista only letting them shrink the partition to 50% the size of the drive)

It has the disadvantage that you will need to learn what partitions Linux needs, and what size they should be etc.

To use the tool you need to boot off the Ubuntu Live CD and start the installation program by double clicking the icon on the desktop. When it comes to partitioning the drive choose the "custom" option.

You will now see a screen with all your hard drives and what partitions are on them. You can now shrink your Vista partition (which will probably the largest one) to any size you feel fit (I shrunk mine to 20GB). Depending on how much software you plan to install on your Windows, I would just add 5-10 GB onto the "used" amount of the drive and make that the size for your Vista partition.

You will now have lots of unpartitioned space on your drive. A basic setup will require 3-4 partitions:[LIST]
[*]Mount point: "/"
partition type: ext3
size: 4-6GB
notes: Root partition - system files and programs go here
[*]"swap" 
partition type: swap  
size: Double your RAM
notes: Virtual memory
[*]Mount point: "/home"
partition type: ext3 
size: A few GB??? Depends what it will be used for. (Mine is the rest of my drive, 150 GB, but I don't care that I can't access this partition from Windows)
notes: This is where a Linux user would put their pictures and movies, it is also used for various configuration files needed for your user account, but the problem is on your dual boot machine it is not possible for windows to read this partition.
_Therefore the data you wish to share between Windows and Linux needs to be stored on a Windows friendly partition_
[*] (My memory fails me to what the partition should be called - I *think* /media/sd{partition number}, there will probably be a default, stick to that)
partition type: FAT
size: This maybe your largest partition depending on how much data you need both windows and Linux to see. I am assuming this is your music, movies, work, etc.
notes: 
[/LIST]
**Important - Do your research! Make sure you know what a "mount point" is. Knowing what tasks you will be doing and how much data you will want to be accessible from both OSs will determine the size of your partitions.**

Another important factor is how much you are going to use each OS. If you are going to use Windows once in a blue moon then maybe the best plan would be to use a piece of third party software to read your /home volume from windows. The one I have used i the past is [http://www.fs-driver.org/]("http://www.fs-driver.org/"). I don't know if it works with Vista, and note that it reads ext2 partitions not ext3 (forgotten what the extra functionality ext3 provides), but there maybe other software out there that can help you.

If you are going to be using Windows most of the time then maybe the best solution is to keep your data on the windows partition which can then be mounted in Linux 

In the end there is no "right" choice it comes down to personal preference. Hope this ramble is helpful,

**-Avi**

---

### Post by DellCA on 2008-04-04
> **elfchick said:**
> I went to get started today and got hung up before I could accomplish anything.  I have four partitions, and I don't know why.  I've looked at other threads regarding partitioning, and just want to see if anyone can reassure me before I get started.  I have:
* 78 MB partition with no label and appears to be 100% free
* 2.5 GB partition with no label, also appears to be 100% free
* Vista partition (C), 
* Recovery partition (D)

The partitions, assuming they are the defaults installed by the factory at Dell are:

* Onboard Diagnostics (aka Utilities)
* Media Direct
* Vista
* Image Restore (recovery)

They may be listed as free space, but they will have data in them.  If you want to remove them you can.  The only real drawback to doing so is that the diagnostics partition isn't easy to put back.  The Media Direct partition can be recreated with a small bit of effort (see [the instructions](http://support.ap.dell.com/support/topics/topic.aspx/ap/shared/support/dsn/en/document?c=hk&l=en&s=gen&dn=1093823) on the Dell website -- they are for Media Direct 2 on XP, but the steps are virtually identical for Media Direct 3 with Vista).

As for the partition numbers, I would personally use fdisk under linux (or whichever partitioning utility you prefer).  As long as you are careful you can do this without breaking anything.  For fdisk, just open a terminal of your choice, run 'fdisk /dev/sda' (or whatever the drive is) and then press P to print out the partition table (and Q to quit without saving changes).

If you have any other questions about this I'll be happy to help.

Larry
Dell Customer Advcocate

---

