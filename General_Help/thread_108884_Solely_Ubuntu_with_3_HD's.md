---
title: "Solely Ubuntu with 3 HD's"
date: 2005-12-27
forum: General Help
---

### Post by hairshirt on 2005-12-27
Hello everyone, I've finally decided to take the plunge and now all my systems (4 incl. 1 G4 PPC) run Ubuntu Linux.  I've tinkered with Ubuntu for the past year on dual-boot systems and I have to say I've been very impressed.  I'm very glad to say that my life has been cleansed of parasitic M$ completely.  Nuff said about that!

Anyway, this is my first post/request for help in a year so as you may agree, I'm used to and capable  of sorting most issues out for myself.

I can't seem to get my head around this fstab and this hard drive config thing.  So a little help from the Ubuntu community would be greatly appreciated.

My main box (my workstation) has three HD's fitted.  1 x IDE, 2 x SATA.  Ubuntu is installed on the IDE drive.  You've probably guessed my requirements already, whereby I would like very much to fully utilise the two SATA drives.

My Current fstab config (it just fails on boot!):

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/sda5	/sda5		ext3	defaults,errors=remount-ro 0       1
/dev/sda6	/sda6		ext3	defaults,errors=remount-ro 0       1
/dev/sdb5	/sdb5		ext3	defaults,errors=remount-ro 0       1
/dev/sda6	/sda6		ext3	defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Thanks in advance you guys.

(Can't upload the six GParted screenshot, however, it's more or less the same as the 5th screenshot.)

---

### Post by dna on 2005-12-27
I would try changing the lines to:

/dev/sda5 /sda5 ext3 rw,user,noauto 0 0

then try mounting.

edit:

Also, why do the sata disks start at partition 5. I'm pretty sure that means they are extended partitions.

---

