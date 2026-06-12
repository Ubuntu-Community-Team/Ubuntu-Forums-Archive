---
title: "Clone Hard Drive"
date: 2008-12-06
forum: General Help
---

### Post by sirdouglas on 2008-12-06
I have a HP Pavilion dv1000 notebook with an 80gb hard drive.  I have just bought a new 320gb hard drive for it, but instead of reinstalling Linux and starting all over, I want to make a cloned backup of my 80gb hard drive, to my external hard drive, and then transfer it all onto the new hard drive.  I referred to this website to figure it out: [http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/](http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/)

So first, I had to make an identically-sized partition on my external hard drive.  I used the livecd and gnome partition editor, and first I resized the external, leaving 71.66 gb (the same as my laptop HD) "allocated."  After this, I formatted the drive with the default as ext2 (is that what it was, ext), but I was not successful being able to write onto this drive, so I tried ext3.  Which is the best way to format?  

Anyways, here's what I typed in to clone my notebook's HD and the results:

sirdouglas@sirdouglas-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   57G   11G  85% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  336K  500M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  596K  500M   1% /dev/shm
lrm                   501M  2.0M  499M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb2              71G  180M   67G   1% /media/disk
/dev/sdb1             208G  200G  8.8G  96% /media/New Volume
sirdouglas@sirdouglas-laptop:~$ sudo dd if=/dev/sda1 of=/dev/sdb2
[sudo] password for sirdouglas: 
dd: writing to `/dev/sdb2': Input/output error
52166977+0 records in
52166976+0 records out
26709491712 bytes (27 GB) copied, 6563.15 s, 4.1 MB/s
----------------------------------------------------------

Where did I go wrong?  What's this input/output error all about?  Is there an easier way to clone my hard drive so I don't have to start all over with my settings and installed programs?  Thanks for the help!

Doug

PS: my HD is SATA

---

### Post by dcstar on 2008-12-07
> **sirdouglas said:**
> 
.......
Where did I go wrong?  What's this input/output error all about?  Is there an easier way to clone my hard drive so I don't have to start all over with my settings and installed programs?  Thanks for the help!


You seem to be trying to copy the root partition you have actually booted up from and are using, this may not be possible due to locked files etc.

Boot off a Live CD and try it, then your hard disk partitions will not be in use.

---

### Post by sirdouglas on 2008-12-07
Thanks for the reply.  I tried the same process using the liveCD, but now another error has occurred saying that permission is denied to the first HD.  Sorry I don't remember the exact words in the Terminal, but after typing sudo dd if=/dev/sda1 of=/dev/sdb2, it responds that permission denied to dev/sda1 or something like that.  Hm, any ideas?  Thanks once again!

Doug

---

### Post by falcon61102 on 2008-12-07
You're probably going to have to use sudo to copy the contents of your drive due to the root permissions necessary.

---

### Post by dcstar on 2008-12-07
> **sirdouglas said:**
> Thanks for the reply.  I tried the same process using the liveCD, but now another error has occurred saying that permission is denied to the first HD.  Sorry I don't remember the exact words in the Terminal, but after typing sudo dd if=/dev/sda1 of=/dev/sdb2, it responds that permission denied to dev/sda1 or something like that.  Hm, any ideas?  Thanks once again!

Doug

Use the gparted copy/paste function to copy the partition from one disk to the other (using the Live CD).

---

### Post by mike555 on 2008-12-07
You could use " remastersys " to make a complete bootable , installable copy of your system, burn it to DVD , you can then install that "copy " on your new hard drive and it should have all your stuff in it .......

---

### Post by sirdouglas on 2008-12-07
Thanks for the input.  That sounds so simple using what dcstar said: Copy/Paste the partition.  Does it really work that easily?  Otherwise the remastersys sounds good as well; does it just copy all my settings or does it make a cloned copy as well, therefore requiring a number of dvds?  In the meantime, I'll try copy/paste and get back to you!
Thanks!

Doug

---

### Post by sirdouglas on 2008-12-07
Update: So I tried the copy/paste function and after copying /dev/sda1 to /dev/sdb2 this error popped up:

An error occurred while applying the operations

See the details for more information.

IMPORTANT
If you want support, you need to provide the saved details!
See [http://gparted.sourceforge.net/larry/tips/save_details.htm](http://gparted.sourceforge.net/larry/tips/save_details.htm) for more information.
---------------------------------------------------------------

Well, I tried the link there, but found myself more confused.  I'm not really a big expert with the whole terminal thing, but I appreciate any of the help you guys throw my way!

Doug

---

### Post by TeXtonyx on 2008-12-07
I use Acronis. One boots up a cd and chooses clone drive and its
about as simple as A->B. Also the second drive needs to be equal
_or larger_ which means you don't have to figure that out. Where
is that missing 9GB, 80GB less 71GB. 

Anyway, nearly all drive manufactures have a diagnostic utility
cd that comes with a clone drive option. You start the process
and come back later. You sound so busy. Unless you are into the
learning process, I would try something more automated. 

I also use Acronis for backups and if remastersys works good 
that is an easier option. The problem is if the backup takes
more than 3 dvds under high compression, handling the dvds 
becomes complicated.
I don't know if remastersys surpasses this complication.

So all in all, some automated clone software seems in order,
though that ARS tutorial will no doubt work with enough blood 
sweat and tears. (from Winston Churchill, Britain's PM, WWII)

I tried cloning on a desktop which then would have two drives.
Well, the UUID doesn't work, so you need another one then tune2*
It was easier to do a backup and then reinstall. 

I think you should use a method that doesn't require an exactly
the same size to partition. I think 71GB is wrong. Use either
the OEM clone tool or an automated backup tool that allows the
old drive to be expanded into the new drive. I would delete the 
71GB and start over, use something for lazy modern slackers. :-)

---

### Post by TeXtonyx on 2008-12-07
> **sirdouglas said:**
> I have a HP Pavilion dv1000 notebook with an 80gb hard drive.  I have just bought a new 320gb hard drive for it, but instead of reinstalling Linux and starting all over, I want to make a cloned backup of my 80gb hard drive, to my external hard drive, and then transfer it all onto the new hard drive.  I referred to this website to figure it out: [http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/](http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/)

So first, I had to make an identically-sized partition on my external hard drive.  

TeX: I found what I think will serve you well. I liked it enough
that I will be using it. When a program is mature enough to have
its installation procedures with screenshots it is also more
stable in terms of fixed bugs. Also I included the quote because
it says that if the new partition is too large, some space is
wasted. I think you should make the new partition 80GB because
that missing 9GB might be unused space within the Ubuntu partition
rather than unallocated (which also means unformatted) space on
the same drive, but outside/beyond the Ubuntu partition/boundary.
It is not going to waste 9GB but maybe 200?(depends) mb, which
is a small price to pay to be sure your partition is large 
enough so that it won't fail. Also, you will use some compression,
so that unused space within the partition will be highly compressed
and will hardly add to the size of the file.  

"you have to unmount before you can use partimage. I suggest booting 
from a live cd" [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
SystemRescueCd contain partimage plus other useful stuff and boots 
live so Os is unmounted. The only drawback is that the most current
release of partimage may not have found its way on to the most current
release os SystemRescueCd->Nov,17,2008. The repositories lag for this.
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page) partimage-0.6.7.tar.bz2 Feb 2008
"If you don't want to install Partimage, you can download and burn 
SystemRescueCd. It's a livecd that allows to use Partimage immediately 
even if your computer has no operating system installed (useful to 
restore an image), and it allows to save an image on a DVD on the fly."
 
[http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html](http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html)
"The partition to restore must have the same size as the saved 
partition. If the partition is smaller than the original one, 
the operation will fail. If it is bigger, space can be lost." 

I'm not saying the other backup program won't work, but it's 
younger, less tested. Let a word to the wise be sufficient. :D

---

### Post by sirdouglas on 2008-12-08
Thank you for the replies everyone.  I think it's time for me to try something else now though because this is just taking way too long with no success.  Instead of aiming for an exact clone of my HD, is there a way for me to at least burn my most current version of Linux Ubuntu with all my currently installed programs onto a DVD?  If so, it makes so much more sense because I can backup music and other media on my external HD and just throw Linux (which is the most time-consuming to get back up-to-date after reformatting) onto a DVD.  Would PartImage do this?  

Once again, I really appreciate all the help from you guys, love the community!

Doug

---

### Post by yonkiman on 2008-12-13
> **TeXtonyx said:**
> I use Acronis. One boots up a cd and chooses clone drive and its
about as simple as A->B. Also the second drive needs to be equal
_or larger_ which means you don't have to figure that out. Where
is that missing 9GB, 80GB less 71GB. 

Which version/flavor of Acronis (I assume True Image) are you using?

Also, does the second drive actually need to be larger, or just large enough for the actual data used?  When I use acronis (8.0) on the PC, I can "clone" a 200G partition that's only got 80G of data to it to a 100G partition.  I'd like to do that with my ext3 boot disk if I can...

---

