---
title: "Rescue of an EXT4 drive"
date: 2009-04-10
forum: General Help
---

### Post by sirschuster on 2009-04-10
Long story short, it seems that I think I managed to corrupt the kernal, here's the error I get when I attempt to boot.

> Starting up
... ACPI aborted because of invalid compression format (err=1)
... RAMDISK: ran out of compressed data
Invalid compressed format
... Kernal Panic - not syncing: VFS: Unable to mount root fs on unknown block (0/0)

I have one file I want to grab before i clear the system (all others are backed up), only problem is that since I'm using a EXT4 fs my usual USB method of recovery is a no go, and the Ubuntu disk just installs and wont run live. I tried systemrescue but without a graphical file manager I'm mostly ineffective.

So.... any tips on how I can get in there and rescue my file or correct this error?

Thanks so much!):P

---

### Post by zephyrcat on 2009-04-10
Go ahead and pull out System Rescue CD again, since that will probably be the easiest way.

Open up a terminal from there and then mount the partition. In order to do this, you will run a command something like this:

mount /dev/hda /mnt/myfiles

The /mnt/myfiles part can pretty much be whatever you like,  but using /mnt is conventional. The /dev/sda part refers to the partition itself. Most likely it will be /dev/hda, but it might also be something like /dev/sda or /dev/hda1. 

For more information on mounting, see here:

[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

After you mount the partition, type cd /mnt/myfiles or whatever you choose.

Finally, type cp /home/username/file.txt /location/where/you/want/to/copy/file/to

Hope that gives you a general idea of what you need to do. Good luck.

---

### Post by sirschuster on 2009-04-11
Thanks zephyr, that worked out perfectly for me. I appreciate the help.

Is there a way for me to mark this posting as solved now?

---

