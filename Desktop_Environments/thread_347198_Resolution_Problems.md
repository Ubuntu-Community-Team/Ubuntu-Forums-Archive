---
title: "Resolution Problems"
date: 2007-01-26
forum: Desktop Environments
---

### Post by Killswitch on 2007-01-26
Hello all!  I am pretty new to Linux, my website runs on a Linux box, and the only experience I have is working very few commands on with that and SSH, so please bear with me :D

So far, I have been able to do pretty much everything normally without problems, my cuz says I am actually doing very well for a first time Ubuntu user.  The only issue I have at the moment is with my resoltion sizes.  

I have checked my xorg.conf file, and I can see the diff. resolution sizes listed there, along with my vid card details.  I have also ranthe command *xrandr -q*, which told me my available resolution sizes...  I have available 800 x 600 and below on a 17 inch monitor!

Is there anyway to force atleast 1024 x 768?  Also, is there any need to look for drivers for my video card or any special software for it?  Its an ATI X700 Pro and Ubuntu seemed to recognize it off the break.

Thanks for any info on this, tried searching but didn't find anything that helped me solve this too much.

---

### Post by taurus on 2007-01-26
Applications -> Accessories -> Terminal
```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.orig
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

