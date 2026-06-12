---
title: "[SOLVED] Fun(NOT) and Games With FStab"
date: 2008-12-16
forum: General Help
---

### Post by -kg- on 2008-12-16
I was posting on this issue in another thread in the Beginner's section and, since it was liable to become a bit technical, thought I should try another thread here in General.

First off:  I *DID NOT* intentionally change anything in fstab to cause any of the partitions on my hard drives (there are two in this laptop) to automatically mount.  The laptop was running as normal up until a couple of days ago, then this problem cropped up and I'm not yet willing to do any editing of my fstab files until I fully understand it.  In fact, this is the first time I've even *looked* at fstab and it's contents.

The original problem is described [on this thread.]("http://ubuntuforums.org/showthread.php?p=6370596#post6370596")  From that thread:

> When trying to unmount volumes from the desktop, I have come up with the following information:

[QUOTE]Cannot unmount volume

You are not privileged to unmount the volume "{Name of Volume}"

Details
{mntent}:line 13 in /etc/fstab is bad
umount: only root can unmount /dev/sdb6 from media/sdb6

And as a further piece of the puzzle: When I launch Nautilus and try to unmount from there (by right-clicking either in the right panel or the tree on the left, I get the message:

> Cannot unmount volume
The volume is not mounted

Even though I know good and well it is mounted...I can view the files on the volume and, if it were not mounted, I wouldn't be presented the "unmount" selection in the right-click drop down menu (right?). I would instead be presented with the "mount" option.[/QUOTE]

Since this point (and from helpful posts I received in that original post) I have done a little study of fstab so that, instead of just following posted information, I could actually *understand* what I was doing...hopefully to be able to use this knowledge in other areas and for other things (like actually causing a partition to automount at boot when *I* want it to).  I still haven't found this information, so here goes:

I have studied a couple of bodhi.zazen's excellant tutorials and posts, including [AutomaticallyMountPartitions,]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") and still haven't found exactly what I want to know.  First off, a post of my current /etc/fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sdb7
UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sdb8
UUID=14d792bb-fb5f-4f54-ab8a-5c113dfdda72  /home          ext3         relatime                    0  2  
# /dev/sdb9
UUID=232b4464-6725-4c4a-9a93-9922027ffe4c  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb6                                  /media/sdb6    ntfs         defaults                    0  0  
/dev/sdb5                                  /media/New Volume  ntfs         nls=iso8859-1,umask=000,ro  0  0  
/dev/sdb5                                  /media/sdb5    ntfs         defaults                    0  0  
/dev/sda2                                  /media/sda2    ntfs         defaults                    0  0  
/dev/sda3                                  /media/sda3    ntfs         defaults                    0  0  
/dev/sdb7                                  /media/sdb7    ext3         defaults                    0  0  
/dev/sdb8                                  /media/sdb8    ext3         defaults                    0  0  
/dev/sdb9                                  /media/sdb9    swap         defaults                    0  0  


sda1 contains unreadable information and I believe is the Toshiba backup partition for restoring Vista, so I can understand that it is not listed (though it is visible in Nautilus).  Under GPartEd there is an exclamation point with it, and says that it is not readable.

Now for the problem(s).  From the original post:

> OK, first regarding the error:
Line 13 tries to mount to /media/New Volume. You should rename the that folder/fstab entry to something without a space in the name, like "NewVolume".

I don't know how that line found it's way into fstab, but I do note that there are *two* lines for sdb5, the "New Volume" one, and one below it.  Do I need both lines, and if not, which one should I get rid of?  Why has the mount point been so named, but all of the rest are assigned sdX (*ALL* of my ntfs volumes are assigned names) in fstab?)?

I have since gone back into Vista (sorry!) and changed all the drive names to ones that have no space.  They now reflect those changes on the (still) automounted drives, both on the desktop and in nautilus.  Guess that changed nothing with the problem, though, because the (erroneous) fstab entry remains unchanged and still gives me the error.  If not erasure, should I change the entry to the actual drive "name" that I re-assigned to that drive?

Another thing I just found out: it seems to be that sdb5 is not even the drive I thought it was.  I thought it might be my ntfs partition on which I have stored my .mp3 files, but instead it points to where I have my Vista installable files stored (not program installs, but storage for the installers).  How that might have happened I have even *less* idea!  As far as I can recollect, the device which is now named "Music" was the original "New Volume" drive, and that's the one I renamed to "Music."  I have not created or removed any volumes in the last couple of days, so I don't think that would have anything to do with it.

However, I have noticed some anomalies in the partitions under GPartEd:

[IMG]http://img.photobucket.com/albums/v634/kg5uc/Screenshot--dev-sdb-GParted-1.png[/IMG]

