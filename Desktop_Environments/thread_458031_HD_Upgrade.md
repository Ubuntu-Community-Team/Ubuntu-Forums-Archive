---
title: "HD Upgrade"
date: 2007-05-29
forum: Desktop Environments
---

### Post by HouseShark on 2007-05-29
I would like to install a larger HD and move my Ubuntu installation to that drive.  Is there a program available, in the repositories, that will allow me to copy my existing drive, and Ubuntu install, to the new "larger" HD.

Thanks.

---

### Post by tszanon on 2007-05-29
I never tried doing this and I'm not sure, but I think it's as simple as copying the contents of the old drive to the new one...maybe you will have to deal with grub, setting it up to boot from the new drive, but I think it won't be any harder than this.

---

### Post by HouseShark on 2007-05-29
Thanks,

Grub was really the only thing that concerned me as I'm sure it is installed in the boot sector of the drive.  I'm not real up on installing it fresh and I fiigured that a drive copy would be the next best option.

One suggestion I have received was to make an ISO back-up of my Root partition and then overwrite that on a fresh install on the new drive.  Any thoughts on this approach.

Thanks again.

---

### Post by tszanon on 2007-05-29
> **HouseShark said:**
> Thanks,

Grub was really the only thing that concerned me as I'm sure it is installed in the boot sector of the drive.  I'm not real up on installing it fresh and I fiigured that a drive copy would be the next best option.

One suggestion I have received was to make an ISO back-up of my Root partition and then overwrite that on a fresh install on the new drive.  Any thoughts on this approach.

Thanks again.
Using cp, creating an ISO-image of the files, creating a partition image using partimage...I see them all as alternative ways of copying the files. If I recall correctly, unlike Windows, Linux doesn't care where, in the disk, the files are written, so there's no need to make sure that the files are still in the same place (partimage).

If you will just copy the files, I see no need for creating an ISO-image. It would be time-consuming and I don't see any benefits over just copying.

Suggestion: boot using a live-cd, mount both drives, copy the old drive to the new drive (remember to use sudo), configure/install/whatever grub on the new drive. It seems to me that it's what you have to do to get there.

There's a link somewhere around here to a post explaining how to reconfigure/reinstall grub. If I see it, I'll paste it here.

---

### Post by HouseShark on 2007-05-29
Thanks again.  I appreciate the help.  Any info you can pass along will certainly help.  I&#8217;m finding out that there are more than one way to approach this issue.

---

### Post by tszanon on 2007-05-29
I don't know what happened, I had already posted here the link I mentioned...anyway, here's the link again: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
It tells you how to reinstall grub, which will be necessary.

---

### Post by HouseShark on 2007-05-30
Thanks again.  I think this gives me all I need.

---

### Post by coffeecat on 2007-05-30
> **HouseShark said:**
> Thanks again.  I think this gives me all I need.

Not quite. Unfortunately, there is one important matter that has been missed. For some obscure reason, the Ubuntu devs use UUIDs to define partitions in /etc/fstab rather than most distros' use of /dev/sda1 or whatever. Have a look in fstab and you will see something like:

```
# /dev/sda1
UUID=a_load_of_gibberish      /          ext3    defaults,errors=remount-ro    0  1
```assuming that sda1 is your root partition, and something along the same lines for any other mounted partitions. If you don't do something about this you'll have major problems trying to boot up after you have cloned your installation to the new hard drive. In fact, it simply won't boot successfully. Believe me, I have a resaonable amount of experience cloning installations of different flavours of Linux and I speak from bitter experience. :(

The easiest thing is to remove the UUID=garbage bit, uncomment the /dev/sda1 and merge the two lines together. If you need help just post back.

Another thing for you to think about. An alternative idea is to use tar. Just make a tar.gz or tar.bz2 file of your root partition (+ any other partitions) to a storage medium and then use a live CD to untar the archives back onto your new drive.  This is what I use and it's really quite easy.

The general principle for cloning an installation to another/partition drive is straightforward. Do it; then edit fstab and menu.lst.

But what I want to know is, what on earth were the Ubuntu devs inhaling when they decided to use UUIDs in the fstab? :evil:

---

