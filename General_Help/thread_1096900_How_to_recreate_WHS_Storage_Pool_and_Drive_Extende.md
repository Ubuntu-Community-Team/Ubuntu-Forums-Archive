---
title: "How to recreate WHS Storage Pool and Drive Extender"
date: 2009-03-15
forum: General Help
---

### Post by mortuk on 2009-03-15
Hey all

Have purchased myself one of these - [http://www.tranquilpc-shop.co.uk/acatalog/BAREBONE_SERVERS.html](http://www.tranquilpc-shop.co.uk/acatalog/BAREBONE_SERVERS.html)

I am basically going to be using it as a home server. I am a great fan of Ubuntu, I use it on my main rig at work (web dev), plus I have a web server with svn etc setup on another box. Use it on my home machines (another web server setup similar to work), and my main rig as well when I am not gaming.

So naturally when it comes to making a home server, its definitely something I would consider. I was looking at WHS because of the storage pool (spans all your drives into one big pool, as I plan to mix drive sizes and configurations etc), as well a the Drive Extender feature, which is their version of RAID I guess but on a directory basis rather than physical volumes.

Can anyone point me in the right direction on how I would go about this in Ubuntu? As it stands I dont want to use WHS, even though it does seem very easy to setup and configure (running one on Vbox atm)

---

### Post by mortuk on 2009-03-18
anyone? have discovered and looked into LVM, but how would it work with ensuring data was duplicated across multiple physical drives?

---

### Post by mortuk on 2009-03-20
Have seen a few Ubuntu Home Server projects popped up but seem to be inactive, is this just not do-able or too time consuming for people?

Any info anyone can point me at would be very useful as I really dont want to have to use an MS product :P

---

### Post by u333untu on 2009-04-06
How is your server going along? Find a way that works for you?
I am wondering about the same question as you. 


Trying to avoid WHS. I want all these features but haven't been able to figure how to do it in ubuntu.
-Mix Hard Drive size
-Data redundancy
-Single storage pool


LVM will allow me to add/remove drive to a single storage pool but it doesn't provide any data redundancy. If a hard drive fails the pool is corrupted. I'm not sure how data is saved to a LVM pool either. Does it evenly spread data over each HD or fill up one at a time.

Linux Software RAID will allow me to have data redundancy but restrict me to same sized HD. I'm not sure how to grow/shrink an array when adding/removing HD.

Rsync will let me have selective directory redundancy like how its done in WHS but it's not automated. I need to setup manually the source/destination. When removing a HD I need to manually shift data.

---

### Post by mortuk on 2009-04-18
had to go the WHS route in the end :(

just wanted something easy as i have just had my first child a week ago and dont have the time nor brain power at the mo to sort it all out

---

### Post by ShadowVlican on 2009-04-27
this thread showed up in a google search "drive extender linux" (i'm looking for a linux alternative for windows home server)

but according to an old discussion found here: [http://www.avsforum.com/avs-vb/showthread.php?t=1043406](http://www.avsforum.com/avs-vb/showthread.php?t=1043406)

seems like a linux alternative of "drive extender" doesn't exists :(

---

### Post by cariboo on 2009-04-27
The term you are looking for is LVM, logical volume management. It's been around a lot longer than Microsoft's drive extender.

---

### Post by mortuk on 2009-06-24
> **cariboo907 said:**
> The term you are looking for is LVM, logical volume management. It's been around a lot longer than Microsoft's drive extender.

although to my knowledge it doesnt handle duplicating of chosen files / folders across multiple physical disks, which really is the main reason for using this and not RAID

---

### Post by najames on 2009-07-05
Take a look at Flexraid and unRAID.  They might do what you want.

[http://www.openegg.org/FlexRAID.curi](http://www.openegg.org/FlexRAID.curi)

[http://lime-technology.com/wordpress/?page_id=46](http://lime-technology.com/wordpress/?page_id=46)

---

### Post by Atamido on 2009-09-12
Unfortunately neither of those are comparable.  They both rely on creating parity data and can suffer pretty big performance hits on writes, as well as being risky to recover.

This is basically how Drive Extender works:

[LIST=1]
[*]There is 1 drive that acts as a Primary drive.
[*]You have X number of additional drives that act as Storage drives.
[*]The Primary drive can also act as a storage drive.
[*]All drives are formatted as NTFS and contain a directory on the root called "DE"
[*]Directories on the Primary drive that are marked as "Duplicate" are the only ones replicated.
[*]When a file is created in a replicated directory, a symbolic link is created on the Primary drive.
[*]The file data is placed on one of the Storage drives in the DE directory using the same file name and directory structure such that a file created as C:\Photos\Rabbit.jpg would have its symbolic link point at (and data stored in) stored as \DE\Photos\Rabbit.jpg
[*]A Storage drive can be attached to another computer, and the stored file can be read at Drive:\DE\Photos\Rabbit.jpg
[*]File data is stored on at least two Storage drives, with drive preference being a combination of available space and location of other files in the same directory.
[*]A failed Storage drive is rebuilt by copying over files that only have one copy in the cluster.
[*]A failed Primary drive is rebuilt by reading the directory structure and files from all of the Storage drives.
[*]Single Storage drive failure is seamless.
[*]Multiple Storage drive failure only results in the loss of files that do not have a second copy somewhere (interesting as there is there possibility of zero file loss with multiple drive failures, depending of file distribution.
[*]There are no requirements regarding using drives the same size.
[*]When creating/writing/modifying a file, only one Storage drive is written to initially with updates to the other Storage drive(s) scheduled at a lower priority so that drive IO isn't tied up.
[*]Only works properly over a network share.
[/LIST]
 As you can see, Drive Extender is extremely simple (and actually gains quite a bit from its simplicity).  You don't need to do anything to access the files stored on an individual drive.  And recreating the array is as simple as reading all of the files on the available drives.

---

### Post by gboudreau on 2009-11-29
I think I found a way to implement WHS Driver Extender-like functionality on Linux.
I detailed the steps I'm currently working on on my blog: [http://www.pommepause.com/blog/2009/11/how-i-plan-to-implement-my-own-whs-drive-extender-like-system/](http://www.pommepause.com/blog/2009/11/how-i-plan-to-implement-my-own-whs-drive-extender-like-system/)

Comments are welcome (in this thread, on as comments on my blog post). I think it does what you guys want.

Cheers.

---

### Post by gboudreau on 2009-12-16
Subscribers to this thread might be interested to know that I just posted the first public version of Greyhole - Easily expandable & redundant storage pool using Samba.
It's an open source implementation of something like Drive Extender.

If any of you guys want to help me test it, I'd be happy to get some help in finding bugs.
Once it's been tested enough, it should become a nice alternative to WHS Drive Extender! :)

You can read the details here:
[http://www.pommepause.com/blog/2009/12/greyhole-easily-expandable-redundant-storage-pool-using-samba/](http://www.pommepause.com/blog/2009/12/greyhole-easily-expandable-redundant-storage-pool-using-samba/)

Cheers.

---

