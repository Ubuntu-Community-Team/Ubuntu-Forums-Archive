---
title: "Do backup on mount?"
date: 2009-03-10
forum: General Help
---

### Post by Rackstar on 2009-03-10
Hey,

I've been using Ubuntu for a while now, and I'm very fond of it. I bought a new USB drive and want to use it as a TimeMachine drive like in mac.

I know ubuntu has TimeVault, FlyBack, SBackup... But how do I get it to backup on mount? TimeMachine (in mac) recognizes the drive, automatically starts to backup.

I hope there is an easy way. Or it would be a good idea to put this in further releases.

If there is a hard way, but a good one, don't hesitate to help me :)

I don't know if this is in the right forum, but I didn't found any other.

Thanks!

---

### Post by Rackstar on 2009-03-11
Does anyone have an idea if this IS actually possible? I have searched the web, but I'm running out of keywords.

It would suprise me if I would be the first one to want to do something like that.

Any help would be hugely apreciated.

---

### Post by keithweddell on 2009-03-11
You need to search for udev - there are a number of threads on this site.  I can't find the one I was looking for which had quite a well developed solution.  But you can probably find it if you search on a variations of udev, backup & udev.

Keith

---

### Post by vanadium on 2009-03-11
> If there is a hard way, but a good one, don't hesitate to help me 
That is always there in Linux. Here is what seems to be a very good thread on how it generally works. [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

---

### Post by Rackstar on 2009-03-11
Thank you very much the udev-hint! I believe this is going to be necessary. 

But I still wonder: how do I start a TimeVault snapshot (or any other backup script for that matter) when I plug my USBdrive in?

Thanks!

---

### Post by Rackstar on 2009-03-11
Sorry: I missed the RUN argument of udev

[http://reactivated.net/writing_udev_rules.html#external-run](http://reactivated.net/writing_udev_rules.html#external-run)

I will try this out in a couple of hours and let you all know how it went.

Thanks for pointing this out for me.

---

### Post by Rackstar on 2009-03-11
Sorry, but does anybody know the command to run a snapshot with TimeVault? I searched the web, but I did not found it.

Thanks in advance!

---

