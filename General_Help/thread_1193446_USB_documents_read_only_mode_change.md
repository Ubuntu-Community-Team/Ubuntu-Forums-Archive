---
title: "USB documents read only mode change?"
date: 2009-06-21
forum: General Help
---

### Post by Camilia on 2009-06-21
Recently had problems with my mouse. Went and bought another one but still couldn't get the mouse to work. Thus booted up with Ubuntu CD.

Found that documents that I dragged from desktop UDisk are in Read only mode.  

Is there a way that I can change the mode of all of the documents in Read only mode?

I deleted pictures and now the documents are in write mode. Perhaps it was full?  Confused for was able to drag a document into UDisk.

---

### Post by quixote on 2009-06-22
The liveCD is read-only, so files you copy from it will be read-only, I think.  You mean that you copied those to a USB drive of some kind?  

Depending on how the USB drive is formatted, that may be causing the problem.  [Here]("http://ubuntuforums.org/showthread.php?t=1031355") it's pointed out that > FAT16 and FAT32 filesystems do not support UNIX permissions. The UNIX permissions which are used are assigned when the filesystem is mounted. So, in other words, right click on the USB drive, select unmount, pull it out, and put it back in again.  File permissions should be magically fixed.

Perhaps that's what you meant when you said that the second time around things were suddenly in write mode?  If you remounted in the interim, that's what you'd expect.

If this doesn't work, ask again.  There are command line ways to get at permissions, but they're a bit more complex.

---

### Post by Camilia on 2009-06-23
> **quixote said:**
> The liveCD is read-only, so files you copy from it will be read-only, I think.  You mean that you copied those to a USB drive of some kind?  

Didn't copy files from a live CD.

> **quixote said:**
> 
Right click on the USB drive, select unmount, pull it out, and put it back in again.  File permissions should be magically fixed. 

Tried that and it didn't fix things.

What I did was delete many pictures. Then next time I opened the USB drive I found that the documents were in write mode.

---

### Post by rushikesh988 on 2009-06-23
I think you should try typing "sudo nautilus" in terminal and brouse filesysytem as root

---

### Post by quixote on 2009-06-23
So let me see if I understand this:
> Found that documents that I dragged from desktop UDisk are in Read only mode.
By UDisk you mean USB drive?  I thought you must mean the desktop of your Ubuntu CD.  Do you want to change these to writable?  

> Is there a way that I can change the mode of all of the documents in Read only mode?The short answer is yes, but you need to be specific about what you want.  In Linux you have 3 modes, readable, writable, and executable, and three different classes of users (owner, group, and everybody) can have any combination of those modes.  

> I deleted pictures and now the documents are in write mode. Perhaps it was full? Confused for was able to drag a document into UDisk.
 Do you want to change the docs that are left to read-only?  These files are on the USB drive, right?  Are you just trying to understand what happened?  If the latter, did you unmount and remount the USB drive?

rushikesh988's suggestion to use nautilus in sudo mode (=root, =admin) might solve the issues for you, but be very careful.  As sudo you can make changes that will leave your system unbootable. Also, because of the way it handles paths, gksudo is usually used:```
gksudo nautilus
```

---

### Post by Camilia on 2009-06-23
> **quixote said:**
> Are you just trying to understand what happened?  If the latter, did you unmount and remount the USB drive?


Just wanted to let all know that I had solved the problem.

There were times that I did just pull the flash drive out. It shows UDisk. Perhaps that is what caused the problem. I shant do that anymore.

Wish I would get as good response as I did to this thread I am having with thread on my printer. I can't it to print with the new black cartridge. I am thinking of restarting to get it try to get it to work.

---

### Post by quixote on 2009-06-23
> There were times that I did just pull the flash drive out.

Eep.  Never, ever pull an SD card, USB drive, or anything like that out without unmounting first.  I found out the hard way with an 8GB SDcard that I turned into a 4.5GB SDcard by doing that.  It so totally messed up the low level formatting, even reformatting didn't get the lost space back.  Forget the data!

Glad to hear things are sorted out.

---

