---
title: "upgrading to larger hard drive with windows and linux partitions"
date: 2009-05-30
forum: General Help
---

### Post by narnie on 2009-05-30
Hello,

I want to upgrade to a larger hard drive. I have a mixed OS environment of Windows on the first partition and Linux ext3/swap on the others.

I would rather NOT do a simple dd copy over because I #1 would like to copy ONLY file info, not the entire partitions (ie, exclude copying unused portions) #2 not have to move the linux partition over to expand the windoze partition which would be quite time consuming with this large a drive/partition (not to mention some significant thrashing of the HD) so I would just like to set everything the way I want it at the very beginning.

I would like to use gparted to set up the new partitions and their sizes on the new larger drive (I've don't this type of thing numerous times and am facile with it)

Then, I would like to copy the old, smaller windows partition over to the larger partition on the new drive. Can ntfsclone or partclone be used for this even tho it is going to a different sized partition? If so, how AND is it reliable? What is the syntax?

rsyncing the ext3 fs should be no problem, but a syntax in the description of this process would be appreciated.

Then, I should just have to rerun grub for "fixing" the mbr on the new drive. That should get linux to work. What about getting windows to work?

Should I run fixmbr from a windows recovery CD first to get the windows working and then run grub-install to get the linux and windows to dual boot?

Will this take care over all needs to make everything work? gparted should set everything up on the partitions including flagging it bootable when boot flag is set. It should set up the partition tables. Then just the ext3 fs over using archiving function of rsync. Then the windows trouble (ntfsclone) on a larger partition. Make windows able to boot with fixmbr. Make windows and linux dual boot with grub-install.

Thanks for any and all help,
Narnie

---

### Post by logos34 on 2009-05-30
I think all you might need to run is **fixboot** to write the windows bootloader code to C: (it's position/disk geometry will have changed), and maybe **chkdsk /r** to do a filesystem check.  But then you never know what's going to happen next with 'doze

Easiest way: use Gparted to create a partition (no need to preformat) roughly the size of the original.  Copy windows using the [copy/move function ]("http://gparted.sourceforge.net/larry/move/move.htm")(disk-to-disk)...Resize/grow it to desired size... Next, boot the live cd and use gparted there (system>admin>part. editor) to copy over linux. (reason: as you probably already know, / cannot be mounted during copy)

Write grub to the mbr of the new disk (make sure to point it to / on new, not old, disk) (see 'restore..' link below).  As long as your menu.lst and fstab use UUID instead of /dev/sdx format, you're done.  (UUID are copied along with the partitions).

The boot flag only matters to windows if using it's own bootloader (which looks for active primary partition)...you're chainloading windowswith grub, and in any event, you're windows menu.lst entry probably already has 'makeactive' option.  Linux/grub doesn't care about the boot flag

---

### Post by narnie on 2009-05-30
Thanks so much for your input. Ur right about fixboot. I wasn't aware that gparted could perform copy functions to another drive. I'm looking at it right now and don't see it (my wife says I can't see things right in front of me). I am on a computer right now that only has 1 HD on it, so perhaps that is why it is not showing up, but where do I look once I get to the computer in question that I'm going to be working on?

Narnie

---

### Post by logos34 on 2009-05-30
the partition has to be unmounted first, otherwise it's grayed out...Then, you can only copy it to the clipboard...You need to connect the other drive, select it in the dropdown menu upper right, then set disklabel before you can paste it in the unallocated space. It's all explained in the link

---

### Post by narnie on 2009-05-30
Oh my! I didn't see that as a link. I'm so sorry! I'll go read that link now.

Thanks for your patience.

Yours,
Narnie

---

### Post by zaphod777 on 2009-05-31
You can probably just use clonezilla. and have it clone the whole drive. then use a live cd and gparted to adjust the partition size.

if you are using ext4 you need to use the unstable cd based on 9.04 rather than the stable witch is based on debian stable.

---

### Post by narnie on 2009-05-31
Thanks, but as I posted above, I want to avoid having to not only copy a 320gb partition, but then turn around and move it as well to make the other partition larger. I'd rather just get partitions the right size to begin with and not have to move the partition over.

---

### Post by SaintDanBert on 2009-09-11
> **logos34 said:**
> 
I think all you might need to run ...

Easiest way: use Gparted ...

Write grub to the mbr ...


I find it very sad that the simple, common task of moving to a larger [laptop] disk drive is not (a) a built-in script on some live DVD, or (b) a public HOWTO. I understand the many of the technical issues and some of the technical details, but this thread is "arcane magic" in my book. 

I offer the following recipe or prescription in hopes that we might make this straight forward for more folks -- especially those who are technical users rather than tinkering users. Please comment, cuss and discuss so that I/we might have a HOWTO when this is completed.

Consider a dual-boot laptop with one HDD of some size. Call this OldDrive. 

Assume the need to remove and replace that HDD with a
new and larger HDD.  Call this NewDrive.

Let's divide the process into three parts:
Part-I ..... prepare NewDrive and copy from OldDrive to NewDrive
Part-II ..... integrate NewDrive into the laptop
Part-III ..... clean and polish the NewDrive configuration

Overview
========
In Part-I, we will leave OldDrive as the laptop boot drive and connect NewDrive as a USB resource. In this configuration, we will make NewDrive partitions and file systems, copy contents from OldDrive to NewDrive.

NOTE -- It never hurts to get a backup copy of the contents of OldDrive.

