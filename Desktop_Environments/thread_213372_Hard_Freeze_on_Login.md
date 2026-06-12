---
title: "Hard Freeze on Login"
date: 2006-07-11
forum: Desktop Environments
---

### Post by jorynd on 2006-07-11
Hey all,

I've been working hard at trying to get an Ubuntu distribution installed on my machine.  Installation appears to go smoothly without any problems.  However, when I boot up into Ubuntu, my machine freezes when the login screen displays and the startup sound goes off.

Some things I have tried are:
1.  I have tried many versions of Ubuntu.  I have an AMD64 processor so I have tried both the x86 and the AMD64 versions of Ubuntu.  As well, I have also tried installing both of those builds of Xubuntu and still came across the same problem.
2.  I thought that perhaps the freeze was related to the sound server based on the fact that it was hanging as soon as the sound was playing so I disabled the startup sound in the gdm configuration file (```
SoundOnLogin=false
```) but it still froze at approximately the same place.

One unusual thing that I discovered I can do to prevent the freeze is to press CTRL+ALT+F1 just before the login screen appears.  I hear the startup sound play as I am kicked over to a non graphical login prompt.  I then go back to gdm with CTRL+ALT+F7 and I am able to login no problem without any freezes.

Obviously I would like to be able to login into Ubuntu without having to press a key combination.  I am going to try a server install of Ubuntu and then run a ```
sudo apt-get install ubuntu-desktop
```

I have a Comp Sci background with a small amount of knowledge with Linux so more technical responses is acceptable if it can help me solve my problem.

Cheers!

---

