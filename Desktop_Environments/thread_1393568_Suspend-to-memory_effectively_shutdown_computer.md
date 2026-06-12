---
title: "Suspend-to-memory effectively shutdown computer"
date: 2010-01-29
forum: Desktop Environments
---

### Post by ApocryphalAuthor on 2010-01-29
I am running a fairly new installation of Ubuntu Karmic 9.10 on a custom built desktop computer.  When my computer suspends (either automatically under power management or manually) everything appears go OK:  the screen goes black and the power LED blinks slowly; however, I cannot wake the computer up by moving the mouse or pressing keys, and when I press the power button, the computer starts up immediately, goes to GRUB, and start up (with now visible error messages or warnings) as if the computer was shutdown instead of put to sleep.

I've searched the forums, and I haven't seen anyone else post this kind of problem.  I'm hoping that someone could point me in the right direction.

As a side note, hibernate-to-hard-disk appears to be functioning normally.

Thanks in advance!

---

### Post by spiderbatdad on 2010-01-29
I think this can be difficult to diagnose. The feature doesn't work well with all hardware. Are you using Nvidia 8400 graphics card; and compiz-effects? 
Can you use [http://paste.ubuntu.com/](http://paste.ubuntu.com/) to paste the output of dmesg, then copy a link to your pastebin back here in another post?

To get dmesg after boot open a terminal and run:
```
dmesg > ~/Desktop/dmesg.txt
```

---

### Post by ApocryphalAuthor on 2010-01-30
Thanks spiderbatdad for you response.

I am using an Nvidia 8400 and compiz-effects (on normal.)

Here is my pastebin of dmesg:
[http://paste.ubuntu.com/365778/](http://paste.ubuntu.com/365778/)

I appreciate the help!

---

### Post by spiderbatdad on 2010-01-30
So the details as you described did not seem familiar to me. I did a magic google search, and came up with this. [http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/](http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/)

Where the author's problem revolved around the nvidia 8400. Have a look and see what you think.

---

