---
title: "DVD freeze"
date: 2005-04-23
forum: Desktop Environments
---

### Post by IdoMcFly on 2005-04-23
On one DVD, I have xine or vlc freeze on a precise time. I can't see any scratch on the DVD but maybe it is the disc. Is there anyway to make the player just drop the corrupt frames and go on ?

---

### Post by heimo on 2005-04-23
This is not a solution to your problem, but something you may be interested of. There's a great tool called dvdbackup. If your DVD drive is /dev/hda, you'll give this command:
dvdbackup -i /dev/hda -o . -M

And it'll dump the DVD to current folder. Then you can play the DVD's from hard disk. Typically DVDs take 3-7 GB space.

Sometimes it makes easier to find what's wrong if you start the player from terminal. That way you may get some errors on the screen when the hangup occurs.

---

### Post by IdoMcFly on 2005-04-25
thank you very much, I'll try these this evening

---

### Post by heimo on 2005-04-25
With dvdbackup you'll get video object files (and some other files) VOB - those are not chapters of the disc, but you can select relevant VOBS to playlist (totem, vlc..) and you can actually skip the irrelevant parts of disc (warning texts at the beginning).

I'm not really into DVD's, so there may be better tools - dvdshrink is one that comes to my mind, but I haven't tried it - to convert, strip unused tracks and things like that. Some flags do exists for the dvdbackup too, but those -i -o -M were the ones I used. *dvdbackup --help* and man *dvdbackup *may be useful.

Thanks!

---

