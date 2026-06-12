---
title: "OpenGL GLX Context steam (not your normal issue)"
date: 2013-12-01
forum: Gaming &amp; Leisure
---

### Post by Swiftjay on 2013-12-01
So first I'll post stats of my machine

Ubuntu 13.10 x86_64
4GB Ram
Nvidia 330M (Non optimus :) )
Now I have downloaded the graphics card drivers from Nvidia's website and installed it manually rather then going to software centre and isntalling it there for two reasons:
1) They are much older graphics drivers 319 there is now 330
2) Sound output before didn't work from my TV and I wanted that

I don't know if that's the issue but I highly doubt it but I get the:

OpenGL GLX context is not using direct rendering, which may cause performance problems.


I have done some extensive searching on the internet people talking about ia32-libs package and trying to install the comparison version which is: 
apt-get install lib32gcc1

I have tried other packages too related but does not work has anyone got any ideas?

---

### Post by dannyboy79 on 2013-12-01
i just went through this issue but with AMD drivers. it has to do with your opengl libraries being symlinked to the incorrect library files. look in your /usr/lib/ and /usr/lib32/ folders, there should be a nvidia folder i think which has the nvidia opengl library files that you should be symlinking to. here's an answer that may help. [http://askubuntu.com/questions/53354/why-is-usr-lib-libgl-so-1-always-linked-to-libgl-mesa-so](http://askubuntu.com/questions/53354/why-is-usr-lib-libgl-so-1-always-linked-to-libgl-mesa-so)
i will say that it's very confusing with all this stuff and I wish you luck

---

### Post by efflandt on 2013-12-02
It is probably best to use Ubuntu packages for nvidia drivers, so X server and everything is coordinated with it. Also it is possible that you may need **nomodeset** boot parameter to use video modules instead of using kernel modesetting (whether that is needed for nvidia varies with Ubuntu versions). But I am not sure how you remove nvidia drivers installed with a script from nvidia itself. One time I messed up nvidia drivers just trying to use apt-get to install different versions, but somehow did not purge the other version and eventually gave up and reinstalled Ubuntu.

My only experience with 64-bit 13.10 and steam is with a laptop that has dual Intel/Nvidia graphics. But the nvidia-experimental-310 (currently 319.60) drivers work fine with my GTX 765M once I sorted out how to use bumblebee (optirun), so I imagine that driver should work fine with the 300M alone. Install **mesa-utils** if you have not already, and try to get a working nvidia driver, so **glxinfo** shows among other things:```
direct rendering: Yes
server glx vendor string: NVIDIA Corporation

client glx vendor string: NVIDIA Corporation
```And under OpenGL it should also show a bunch of NVIDIA related things.

Once you get that working, you may need to add a file /etc/ld.so.conf.d/steam.conf per post #3 in [http://ubuntuforums.org/showthread.php?t=2188201](http://ubuntuforums.org/showthread.php?t=2188201) so steam can find 32-bit libs it needs. You also may need to install a couple of i386 libs I mention there, but not sure if you need anything special to launch games (ignore the optirun command). I did not need any of this for my 64-bit 12.04 desktop with GTX 550 Ti (which also uses nvidia-experimental-310 drivers), but I had installed ia32-libs before I ever installed steam, and that package is not available in 13.10 which includes some 32-bit libs (but maybe not everything you need).

---

### Post by Swiftjay on 2013-12-03
So an ubuntu update just came out obviously a new kernel due to me  having to re-install my graphics card drivers again, guess what it  started to magically work again.  Sorry dannyboy I meant to reply back  saying your method didn't work.  I'm guessing this was a kernel issue I  hope, I'm just happy I don't have to use outdated drivers and can run  steam.  Closing thread.  Hope this helps others.

Ah optimus my one true mortal enemy I'm quite surprised you were able to get it working so well as I litraly threw my laptop away like a bad habit because of it.

---

### Post by dannyboy79 on 2013-12-03
glad you got it working, mark the thread solved.

---

### Post by oldrocker99 on 2014-03-06
I had the Steam warning after a fresh install of 13.10 (don't ask) and the 331 drivers. I tried a bunch of suggestions, but what finally worked was to simply reinstall the 331 drivers, and now all is well.

---

