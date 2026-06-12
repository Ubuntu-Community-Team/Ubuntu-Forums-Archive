---
title: "Hard drive appears to be full, can't work out why"
date: 2009-01-16
forum: General Help
---

### Post by infinitejones on 2009-01-16
GParted and System Monitor are telling me that my /dev/sda2 (which contains everything except /home and /boot) is 99% full. It's a 75GB partition and the free space is currently only about 30MB, apparently. See attached screenshots. This is causing problems, obviously.

[IMG]http://www.m3l.org.uk/gparted.sm.png[/IMG]
[IMG]http://www.m3l.org.uk/sysmon.sm.png[/IMG]

However, Disk Usage Analyzer doesn't/can't tell me why the partition is appearing to be full. Screenshot of this attached too.

[IMG]http://www.m3l.org.uk/analyzer.sm.png[/IMG]

I'll re-iterate - /home is on a separate partition, so even though that's showing 30.2GB, that data isn't on the partition that's 99% full. The total of everything else (/usr, /var, /lib etc) isn't much more than 3GB.

So why does Ubuntu think that /dev/sda2 has 74GB of data on it? Is it a disk fault? Obviously re-formatting and re-installing is one solution, but is there another to find out what's filling it up and how to clear it?

---

### Post by taurus on 2009-01-16
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by drs305 on 2009-01-16
The linked post below discusses ways the disk can fill up unexpectedly. Common causes are undeleted trash in either the user's or root's trash bins, backup files mistakenly placed in the wrong directory, large numbers of package files in /var/cache/apt/archives, large log files, or a partition than is smaller than expected.

The tutorial explains how to find and clean up many of these problems.

I currently am unable to edit the tutorial, but am trying to add a section which discusses backups which are mistakenly written to a folder (usually a subfolder of /media) instead of to another device which would normally be mounted in /media. If you unmount all your external and/or additional devices ( sudo umount -a ) and find you still have large files in /media or a subfolder, this might be the cause.

Here is the link I mentioned earlier:
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by ajcham on 2009-01-16
I'm not sure of the cause of the problem - as Baobab (Disk Usage Analyzer) indicates, the used space reported by System Monitor etc. is not actually being used at all, unless there are some other files that can't be seen when running Baobab as a user.  Maybe running it as root will identify the used space. I doubt it'll help, but it's worth a shot:
```
gksu baobab
```

drs305's advice, above, is probably more useful, but my gut instinct is that 70GB is a lot of space to be explained in this way.

My real reason for posting however, was just a small aside for future reference - you are letting a lot of drive space go to waste on oversized partitions. / certainly doesn't need to be any larger than 20GB, and even that is a significant overestimate.  10GB - 15GB  should be more than adequate for most users.

Also /boot is far too large - this could have been set at 512MB quite comfortably.  Unless you come to the point where you absolutely need the extra space I wouldn't bother repartitioning, but should you ever perform a reinstallation you can free up an extra 60GB or so for your /home partition.

---

### Post by infinitejones on 2009-01-17
Thanks for all your replies! I worked out what was happening - I was using sbackup and I'd set it up to backup to an NFS mount on an external server, but it wasn't mounting properly so all the backups were being saved locally. Third paragraph of drs305's post, in actual fact!

No idea why it wasn't showing up in baobab but I've deleted all the locally saved backups and the problem's gone. Thanks again everyone.

---

### Post by dcstar on 2009-01-17
> **infinitejones said:**
> 
.........
No idea why it wasn't showing up in baobab but I've deleted all the locally saved backups and the problem's gone. Thanks again everyone.

Files that are readable by root only - like backups - will not be "seen" by any user run program.

If you did: "sudo baobab" they would show up.

---

