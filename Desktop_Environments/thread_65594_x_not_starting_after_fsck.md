---
title: "x not starting after fsck"
date: 2005-09-14
forum: Desktop Environments
---

### Post by jennhi on 2005-09-14
Hello all!

I'm running Kubuntu on an Intel system, and I play Stepmania -- installed with a few snags but runs like a charm most of the time. Once it froze up for more than 30 seconds, so after unsuccessfully trying to close it, I tried to restart X without luck; X wouldn't restart after closing (it said to contact the admin -- whoops, that's me). So I tried to restart the computer, and it came up with a kernel panic.

With a heavy sigh, I attempted to reinstall Kubuntu without formatting anything, and it came back with all of these read-only filesystem errors. After reading [this](http://ubuntuforums.org/showthread.php?t=65443) thread, I ran fsck using the live disk and fixed up hda1. Now Kubuntu starts up without panicking but it won't run X; and a lot of other things during startup "failed". Tried reinstalling again, which it won't (something to do with not liking the partitions, even though they're all ext3), unless I decide to format the drive again, and I don't want to lose any valuable information (again).

The question is, is there any saving this without having to wipe the drives again and rebuild? Can I submit any information to you guys that can be retrieved off the 
logs? I'm fairly sure this has come up in other forums too, but I have no idea what keywords to search for.

Any information would be of great assistance!
Thanks!
jennHi

---

### Post by zAo on 2005-09-14
First try
```
dmesg | tail -50
```

---

### Post by jennhi on 2005-09-14
Do I do this using the Live CD or logging in regular? If I log in regular, how can I get it to output to a file?

Thanks!
jennHi

---

### Post by cwaldbieser on 2005-09-14
[QUOTE=jennhi]Do I do this using the Live CD or logging in regular? If I log in regular, how can I get it to output to a file?

Thanks!
jennHi[/QUOTE]

```
dmesg | tail -50 > log.txt
```
will put the data in a file.

---

### Post by jennhi on 2005-09-14
[QUOTE=cwaldbieser]```
dmesg | tail -50 > log.txt
```
will put the data in a file.[/QUOTE]
 thanks -- I will do that this evening and report back in the morning!

---

### Post by mlomker on 2005-09-14
[QUOTE=jennhi]of other things during startup "failed". Tried reinstalling again, which it won't (something to do with not liking the partitions, even though they're all ext3), unless I decide to format the drive again, and I don't want to lose any valuable information (again).
[/QUOTE]

I'm not crazy about the default pick of two partitions.  If you ever do decide to format then I'd strongly recommend manually partitioning your system so that /home is on its own partition.  That would allow you to reinstall the operating system without losing *too* much stuff.

---

### Post by jennhi on 2005-09-14
[QUOTE=mlomker]I'm not crazy about the default pick of two partitions.  If you ever do decide to format then I'd strongly recommend manually partitioning your system so that /home is on its own partition.  That would allow you to reinstall the operating system without losing *too* much stuff.[/QUOTE]
 Ironically, that is my setup. /home is mounted on another partition and /tmp is another one. / is mounted on hda1. I don't want to lose any of these partitions if I can help it.

---

### Post by jennhi on 2005-09-14
[QUOTE=cwaldbieser]```
dmesg | tail -50 > log.txt
```
will put the data in a file.[/QUOTE]
 I was unable to get access, even using "sudo". I did get a long output of dmesg without outputting to a file, but every time I tried to output to a file, it would only say "permission denied". Unfortunately, I don't know of a way to create a new file (in case it just doesn't work unless the file exists), and emacs does not seem to be installed (being the only non-X text editor I know of) and does not appear to be in the apt-get databases, so I'm stuck. Does anyone know how to get to this info using the Live CD or another way to get to this info? 

Thanks!
jennHi

---

### Post by mlomker on 2005-09-15
Yup.  Dmesg is a just a fancy way of looking at the contents for the last boot-up in /var/log/kernel.log.  Grab the last few pages in there.

---

### Post by jennhi on 2005-09-15
This system appears determined to thwart my every move. I've tried to mount the partition while running the Live CD using "sudo mount /dev/hda1 /media/linux", which worked after running fsck on hda1 a second time. Unfortunately, it gave me an I/O error after trying to open up kern.log in gedit, or trying to copy it to the desktop. Is there hope?

---

### Post by mlomker on 2005-09-16
[QUOTE=jennhi]Is there hope?[/QUOTE]

Sounds like a hard disk failure.  You shouldn't get errors like that after fsck.

I'd probably try reinstalling the operating system to see if it can complete or not.  If you get IO errors after a reformat then you need a new disk.

---

### Post by jennhi on 2005-09-16
Yeah, that does sound like the only way to go at this point. It won't install over the existing system, so I'll have to wipe that partition and start over; hopefully it won't also insist that the /home partition also be wiped.

It's also probably time to get a new drive, but that's not for another month, probably. Thanks for the help! I'll post to this thread if it doesn't work.

---