Note that this is a screenshot of my sdb drive.  The whole drive is contained in an extended partition, sdb1 (my sda drive being the boot drive with 2 ntfs primary partitions).  However, the logical partitions are listed as sdb5 through sdb8.  What happened to sdb2 through sdb4? And why are the partitions numbered out of order?  Does Linux number them partially according to file systems?

Anyway, what *specifically* would one need to change in fstab to make a drive automount, and how is it disabled?  Why is it that the "New Volume" sdb5 entry was named as such, and why none of the others (ALL the ntfs drives are named so I can tell the difference between them)?  Will changing this setting enable user (i.e., my) permissions to mount and unmount volumes in Nautilus and on the desktop like before, or do I need to take other steps elsewhere?

And though this question will likely be hard to find an answer to, what might have caused all the drives to start automounting all of the sudden and all the permissions to change so that I can't mount or unmount them from Nautilus?

One final question:  I know that the drive named "filesystem" is my Linux OS files, etc.  I have a 10 GB /root (sdb7) and a 30 GB /home (sdb8) partition, .  However, when I pull a "properties" on the "Filesystem" partition under nautilus, I get (edited):

> Contents: 579,462 items, totalling 33.7 GB

Free Space: 5.4 GB

Now /root is shown in Nautilus as a 10 GB Filesystem, then I have the Filesystem drive, which I assume is /home.  When I pull "properties" on the /root (10 GB Filesystem), I show 5.4 GB free, but you can see (under GPartEd, above) that the /home partition is 30 GB (27.94, to be exact).  It also shows 625.55 MB used, with 27.33 GB free.  There is one partition (sdb5) which has 5.21 GB free, but that can't be right, both because of the free size, and because sdb5 is an NTFS partition.

In short, the only partition I have on sb that is anywhere near 35 total GB is ntfs, and when I click on the "filesystem," I definitely come up with Linux related folders (like bin, boot, etc) and if that's not enough, I also have vmlinuz listed.

How is it that so much space is listed, with so little free space left, when I pull a properties on this drive and yet GPartEd tells a totally (even wildly) different story, *especially* on a /home partition which is shown by GPartEd to be so spectacularly empty?

Strange stuff (at least to me) going on with this installation.  I won't even get into my desktop (yet), which has a few problems of it's own.

'Nuff for this round.  Just let me know if you require any further information.

---

### Post by taurus on 2008-12-16
No, you don't need two entries for /dev/sdb5 so edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and remove these lines.

```

/dev/sdb5 /media/New Volume ntfs nls=iso8859-1,umask=000,ro 0 0 
/dev/sdb7 /media/sdb7 ext3 defaults 0 0
/dev/sdb8 /media/sdb8 ext3 defaults 0 0 

```
Then, you also need to modify the last one, /dev/sdb9, from

```
/dev/sdb9 /media/sdb9 swap defaults 0 0 
```
to 

```
/dev/sdb9   none   swap   sw   0   0
```
Save it and reboot.

Not sure what you did you your /dev/sdb but you have a bunch of unallocated spaces between partitions.

---

### Post by savagenator on 2008-12-16
EDIT: Taurus did a great job explaining fstab.

This is actually very interesting, and my conclusion is very uncertain.

As for you strange partition setup, it is out of this world. It may be that there is corruption in your drive causing gparted to see it as empty, or maybe a Vista problem, I do not know. Make sure you shut down cleanly in Vista though.

I would backup your Vista and Linux files and do a reinstall of LInux with a good partition scheme, deleting all currect linux partitions and then creating new ones that are taking up all the unallocated space.

---

### Post by -kg- on 2008-12-16
Thanks for all the quick responses!

> Then, you also need to modify the last one, /dev/sdb9, from

Code:

/dev/sdb9 /media/sdb9 swap defaults 0 0

to

Code:

/dev/sdb9   none   swap   sw   0   0



Actually, I would assume that I could just delete that line, since it is covered up the list, just above the "dev/sd0" line, right?

> As for you strange partition setup, it is out of this world. It may be that there is corruption in your drive causing gparted to see it as empty, or maybe a Vista problem, I do not know. Make sure you shut down cleanly in Vista though.