### Post by fordfan753 on 2005-12-27
The only thing I can suggest is the mount points...do they all exist? Traditionally things are mounted in /mnt/*name* or /media/*name* not /*name*

Also, I don't agree with the options you put on the SATA drives.

Does it give you a reason for failing? ie error message.

---

### Post by hairshirt on 2005-12-27
Thanks Guys.  It's heartening to see there's support out there.

They are extended drives (partitions).  I enclosed some screen shots detailing this (I think).

Also fordfan753: I didn't understand what you wrote “Also, I don't agree with the options you put on the SATA drives.”  Do you mean what I've done or the suggestion dna made?

Thanks again chaps.

---

### Post by Zwack on 2005-12-27
[QUOTE=hairshirt]
/dev/sda5	/sda5		ext3	defaults,errors=remount-ro 0       1
/dev/sda6	/sda6		ext3	defaults,errors=remount-ro 0       1
/dev/sdb5	/sdb5		ext3	defaults,errors=remount-ro 0       1
/dev/sda6	/sda6		ext3	defaults,errors=remount-ro 0       1
[/QUOTE]

The bottom line should probably read
/dev/sdb6      /sdb6 ....

Try the following command

ls -ld /sd*
you should see the directories listed, if not then your mount points don't exist.  You need to create them, but do you really want to mount them as /sd???  I would suggest thinking about what you intend to use these for.  Perhaps create a mirrored or striped disk set (do you want redundancy or speed?) using LVM and then carve partitions out as you need them.  Remember you don't need to mount all of the partitions at the top level, you can mount them wherever you want.

What happens when you try to mount them by hand?

sudo mount /dev/sdb5

Can you paste the output?

I hope that this helps,
    Z.

---

### Post by hairshirt on 2005-12-27
Hi Zwack

mount: mount point /sdb5 does not exist

I'm starting to feel like a plonker!  As in: I don't think therefore I plonk!

---

### Post by hairshirt on 2005-12-27
But how does one mount the drive/partition to create a start point?

---

### Post by infoseeker on 2005-12-27
I would do something like this:
(First create the mount point, do so for each partition)

#sudo mkdir /disk5           (or partition5, or what ever you want to call it)

Then----->

#sudo mount /dev/sdb5 /disk5

Your fstab entry might then be
> /dev/sda5 /disk5 ext3 defaults,errors=remount-ro 0 1

Just my 2 cents worth ;)

---

### Post by hairshirt on 2005-12-27
Okay... I've got the first partition on each drive done, however, I seem to be unable to mount the second/last partition on each drive (sda6 & sdb6).

Ran $ sudo mount -a and recieved the following error massage:

mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Thanks chaps.

---

### Post by hairshirt on 2005-12-27
Okay... There was a typo in my fstab config.  Now I just receive the follow error:

mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

However, I'm still unable browse the last partition on each HD with "Disks Manager".

Any more help out there.  Thanks...

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-27
Here's what I see: You've got three hard drives, two 150gb and one 80gb. Most of the 80gb drive is fulll but it appears you're so far using pretty much nothing of the two larger drives. At this point you have the option of doing things robustly.. here's what I would suggest.

Make partitions on the two larger drives that are exactly the same size as the largest partition on your first (smaller) drive. The only reason you're doing this is so you can employ them all in a RAID5. This will protect your data when one of those drives craps out (and they will, absolutely, fail some day - my experience is sooner than you expect). 

If you make partitions on the two larger drives of exactly the same size you will have space left over (obviously). You can make these their own partitions for other stuff and use them like any other, they just won't be protected from failure like the "main" drive you would create.

When you partition the two large drives then you set up a RAID5 using mdadm (it's very simple). You initialize the drive with an empty slot, which means it will be a RAID but not protected from failure. You do this because you have to get your data off the main drive. So, ater running mdadm you have a70gb drive on hda, and you have a 140gb drive that spans your two sda drives. You just copy the data from your main drive into the new, larger partition you made using mdadm,and then you add the main drive (where your data lives right now) into the RAID after you are sure everything copied properly. At that point you would have a 150gb RAID that actually uses 225GB of your storage but your data is safe in the event of a single drive failure.

In the last five years, 6 out of 6 new drives I have bought have gone back to the manufacturer for warranty repair. Since you have the resources right there in front of you to do this you can save yourself a lot of trouble in the longer haul by doing things properly **before** you get those two larger drives so full of data you can't move stuff around.

That's my suggestion based on some pretty bad experiences with data loss. I realize my rough outline may sound intimidating if you're new to linux but it's not hard and I'll be happy to walk you through it if you would like to go that route.

---

### Post by hairshirt on 2005-12-27
Okay... Rebooted the box and I can mount (automatically) all partition except the second partitionon the first drive (sda6).

Any ideas fellas?

PS. Thanks &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046;.  I have been toying with the idea of employing RAID.  Just want to get stuff working first.  The first, smaller HD, is so full because it contains stuff from my previous Windoze config, ready to be deployed on the two larger drives.  Thanks anyway.

---

### Post by Zwack on 2005-12-27
[QUOTE=hairshirt]Okay... Rebooted the box and I can mount (automatically) all partition except the second partitionon the first drive (sda6).
[/QUOTE]

I'm glad that we are getting somewhere now.  

So let's try a  few commands.

ls -ld /sda6

Does that show a directory?

sudo fdisk -l /dev/sda

does that show an sda6 partition?

If both of those are o.k. then I wonder if you actually created a filesystem on that disk partition.  Looking at your gparted screenshots it looks to me like you created  sda6 as an ext2 partition not an ext3 one.  try the following...

sudo mount -t ext2 /dev/sda6 /sda6

If that works then you might want to destroy and rebuild sda6.

If none of this works then tell us what errors you got and we'll work from there.

Z.

---

### Post by hairshirt on 2005-12-27
Right... All done now and it all works.  The problem of mounting the last partition on the second HD was solved by simply reformating the partition.  All seems to work now... Touch wood.

I was intrigued by some of the suggestions a few have made re. my fstab config file.  For your ref.:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/sda5	/sda5		ext3	[COLOR="Red"]defaults,errors=remount-ro[/COLOR] 0       1
/dev/sda6	/sda6		ext3	[COLOR="Red"]defaults,errors=remount-ro[/COLOR][COLOR="Black"] 0[/COLOR]       1
/dev/sdb5	/sdb5		ext3	[COLOR="Red"]defaults,errors=remount-ro [COLOR="Black"]0[/COLOR][/COLOR]       1
/dev/sdb6	/sdb6		ext3	[COLOR="Red"]defaults,errors=remount-ro[/COLOR] 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Any suggests?  I just used what I thought was the default on the 1st HD which was configered that way by Ubuntu was it was installed.

---

### Post by hairshirt on 2005-12-27
Sorry Zwack, missed your reply as I was typing when you posted.

Sorry Mate, as I could have saved you the trouble.

---

### Post by hairshirt on 2005-12-27
What's this folder "lost&found"?

And why don't I have permissions to copy to the drive or create a new folder?  Very confusing indeed!

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-27
lost7found is where recoverd files go when fsck discovers an error somewhere. You have to be root to access it.

Did you set write permissions on the folders where you mounted those drives? Try this in a terminal window:

sudo chmod -R 777 /sda5
sudo chmod -R 777 /sda6
sudo chmod -R 777 /sdb5
sudo chmod -R 777 /sdb6

---

### Post by fordfan753 on 2005-12-27
[QUOTE=hairshirt]Thanks Guys.  It's heartening to see there's support out there.

They are extended drives (partitions).  I enclosed some screen shots detailing this (I think).

Also fordfan753: I didn't understand what you wrote “Also, I don't agree with the options you put on the SATA drives.”  Do you mean what I've done or the suggestion dna made?

Thanks again chaps.[/QUOTE]

I just meant what dna was getting at, I only use those options on the root partition, but on the others I use different options allowing users to write anywhere on the drive.

---

### Post by hairshirt on 2005-12-28
Okay... Thanks but I didn't do it anyway.

Thanks for all your help guys.

---

### Post by psusi on 2005-12-28
> **&#1055 said:**
> 
Make partitions on the two larger drives that are exactly the same size as the largest partition on your first (smaller) drive. The only reason you're doing this is so you can employ them all in a RAID5. This will protect your data when one of those drives craps out (and they will, absolutely, fail some day - my experience is sooner than you expect). 

You do NOT want to make a raid5 volume using all 3 disks.  Firstly, it would require destroying the data on the existing disk, and secondly, the speed of the array is limited by the slowest drive in the array, so you should only raid drives of the same model.  

> **&#1055 said:**
> 
In the last five years, 6 out of 6 new drives I have bought have gone back to the manufacturer for warranty repair. Since you have the resources right there in front of you to do this you can save yourself a lot of trouble in the longer haul by doing things properly **before** you get those two larger drives so full of data you can't move stuff around.

Wow... what kind of drives have you been buying?  In the last 10 years I have owned 8 drives, and only had 1 fail.  That one was a refurbished 10,000 rpm drive and it still lasted 3 years running 24/7.  For that matter, it never really failed... I just decided to stop using it when I realized that it was making a LOT of noise ( so was probably going to fail soon ).  

If the two new SATA drives are the same model, then I'd recomend using them as one big raid0 array.  Keeps all your storage in one partition for ease of use, and it will be nice and fast.  You can either mount it in /media/*name* so it shows up on your desktop, or use it for /home.  

As allways, you should make regular backups of any data that is important to you.

---

### Post by Zwack on 2005-12-29
[QUOTE=psusi]If the two new SATA drives are the same model, then I'd recomend using them as one big raid0 array.  Keeps all your storage in one partition for ease of use, and it will be nice and fast.  You can either mount it in /media/*name* so it shows up on your desktop, or use it for /home. [/QUOTE]

RAID0 is just striping so it will speed up disk access but will not provide you with any redundancy.  I would be tempted to create a RAID 1 array myself.  You will still get fast read accesses but you could afford to lose one disk and still have access to your data.

Backups are essential anyway.  A RAID 1 array will portect you from hardware failure of a single drive, but a brain fart can accidentally destroy both copies...  Whoops I didn't mean to type rm /full/path/ * while in the root directory.  (I have done that, and recovered the system successfully).

Z.

---

### Post by psusi on 2005-12-29
Raid1 read is a little faster than a single disk, write isn't.  Raid0 is still much faster at both.  The most important reason to me though, is that with a raid1 you only get the space of a single drive, which seems like a big waste to me.  

The only time I would consider using a raid1 instead of a raid0 is on a server where it is more important to withstand a hardware failure than to have speed or space.  Of course, then it is a better idea to use 3-5 drives and set up a raid5, which gives you the fault tolerance as well as most of the speed and space.  

And of course you DO make regular backups don't you? ;)

[QUOTE=Zwack]RAID0 is just striping so it will speed up disk access but will not provide you with any redundancy.  I would be tempted to create a RAID 1 array myself.  You will still get fast read accesses but you could afford to lose one disk and still have access to your data.

Backups are essential anyway.  A RAID 1 array will portect you from hardware failure of a single drive, but a brain fart can accidentally destroy both copies...  Whoops I didn't mean to type rm /full/path/ * while in the root directory.  (I have done that, and recovered the system successfully).

Z.[/QUOTE]

---

### Post by Zwack on 2005-12-29
[QUOTE=psusi]Raid1 read is a little faster than a single disk, write isn't.  Raid0 is still much faster at both.  The most important reason to me though, is that with a raid1 you only get the space of a single drive, which seems like a big waste to me.  

The only time I would consider using a raid1 instead of a raid0 is on a server where it is more important to withstand a hardware failure than to have speed or space.  Of course, then it is a better idea to use 3-5 drives and set up a raid5, which gives you the fault tolerance as well as most of the speed and space.  

And of course you DO make regular backups don't you? ;)[/QUOTE]

RAID 1 Read can be significantly faster than single disk with the right implementation.  You are reading alternate "blocks" from alternate disks just like RAID 0.  RAID 1 has to write everything to both disks so it is slower than RAID 0.  depending on the implementation it can be as slow as a single disk or slower.

I would suggest that you get four disks and use RAID 0+1.  This gives you four disks for reads and two disks for writes so you will be faster than RAID 0 on reads and the same speed on writes.  Sure RAID5 gives you more space but unless you are using a hardware RAID controller you are sacrificing some of your processor power to do the checksum calculations.  

Of course I work on serious server hardware all the time so it depends on where your emphasis is and what benefit you want.  If you want protection/fault tolerance then RAID 1.  If you want raw speed then RAID 0.  If cost is no object then Fibre Channel to an external disk array with lots of Cache and hardware RAID controllers.  :-D

And we both agree that backups are essential whatever you are doing.  No amount of fault tolerance is going to help you when you type rm -rf /

Z.

---

### Post by psusi on 2005-12-29
Calculating XORs is VERY fast/easy.  The CPU isn't even going to notice the extra work even if you have the raid5 array writing flat out as fast as it can go.

---

### Post by Zwack on 2005-12-29
[QUOTE=psusi]Calculating XORs is VERY fast/easy.  The CPU isn't even going to notice the extra work even if you have the raid5 array writing flat out as fast as it can go.[/QUOTE]

Depends on the amount of data you're working with...  We've seen noticeable differences on some of our servers... The simple fact is that if you are reading and writing a lot of data then calculating that XOR is still an extra step that doesn't have to be done for RAID 0+1.  

Of course I doubt many people out there are running machines with terabyte databases...  We have a few of those...

Z.

---

### Post by hairshirt on 2006-01-01
[QUOTE=Zwack]Depends on the amount of data you're working with...  We've seen noticeable differences on some of our servers... The simple fact is that if you are reading and writing a lot of data then calculating that XOR is still an extra step that doesn't have to be done for RAID 0+1.  

Of course I doubt many people out there are running machines with terabyte databases...  We have a few of those...

Z.[/QUOTE]


Ooooooo

---

