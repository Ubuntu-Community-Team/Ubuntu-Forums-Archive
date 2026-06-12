---
title: "How big should a boot partition be?"
date: 2006-05-12
forum: Desktop Environments
---

### Post by bpont on 2006-05-12
I've Googled this and the magic number fluctuates all over the place.  Recommended boot partition sizes range from 100mb, 51mb, 32mb, 8mb.  The biggest kernel I've ever compiled was about 3mb.  Why would anyone need such huge boot partitions?  Why is there such a variance in recommended sizes??  Thanks!

---

### Post by mlind on 2006-05-12
It really depens how many kernels you want to have installed
simultaneously. I usually have 2-3 different kernels installed, and few small
bootsplash images on /boot partition. My boot partition is sized as 100 MB, 
but it never has filled up.

Currently I have 1 kernel installed and it takes about 15 MB, do the math yourself :)

If you're planning to make new Ubuntu install, I suggest you create a separate boot
parition something like 50-100 MB. For the remaining paritions use LVM.

---

### Post by bpont on 2006-05-12
[QUOTE=mlind]

If you're planning to make new Ubuntu install, I suggest you create a separate boot
parition something like 50-100 MB. For the remaining paritions use LVM.[/QUOTE]

Thanks for the advice, mlind.  I don't know much about LVM, but Googled it and it seems intriguing, but a bit daunting to set up.  Do you have any good links to share?  The ones I found seemed a bit outdated.  

Since the disk I'm partitioning is a bare second disk and my first disk has Windoze 98 on it, I guess I'd need a LIVE CD that already has the LVM tools I'd need.  Again, can you make a recommendation here?  I'm guessing the most standard kernels (incl. Ubuntu) support these partitions...

---

### Post by mlind on 2006-05-12
[QUOTE=bpont]Thanks for the advice, mlind.  I don't know much about LVM, but Googled it and it seems intriguing, but a bit daunting to set up.  Do you have any good links to share?  The ones I found seemed a bit outdated.
[/QUOTE]

LVM isn't that hard to setup atleast, terminology is bit scary though.

Try if these guides help
[http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)
[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/sysadmin-guide/s1-lvm-diskdruid-manual.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/sysadmin-guide/s1-lvm-diskdruid-manual.html)

When you're doing a fresh install, choose custom partition instead of the wizard.
Create ext3 /boot partition first (bootable flag on), and don't put it inside LVM.

Then continue with LVM creation process. When you get the LVM setup done,
you create other partitions as LVM logical volumes. Remember to create swap
partition too. You could even use separate / and /home logical volumes, so that
upgrade process is easier. /home directory will stay safe if you decide to format / partition.

[QUOTE=bpont]
Since the disk I'm partitioning is a bare second disk and my first disk has Windoze 98 on it, I guess I'd need a LIVE CD that already has the LVM tools I'd need.  Again, can you make a recommendation here?  I'm guessing the most standard kernels (incl. Ubuntu) support these partitions...
[/QUOTE]

Ubuntu installCD or liveCD will both have partition tools for you, but I've only
used the installCD. If your disk is formatted FAT32, you should be able to cut
slack space for Ubuntu install easily. I'm not sure about NTFS. I've usually just
resized free space while on Windows, then allowed Ubuntu installer only to use
available free space for installation.


I usually setup partitions like this
/boot 50-100 MB, outside LVM
swap (size of my RAM), in LVM
/        5GB, in LVM
/home (rest of the space), in LVM

---

### Post by bpont on 2006-05-12
Mlind, great advice...I will try it...however, I'm not sure you answered my question about the LVM tools.  I do have an old Hoary Ubuntu setup disk with fdisk, parted, etc...but does it also have the LVM tools I need?

---

### Post by mlind on 2006-05-13
[QUOTE=bpont]Mlind, great advice...I will try it...however, I'm not sure you answered my question about the LVM tools.  I do have an old Hoary Ubuntu setup disk with fdisk, parted, etc...but does it also have the LVM tools I need?[/QUOTE]

Nessary partition tools (for LVM too) are included on Ubuntu install and live cd's.
Just download the Ubuntu distribution install-cd, burn the .iso image to a cd and
then boot from the cd.

For Breezy, you just download ubuntu-5.10-install-i386.iso from Ubuntu's mirrors,
burn the image using your preferred application, then boot using the cd.

btw. before you can create any LVM volume groups, you must allocate free space
for LVM to use.

---

### Post by bpont on 2006-05-13
Thanks again, mlind...actually, I fooled around with a live cd I had and successfully created the physical volume, volume group and a logical volume for swap.  So far, so good.  Now I must determine how big of a logical volume to create for Ubuntu Dapper.  For simplicity, I think I'm just going to put the entire installation (except /boot) on one logical volume.  I'm keeping my personal content, (music, video, etc.) on a windoze partition to have ubiqutious access, so I don't need to factor that into the equation.  I've read that filesystems prefer to expand, rather than shrink, so I'd rather create a smaller, conservative logical volume for Ubuntu and expand as needed, than create something huge and then have to shrink it if I need the space elsewhere.  That said, is there any Ubuntu documentation that explains minimum space requirements for a base install, size recommendations for an average system, a system with lots of apps, etc.?  I think I'll do some research on that and try to calculate a good volume size from what I read.  How much space would you recommend for a decent Dapper system that I can add to?

As always, thanks!

---

### Post by mlind on 2006-05-13
There could be some pointers about space requirements on Ubuntu's reference
documentation (or somewhere in wiki), but on quick look I couldn't find any.

Space requirements are relative to the sofware what your planning to install.
Basic Ubuntu installation without any modifcations should fit on 5-6GB okay, maybe
less - but I'm just guessing here. I'd start with atleast 7 GB if you have space to
waste.

If you later plan to install some relational database and/or server capabilities, and
you could need building dependencies installed at some point, so I'd say provide
more than 6 GB :mrgreen: 

I know these are very diplomatic aswers, but things depend on how you like your cake baked.

---

### Post by bpont on 2006-05-13
Mlind, based on what you said I'm thinking 10-15Gb would be plenty to start with, which I can well afford.  I'll keep checking around on this, but thanks again for all the great advice!

---