In Part-II, we will remove OldDrive and install NewDrive as the laptop boot disk. In addition, we will connect OldDrive to the laptop as a USB resource. (If we need to grab content from OldDrive it will be available.)  Remember to mount OldDrive read-only since it is your failsafe ... and you have the backup copy too, right?!  

NOTE-- We do not expect NewDrive to boot for a variety of reasons. Instead we will use a live DVD to boot the laptop and use the live DVD tools to make NewDrive boot.]

In Part-III, the laptop will boot using NewDrive but there may be rough spots and pot-holes left over from the move.

=== to be continued ===

PS/  I am going to eat my own dogfood as I write this. I have a Thinkpad with a 160 GB drive that is dual-boot WinXP and Ubuntu Hardy.
I have a new 320 GB drive and USB case. Let the fun begin.

---

### Post by StuartN on 2009-09-11
> **zaphod777 said:**
> You can probably just use clonezilla. and have it clone the whole drive.

I used Clonezilla last weekend to move four partitions containing GRUB and two operating systems onto a new, empty drive. I temporarily removed my primary slave data drive, plugged the new drive in as the primary slave, booted Clonezilla from a USB memorystick and cloned the old primary master onto the new primary slave. Then I unplugged the old drive and plugged in the new drive in place as master, replaced the data drive and (magic!) it booted up just like before, except the primary master drive is now 90% free.

Of course having the data all on a second drive to begin with means that I am only messing with the OS drive, so I don't care about moving partitions (especially with only 10% used).

Clonezilla is a great product.

---

### Post by SaintDanBert on 2009-09-11
Part-I -- Prepare the New Drive

In this phase, we will leave our laptop as-is [aka, OldDrive] and connect a new and larger drive [aka, NewDrive] as a USB resource.

Our OldDrive looks likes this as created and delivered by our laptop vendor.

```

user@host:~$ sudo sfdisk --list /dev/sda

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   3916-   3917-  31457280+   7  HPFS/NTFS
/dev/sda2      18707+  19456-    750-   6017760   12  Compaq diagnostics
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
                end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda3       3916+  18706   14791- 118806665+   5  Extended
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       3916+   3928      13-    102349   83  Linux
/dev/sda6       3929+   3941      13-    104391   83  Linux
/dev/sda7       3942+  14974   11033-  88622541   8e  Linux LVM
/dev/sda8      14975+  18706    3732-  29977258+   c  W95 FAT32 (LBA)

```

The as-built configuration has Windows-XP and Ubuntu Hardy in a dual-boot configuration. In addition, there is a laptop manufacturer supplied Diagnostic
and Recovery "utility" partition. There is a FAT32 win-dose "data drive" (D:).
The remainder of the drive space is linux swap and linux virtual disk (LVM) configuration.

In addition to a move to the larger drive, we plan to alter the use of LVM. Specifically, the vendor put /home inside the virtual disk space so that it would be easy to resize as per-user file needs grew. This creates a problem during rare win-dose sessions because there are no utilities that will reach into linux LVM space.  There are utilities that will permit win-dose to read-write EXT2/EXT3 file systems directly. [see [http://www.fs-driver.org/](http://www.fs-driver.org/) ] I want to use this to access /home from WinXP.

Since we are using win-tel based computers, our disks are subject to the configuration and usage requirements of that world.  This means:
 == drive may have at most four primary partitions
== one of those partitions may be "extended"
== an extended partition may in turn hold at least one secondary
(sometimes called "logical") partition.
== an extended partition may hold up to 255 secondary partitions
(Does more than 8 or so make any practical sense?)
== M$-DOS and M$-WinXX require that the "system drive" (C:) be
(a) a primary partition
(b) a partition that is marked "active" in the partition table.
NOTE -- Don't worry about this as the GRUB boot loader will manage the "active" issue for us dynamically.

Given these rules, one partition plan might look like this:

Partition     Description
I             Primary, DOS bootable, Vendor utility and diagnostic space
II            Primary, WinXX system (C:), bootable, system drive
III           Primary, linux /boot
IV            Extended
IV-a          logical, WinXX data (D:)
IV-b          logical, linux /  (root)
IV-c          logical, linux /home
IV-d          logical, linux LVM, "swap" /var, etc., rest of the drive

I invite and encourage folks to critique this partition plan. There are at least two questions:

Q1.  Does this list of partitions do the job? Do we want or need other partitions?
Q2.  Does this partition order do the job? Does some other order make better sense?
NOTE -- The vendor utility space might have a vendor-forced, vendor-fixed location in the grand scheme of things. (I know of one vendor that requires their utility partition be primary #2 -- not #1 or #3 or #4 -- and certainly not logical.)

Our next issue is the amount of space for each partition. The size of the target NewDrive is the governing factor here, but here we might create some guidelines.

The Vendor Space takes what it takes -- typically 5-10 GB.

The /boot partition only needs about 500 MB (yes, meg not gig), and that is generous.

The /home partition is whatever you want for how ever you work and how many unique real users will use the workstation.  I like to have a public read-write /wrk folder tree that is similar to /home (consider /home/john and /wrk/john) for active project files and data.

The root (/) partition can vary based on a couple of things.  If you include /var, /opt, /usr/local, /var/www, /var/tmp, and such into root, you need one sort of space. If any or all of these are separate partitions in LVM, then root can be smaller and you can manage the relative sizes of these spaces.

===== to be continued ===
PS -- Again, I'm deploying what this says as I write it.  I invite comments and suggestions for improvement. I encourage links to other threads or pages that address these matters. Remember our mission: Given a dual-boot laptop HDD, replace it with a larger HDD that does the same things.

---