### Post by pebo on 2007-05-30
> **coffeecat said:**
> But what I want to know is, what on earth were the Ubuntu devs inhaling when they decided to use UUIDs in the fstab? :evil:From [here]("https://bugs.launchpad.net/ubuntu/+bug/72016")> (We're using UUIDs to allow you to change your hard-drive cabling without stopping your machine from booting, AND because all of those /dev/hd* paths will be changing to /dev/sd* paths in feisty or later)Still think I can live without those UUIDs though...:(

---

### Post by tszanon on 2007-05-30
Yeah, you're right. Since I still use Dapper, I completely forgot about those UUIDs...I'm sorry.
Then, correcting myself:
1. copy the files;
2. reconfigure grub;
**3. reconfigure fstab.**

Now I think you have all the info you'll need. :)

---

### Post by coffeecat on 2007-05-30
> **pebo said:**
> From [here ]("https://bugs.launchpad.net/ubuntu/+bug/72016"). Still think I can live without those UUIDs though...:(

> (We're using UUIDs to allow you to change your hard-drive cabling without stopping your machine from booting, AND because all of those /dev/hd* paths will be changing to /dev/sd* paths in feisty or later)Ironic then that the recent kernel upgrade from 2.6.20.15 to 2.6.20.16 has changed the /dev/sd* paths back to /dev/hd* for a lot of people. :roll: Which, of course, is a problem if you've edited fstab the way I've suggested. Recognise the voice of bitter experience again? :evil: 

But it's a matter of debate whether more people 'change your hard-drive cabling' than do what the OP wants to do. 

Thanks for the link, **pebo**. But it still doesn't explain what they were inhaling. :lol:

**Edit:** OK, sorry. I'm being unfair to the devs. What with hd* changing to sd* and back to hd* it might be safer to stay with UUIDS. **HouseShark**, I believe you can determine the UUIDs of the partitions on the new HD with the command 'blkid'. Best of luck.

Ain't Linux fun? Any more of this and I'll buy myself a Mac. No, only joking. Honest :(

---

### Post by HouseShark on 2007-06-06
Ouch --- well sort of.  Good thing I got tied up at work and haven't had the time to actually attempt a copy yet.

I think I understand how to exchange the UUID wiht the verbose drive designation, but if the drive assignment will remain the same, after migration, i.e. hda1 --- does it realy make any difference.  Unless the UUID contains information about the drive itself ---  like manufacturer and drive serial number, which I'm thinking it does, but then again I couldn't find enough info on UUID's to explain what they really contain when associated with file systems.

Either way, wouldn't it be simpler to edit fstab before copying the partition to the new drive.  That way the next boot to the new drive would be "just like home."

I'm actually leaning towards using GParted on live CD to make the copy.

---

### Post by HouseShark on 2007-06-12
I guess everyone gave up on me ---- well I'll post my the results of my migration, if for no other reason in the interest of posterity.

Below are the procedures I used to move my Ubuntu installation to a larger HD and the results (total time expended – 2.5 hrs):

1) Used GParted Live CD to copy hda1 to secondary “data” drive.

	Result: hda1 copy now resides as sda7.

2) Performed fresh Ubuntu install from Live CD on destination drive to ensure GRUB and drive geometry set-up is correct.

	Result: Standard Ubuntu install (2 partitions) on drive.

3) Booted back to GParted Live CD and deleted hda1 on destination drive and copied sda7 to drive and expanded size of partition.

	Result: Destination drive ready for reboot.  Ubuntu partitions reside in sda7 and hda1.

4) Shut down GParted Live CD and reboot Ubuntu on new drive.

	Result: Normal boot and log-in into Ubuntu and notification/installation of regular updates with two minor exceptions: 1) RAM GDesklet issued error, on start-up, associated with Swap File.  2) Drive monitor GDesklet displayed wrong size for / (root).  Note: size displayed for / was size of the original installation on the smaller drive (the same size of the partition sda7).

5) Shut down and re-install and boot to original (small) HD --- (removable drives).

	Result: Normal boot and log-in with same two GDesklet errors as boot to new drive.  Force check of updates – “none available” reported (updates performed on new drive should have been available for this installation).

6) Shut down and re-boot into GParted Live CD and delete partition sda7, shut down and re-boot to new large HD.

	Result:  Normal boot and log-in into Ubuntu.  Re-notified of available updates and GDesklet errors gone.

Conclusion/assumptions: UUID’s for mount designation may only be a problem for migrating installations when associated with certain chip-sets.  Ubuntu assigns drive designations in priority, sd then hd, thus any visible/bootable Ubuntu partition residing on sd will boot first.

Hope someone will find my learning experience helpful.

---

