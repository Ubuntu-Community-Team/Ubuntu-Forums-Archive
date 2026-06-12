---
title: "[SOLVED] Problem  with AWN-extras and librsvg-dev"
date: 2007-10-15
forum: Desktop Effects &amp; Customization
---

### Post by slughappy1 on 2007-10-15
So I installed AWN according to their web sites instructions. But when I tried to follow the instructions to get the AWN-Extras on page [http://awn.wetpaint.com/page/AWN-Extras](http://awn.wetpaint.com/page/AWN-Extras) I get an error that says that it can't find the package librsvg-dev:

jason@jason-laptop:~/avant-window-navigator$     sudo apt-get install build-essential automake1.9 autotools-dev bzr libgnome-menu-dev librsvg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
automake1.9 is already the newest version.
autotools-dev is already the newest version.
autotools-dev set to manual installed.
bzr is already the newest version.
E: Couldn't find package librsvg-dev

Anybody know why? Or better yet how to fix this? Thanks

---

### Post by brickbat on 2007-10-19
me too...bump

---

### Post by slughappy1 on 2007-10-20
Well I ended up upgrading to 7.10 and following the guide on how to install AWN from their website, and it worked perfectly. I don't know why it didn't work with 7.04, it had in the past with an installation of 7.04.

---

### Post by Inxsible on 2007-10-25
I am using 7.10 64 bit and I still have the same problem. :(

---

### Post by thesmartace on 2007-11-06
librsvg-dev didn't seem to exist for me either but I noticed that librsvg2-dev did so I installed that instead. Seems to have worked fine...

There are a few other packages that need to have a '2' added to work as well.

---

### Post by slughappy1 on 2007-11-06
Well actually I installed AWN-Curves, which appears to just be AWN with one more option of the look of the bar. But if you follow the guide on 	[http://ubuntuforums.org/showthread.php?t=572019](http://ubuntuforums.org/showthread.php?t=572019) it installs all of the applets (extras) as well.

---

### Post by pressurepoint on 2007-12-02
> **thesmartace said:**
> librsvg-dev didn't seem to exist for me either but I noticed that librsvg2-dev did so I installed that instead. Seems to have worked fine...

There are a few other packages that need to have a '2' added to work as well.

This worked for me.... Thank you so much.

How did you find librsvg2?

---

