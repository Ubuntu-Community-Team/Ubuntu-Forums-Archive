---
title: "Repartitioning Question"
date: 2006-06-12
forum: Desktop Environments
---

### Post by Admiral Valdemar on 2006-06-12
I've recently gone about shrinking my Windows partition so as to give the majority of the drive to Ubuntu, especially since I aim to use only the Windows section for gaming while I use VMware for emulating Windows for anything else.

The problem is the usual space before a partition, since Windows is at the start of the disk, now there's a space after it and before the Ubuntu and swap partitions.

I have copied an image of the Ubuntu partition to my USB HDD as a backup, because I want to know if I can delete the Ubuntu partition on my main drive (given GParted and QTParted won't let me move an Ext3 partition to take up that extra space) and then restore it from my USB HDD but at the start of this big chunk of free space I now have.

Anything I should know about this?

---

### Post by talowe on 2006-06-12
[QUOTE=Admiral Valdemar]I've recently gone about shrinking my Windows partition so as to give the majority of the drive to Ubuntu, especially since I aim to use only the Windows section for gaming while I use VMware for emulating Windows for anything else.

The problem is the usual space before a partition, since Windows is at the start of the disk, now there's a space after it and before the Ubuntu and swap partitions.

I have copied an image of the Ubuntu partition to my USB HDD as a backup, because I want to know if I can delete the Ubuntu partition on my main drive (given GParted and QTParted won't let me move an Ext3 partition to take up that extra space) and then restore it from my USB HDD but at the start of this big chunk of free space I now have.

Anything I should know about this?[/QUOTE]

I don't know if you can copy a partion image of one size to a partition of another size.  The ext3 file system would have to be resized (I think).

gparted should let you move and resize ext3 partitions, they can't be mounted at the time though.  You have to boot from a live cd or another drive.

---

### Post by spvo on 2006-06-12
Talowe, even booting from a live cd may not help him.  GParted cannot always move a partition, even when it is booted from a live cd and no hard drives are mounted.  I believe, although I'm not fully sure, you can't move a partition if the tail end of the newly moved partiton would overwrite the old start position.  I am actually in the same situation at he is.  I deleted my breezy partiton, and now I have a huge chunk of unpartitioned space I can't add to dapper or my home partition. Oh well.

---

### Post by beameup on 2006-06-13
Have you tried running QTParted from a Knoppix LiveCD? I've had that work for me when Gparted wouldn't in the past.

---

### Post by Admiral Valdemar on 2006-06-13
I've tried QTParted using Knoppix 4.0 and it doesn't seem to want to let me move the partitions either. This is a blow, since I thought Ext3 being the base FS for Linux would at least be moveable now, I could understand NTFS and XFS etc. not being, but it seems odd Ext2 and 3 are stuck.

I guess I'll just have to mount the new partition as another Ext3 and name it /home and store some files there, though it's too small to have all my home files in which includes 50 gigs or music and video.

---

### Post by DougC on 2006-06-13
How did you make the image?

If you just used tar you should be ok.

just boot from a live cd delete your old partitions and recreate using whatever filesystem type you like (although I'd avoid XFS for the / partition).

When done, mount the new partition copy over your tarball and untar.

Remember and modify your /etc/fstab and probably /boot/grub/menu.lst to reflect any changes in partition numbers after you untar.

I've done this before for changing filesystem type but never on the / filesystem so be carefull.

---

### Post by Admiral Valdemar on 2006-06-13
I used PartImage to copy a single piece .img over to the USB hard disk. I had considered breaking it up into smaller chunks, but the USB drive is Ext3 now as well, so it doesn't have that 4 gig limit of FAT32 or NTFS.

What app. would I use from the Knoppix CD to copy over the image to the new partition?

---

### Post by DougC on 2006-06-13
Sorry, don't kow anything about PartImage. I personally would have used tar to backup then untar in the  new partition.

---

### Post by Admiral Valdemar on 2006-06-13
Hmm, guess I'll have to read up on it then. I usually use SimpleBackup which creates tar archives.

---

### Post by dksdk on 2006-06-13
hi if your empty space is as big as your ubuntu partition try booting from a gparted cd and copy and paste your ubuntu partition to the empty space. if that goes well you can delete the old ubuntu partition and extend the new one to the remaining space. you can create a swap as well.

this is all risky and it has worked for me before.
you will have to backup all your data before attempting.

and i had a problem after attempting this and i had to install grub afresh and for that you will need live/install cd.

will have to check youe fstab to make sure all is well.

---

### Post by az on 2006-06-13
[QUOTE=dksdk]hi if your empty space is as big as your ubuntu partition try booting from a gparted cd and copy and paste your ubuntu partition to the empty space. if that goes well you can delete the old ubuntu partition and extend the new one to the remaining space. you can create a swap as well.

this is all risky and it has worked for me before.
you will have to backup all your data before attempting.

and i had a problem after attempting this and i had to install grub afresh and for that you will need live/install cd.

will have to check youe fstab to make sure all is well.[/QUOTE]
Exactly.  Ext3 *is* moveable.  You just can't move the beginning (*sigh*)  But if you have made a backup with partimage, you will be able to delete the curret partition that is too big to move and redo your partitioning.

You will then restore the partimage image to that partition.  You will have to grow the filesystem to use all the partition size, since partimage copies the whole filesystem bit-by-bit.  You will end up with a partition that is able to hold a bigger filesystem, but whose filsystem is the same size as when you copied it.

Just resize the partition to go to the end of the new big partition.

---

### Post by Admiral Valdemar on 2006-06-13
I just formatted the free space as /opt, and it seems to be okay. The risk of moving partitions was annoying me, so I thought I'd keep it as a separate partition. What is /opt for anyway?

---

### Post by az on 2006-06-13
[QUOTE=Admiral Valdemar]What is /opt for anyway?[/QUOTE]

It's usually useless.

[http://www.debian.org/doc/packaging-manuals/fhs/fhs-3.8.html](http://www.debian.org/doc/packaging-manuals/fhs/fhs-3.8.html)


Your space will pretty much not be used.

---

### Post by Admiral Valdemar on 2006-06-13
Actually, I've just had something of a revelation now. I've been toying with the idea of an encrypted Ubuntu installation (likely using TrueCrypt) and I'm curious whether I can basically copy my installation as is now, and then format the drive to this encrypted filesystem, then load my previous Ubuntu installation on to it, rather than simply start afresh.

Is this actually doable? It's something I've been considering for a time and may implement.

---

### Post by Scunizi on 2006-06-18
Since everyone is talking partitioning I thought I'd post my question here instead of creating a new thread.  My root "/" partition is 3g and 99% full.  I'd like to add space to it from my home partition which would mean shrinking home and allocating the new space to /.  Can I do this? What program would allow me to do this?  I'm running 2 SATA's with Ubuntu on sdb3 & 6 & /.  sdb1 is NTFS from my windows side.  If I need to shrink the NTFS to make it work that's ok.  I just need some guidance.  Thanks!

---

### Post by dmroberson on 2006-06-28
[QUOTE=Admiral Valdemar]Actually, I've just had something of a revelation now. I've been toying with the idea of an encrypted Ubuntu installation (likely using TrueCrypt) and I'm curious whether I can basically copy my installation as is now, and then format the drive to this encrypted filesystem, then load my previous Ubuntu installation on to it, rather than simply start afresh.

Is this actually doable? It's something I've been considering for a time and may implement.[/QUOTE]

I don't think that will work, at least not the way I tried it, so far.  I've tried encrypting the entire hard disk, and the entire thing becomes unreadable to the OS.  When I restore my backup, using the script here: [http://www.io.com/~treeflyr/mkbkup/](http://www.io.com/~treeflyr/mkbkup/)

I get an error that the table is not recognized.

I think I'm gonna try to just encrypt the / partition and see if that works.  I'll post again with those results, but I know encrypting the entire hard disk will not work.

---

### Post by Kouya on 2006-06-30
I had the same problem. I booted from the live cd and copied the linux ext3 partition to the front so that I would be able to extend it (rightside..i think u know what i mean). However when i re-booted, grub showed an error and i could not even get into XP. had to reinstall linux on my spare drive all over again.

---

### Post by marcusg on 2006-08-16
I have the same question as others in the thread. I originally partitioned my disc with 3 partitions, one for Windows (I dual boot) one for / and the 3rd is divided between the liunx swap and a fat32 that I used for sharing files between ubuntu and windows. 

now i want to get rid of the fat32 partition and extend my / partition so that it uses up all of the availabe space. 
i've managed to use qtparted to delete the fat32, but cannot seem to grow the / partition. qtparted says that the swap and 3rd partition are both mounted.

here's a screenshot that shows the problem -> [http://flickr.com/photos/marcusg/216667213/](http://flickr.com/photos/marcusg/216667213/)

I'm using dapper and running qtparted from the live cd.

thanks
marcus.

---

