---
title: "Display Issues"
date: 2008-04-13
forum: Desktop Effects &amp; Customization
---

### Post by nextbgates95 on 2008-04-13
I have Hardy Heron beta.  I had compiz fusion working perfectly, but changed display settings so I could project to a TV.  It worked completely fine until trying to switch back to Display 1, when the fglrx drivers stopped working, and it booted into low res mode.  I have tried everything, and I cannot re-enable desktop effects, even though according to restricted drivers i am using fglrx.  i have tried installing xgl, which doesnt work, and EnvyNG just takes me back to low res mode.

I just need help enabling effects again, and still being able to project to my tv without any problems.

Thanks

---

### Post by Zorael on 2008-04-13
To get an idea what might be wrong, could you perhaps paste the contents of /var/log/Xorg.0.log here?


You could also reset your xorg.conf file and try to rebuild it from scratch, adding whatever options you had earlier until you get to a point where it breaks again. Just make sure to back it up. It's located at /etc/X11/xorg.conf.

The reset command would be the following.
```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by nextbgates95 on 2008-04-13
OK...I have been tinkering with it throughout the day, and I just need to start over.

I have deleted all xorg.conf files, and have been running x from the default xorg.conf file.  I have uninstalled fglrx and xgl.

My card is an ATI Radeon X300SE with DVI, VGA, and S-Video out.  I need the TV connected through S-Video, and my monitor connected through VGA.  I believe that i had fglrx running before.

---

