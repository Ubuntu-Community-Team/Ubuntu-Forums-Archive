---
title: "Syncronize between Ubuntu and WinXP"
date: 2006-08-27
forum: Desktop Environments
---

### Post by racsw on 2006-08-27
Hello,
  I spend most of my time for our business on Ubuntu 6.06, but I have dual HD's with WinXP installed on the other.
  I need a way to synchronize files in certain directories in Ubuntu and WinXP so that they both contain the latest versions of each filename and also contain copies of any new files created, anotherwords, a mirror image.
  For instance, in both Ubuntu and WinXP, I have a directory called Acrobat, where we keep all our pdf files for the business.  Sometimes I create or update in WinXp, sometimes in Ubuntu, but I need these to be syncronized.
  The other related problem is although my Desktop in Ubuntu shows my other HD as sba1, and I can read and grab files, I cannot install any files in WinXP from Ubuntu, it keeps saying I don't have Permissions.  I even do it as root, and I get the same message, so I don't know what wrong here.

Can someone help me fix this permissions issue, and let me know if there's a way to syncronize files across these two HD's and OS's?

Thanks,
Robert

---

### Post by lagagnon on 2006-08-27
The easiest and safest way that I know of (there are probably other ways) is top have a distinct seperate VFAT partition that would be easily seen between the two OS's and just place files that need to be syncronized and shared into that partition. A VFAT parttion will show up in Windows without any effort and will be picked up as an icon in Ubuntu on your desktop. 

You may need to use qtparted from a LiveCD to do the partitoning using free space on your hard drive.

---

### Post by dentaku65 on 2006-08-27
> **racsw said:**
> Hello,
  I spend most of my time for our business on Ubuntu 6.06, but I have dual HD's with WinXP installed on the other.
  I need a way to synchronize files in certain directories in Ubuntu and WinXP so that they both contain the latest versions of each filename and also contain copies of any new files created, anotherwords, a mirror image.
  For instance, in both Ubuntu and WinXP, I have a directory called Acrobat, where we keep all our pdf files for the business.  Sometimes I create or update in WinXp, sometimes in Ubuntu, but I need these to be syncronized.
  The other related problem is although my Desktop in Ubuntu shows my other HD as sba1, and I can read and grab files, I cannot install any files in WinXP from Ubuntu, it keeps saying I don't have Permissions.  I even do it as root, and I get the same message, so I don't know what wrong here.

Can someone help me fix this permissions issue, and let me know if there's a way to syncronize files across these two HD's and OS's?

Thanks,
Robert

