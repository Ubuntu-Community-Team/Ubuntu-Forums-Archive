---
title: "Mac formatted iPod Classic??"
date: 2009-05-09
forum: General Help
---

### Post by AntEater on 2009-05-09
I have an iPod classic (160gb) that I've never been able to get to work properly with Linux. I noticed the other day when using iTunes on my Mac that the iPod itself is Mac formatted. Is that a problem when using the iPod with Ubuntu? Do I need to attach it to a PC and have it formatted with iTunes in Windows in order for it to work with Ubuntu?

---

### Post by chriskin on 2009-05-09
> **AntEater said:**
> I have an iPod classic (160gb) that I've never been able to get to work properly with Linux. I noticed the other day when using iTunes on my Mac that the iPod itself is Mac formatted. Is that a problem when using the iPod with Ubuntu? Do I need to attach it to a PC and have it formatted with iTunes in Windows in order for it to work with Ubuntu?

i can't find logic on your idea, but it might be my brain's problem

i finer idea would be , though, to install packages related to mac formatted frives

to be more specific, open Synaptic Package Manager and install all that are found when you search for HFS

---

### Post by Tipped OuT on 2009-05-09
The logic is, to use the Windows version of iTunes, to format his iPod correctly, in hopes it will be compatible with Ubuntu since the Mac format is not working for him.

---

### Post by chriskin on 2009-05-09
> **Tipped OuT said:**
> The logic is, to use the Windows version of iTunes, to format his iPod correctly, in hopes it will be compatible with Ubuntu since the Mac format is not working for him.

if he wants if formatted, he can always format it via gparted on linux, no need to reboot.
and linux has rather good support on hfs drives, once the user installs the packages
that's why i said that i can't understand why formatting would be a solution, mac would be having problems then :P

---

### Post by Tipped OuT on 2009-05-09
It's the noob way (easier way) for him, I'm not saying it makes sense. :P

---

### Post by AntEater on 2009-05-09
> **Tipped OuT said:**
> It's the noob way (easier way) for him, I'm not saying it makes sense. :P

I've been running Linux since 1995 (along with FreeBSD, Solaris, Ultrix, True64, HPUX, Irix, etc.) and only recently have moved from Slackware to Ubuntu.  I'm very well versed in drive partitioning formatting and tweaking filesystem parameters.  I haven't, yet, dug into the details of what Apple does with the file system and database on the ipod.


Noob issues aside, I was only wondering if there were any functional difference with how the various Linux applications deal with reading the ipod when it is formatted hfs instead of fat32.  Apple has been known to do some unusual things at times and didn't know if it mattered when working on Linux.  I do know, at least in the past, that you had to have an initial sync with iTunes to create the initial database on the iPod before attempting to sync with Linux applications.  In addition, Ubuntu has defaulted to mounting hfs+ partitions in read-only mode and didn't know if it would default to that behavior with the ipod as well.  If others are able to successfully sync a Mac formatted iPod with Rhythmbox or Amarok then I have to start looking for another solution to the problems I'm seeing.

---

### Post by AntEater on 2009-05-09
I'm following up on my own thread for the sake of any others that run across this issue.  The "Mac formatted" ipod is journaled HFS+ and mounts in read-only mode by default.  That appears to have been the issue all along. Solution: remove the journaling  (from a Mac) or convert to old hfs or fat32.

---

### Post by Soffia on 2009-07-06
I have been having the same problem with a mac formatted ipod it is coming up as 'read only'.   I tried to turn off journaling in the disk utility on the mac but the ipod doesn't come up as a drive.  How do I then turn off the journaling?

---

### Post by zachthejones on 2009-07-08
I had the exact same issue with my ipod...the problem is the type of formatting used when the ipod is used regularly with a Mac. If you plug the ipod into a windows computer and fire up iTunes it'll detect the ipod and ask if you want to format it to work with that computer. Say "yes" and it'll format it to NTFS (I think that's the format....). Now you can use it with your ubuntu installation.

The problem with using an ipod in Linux is that, while you can use it on multiple linux computers and installations (as long as you don't use iTunes), a windows or mac installation will try to re-format the ipod because iTunes thinks only one installation of iTunes should control an ipod. Irritating and ludicrous.... So stick with linux!!!!

heh heh [here's]("http://linux.zachjones.net/2009/01/15/using-a-5th-gen-ipod-with-amarok-in-ubuntu-read-only-error/") my blog post on my little adventure figuring this out...

---

### Post by Chronon on 2009-07-08
Admittedly, I haven't used an iPod since the 5g at least a couple of years ago.  However, according to my experience with it and successfully docking it to several installations of iTunes, I can tell you that if you manually manage everything and format it to FAT32 (the Windows format) then it should be able to connect to any computer.

---

