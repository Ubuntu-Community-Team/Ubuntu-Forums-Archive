---
title: "Undetected files?"
date: 2009-06-19
forum: General Help
---

### Post by qwerty800 on 2009-06-19
Hi!

I actually run on a Fedora live usb!

Here is why!
A week ago, I tried to recover a deleted video on my camera.
I misentered the command and it started recovering my hard drive.

After five minutes (The it took me to realize it), I stopped the operation, and deleted the output *(sudo rm -r /recovery/foremost/*)*.

However (aother five minutes later, I started to see the icons on my pannels dissapear...

As you all know, rm remove the folders in alphabetical order. Most of the icons that I had in my pannels mere located in /home. And before home, there is bin:lol:, boot:-), dev:icon_frown:... 

Let's face it, my system is now lost!
But I sill want to get back some of my files, to keep an archive of my work!

So I took a fedora Live USB that I made some times ago, installed foremost, and ran it!

But what?
Well, after like 4 hours, I got plenty of empty directories, and a 124 MB file telling me that foremost recovered some million of files, which should be in there!

And effectively, the folder weighted 30 GB!

I first tought i hadn't the permissions to see these files, so my first action was to do a *chmod -R 766 /media/recovery*.

And guess what!
There is no more empty folders, no more 124 MB log file, but the folder still weight 30 GB!

So it seems rather evident to me that the files are there, but they're invisible!

Even "ls -al" doesn't show anything!

Would they be a way to see these files?

---

### Post by 123456789123456789123456 on 2009-06-19
the recovered files are where?
flash, or hard disk?

here is what I know, fadora core, and debuian core, linux versions are mostly incompatable, in a lot of ways.

It may have recovered the files, but it may take the Ubuntu live cd to see them
I don't think that fadora core likes ext3, but that is what Ubuntu uses all the time
that may also cause problems

---

### Post by qwerty800 on 2009-06-20
Would that work with a 7.10 live cd?

---

### Post by K.Y.A on 2009-06-20
A bit old, but yes..

---

### Post by qwerty800 on 2009-06-20
Wait!

If fedora can read my original ubuntu drive, and all the files there's in, why couldn't it real the recovery drive made of it?

---

### Post by qwerty800 on 2009-06-21
I'm getting tiered of running on a live USSB, not being able to shut down my computer!

Here, i'm going to overwrite the recovery partition, ant I will try to recover avain, but this time, from a REAL and complete system!

---

### Post by blueridgedog on 2009-06-21
> **123456789123456789123456 said:**
> 
here is what I know, fadora core, and debuian core, linux versions are mostly incompatable, in a lot of ways.

It may have recovered the files, but it may take the Ubuntu live cd to see them
I don't think that fadora core likes ext3

It is safe to say that almost all Linux distros support ext3.  What incompatibilities are you referring to?

---

