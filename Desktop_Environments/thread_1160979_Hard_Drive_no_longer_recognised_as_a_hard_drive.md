---
title: "Hard Drive no longer recognised as a hard drive"
date: 2009-05-16
forum: Desktop Environments
---

### Post by MadnessRed on 2009-05-16
I was trying to make a hard-drive mount on startup using the quides on this thread.

[http://ubuntuforums.org/showthread.php?t=948972](http://ubuntuforums.org/showthread.php?t=948972)

problem is that whilst the drive is not mounted to a folder, it is not listed as a Hard Drisk drive in "Computer"

How can I get it back?

---

### Post by ajgreeny on 2009-05-16
What file system is the drive formatted to?
Also did you use the ntfs-3g package shown in the other thread as a possible answer?

In fact, in spite of your comment, I think the drive **must** be mounted to a folder somewhere in your filesystem in order for you to see it and work with it.  However, it may not show up as a separate partition or drive in Places, but it should still be available if you navigate to the correct place in your filesystem.

I think it may be necessary to mount it to /media in order for it to show as a separate drive.

---

### Post by MadnessRed on 2009-05-16
> **ajgreeny said:**
> What file system is the drive formatted to?
Also did you use the ntfs-3g package shown in the other thread as a possible answer?

In fact, in spite of your comment, I think the drive **must** be mounted to a folder somewhere in your filesystem in order for you to see it and work with it.  However, it may not show up as a separate partition or drive in Places, but it should still be available if you navigate to the correct place in your filesystem.

I think it may be necessary to mount it to /media in order for it to show as a separate drive.

sorry, yes ignore the must.
I meant to say it was :/ I set the etc/fstab to mount is to /media/DATA. And I could get it via browsing to /media/DATA but it was not showing up under Computer or the Places menu.

I removed it from fstab and restarted and it is back though, is there an alternative way to do it, like add "mound dev/sda3" to the startup processes.

It just a bit annoying having to open the hard drive, just to listen to music for example, I would rather the hard drive was already mounted.

---

### Post by MadnessRed on 2009-05-16
> **yamtech said:**
> Reconnect it and try it. Some time it shows due to virus.

I have it back how it was now, just by removing line from fstab, I want to know if there are any other ways to mount it on startup

---

