---
title: "My mouse has gone insane..."
date: 2007-05-08
forum: Desktop Environments
---

### Post by j0ney3 on 2007-05-08
I'm really at my wits end here, I've never come across a problem like this that I couldn't find any info about.  About two weeks ago, my mouse just started to automatically grab and/or move everything it hovered over.  I was seeing tons of "MARK" logs in syslog and it is automatically copy n pasting things into firefox and my terminals, also going back pages, etc.  So, of course, I swapped out my mouse...it didn't help, so I tried yet another mouse, nothing.  I tried booting into windows and everything is fine.  I can't seem to find any oddities in dmesg or syslog to indicate the nature of this problem, I've tried 3 different mice, all to no avail.  I really don't want to wipe my machine, any help would be much appreciated.

Thanks in advance

---

### Post by WNDS1701 on 2007-05-08
Hello!


I don't have a tip to really solve the problem, but do you have an extra partition for your /home directory? If you do, then you can wipe your machine and your settings won't be gone because they are saved int /home/username. Perhaps this will ease your pain faster than searching for a bug that nobody here has had. If you don't have one, simple use GParted, create a partition, copy all the stuff there and then give it a new start from scratch. If you experience that problem again, perhaps it would be useful to post some more details about your machine so that somebody can go into it more deeply.


All the best and good luck!

---

### Post by j0ney3 on 2007-05-09
Yeah, good point about the settings, I suppose I could do the same w/ my xorg as well.  I'm not giving up hope yet though.

---

### Post by j0ney3 on 2007-06-01
I hate to make myself look like an idiot but I'm posting this for the benefit of any other who may share my fate.  My mouse was bad!  I didn't think it possible b/c I unplugged it and the symptoms were still occurring, however, when I unplugged it, plugged in a new mouse and rebooted my machine all was back to normal. :)

---

