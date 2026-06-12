---
title: "New HDD`"
date: 2008-12-29
forum: General Help
---

### Post by CollisionInc on 2008-12-29
I installed Ubuntu Intrpied on a 20gig HDD initially and now the drive is full. Is it possible to copy/mirror the drive onto an 80gig HDD so that i do not have to reinstall and update on a new HDD
:confused:

---

### Post by jpkotta on 2008-12-30
This is an overview.  There are articles for each step in the community docs [https://help.ubuntu.com/community/UserDocumentation](https://help.ubuntu.com/community/UserDocumentation).

Make sure your new drive is partitioned and formatted with a Linux filesystem (NTFS or FAT are not recommended for a root partition).

Boot from a Live CD.  Mount the two HDs, using a command similar to:
```
sudo mkdir /media/new /media/old 
sudo mount /dev/sda1 /media/old
sudo mount /dev/sdb1 /media/new
```
It is very possible that your device names are different.

Then copy old to new with the -a (archive) option.  This will preserve all the permissions, etc.
```
sudo cp /media/old/* /media/new/
```

Finally, you will probably have to edit your /etc/fstab, because the new drive will have a different UUID.  Find the UUID of the new drive with ```
vol_id /dev/sdb1
``` and replace the UUID= statements in /media/new/etc/fstab.  You will probably have at least a root partition and a swap partition; you need to update the UUID for each partition in fstab.

---

### Post by redilyn on 2008-12-30
I would suggest just moving your /home to the new hard drive as it is most likely what is taking the most space.

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

If you do this you should have lots of space for ubuntu, no need to reinstall lose settings etc etc.

---

### Post by logos34 on 2008-12-30
> **redilyn said:**
> I would suggest just moving your /home to the new hard drive as it is most likely what is taking the most space.

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)


Yes, if you want to keep the 20gb drive you could use it for / (your system partition) and make a separate /home on the 80gb. But if you do so don't use the cpio command in that link--I've stopped recommending it because of permissions problems afterwards with logging into the user desktop.  Use the cp -a method (see link in my signature below).

If you plan to replace the current drive, you could just copy the entire thing to the 80gb with dd command (includes the MBR, /swap and everything):

> [Cloning an entire hard disk]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/"):
Code:

[COLOR="Red"]dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror[/COLOR]

/dev/sda is the source. /dev/sdb is the target. Do not reverse the intended source and target. It happens. Notrunc means 'do not truncate the output file'. Noerror means to keep going if there is an error. Normally dd stops at any error. 



---

### Post by redilyn on 2008-12-30
Could you elaborate on the permission problems?

I usually recommend that link and have no encountered the error you are referring too.

Not doubting you, just trying to increase my knowledge. :)


I just looked at the link you recommended. I notice 2 things.

1) It says login as root. I thought you couldn't login as root in ubuntu.

2) It makes no mention of uuid entry in fstab. That is required if moving to a new partition.

---

### Post by logos34 on 2008-12-30
> **redilyn said:**
> Could you elaborate on the permission problems?

I usually recommend that link and have no encountered the error you are referring too.

Not doubting you, just trying to increase my knowledge. :)


I just looked at the link you recommended. I notice 2 things.

1) It says login as root. I thought you couldn't login as root in ubuntu.

2) It makes no mention of uuid entry in fstab. That is required if moving to a new partition.

there's threads on the permissions thing--.dmrc file is one.  I've got one bookmarked somewhere...i'll post it if I find it


1) Sure you can:

sudo -i

Or you can simply use 'sudo' before each one as needed

2) Ubuntu may have switched to uuids since Feisty, but you don't have to use them--you can continue using '/dev/sdxy' format.  quite a few still do.

---

### Post by redilyn on 2008-12-30
You learn something new everyday.

I thought for sure uuid was required. In fact I'm sure i tryed it without a uuid before and it didn't work.

Also I didn't know about sudo -i.

I always used sudo -s which i thought gave a root prompt.

---

### Post by jpkotta on 2008-12-30
```
sudo -s
```starts a root shell.  It is basically the same as ```
sudo bash
```

```
sudo -i
``` starts a login shell.  It's like logging in as root from the login prompt.  I prefer this one.

---

### Post by sosaudio1 on 2008-12-30
> **redilyn said:**
> You learn something new everyday.

I thought for sure uuid was required. In fact I'm sure i tryed it without a uuid before and it didn't work.

Also I didn't know about sudo -i.

I always used sudo -s which i thought gave a root prompt.

I know that you can even mix and match within your fstab entries....meaning you can have one drive picked up with UUID from install, then add a second with the /dev and have it mount and run just like normal...I even discovered later that the added HDD has a UUID, I just never used it in my fstab. Works with Ubuntu 8.04 and Linux Mint 5. Probably with 8.10 and LM6 too.

L8R
Rich

---

### Post by logos34 on 2008-12-30
> **sosaudio1 said:**
> I know that you can even mix and match within your fstab entries....meaning you can have one drive picked up with UUID from install, then add a second with the /dev and have it mount and run just like normal...I even discovered later that the added HDD has a UUID, I just never used it in my fstab. Works with Ubuntu 8.04 and Linux Mint 5. Probably with 8.10 and LM6 too.

+1

you can even CHANGE the default UUID of a partition generated at installation time:

tune2fs -U random /dev/sdxy

or time-based:

tune2fs -U time /dev/sdxy

Frankly, I used to hate UUIDs--when the devs first made the switch I felt it was unecessary for everyday desktop use and sometimes caused more confusion than they cleared up, but I'm cool with them now.  They come in handy with external storage, and can be a life-saver in cases where you have two different sata controllers playing musical drive letters with your disks at every boot!

---

### Post by don_xvi on 2009-01-04
Hi, folks, I've used the dd technique to image my old hard drive onto my new one, what's now my best way to utilize the new space ?
Now, I have a 10 GB partition that's copied over, then two small swap partitions, then empty space I want to expand my operating partition into.  Can I just delete the two swap partitions, expand and recreate swaps ?  Why do I have 2 swap partitions, is one left from a previous installation ?  And how big should they be, anyways ?  Of course, some of these followon questions can be answered elsewhere, so the important part is how to make use of the new space ?
I'm trying to use the resize/move function in GParted, but that won't seem to let me move a partition elsewhere on the disk, only to reallocate a smaller version of the partition within it's current space.

---

### Post by logos34 on 2009-01-04
look in your /etc/fstab for the swap--that's the one the system is using.  Delete the other one.

Post a screenshot of Gparted if you could, as well as 

sudo fdisk -l

---

### Post by don_xvi on 2009-01-04
Oh of course !  I'm getting far enough with this that this all made sense !  fstab indicated that the OS was actually using both swap partitions, but since I have 4GB and rarely get into swapping, I just went ahead and swapoff'ed both of them and deleted their partitions, then used my live CD to expand the operating partition to 40 GiB.  I may turn swap back on now, or may not.

Thanks for the pointer !

---

### Post by logos34 on 2009-01-04
ok.  Just beware that you can't hibernate without a swap _>_your ram (4 GB).  Maybe that's not an issue for you, but I thought I'd mention it. 

Also, if you decide you want swap back, you can't simply do 'swapon'--you have to manually create a swap partition in gparted ('linux-swap') and put an entry back into fstab.

good luck

---

