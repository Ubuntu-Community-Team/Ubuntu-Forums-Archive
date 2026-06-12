---
title: "Newbie: Partition help..."
date: 2009-01-02
forum: General Help
---

### Post by Hikertrash on 2009-01-02
Hi,

New to Ubuntu and have a couple questions about partitioning.  I've used PartedMagic in the past, once, but could use a refresher.  I've attached a screenshot of what my HDD looks like now.  I just upgraded to a bigger HDD using Seagate DiscWizard and I'm not sure why I allowed so much for XP since I have a separate D: for Data (which is also the default partition for My Documents.  Since I have lots of room.  I guess it doesn't matter. 

I'm willing to allow 25GB or so for Ubuntu.  I've been told it's best to set up a /,  /swap, and /home partition, in that order.  For simplicity sake, I have a feeling it's best to create the Ubuntu partitons from the end of the D: drive.  Of particular concern is it OK to add these to the extended partition. shrinking it first of course?  Will I lose data?  D: contains all my music and photos (it is backed up)

Among other things, I could use suggestions as to what size these partitions should be.

Also, at a later time, I'd like to use my Media Direct button as the power button to boot into Ubuntu, saving the normal power button for XP.  I'll be using this thread here as reference.

[http://ubuntuforums.org/showpost.php?p=3113451&postcount=8](http://ubuntuforums.org/showpost.php?p=3113451&postcount=8)  (Mew has agreed to help there in a few days)

My concern with that is will it matter where the Ubuntu boot loader is on my drive?  


Of course, I'm open to all suggestions and thankful for your time.

---

### Post by Alterax on 2009-01-02
Partitioning's fun.  Unless you're unaccustomed to it.  No biggie though.

1.  Calculating partition sizes:

  Swap space is the easiest.  Do roughly 1-1 1/2 times your system RAM.  It doesn't really require a lot; if you actually do require more swap space than that, then your system performance will not be as good because disk access is much slower than RAM (look up "Disk Thrash").  I'll get into the rest here in a moment.


2.  A /home of its own:

  Next, I really don't see an overwhelming need to separate / from /home, not for a typical desktop installation.  In fact, unless I'm spanning multiple drives OR building huge databases, I usually don't separate them.
However, if you'd still like to split them, I recommend splitting 15 GB off for the / partition and the remainder (after allocating swap space) to the /home directory.

3.  Rustling up the GRUB:
Finally, by default Ubuntu uses GRUB, the Grand Unified Boot Loader.  Grub has the advantage of being able to put it outside the MBR.  Since you're dual booting, let it put it where it wants to, although I've had no issues in putting in anywhere on the disk.

Le

> **Hikertrash said:**
> Hi,

New to Ubuntu and have a couple questions about partitioning.  I've used PartedMagic in the past, once, but could use a refresher.  I've attached a screenshot of what my HDD looks like now.  I just upgraded to a bigger HDD using Seagate DiscWizard and I'm not sure why I allowed so much for XP since I have a separate D: for Data (which is also the default partition for My Documents.  Since I have lots of room.  I guess it doesn't matter. 

I'm willing to allow 25GB or so for Ubuntu.  I've been told it's best to set up a /,  /swap, and /home partition, in that order.  For simplicity sake, I have a feeling it's best to create the Ubuntu partitons from the end of the D: drive.  Of particular concern is it OK to add these to the extended partition. shrinking it first of course?  Will I lose data?  D: contains all my music and photos (it is backed up)

Among other things, I could use suggestions as to what size these partitions should be.

Also, at a later time, I'd like to use my Media Direct button as the power button to boot into Ubuntu, saving the normal power button for XP.  I'll be using this thread here as reference.

[http://ubuntuforums.org/showpost.php?p=3113451&postcount=8](http://ubuntuforums.org/showpost.php?p=3113451&postcount=8)  (Mew has agreed to help there in a few days)

My concern with that is will it matter where the Ubuntu boot loader is on my drive?  


Of course, I'm open to all suggestions and thankful for your time.

---

### Post by Hikertrash on 2009-01-03
The explanation for the separate /home partition was if you need to reinstall Ubuntu or upgrade the distro, I could just install into the / partition and can leave your personal files undisturbed.

He also suggested the order /, /swap, /home although I've seen it in different orders

---

