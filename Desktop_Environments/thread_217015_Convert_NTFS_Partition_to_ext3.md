---
title: "Convert NTFS Partition to ext3"
date: 2006-07-16
forum: Desktop Environments
---

### Post by dartmusic on 2006-07-16
While the subject of this post might seem simple, I'm trying to gather some info before undertaking this.

I built an HTPC a couple of months ago, but didn't have an ivtv compatible tuner card, so I loaded XP and MediaPortal.  After much frustration, I bought a Hauppauge card, loaded Ubuntu and MythTV, much to my joy, though when I loaded Ubuntu, I kept the XP partition, just in case I couldn't get Myth working appropriately.

So, here's my concern: I want those 60 or so gigs back that I left as the XP partition.  What is the best way to increase my "main" Ubuntu partition (running Dapper, btw) without borking it.

Any tips?

Thanks!

---

### Post by sciyoshi on 2006-07-16
Theres no way to convert an NTFS partition to an ext3 one, if that's what your asking. If you just want to erase your old windows partition, you can 
delete it and resize the first one... look at GParted or Disk Manager.

Samuel

---

### Post by [S|G] on 2006-07-16
Do you want to keep any of the data you have on your NTFS partition? If so, I believe you'll need to back it up first. I'm not sure if there's a way to do a simple "conversion" from ntfs to EXT3. 

It's more like erasing the NTFS and resizing your EXT3 into the resulting free space. You'll need to boot from a live-cd to do that, since you'll need to work with your root directory unmounted.

---

### Post by dartmusic on 2006-07-16
Yes, I want to delete the NTFS partition and no, I don't want to keep anything that's there.

I'm not sure how to go about doing this.

---

### Post by Renko on 2006-07-16
Then QTParted is your tool :)

I have done this in the past with a Knoppix CD-Rom which does include QTParted. An Ubuntu CD + internet connection will work too I suppose. It's not that hard, QTParted works quite easy.

---

### Post by [S|G] on 2006-07-16
1. If you have an Ubuntu live-cd, boot from it
2. Start gparted.
3. Delete the NTFS partition
4. Resize your EXT3 partition into the free space
5. Apply Changes
6. Reboot

---

### Post by jimmygoon on 2006-07-16
* SysRescueCD for qt_parted which I like better than ([http://www.sysresccd.org/](http://www.sysresccd.org/))
* gParted Live disc ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php))

---

### Post by dartmusic on 2006-07-16
I got as far as #4 below, but there is no option to resize the ext3 partition INTO the free space.  I can create a NEW partition in the free space, but that's not what I want to do.

Any ideas?


> **'[S|G] said:**
> 1. If you have an Ubuntu live-cd, boot from it
2. Start gparted.
3. Delete the NTFS partition
4. Resize your EXT3 partition into the free space
5. Apply Changes
6. Reboot

---

### Post by [S|G] on 2006-07-16
Is the NTFS partition the one exactly after your EXT3? I know that you can resize your partition into free space after the end of the partition. If there are any other partitions beetween the EXT3 and the free space (i.e. [EXT3]-[Swap]-[Free Space]) then you won't be able to simply resize it. I'm not sure if you can resize on space before the start of the partition as well.

You can, however, create a new partition and mount it as your home, for example, or as a data-holding directory under your /home/YourUser.

---

### Post by dartmusic on 2006-07-16
I was afraid of that.  I just hate having these sort of odd workarounds to remember.  That's what I get for not trusting the mighty Ubuntu!!  (ha...)

Thanks for your help, everyone.

---

