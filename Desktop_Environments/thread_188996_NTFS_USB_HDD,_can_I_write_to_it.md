---
title: "NTFS USB HDD, can I write to it?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by dmorel on 2006-06-04
So I have this big old USB Hard Disk Drive that I use to store media on. It mounts when I boot and I can access files on it no problem. 

Using SAMBA I have shares set up on it so that my xbox media center can access it on the network and play whatever...

However, I can't write anything to it, as it is a "read only disk." nor can I change the permissions on the disk itself.

Any pointers on how I can make this disk writable from ubuntu?
tia
-morel

---

### Post by amdfreak on 2006-06-04
Are you sure you want do to this? I realize that I may be a newbie in the Ubuntu world, but I do know that writing to USB disks in Linux is usually not a good idea. Can you create a FAT32 partition on your USB disk? I know that Linux will write to a FAT32 partition if configured correctly. Again, I'm not really that experienced so don't take my word as gospel, but this much I do know.

---

### Post by dmorel on 2006-06-04
I definately *want* to do this, yes... can I do it, and should I do it... well that may be another matter ;)

I've read a bit about fuse, but it seems flakey with USB drives, rather then internal HDD's, so  I was hoping someone might have a better suggestion for me.

thanks for your thoughts!
-morel

---

### Post by xFera on 2006-06-04
Sorry but nowadays you **can't** write on any NTFS partitions, wherever are they phisically installed. If you need to write on it, and share files safely with windows, you better have to migrate it to a FAT32.

---

### Post by DrBair on 2006-06-04
The lastest and greatest from the linux-ntfs project, writing is getting pretty good. The biggest limitation is that you can only make 8 files in a new directory before it starts yelling at you. Good news is that it hasn't clobbered any NTFS filesystems yet!

---

### Post by frying_fish on 2006-06-04
If you want to interact with it in windows and still have write capability in both, (and go beyond the 4GB file size limit for FAT32) then use ext3.  and head over to [http://www.fs-driver.org/](http://www.fs-driver.org/)  to attain a windows driver so that you can read/ write to it in windows.  Yes this will mean you have to format it, but, if you can back the data up onto another partition first then do so and you won't lose anything.

---

### Post by chaumurky on 2006-06-04
[quote=dmorel]So I have this big old USB Hard Disk Drive that I use to store media on. It mounts when I boot and I can access files on it no problem. 
 
Using SAMBA I have shares set up on it so that my xbox media center can access it on the network and play whatever...
 
However, I can't write anything to it, as it is a "read only disk." nor can I change the permissions on the disk itself.
 
Any pointers on how I can make this disk writable from ubuntu?
tia
-morel[/quote]
 
Have a look at fuse.
 
[http://ubuntuforums.org/showthread.php?t=142481]("http://ubuntuforums.org/showthread.php?t=142481")

---

### Post by dmorel on 2006-06-04
Chaumurky, thanks but from above...
> I've read a bit about fuse, but it seems flakey with USB drives, rather then internal HDD's, so I was hoping someone might have a better suggestion for me.

Fish, 
thanks... probably you're correct that the best way for me to go is to reformat the disk. Moving 270 gigs of stuff off it is the problem, I don't have anywhere to put it! ;) I'm sure I'll come up with something...

DrBair,
Anything in particular you can point me towards?

xFera,
I don't think you are correct about that.

thanks.
-morel

---

### Post by chaumurky on 2006-06-05
[quote=dmorel]Chaumurky, thanks but from above...
 
 
Fish, 
thanks... probably you're correct that the best way for me to go is to reformat the disk. Moving 270 gigs of stuff off it is the problem, I don't have anywhere to put it! ;) I'm sure I'll come up with something...
 
DrBair,
Anything in particular you can point me towards?
 
xFera,
I don't think you are correct about that.
 
thanks.
-morel[/quote]
 
Whoops, sorry about that. I should have looked more closely. :roll:

---

### Post by chaumurky on 2006-06-05
(double post)

---

