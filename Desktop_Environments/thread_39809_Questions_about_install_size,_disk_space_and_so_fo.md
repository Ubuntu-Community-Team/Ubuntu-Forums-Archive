---
title: "Questions about install size, disk space and so forth..."
date: 2005-06-06
forum: Desktop Environments
---

### Post by SpiderMagico on 2005-06-06
I did a quick search for this; it yielded nothing very useful.

First:  What is the install size of the defualt Ubuntu 5.04 installation?

Second:  Using nautilus and the terminal, I've checked out my free space, but it doesn't seems to be right by a long shot.  An easy example of this is my MUVO flashstick [128].  It has nothing on it whatsoever (as ls reports, and also my Muvo player as well), but the freespace reads as only ~ 85 mb.  At one point, I did have some mp3's on there that have since been deleted.  During that time, only ~85 mb remaining was probably correct.  What pisses me off is that I even though there is not data on the flashstick, I can only write to the ~ 85mb that Ubunutu thinks is remaining.

Note :  I am not a jackass to the flashstick; I always unmount properly, wait a few seconds, and so forth.  I don't think I've damaged it.

I wonder if this is happening to my harddisk, and that really pisses me off.

Any ideas about what's happening, or more importantly, how to fix this?

---

### Post by shakin on 2005-06-06
can you post the results of these three commands
```

$ df -h
$ cat /etc/fstab
$ fdisk -l

```
And also post what your drive sizes should be (for each drive in 'fdisk -l').

---

### Post by az on 2005-06-06
Hoary takes up about 2 gigs of hard drive space.

When you delete stuff from nautilus it puts it into the trash.  In this case there is a hidden .trash folder on your usb stick.  Change the settings to display hiddel foles and you shold be able to delete the deleted files.

It is not a bug, it is a feature.

You can change the gnome settings to make nautilus show a delete option as well as the send to trash,,,

---

### Post by SpiderMagico on 2005-06-06
To clarify - I know what a hidden folder is and how to find it.  When I stated that there was no data on the flashstick, I meant it.

It appears to have been something more serious.  My machine just died.

I'd appreciate it if the thread was closed; I can't seem to find a way to do so myself.

---

