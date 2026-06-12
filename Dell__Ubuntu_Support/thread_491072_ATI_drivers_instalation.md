---
title: "ATI drivers instalation"
date: 2007-07-03
forum: Dell  Ubuntu Support
---

### Post by Dearhell on 2007-07-03
I have followed this [guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) in order to install ati driver (I have used method 2, downloading the driver from ATI)

But after following all the steps (also rebooting of course), I still get this message typing fglrxinfo:

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
```

Instead of something like this:

```
[display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON x300 Generic
OpenGL version string: 2.0.6474 (8.38.6)
```

Any idea why the drivers aren't installed?

My laptop it's a Dell Inspiron 9300, my card a Mobility x300 and I use Ubuntu Feisty Fawn

---

### Post by neptho on 2007-07-04
Try running this:

```
%lsmod | grep fglrx
```

If it replies with anything, it's loaded.  That's good.  If not, fglrx isn't being loaded.

If it is being loaded, try running:

```
%dmesg | grep fglrx
``` 

That should show you any information and/or errors it is having.

---

### Post by Dearhell on 2007-07-05
lsmod | grep fglrx:

```

fglrx                 686188  18 
agpgart                35400  2 fglrx,intel_agp

```



 dmesg | grep fglrx:

```

[   17.808000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   17.812000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[   17.812000] [fglrx] module loaded - fglrx 8.38.6 [Jun 22 2007] on minor 0
[  235.536000] [fglrx] total      GART = 130023424
[  235.536000] [fglrx] free       GART = 114032640
[  235.536000] [fglrx] max single GART = 114032640
[  235.536000] [fglrx] total      LFB  = 33423360
[  235.536000] [fglrx] free       LFB  = 3551232
[  235.536000] [fglrx] max single LFB  = 3551232
[  235.536000] [fglrx] total      Inv  = 0
[  235.536000] [fglrx] free       Inv  = 0
[  235.536000] [fglrx] max single Inv  = 0
[  235.536000] [fglrx] total      TIM  = 0

```

---

### Post by neptho on 2007-07-05
Now that's strange.  It's loaded, and it appears that it's running.

Try ```
%glxinfo | grep direct
```

If it says 'Yes', then you are using direct rendering.  You may have to install mesa-utils to get glxinfo on your system.  I've been recently testing Beryl+KDE with Xgl, so mine says 'no' even when it is using the ATI driver.  However, it should not be saying MESA if you are using the normal fglrx+XOrg X system.

It looks, though, that you may have updated your fglrx by hand.  Have you attempted to recompile the module for it, just to see if it's unhappy with the latest 2.6.20 (#16-2) kernel that was recently released?

---

### Post by revilodraw on 2007-07-08
Well I am having the same problem trying to get my Dell Inspiron 6400 to boot into Feisty for the first time...
I get a blue screen talking about xorg and i have looked around for help and nothing has helped yet...

'glxinfo | grep direct' gives me "Error: unable to open diplay"

Also when I opened the xorg.conf file with nano, it was empty....

Any ideas??

---

### Post by tahnok on 2007-07-08
Did ubuntu say anything about using restricted drivers when you first installed the drivers? If so did you tick of the box that says enabled? I had a similar problem with my dell 6400 atix1400 where the driver was in use, but it didn't think it was in use. After I ticked that little box off it worked, it's under restricted drivers under system I think. Hope that helps.

---

