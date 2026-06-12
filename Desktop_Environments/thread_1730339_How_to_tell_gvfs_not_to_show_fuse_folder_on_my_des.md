---
title: "How to tell gvfs not to show fuse folder on my desktop"
date: 2011-04-15
forum: Desktop Environments
---

### Post by anatolik on 2011-04-15
I am working on an application that utilizes [libfuse]("http://sourceforge.net/projects/fuse/") library. The application creates a virtual filesystem and runs some commands from there.

The problem is when I mount the filesystem, gvfs (or if to be precise this binary /usr/lib/gvfs/gvfs-gdu-volume-monitor) creates a desktop icon that points to my filesystem.


```
$ gvfs-mount -i -l
Mount(0): 11 -> file:///home/anatol/tmp/fuse/11
  Type: GProxyMount (GProxyVolumeMonitorGdu)
  default_location=file:///home/anatol/tmp/fuse/11
  themed icons:  [drive-harddisk]  [drive]
  can_unmount=1
  can_eject=0
  is_shadowed=0
```


This is not what I really want. My folder (/home/anatol/tmp/fuse/11) is a temporary filesystem that lives several seconds and I don't want to have a link to it from the desktop. How to tell the gvfs not to show it?

You can find a repro case program here [http://sourceforge.net/apps/mediawiki/fuse/index.php?title=Hello_World](http://sourceforge.net/apps/mediawiki/fuse/index.php?title=Hello_World)  just copy the program below and compile it with
$ gcc -Wall `pkg-config fuse --cflags --libs` hello.c -o hello

---

### Post by tiger12506 on 2013-03-27
gconf-editor

key: /apps/nautilus/desktop
value: volumes_visible

Set false
------------------------

I know. Old thread. But I would have been helped if there had been an answer...

---

### Post by wildmanne39 on 2013-03-27
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

