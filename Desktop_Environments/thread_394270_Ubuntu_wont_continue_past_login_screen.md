---
title: "Ubuntu wont continue past login screen"
date: 2007-03-26
forum: Desktop Environments
---

### Post by Tatty on 2007-03-26
Hi all,

Ive been happily using ubuntu for a few months now, been running Edgy for the last two months.

About an hour a go i installed Reconstructor to have a bit of a play with it.  My computer started to get really slow, i soon realised that i had completely filled my hard drive - which didnt suprise me as my partition is quite small (this install is my first real test with linux).  So i deleted some things and cleared about 2Gb.  

I ran reactor again and all of a sudden the computer starts complaining it has no disk space left.  It was all getting very slow too, so i thought a reboot might be in order.

So i rebooted, and it got to the login screen happily.  I entered my username and password and the screen disappeared as if it was loading the desktop.  then after a few seconds the login screen reappeared and sat there, staring at me.

No matter how many times i enter my username and password it doesnt load the desktop.  I tried running an older kernel listed in my boot menu, but it didnt make any difference.

Any ideas?  Thanks all...
:-(

ps.  Sorry if this is in the wrong forum, but it seemed like a desktop environment problem to me...

---

### Post by taurus on 2007-03-26
Boot into recovery mode from GRUB menu and clean up your cache.

```
aptitude clean
df -h
shutdown -r now
```
Now, log in with your username and password and you might want to have a look at your trash bin to make sure it is empty; otherwise, it just takes up some valuable space.

Applications -> Accessories -> Terminal
```
ls -la ~/.Trash
```

---

### Post by Tatty on 2007-03-26
Thanks so much taurus  that sorted me out!

The time has come to start clearing out my disk i think :-)

---

