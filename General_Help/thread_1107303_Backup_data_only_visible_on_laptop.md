---
title: "Backup data only visible on laptop ???"
date: 2009-03-26
forum: General Help
---

### Post by Onesimus on 2009-03-26
I have a number of computers all running Ubuntu 8.10.  I periodically backup each of these systems onto an external hard drive (Buffalo DriveStation 500Gb) using grsync.  The partition is formatted at ext3.

I recently had to replace a hard drive in one of the computers due to an imminent failure.  I thought no problem, all I need to do is re-install Ubuntu and copy the files from the external hard drive.  This is where the problems began !

When I attach the external hard drive to this computer it indicates that none of the files are present (just empty directories with size indicated by ? items).  However, it does indicate that 60Gb of space is used up.  If I attach the same external hard drive to my laptop, I can see _all_ the data.  

What gives ???

I did wonder whether it might have something to do with that there are not only different users, but also different no.s of users, on each of the computers.  Is it something to do with UUID and GUID, but I don't really know much beyond that.

Any help would be greatly appreciated !!!

---

### Post by jerrrys on 2009-03-27
you didnt say what backup your using so im guessing....

[http://www.google.com/search?q=simple+backup&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=simple+backup&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by Onesimus on 2009-03-28
I did say.  I was using grsync.

After further inspection, it may be a bug within Nautilus because I could see the files using the command 'ls -l' at the terminal.  I have reported this as a bug and await to see what happens.

---