Hi there is a guide how to implement ntfs partition read/write for Ubuntu, but the post is in italian:
[http://forum.ubuntu-it.org/index.php?topic=29537.0](http://forum.ubuntu-it.org/index.php?topic=29537.0)
sorry!

---

### Post by racsw on 2006-08-27
I was thinking of a different route, that of a script of some sort that would cycle down through the two different directories, compare file timestamps, and transfer the files appropriately.

In order to achieve this, however, I have to figure out why I can't send a file to my sda1 HD.

Regards,
Robert

---

### Post by dentaku65 on 2006-08-27
> **racsw said:**
> I was thinking of a different route, that of a script of some sort that would cycle down through the two different directories, compare file timestamps, and transfer the files appropriately.

In order to achieve this, however, I have to figure out why I can't send a file to my sda1 HD.

Regards,
Robert

The why is that Ubuntu cannot write to an ntfs patition (as is supposed to be your sda1 WinXP); must be configure the system to do so. Then you can even write a script (Ubuntu side) that doing the tranfers.

---

### Post by givré on 2006-08-27
Your solution is probably there : [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by racsw on 2006-08-27
Ah, so that's it...

Well, I don't read Italian, so maybe there's another doc somewhere so explains how to do this.  Until I find one, I'll have to copy that entire directory to my flashdisk, and load it into another directory on my Ubuntu system, then run the script.

Thank you for your help,
Robert

---

### Post by givré on 2006-08-27
I sometime think that i am the invisible man :cool: 
the traduction you search (which is not a traduction, but a up to date HowTo) :
> Your solution is probably there : [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by cjraven on 2006-08-28
You might want to give some thought to reformatting the shared partition/disc as ext3. There's an excellent driver for XP to read and write to ext3 filesystems, and of course, in Linux it's a native filesystem.

You can find the driver here: [http://www.fs-driver.org/]("http://www.fs-driver.org/"). I've installed it and damn near "torture tested" the partition it was installed to. Thus far it's been rock solid stable (3 weeks of constant read/writes, moving huge files over, and thousands of small files). I can report that as of this morning, there are absolutely no issues to report.

I would recommend this approach over FAT32 (vfat) for a few distinct reasons:
1) FAT32 fragments like hell. It's terrible in that regard.
2) Security in FAT32 is as close to non-existent as you're gonna get
3) FAT32 will not support large files over 2GB. Plant an image file of either your Windows or Linux install on there (usually 4GB+) and you're in trouble...same applies to large db's and other entities of comparable size.

**BUT**
Before you convert your partition/drive - please PLEASE - back up and move **ALL** the data off there, then format (using partition magic or some such utility) to ext2/3. No kidding...seriously...you *do* really need to do this. You cannot "format in place" as - for example - you could with a FAT32 -> NTFS conversion (which can be done from the command line in XP/2K) and generally doesn't hose data. This operation _will_ hose your data.

The difference between the two BTW is that ext3 is a journalled filesystem - and thus a better choice.

Good luck & HTH
-Colin

---

### Post by funchords on 2006-08-28
Robert,

I think you're being a geek. :-)  Spare yourself the heartache of dealing with syncing directories, trying to figure out what to do if both copies have been updated, or if one side was deleted and the other wasn't.

Install the NTFS rw support in Linux, and the ext2/3 support in Linux and just use one directory.  Or install a small vfat partition as suggested.

--Robb (who has been there and done that)

---

### Post by andb on 2006-08-28
Simply put, the most effective solution is to have a seperate partion, shared by both OSes to store data. By having ONE copy, you know you are always working with the newest version.

Long term, cjraven's advice will be the easiest and most reliable. Both VFAT and NTFS are very wasteful. Fragmaentation on vfat, filesystem overhead on NTFS. EXT2/3 will give you a fragmentation resistant partition with low filesystem overhead, plus you know that all the great linux disk utilities will be compatible with it. NTFS is still proprietary, hence the issues with supporting it. EXT is opensource, hence the great drivers for it available in WinXP.

---

### Post by racsw on 2006-08-28
Thanks, guys for all your help :D 

Robert

---

### Post by racsw on 2006-08-28
I found a much simpler solution.
I did not want to screw around with partitions, as it seemed like overkill for such a small problem, and at too great a risk.

I accessed my sda1 (WinXP) directory from Ubuntu, copied the two directories to be synced with two directories in Ubuntu to the Documents section.
No problem.

Then I did an apt-get and installed Unison with the GTK GUI frontend.
I executed the program, and a couple of mouse clicks later, both sets of directories contained the latest files and most recent revisions.

I simply copied the synced directories to my USB flashdisk, rebooted, and copied them over into WinXP.  Easy, easy, and no partitioning involved.

That Unison is a great program, I love it. :D 

Regards,
Robert

---

### Post by funchords on 2006-08-28
Unison ... That's a new one on me -- thanks for the tip!  I'll try it out!

---

### Post by mssever on 2006-08-28
> **racsw said:**
> I found a much simpler solution.
I did not want to screw around with partitions, as it seemed like overkill for such a small problem, and at too great a risk.

I accessed my sda1 (WinXP) directory from Ubuntu, copied the two directories to be synced with two directories in Ubuntu to the Documents section.
No problem.

Then I did an apt-get and installed Unison with the GTK GUI frontend.
I executed the program, and a couple of mouse clicks later, both sets of directories contained the latest files and most recent revisions.

I simply copied the synced directories to my USB flashdisk, rebooted, and copied them over into WinXP.  Easy, easy, and no partitioning involved.

That Unison is a great program, I love it. :D 

Regards,
Robert
Unison sounds cool, but if you follow cjraven's suggestion, you don't have to reformat any partitions (assuming that one of your current Ubuntu partitons is ext2/3). This is what I do--although it's been quite a while now since I've booted Windows...

---

