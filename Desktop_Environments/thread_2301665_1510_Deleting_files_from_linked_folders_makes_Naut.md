---
title: "15:10: Deleting files from linked folders makes Nautilus crash"
date: 2015-11-04
forum: Desktop Environments
---

### Post by dlalonde2 on 2015-11-04
I have a habit, on every version of Ubuntu or on Windows, to keep all my files on a seperate partition and then I link them to my home folder. But on 15.10, when I delete a file from those folders, it crashes Nautilus. Then, when I restart Nautilus and try to delete the file again, I get a message that says that it cannot be move to trash and if I want to delete it permanently.

Anyone have this problem? How can I solve it?

---

### Post by ajgreeny on 2015-11-04
Is the separate partition on the same internal disk or is it on an external disk?  Is the partition auto mounted at bootup or session start?

---

### Post by flocculant on 2015-11-04
there were a few gvfs bugs cropped up during the 15.10 dev cycle - I do remember seeing something like this

[lpbug]1497918[/lpbug]

was reported against thunar - but it's entirely possible that it should be gvfs related instead

Maybe [https://bugzilla.gnome.org/show_bug.cgi?id=743739](https://bugzilla.gnome.org/show_bug.cgi?id=743739)

[nautilus bugs by date ]("https://bugzilla.gnome.org/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&field0-0-0=product&field1-0-0=product&field1-0-1=component&field1-0-2=alias&field1-0-3=short_desc&field1-0-4=status_whiteboard&field1-0-5=content&order=changeddate%20DESC%2Cpriority%2Cbug_severity&query_based_on=&query_format=advanced&type0-0-0=substring&type1-0-0=substring&type1-0-1=substring&type1-0-2=substring&type1-0-3=substring&type1-0-4=substring&type1-0-5=matches&value0-0-0=nautilus&value1-0-0=trash&value1-0-1=trash&value1-0-2=trash&value1-0-3=trash&value1-0-4=trash&value1-0-5=%22trash%22")

---

### Post by dlalonde2 on 2015-11-04
> **ajgreeny said:**
> Is the separate partition on the same internal disk or is it on an external disk?  Is the partition auto mounted at bootup or session start?

All on the same internal disk. I only have one disk with multiple partitions. It's automounted at bootup in fstab.

> **flocculant said:**
> there were a few gvfs bugs cropped up during the 15.10 dev cycle - I do remember seeing something like this

[lpbug]1497918[/lpbug]

was reported against thunar - but it's entirely possible that it should be gvfs related instead

Maybe [https://bugzilla.gnome.org/show_bug.cgi?id=743739](https://bugzilla.gnome.org/show_bug.cgi?id=743739)

[nautilus bugs by date ]("https://bugzilla.gnome.org/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&field0-0-0=product&field1-0-0=product&field1-0-1=component&field1-0-2=alias&field1-0-3=short_desc&field1-0-4=status_whiteboard&field1-0-5=content&order=changeddate%20DESC%2Cpriority%2Cbug_severity&query_based_on=&query_format=advanced&type0-0-0=substring&type1-0-0=substring&type1-0-1=substring&type1-0-2=substring&type1-0-3=substring&type1-0-4=substring&type1-0-5=matches&value0-0-0=nautilus&value1-0-0=trash&value1-0-1=trash&value1-0-2=trash&value1-0-3=trash&value1-0-4=trash&value1-0-5=%22trash%22")

It looks like it's a similar bug. I've tried recreating the .Trash folder as well to no avail. Hope this gets solved soon!

---

### Post by dlalonde2 on 2015-11-04
mmm I just noticed the bug also occurs on 15.04. It doesn't seem to be the case if the link comes from the same partition though.

---

### Post by ELD on 2016-02-12
Was there any progress on this, it's quite annoying.

Nemo also has the same issue, so it's certainly not just Nautilus.

---

### Post by praetervictum on 2016-02-22
I'm on 15.10, also experiencing this issue - whenever I try do delete a file in Nautilus (select, hit Delete key), Nautilus just quits. Some finer points of my experience that I hope will help: 
[LIST=1]
[*]The problematic folders - Documents, Music, Video - are mapped to ones on a separate, NTFS drive, mounted at boot with the following line in fstab:
[LIST=1]
[*]UUID=XXXXXXXXXXX /media/james/ds4tbr ntfs-3g defaults,uid=1000 0 0
[/LIST]

[*]The problem only occurs if I try to delete a file from one of these three folders.  I didn't remap the Downloads symlink, so it points to the default location of /home/james/downloads on my boot drive, and Nautilus works as expected, there.
[*]Within those three problematic folders, I can still delete files in subfolders (so /Documents/test/test.txt == good, while /Documents/test.txt == bad).
[*]I can also create and delete new folders without a problem.
[/LIST]

I tailed syslog while I recreated the problem, and this is the entry the pops up: 

```
Feb 22 01:06:04 unit0 org.gnome.Nautilus[1507]: *** Error in `/usr/bin/nautilus': double free or corruption (fasttop): 0x00007f9d1002e420 ***

```
Searching around, I don't see any specific mention of this bug.  
There are a number of links on [http://reqorts.qa.ubuntu.com/reports/launchpad-database/bugs-with-most-users-affected.html](http://reqorts.qa.ubuntu.com/reports/launchpad-database/bugs-with-most-users-affected.html), 
but none of them mention Nautilus, and the dates of these bugs are all over the place (some as old as 2007 - Ubuntu 9.04).

---

### Post by praetervictum on 2016-02-22
Aaaaaaaand I just found the following: 

[https://www.mail-archive.com/desktop-packages@lists.launchpad.net/msg428055.html](https://www.mail-archive.com/desktop-packages@lists.launchpad.net/msg428055.html)

The exact error named here appears in my syslog just above the message I quoted.  This appears to be the same bug. 

I guess we just have to wait for the fix.

---

