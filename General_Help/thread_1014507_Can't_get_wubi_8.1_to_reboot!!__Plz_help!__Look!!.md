---
title: "Can't get wubi 8.1 to reboot!!  Plz help!  Look!!"
date: 2008-12-17
forum: General Help
---

### Post by teddyearp on 2008-12-17
When I installed Ubuntu 8.1 via wubi, when it's done and reboots, all I get is a "Booting GRLDR" message, like forever.  I waited and waited, but that's all I get.  Then all I can do is shut off my comp.  Now I'm skeered to to anything with it at all.  Any help???

PLEASE??!!

---

### Post by Jammanuser on 2008-12-17
> **teddyearp said:**
> When I installed Ubuntu 8.1 via wubi, when it's done and reboots, all I get is a "Booting GRLDR" message, like forever.  I waited and waited, but that's all I get.  Then all I can do is shut off my comp.  Now I'm skeered to to anything with it at all.  Any help???

PLEASE??!!

Don't use 8.1...use 8.10. Download and install from [this link]("http://www.wubi-installer.org/")

Hope this helps! ):P

Jam Man

:guitar:

---

### Post by magmon on 2008-12-17
> **Jammanuser said:**
> Don't use 8.1...use 8.10. Download and install from [this link]("http://www.wubi-installer.org/")

Hope this helps! ):P

Jam Man

:guitar:

8.1 is 8.10...

---

### Post by Jammanuser on 2008-12-17
> **magmon said:**
> 8.1 is 8.10...

yeah...i know! :D i was just #1 trying to make a joke, and #2 giving the link to the **official** wubi-installer, just in case he downloaded it from somewhere else, or used the LiveCD...;)

Cheers! ):P

Jam man

:guitar:

---

### Post by teddyearp on 2008-12-18
Well, thanks for the replies, folks.  Just so you know, I did d/l the proper WUBI from the official site.  The first time, with my Pent D805 (dual core), it d/l the 64bit version of Ubuntu.  So, I tried it after d/l the proper Ubuntu i386 file, but the results I got were as I posted.

I already posted this self same problem in another thread, but nobody replied.  Why?  I don't know.:confused:  But it's been my experience _here_ that the thread titles that are like this one, and without much technical information within the post, get the most results.  Go ahead and flame me, or ban me, or whatever, but when I posted this problem with all the details in this thread here, it went unanswered without ANY replies:

[http://ubuntuforums.org/showthread.php?t=1013410](http://ubuntuforums.org/showthread.php?t=1013410)

So, although I do appreciate the joke, IMHO the joke is on you folks.  And now, it's a moot point, since I used the 8.04, did all the updates, then upgraded to 8.1 anyways.  In my original post linked above, I was just hoping to not have to go through all that time and trouble, but. . .  So be it and so it is.

At least if that's the way you folks want to deal with user's problems here.  Next time, I'll just post again as a total n00b.

Thanks.

---

### Post by ago on 2008-12-19
Press the insert key rapidly when grub4dos start to get a more verbose output
It might be that the drive where you installed is not accessible at boot time (it may happen with raids, external disks or encrypted disks).

---

### Post by wwarren on 2008-12-22
I also had the problem where it hangs at "Booting GRLDR". I had a FAT32 formatted USB hard drive plugged in and it seemed to be trying to read from it. Unplugging that drive fixed the problem entirely. I then investigated what was on the drive and found a folder called "System" that had Western Digital files on it including an autorun. I erased that folder and Wubi booted fine every time. At least up until I added another USB drive formatted as NTFS. Now its getting stuck again as it tries to access this new drive and there's nothing on this drive but data.

---

