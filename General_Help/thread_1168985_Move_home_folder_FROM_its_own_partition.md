---
title: "Move home folder FROM its own partition?"
date: 2009-05-24
forum: General Help
---

### Post by rewrittenfromscratch on 2009-05-24
My laptop has a decent-sized hard drive, so I decided that after I'd reclaimed about 80 gigs from Windows, I'd triple-boot Vista, Intrepid, and OpenSUSE (just to get a feel for it). 

Unfortunately, in my excitement at having so many options at boot time, I made a stupid mistake and installed Ubuntu onto a 65-gig partition and placed my home folder on a 14-gig partition. 

Of course, my root directory doesn't take up more than 4 gigs, whereas my home partition fills nearly instantaneously (especially when I begin editing and creating DVDs). 

So while most people ask if there's a way to move their home folder to it's own partition, I'm wondering if there's a way to do the inverse. I'm also curious as to whether there's a way to resize my root partition without corrupting my install. In the end, I'd like to have the root directory installed on a 10-gig partition and my home folder on a 60-70 gig partition.

I'm now using Jaunty and Windows 7; my OpenSUSE install is gone (I didn't like it in the least, so I reformatted that partition).

---

### Post by benerivo on 2009-05-24
I'm guessing here, but i think if you edit /etc/fstab to delete (or mark out) the /home partition mount, and then reboot, it will automatically use the root partition to store /home. So you would reach the gdm screen, and login. You would get a default desktop. In this desktop environment, i would mount the partition /home was on, and copy over the files to the newly created /home/me folder. Then logout and back in straight away.

But then you said you would want to shrink the root partition and put /home back on its own (large) partition. I think you are okay to shrink and enlarge using gparted from the live cd, whilst keeping the partitions compatible with fstab (just don't delete or create partitions), and then use one of the many tutorials for 'moving /home to its own partition'. If i was going this far, i would personally just back up my files to external storage and then reinstall.

---

### Post by kansasnoob on 2009-05-24
It sounds to me like the simplest thing would be to use Gparted (aka: Partition Editor) from any Ubuntu live CD to resize the partitions.

It would be very helpful to actually see a screenshot of the drive. You could install Gparted:

```
sudo apt-get install gparted
```

Then go to System > Administration > Partition Editor and post a screenshot. the screenshot app is in accessories and you can attach it using the paper clip at the top of this form.

Note: you won't be able to do your resizing with this installed version of Gparted as your partitions must be unmounted to work with them.

---

### Post by rewrittenfromscratch on 2009-05-24
Here's my Gparted screenshot.

---

### Post by kansasnoob on 2009-05-24
Well, it's not going to be particularly easy, because your Windows partition is in between / and /home, but what you could do is use Gparted from the live CD and shrink sda5 (your / partition) to about 6 or 7 GB, then click on the new unallocated space and create a new ext3 partition (should come out as sda7).

Then you'd have to use something like Partimage to copy your existing /home to the new partition. Really a lot of work, and you'll have to change things in fstab, play with uuid's, etc.

One thing I will worn you of right now is **do not** move the beginning of your Vista partition! In fact if you decide to do any resizing/moving of Vista I highly recommend using only Vista's own partitioning tools!

IMHO with only 3.23 GB of data stored on your Ubuntu /home partition the simplest thing would be to back it up and reinstall selecting "manual" and indicating "/" goes on sda1 and "/home" goes on sda5.

---

