---
title: "Mouse Pointer Erratic/Jumpy Few Seconds After Startup..."
date: 2006-07-28
forum: Desktop Environments
---

### Post by eiraku on 2006-07-28
Hey there folks... 

I just moved to using Ubuntu Dapper on my Fujitsu C2220 a week ago. Things worked (extremely) well out of the box, and the few problems (FN+Function key for volume control combination) were quickly ractified... :D 

But now I'm faced with a new problem... After installing the faster-dapper.sh script, it seems that every time, for the first few seconds of movement, my mouse cursor movement is unncontrollable and for the most part too fast to handle... But only for a few seconds, after that its just fine... :sad:

A temporary workaround is moving the mouse a bit at the login screen (where its craziness wont do stuff like moving my panels around, which it does sometimes when I forget to do the login screen movement stuff), and a night's worth of googling were for the most part, fruitless... :confused:

Maybe it has to do with the ALPS touchpad that is present on the C2220, as  the scroll wheel (scroll-buttons actually) is not working as well... 

I also did an install of gcursor to change the mouse cursors before realising that GNOME could do a better job on its own... At which point I uninstalled it...   

It's not really a HUGE issue, but it would save me a whole lot of patience dealling with a crazy pointer after startup... :D 

Any help would be appreciated!

---

### Post by Anduu on 2006-07-28
If i knew what this "faster-dapper.sh" script was all about....I would assume it did something to cause this...

---

### Post by eiraku on 2006-07-29
It's a script by Jeff Schroeder (more info [here]("http://www.dylanknightrogers.com/2006/07/17/faster-dappersh/")) that does:

cfq - The Completely Fair Queuing kernel process scheduler is better at handling high cpu usage that the default noop. In newer kernels and the next version of Ubuntu, cfq is the default.

hdparm - enables IDE hard drive speed tweaks

remove ipv6 - speeds up networking. Especially dns lookups

preload - [http://sourceforge.net/projects/preload](http://sourceforge.net/projects/preload)

prelink - speeds up large binaries

ext3 filesystems - enables dir_index which is known to increase performance in large directories

services - unnecessary services are removed. These slow down the boot process and sit in the background eating CPU / ram unless they are removed :)

gnome tweaks - saves some ram

*These are what the script author actually said, taken from site above*

Any ideas guys?

---

### Post by eiraku on 2006-07-30
More searching, no luck... Not to mention my lappy has been sent for hinge repairs... Maybe it has to do with CFQ?

---

