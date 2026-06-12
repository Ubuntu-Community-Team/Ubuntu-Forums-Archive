---
title: "Trouble with automount of NTFS USB Drive"
date: 2009-04-22
forum: General Help
---

### Post by heptagonal on 2009-04-22
Hi all ...
 
This is my first post, so please indulge the wordiness.  I'm trying to describe a nit-picky problem very precisely.
 
I'm not new to Linux, but I'm still stumped at times with Ubuntu problems.
 
I am trying to determine why a large (250GByte) portable Western Digital USB hard drive that I recently repartitioned and formatted NTFS on one of my Ubuntu machines (call it machine A) will not automount on that machine but it automounts just fine on another Ubuntu machine (call that one Machine B).:(
 
Both machines are running Hardy Heron (8.04 LTS) with all recent updates.
 
I did create a problem when I first setup the drive by specifying a mount point that contained separators (/media/wd-USB-W).  I recovered from this by googling and found someone else had encountered this same problem.  I guess when you create an external drive you're NOT supposed to specify "/media/.. etc in the mount point, nor are separators supposed to be used.  I don't remember what the fix was, but it was simple.  
 
However ... 
 
I now have to manually mount this drive on Machine A but not on Machine B.  The drive automounts just fine on Machine B.  On machine A, the automount fails with a pop-up window that reports: "The volume WDUSB uses the NTFS file system which is not supported by your system".  This message is not true because if I manually mount the drive via "sudo mount /dev/sdb1 /media/wdusb" it works just fine!  What's happening here?  NTFS is very well supported on my system!  Why am I getting this funky error message?:(
 
What I am trying to do is very simple:  I don't trust dual-boot configurations (I've been "burned" very badly in the past) so I keep all my machines separate.  I have a need to share large volumes of data between Ubuntu (where I do most of my work) and Windows (where I must deliver my work).  A large portable USB drive seemed to be the best way to accomplish this.  It's much faster than trying to share the data over a network.
 
I would have prefered to stay with a FAT-32 format drive, but Windows has issues with this format in large capacity drives.  That is the reason I am trying to use NTFS - too bad Windows doesn't know what to do with ext3 ;)
 
Can anybody explain what I might have fouled up on Machine A that causes it to refuse to automount this drive?  What is the best recovery action?  I am tempted to re-install Ubuntu from scratch on machine A, but that, I'm sure, is ugly overkill.
 
Any advice?:confused:
 
Thanks !
 
--Heptagonal

---

### Post by cariboo on 2009-04-22
Install ntfsprogs, it includes a utility that will automount your external drive. Ntfsprogs is in the repositories, and can be installed using Add/Remove Programs or Synaptic Package Manager.

---

### Post by heptagonal on 2009-04-22
Hi cariboo907,
 
Thanks very much for looking into my problem!
 
Unfortunately, I had already tried what you suggested and that did not change the symptoms at all.  Machine A has ntfsprogs installed.  Machine B, however, does not - yet it automounts the portable NTFS USB drive just fine.  I believe that with Hardy Heron, ntfs support is provided by default during installation of Ubuntu.  Is this correct?
 
I suspect that the problem I'm having arose because of the bad input I provided in the mount point specification when I first setup the drive.  Apparently, there are some issues with this in Hardy.  I am trying to rationalize what could be different between the two machines that causes one to behave properly and the other to fail.
 
I am hoping there is something minor that I have corrupted in machine A that can be easily repaired.
 
I have no other explanation for why the drive automounts just fine on machine B - including the very first time that it ever saw the drive.
 
Any further ideas?
 
Regards,
 
--heptagonal

---

### Post by yaroto98 on 2009-04-22
There are some picky mount flags in NTFS. I've had issues like this before. One thing that seems to work wonders is mount the drive in windoze, safe remove it, then it should be good to go to swap back and forth between A and B. (next time I'd go for FAT32)

---

### Post by heptagonal on 2009-04-22
Hi yaroto98,
 
Thanks for your suggestion.
 
I tried this but, unfortunately, it did not change the symptoms either.  The drive still automounts just fine on Ubuntu machine B but will not automount on Ubuntu machine A even after mounting and safely unmounting on a Windoze machine.
 
Also ... I thought that Windoze had troubles (poor performance) with large drives ( > 200 GByte) formatted as FAT32.  If this is not true, then I'll just go back and re-create the drive in this format.  I would have preferred to stay away from NTFS anyway.
 
Thanks!
 
--heptagonal

---

### Post by fballem on 2009-04-22
Does this bug describe the problem that you're having?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347034)

I'm finding a lot of posts reporting the problem.

---

### Post by heptagonal on 2009-04-24
To fballem,
 
Thanks for responding to my posting.  Unfortunately, the bug you describe is a little bit different from the one I am experiencing.  I am working with Hardy Heron, not later releases.  Also, the problem I am having is not with initial failure to automount on boot-up.  I am experiencing a consistent hard failure of automount on NTFS formatted media on ONE particular Hardy Heron machine that I am using.  It also happens to be the machine where I first set up the large capacity USB drive that is failing.  Other Hardy Heron machines that I use automount this same drive without issues.
 
Other than re-installing Hardy Heron from scratch on the one failing machine, I am looking for better alternatives.
 
Thanks!
 
--heptagonal

---

### Post by heptagonal on 2009-04-30
To All:
 
Unexpectedly, I found the root cause of my problem.  It turns out that the most recent updates to Hardy Heron seem to clobber the ability to automount NTFS formatted large drives.
 
In my previous post, I described a situation where two Hardy Heron (8.04 LTS) computers were behaving differently with respect to automounting a large portable USB hard drive formatted as NTFS.  At the time I made the post, I had no idea why this was happening.
 
This week, I finally got around to accepting, using the Update Manager, a new kernel image and other updates (kernel Image 2.6.24-23generic) on the machine that had previously been automounting NTFS just fine.  After the update, the second machine began to misbehave in the same way as the first.  Bummer! 
 
I am glad to know what the problem is, BUT I don't like the workaround!  I've now reformatted the large USB hard drive into ext3 format and I now only use it on the linux systems.  When I need to export/import Windoze data to/from the USB hard drive, I first capture it on a large USB thumb drive (formatted as FAT32) and then transfer it again (on the Linux machines) to the ext3 USB hard drive.  This is a convoluted way to do things!
 
It is unfortunate that updates are being released that introduce bugs and compromise previously operational services.  I have no love for Windoze, BUT in my place of employment it is the final destination for much of what I am paid to do.  It would be "nice" to have a big "data barrel" that I could easily roll back and forth between the Windoze and Linux worlds.   Windoze won't work well with FAT32 on large capacity drives and just about forces you to use NTFS.
 
Does anybody out there have any advice about reporting bugs back to the Ubuntu developers?  I have never done this before.  Perhaps the problem is already known and I am in the dark?
 
--Heptagonal

---

### Post by Monotoko on 2009-04-30
I saw this thread a few days back and attempted to find out what was causing your problem but couldnt find a cause, im glad you found it was a bug, and a temporary workaround.

Here is the launchpad: [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

report bugs there :)

---