Actually, I mostly left it that way before installation.  I needed to go into Vista for some reason to resize the partitions for the Ubuntu installation (actually, I think it was that I didn't quite trust GPartEd to correctly manipulate ntfs (especially created by Vista)).  Anyway, for some reason, I was able to shrink the partitions, but was unable to move them afterwards (stupid Micro$oft products!).  So I went ahead and created my ext3 and swap partitions in the free space, leaving room for subsequent (experimental) installations.

Still, though...what caused my partitions to start automounting, and how do I turn that off?
Wasn't anything that Vista *did;* it was what Vista *couldn't do!*

---

### Post by savagenator on 2008-12-16
Wow, that is a very strange thing. You might be able to move partitions with gparted, but I do not know.

to stop the kernel from automounting your drives you comment out the lines of your drives in fstab. Just put a '#' before the line you want to comment out.

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb7
UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 / ext3 relatime,errors=remount-ro 0 1
# /dev/sdb8
UUID=14d792bb-fb5f-4f54-ab8a-5c113dfdda72 /home ext3 relatime 0 2
# /dev/sdb9
UUID=232b4464-6725-4c4a-9a93-9922027ffe4c none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
#/dev/sdb6 /media/sdb6 ntfs defaults 0 0
#/dev/sdb5 /media/New Volume ntfs nls=iso8859-1,umask=000,ro 0 0
#/dev/sdb5 /media/sdb5 ntfs defaults 0 0
#/dev/sda2 /media/sda2 ntfs defaults 0 0
#/dev/sda3 /media/sda3 ntfs defaults 0 0
/dev/sdb7 /media/sdb7 ext3 defaults 0 0
/dev/sdb8 /media/sdb8 ext3 defaults 0 0
#/dev/sdb9 /media/sdb9 swap defaults 0 0
#I added this line as the correct version and commented it out because it is a replicate of the above swap.
#/dev/sdb9 none swap sw 0 0 

Keep in mind, I would restart and make the partition as follows:

keep /dev/sdb5 (ntfs) as first, resize it to inclue the first unallocated space
delete /dev/sdb7 (ext3 /) and /dev/sdb9 swap and replace them both with one big ext3 partition.
Leave /dev/sdb6 as is.
expand /dev/sdb8 (ext3 /home) to fill the rest of the unallocated space, leaving about 1gb of room for swap.

OR!!!!

Use gparted to delete all linux partitions, move your first ntfs partition to the front, then the second to be right next to the fist, then setup a root (/) partition and a home (/home) parititon after those 2, leaving no unallocated space.

---

### Post by savagenator on 2008-12-16
Wow, that is a very strange thing. You might be able to move partitions with gparted, but I do not know.

to stop the kernel from automounting your drives you comment out the lines of your drives in fstab. Just put a '#' before the line you want to comment out.

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb7
UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 / ext3 relatime,errors=remount-ro 0 1
# /dev/sdb8
UUID=14d792bb-fb5f-4f54-ab8a-5c113dfdda72 /home ext3 relatime 0 2
# /dev/sdb9
UUID=232b4464-6725-4c4a-9a93-9922027ffe4c none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
#/dev/sdb6 /media/sdb6 ntfs defaults 0 0
#/dev/sdb5 /media/New Volume ntfs nls=iso8859-1,umask=000,ro 0 0
#/dev/sdb5 /media/sdb5 ntfs defaults 0 0
#/dev/sda2 /media/sda2 ntfs defaults 0 0
#/dev/sda3 /media/sda3 ntfs defaults 0 0
#/dev/sdb7 /media/sdb7 ext3 defaults 0 0
#/dev/sdb8 /media/sdb8 ext3 defaults 0 0
#/dev/sdb9 /media/sdb9 swap defaults 0 0
#I added this line as the correct version and commented it out because it is a replicate of the above swap.
#/dev/sdb9 none swap sw 0 0 

Keep in mind, I would restart and make the partition as follows:

keep /dev/sdb5 (ntfs) as first, resize it to inclue the first unallocated space
delete /dev/sdb7 (ext3 /) and /dev/sdb9 swap and replace them both with one big ext3 partition.
Leave /dev/sdb6 as is.
expand /dev/sdb8 (ext3 /home) to fill the rest of the unallocated space, leaving about 1gb of room for swap.

OR!!!!

Use gparted to delete all linux partitions, move your first ntfs partition to the front, then the second to be right next to the fist, then setup a root (/) partition and a home (/home) parititon after those 2, leaving no unallocated space.

EDIT: you can mount your drives in gnome using nautilus, you do not need /etc/fstab. And try not to make duplicates in fstab

---

### Post by -kg- on 2008-12-16
> to stop the kernel from automounting your drives you comment out the lines of your drives in fstab. Just put a '#' before the line you want to comment out.

But according to what I've read, if the drives are not listed in fstab, the only way to mount them is as root.  Before, I was able to mount them using Nautilus (not "sudo nautilus" in the terminal).

I not only want to be able to mount my ntfs drives this way (the way it was before), I want to be able to automount one of the ntfs drives (the correct one...sdb6) as well. I would like access to my mp3 files without having to remount the appropriate drive every time I reboot.

---

### Post by savagenator on 2008-12-16
No, my belief (not using ubuntu at the moment) is that you do NOT need them in fstab, they will show up in mtab and in nautilus as unmounted media, you double click and they mount (you dont need to be root as far as i know, hal will do the rest)

Your problem will be that the drives mount themselves to different location every time you mount them in gnome. For example, if you mount /dev/sdb7 and then /dev/sdb8, sdb7 will mount in /media/disk and sdb8 will mount in /media/disk-1, different locations, different music paths for your music players.

---

### Post by bodhi.zazen on 2008-12-16
You can not mount partitions / network shares with the mount command, if they are not in fstab, if you are not root.

You can mount them in other ways, such as pmount, gnome-volume-manager, smbmount, etc.

This line was malformed :

> /dev/sdb5                                  /media/New Volume  ntfs         nls=iso8859-1,umask=000,ro  0  0

First, fstab does not like spaces, so "New Volume" will throw you.

Either re-name the mount point or use

New\040Volume (Yes it is strange, I know).

Second, you are mixing "ro" and "umask" options, just use umask.

Third, if you want ro , you can use ntfs
If you want rw, use ntfs-3g

---

### Post by -kg- on 2008-12-16
> ***I'm afraid I can't do that, Dave.***

And why not, Hal?

***Because you must first give me your password.***

:lolflag:

You were right.  I went in and commented out all the unnecessary lines (first making a back-up, of course) and it all worked as planned.  The only thing was, when I clicked on the first drive to mount it, it asked for my password, and there was a tick box (already ticked) that would remember this answer for the operation.  Another tick box was available (unticked) that would make it only for the session.  Once I entered my password, the other drives would mount and unmount as I wished.  GREAT!

As an inference, I now know that, if I want a certain drive to automatically mount at boot time, I just un-comment the appropriate line in fstab and it will do so.

However, what I was thinking was influenced by information found at [this link:]("http://ubuntuforums.org/showthread.php?t=283131")

> The mount command and fstab go hand in hand:

   1. Options for mount and fstab are similar.
   2. If a device/partition is not listed in fstab ONLY ROOT may mount the device/partition.
   3. Users can mount a removable device using pmount.
   4. Users may mount a device/partition if the device is in fstab with the proper options.


Of course, now that I think about it, when Nautilus initially asked me for a password to perform the operation, I suppose that *did* pass me off to root.  I was just under the impression that the drive(s) wouldn't even show up as available unless they were in fstab.

Like I said; I don't know how fstab got set up as it was.  This is the first time I've ever even looked into fstab (I'm a relative newbie to Linux, though not at all to computers), let alone edited it.  I *am* a bit curious as to how it could have got that way without user (i.e., my) intervention.

Is there software or script commands that might do it?  I thought it might have been an mp3 player, as my original "New Volume" drive was named that, but the partition that was being mounted to that mount point had nothing to do with that drive.

Oh well, live and learn.  The day I stop learning something new is the day they'll be pealing my cold blue fingers off my keyboard!

:lolflag:

---

### Post by -kg- on 2008-12-16
Hi bodhi.zazen...you posted during the time I was typing up my previous reply:

> First, fstab does not like spaces, so "New Volume" will throw you.

Either re-name the mount point or use

New\040Volume (Yes it is strange, I know).

Yes, well, I commented it out and now everything is zen with me. :p

If I want to automount that drive (I won't, but will another) I will uncomment the appropriate line and go from there.  And on the "\040", yes, I know.  I read your tutorials

> Second, you are mixing "ro" and "umask" options, just use umask.

Third, if you want ro , you can use ntfs
If you want rw, use ntfs-3g 

No ***"I"*** am not mixing anything.  I have had absolutely nothing to do with fstab up until today.  That's why I was so confused.  Some software, update, or *something* (and yes, it could have been my fault, but nothing I've done had anything to do with editing /etc/fstab that I know of) modified that fstab file.  I'd really like to find out what, but as long as I know now how to fix it, I'll just keep my eyes open and perhaps catch the culprit in the act.

To use ntfs-3g, how do I set that?  Under Options?  Change the particular line from "Defaults" to what?  Or am I to edit the file type?  I might have missed that (was looking for other information)...I'll re-read the tutorials.

---

### Post by -kg- on 2008-12-16
***BEAUTIOUS!!***  Everything worked as I hoped.

I un-commented the appropriate line (for sdb6 which contains my mp3 files) and changed the file type to "ntfs-3g" (making sure I had the ntfs-3g drivers installed in Synaptics), and that partition auto-mounted.  I then made a test document through Open Office and successfully saved it to and deleted it from that ntfs partition.

While I still would like to know what changed the doggone file in the first place, I guess I should mark this thread as solved.  Thanks to everyone who helped a newbie along, and I have learned a few things in doing all this.

:biggrin: =D>

---

### Post by bodhi.zazen on 2008-12-16
Sweet :)

---

### Post by -kg- on 2008-12-16
Oh, BTW Taurus, I forgot to mention one of your comments.  If you read this again:

> Not sure what you did you your /dev/sdb but you have a bunch of unallocated spaces between partitions.

Notwithstanding the *large* free spaces, which I left intentionally, it seems that often GPartEd will leave small slices of free space between partitions it creates and other partitions that already exist.  I've noticed this any number of times and wondered why that happens.

On my desktop (on which I have around 2 1/2 TB in 4 hard drives; 3 internal and one external) I have created a number of partitions with GPartEd, and I have noticed this propensity over and over.  If I create a partition at the end of a hard drive, there will be a small slice of free memory left, and the only way I can put the partition to the end of the hard drive is to expand the existing partition into it.  Same thing with hard drives created in the middle.

I don't know about the space in front of the first partition (that was created by Vista, if I remember correctly) but when I created the /root partition, I created it to butt up to the first partition, and I got the space.

Same with the space between sbd6 and sbd8.  When creating sdb8 I had it butting up to sdb6, but when finished with the operation I had that small free space between them.  Don't know why, but I suppose as long as it isn't outrageous, I can live with it.  If it gets outrageous, I can either extend or move one of the partitions.

Anyway, as much as I've used GPartEd (both the Ubuntu LiveCD and the GPartEd LiveCD), I'm pretty sure it's a peculiarity of GPartEd.

:-k

---

### Post by -kg- on 2008-12-16
> Sweet 

And BTW, I *love* your avatar!

:grin:

---

### Post by bodhi.zazen on 2008-12-16
> **-kg- said:**
> And BTW, I *love* your avatar!

:grin:

Thanks :redface:

---

### Post by randiroo76073 on 2008-12-16
I'm not sure if this will help, but when you use gparted do you make sure that "space preceeding" & "space following" are zeroed out & do you have "round to cylinders" checked, if so uncheck it.
HTH

---

### Post by -kg- on 2008-12-16
> I'm not sure if this will help, but when you use gparted do you make sure that "space preceeding" & "space following" are zeroed out & do you have "round to cylinders" checked, if so uncheck it.

Now that, I don't know.  Would that be present in GPartEd LiveCD (I suppose it would)?  As far as "space preceeding/following" goes, yes, every time (at least every time I *intend* to zero it out).

bodhi.zazen:  Just a suggestion...from your [How To fstab]("http://ubuntuforums.org/showthread.php?t=283131") tutorial:

> /etc/fstab is a system configuration file and is used to tell the Linux kernel which partitions (file systems) to mount and where on the file system tree.

It might clarify and cause less confusion (like, to me! :p ) if you worded it as such:

> /etc/fstab is a system configuration file and is used to tell the Linux kernel which partitions (file systems) to **_automatically_ **mount **_at boot time_** and where on the file system tree.

and:

> If a device/partition is not listed in fstab ONLY ROOT may mount the device/partition.

might be clarified by adding the very words you used in this post:

> If a device/partition is not listed in fstab ONLY ROOT may mount the device/partition. You can mount them in other ways, such as pmount, gnome-volume-manager, smbmount, (nautilus) etc.

The Community Documentation page, [AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") does not make it clear that the fstab file is for mounting drives at boot time.  I (and many others) am a big dummy and don't draw inferences very well without shoving my nose in it and saying "Look at that sh..." well, without a starting statement of "fstab is a configuration file that Linux uses to automatically mount some or all of the drives (or partitions) on your hard drive AT BOOT TIME.  (Well DU-u-UH!...I say now that I know it!)

:lolflag:

Like I said; some of the documentation needs to be simplified (and clarified) a bit for the newer initiates to Linux (like me) so they can grasp a very basic understanding of what's going on.

I started with computers in the early '80s (before there was Windows...I remember seeing Windows 1.0  on the software shelf) and went through DOS, W-95 (I'll skip 3.X...didn't like it), W98/SE, 2KPro, ME, XP, and Vista.  A few other OSes as well (BeOS, OS2 Warp 4).  Linux is continually throwing me curves, though, and it's a bit rough of a learning (and especially **unlearning**) curve.

I feel the newbie's pain...some (if not most) of them are having a rougher time of it than me, just because they don't have my background.

---

