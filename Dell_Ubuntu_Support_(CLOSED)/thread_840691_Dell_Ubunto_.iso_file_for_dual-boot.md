---
title: "Dell Ubunto .iso file for dual-boot?"
date: 2008-06-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TimDaniels on 2008-06-25
I would like to use a Dell Ubuntu re-install .iso file, with all its drivers, to install Ubuntu as a dual-boot with Vista on my XPS M1330 laptop.  But I don't know if it will supply the contents of just one partition (the Linux root partition), or if it will replace the entire contents of the hard drive, wiping out Vista in the process.

  Can anyone tell just what the .iso file provides and how much it wipes out?

  Can anyone tell me if it will put Grub just in the MBR or if it gives the option to put Grub in the Linux root partition?  (I want Vista's boot manager to control the dual-boot.)

Tim Daniels

---

### Post by logos34 on 2008-06-26
wow it's big (~4 gb)...It's basically the text-mode installer...The partitioner will ask you where to install root and swap.  And yes, toward the end of the installation process it will ask you where to put grub (tell it root).

Make sure to use Vista's own disk utility to shrink it, not gparted or the partitioner on the dell ubuntu install dvd

---

### Post by TimDaniels on 2008-06-26
Thanks for the reply!


> **logos34 said:**
> ...The partitioner will ask you where to install root and swap.  And yes, toward the end of the installation process it will ask you where to put grub (tell it root).
I infer, then, that one can create the root and swap partitions oneself anywhere and of sizes that one desires, and then just tell the installer to use those pre-made partitions.  Is that right?

> 
Make sure to use Vista's own disk utility to shrink it, not gparted or the partitioner on the dell ubuntu install dvd
I'm aware of the danger of mixing Vista partitions with partitions made with pre-Vista OSes and 3rd-party utilities, and thanks for expressing the caution.

In dealing with that, I've already cloned the original Vista to an external hard drive, deleted Vista's Dell-generated partition, made a new partition with Gparted, and copied the clone back to the new partition - and it works!  So I expect that using Gparted later will not be a problem.

BTW, Gparted shrunk the Vista partition from 149GB down to 60GB with no problem.  (Vista's Disk Management could only get it down to about 100GB.)  My Casper 4.0 live CD got it down to 40GB in the cloning transfer.  I copied the clone back to the internal hard drive in that size, and it booted and ran OK (after running "bootrec /rebuildbcd" from the Vista recovery disk).  I've since adjusted the partition to 90GB and re-copied the clone to it since I'm alotting about 60GB to Linux.

I had planned to give 3GB to MediaDirect 3.5, but the extended partition that the MediaDirect re-installation disk makes for it doesn't seem to like being moved or re-sized, or the logical drive within it doesn't like sharing the extended partition with other logical drives.  So until Dell releases MediaDirect 4.0, that app and its "embedded OS" will not be a feature of my Dell laptop.

Tim Daniels

---

### Post by logos34 on 2008-06-26
> **TimDaniels said:**
> In dealing with that, I've already cloned the original Vista to an external hard drive, deleted Vista's Dell-generated partition, made a new partition with Gparted, and copied the clone back to the new partition - and it works!  So I expect that using Gparted later will not be a problem.


Glad it worked for you.  I'm actually surprised you were able to manipulate the partitions the way you did and have vista run...a lot of people have had problems unless they use vista's tools.  Maybe it's just the shrinking of a vista ntfs partition with Gparted or the ubuntu installation partitioner that causes problems.

---

### Post by TimDaniels on 2008-06-27
Vista's new partitioning scheme can be a pain if Vista (or its installer) doesn't do all of it.  If you just dump the Vista-created partitions and re-create them with Gparted, and then use Gparted or other pre-Vista partitioning utility consistently thereafter, all goes well.  It's mixing the Vista and pre-Vista partitioning schemes that causes problems.  Gparted is really handy for what I'm doing because it can run from a live CD or live USB thumb drive.  That means it doesn't have to be installed on the hard drive, and it doesn't have to take up a dedicated partition (like BootItNG does).  As for the OS within the partitions, it can be cloned and imaged and copied back and forth without any concern with the type of partition into which it's being put.  (Just remember to put its boot manager into a Primary partition that is marked "active", and for Vista, run "bootrec /rebuildbcd" from the Recovery Console in the Vista installation DVD to adjust the BCD store to its new position on the hard drive.)

Tim Daniels

---

### Post by logos34 on 2008-06-27
> **TimDaniels said:**
> Vista's new partitioning scheme can be a pain if Vista (or its installer) doesn't do all of it.  If you just dump the Vista-created partitions and re-create them with Gparted, and then use Gparted or other **pre-Vista** partitioning utility consistently thereafter, all goes well.  It's mixing the Vista and pre-Vista partitioning schemes that causes problems.  

But that doesn't explain why people with Vista-only machines have trouble partitioning and dual booting when they try to use gparted or the ubuntu installer partitioner.  Not everyone does, but a lot do.  

> As for the OS within the partitions, it can be cloned and imaged and copied back and forth without any concern with the type of partition into which it's being put.  (Just remember to put its boot manager into a Primary partition that is marked "active",

Exactly. Boot files have to be on a primary flagged 'boot' or 'active.'  (For a while I triple booted 32- + 64-bit windows + linux on one hard disk).  Apparently, though, there is a way to boot a second windows installation on a logical partition even after the primary partition with the boot files is removed, but I was never able to get it to work when I experimented with it some time back.  I would also swear I've seen a way to clone windows to a logical and have it boot without a primary (using grub to chainload), but maybe I dreamed it...

> and for Vista, run "bootrec /rebuildbcd" from the Recovery Console in the Vista installation DVD to adjust the BCD store to its new position on the hard drive.)

hmm, so that's the command

Anyways, enjoy!

---

### Post by TimDaniels on 2008-06-27
> **logos34 said:**
> But that doesn't explain why people with Vista-only machines have trouble partitioning and dual booting when they try to use gparted or the ubuntu installer partitioner.  Not everyone does, but a lot do.

The reason has to do with the greater offset that Vista uses for the data portion of its partitions.  Here are some links explaining the problem:
[http://support.microsoft.com/kb/931854](http://support.microsoft.com/kb/931854)
[http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html)

There's a fix for the Vista registry, but do you really prefer Vista's partition management over that of XP or Gparted?
[http://support.microsoft.com/kb/931760](http://support.microsoft.com/kb/931760)

BTW, about my question to you - does the Dell .iso file for restoration of Linux give you the option to specify the size and location of the partition into which it will place Ubuntu or does it make the partition and determine its size automatically?

Tim Daniels

---

### Post by logos34 on 2008-06-27
> **TimDaniels said:**
> 
BTW, about my question to you - does the Dell .iso file for restoration of Linux give you the option to specify the size and location of the partition into which it will place Ubuntu or does it make the partition and determine its size automatically?

You'll come to a screen something like this:

> [CENTER][COLOR=#cc0000][FONT=Bitstream Vera Sans Mono][!!] Partition Disks[/FONT][/COLOR]
                      [/CENTER]
                       [FONT=Bitstream Vera Sans Mono]
This installer can guide you through partitioning a disk (using different standard schemes) or, if you prefer, you can do it manually. With guided partitioning you will still have a chance later to review and customize the results.

If you choose guided partitioning for an entire disk, you will next be asked which disk should be used.
                     
                Partitioning method:
                      
                 [COLOR=black]Guided - resize SCSI1 (0,0,0), partition #1 (hda1) and use freed s[/COLOR]
                 Guided - use entire disk
                Guided - use entire disk and set up LVM
 [/FONT][FONT=Bitstream Vera Sans Mono]Guided - use entire disk and set up encrypted LVM[/FONT]
[FONT=Bitstream Vera Sans Mono]                 [COLOR=#cccccc]Manual[/COLOR]                                                           
                      [/FONT]                                                                                                                                              [FONT=Bitstream Vera Sans Mono]<Go Back>  [/FONT]'Guided' will do it automatically for you.

Select 'Manual' you will be allowed to choose the mount point/partition, size, fs type and other options for / and /swap

---

### Post by TimDaniels on 2008-06-28
> **logos34 said:**
> Select 'Manual' you will be allowed to choose the mount point/partition, size, fs type and other options for / and /swap

Too bad.  I was hoping that I could tell the installer to put Ubuntu in partitions that I had previously created for it, not partitions that I direct the installer to make at the time of installation.

Tim Daniels

---

### Post by logos34 on 2008-06-28
> **TimDaniels said:**
> Too bad.  I was hoping that I could tell the installer to put Ubuntu in partitions that I had previously created for it, not partitions that I direct the installer to make at the time of installation.

no, you misunderstand--you CAN install on a pre-existing partition.  Just point it to that partition, you don't even have to format it if you've done that already...tell it to put root there (mountpoint '/') and 'no' to 'format.'

---

### Post by TimDaniels on 2008-06-29
> **logos34 said:**
> --you CAN install on a pre-existing partition.

OK, got it.  Thanks.  That gives a lot more flexibility.  (I was about to look at other options.  Whew!)

Tim Daniels

---

