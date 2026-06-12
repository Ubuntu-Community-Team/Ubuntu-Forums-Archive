---
title: "New fglrx driver?"
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by Caligula on 2008-02-19
hello all,

I was wondering, what is the current release of the fglrx driver?
And, what is the release we get through the restricted drivers manager?

Thanks,

Josh :)

---

### Post by yota on 2008-02-19
You can find the latest driver at [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)
At the time of writing the version is 8.2 (new versioning number ubuntu-like that stands for 02/2008) or 8.45.5 (old versioning).

At [http://packages.ubuntu.com/](http://packages.ubuntu.com/) you can find details about the packages contained in the official ubuntu repository; fglrx is in version 8.37.6.

As you have seen amd decided to change the versioning number and the schedule of linux driver after the gutsy release, Now you can expect nearly one new driver each month with year.month version number.

Hope this helps!

---

### Post by Caligula on 2008-02-19
Thanks!
That's exactly what I needed :)

Do you know perhaps how the new driver is in terms of performance?
Can I, say, run compiz fusion with it with AIGLX using my Radeon Xpress x1150?

Thanks again!

---

### Post by yota on 2008-02-20
Even if the ati drivers for linux are far (really far) behind the nvidia ones in terms of features/performance/stability I've found 8.1 and 8.2 releases to be a significant step in the right direction. The path is still long and I hope that the radeonhd project will soon overtake fglrx, but meanwhile we have something that mostly works.
I suffered lots of dual-head issues (before 8.2) that now are partially corrected and let me do most of the things I'd like.

AIGLX is not supported by the driver in the repository, if you want it, you must upgrade to the latest one.

---

### Post by Caligula on 2008-02-20
ok...
I've installed the 8.01 one with envy, and I do have to say wow.

I remmember using 3.X drivers back in october, and trying to use AIGLX, it was a complete disaster.

I've tried to run AIGLX now, it's still slower than using xgl, but it definitely a step in the right direction, it feels they finally got the ball rolling at ATI. Is it worth it to uninstall the 8.01 one with envy and installing the 8.02 manually?

Where can I find news on amd's open source driver? Are there any plans for it to support 3D acceleration any time soon?

EDIT: 8.1/8.2 :-)

EDIT 2: 8.01/8.02!!! lol

---

### Post by yota on 2008-02-20
The radeonhd project page is at [http://wiki.x.org/wiki/radeonhd](http://wiki.x.org/wiki/radeonhd) 
Beware, don't be fooled by the version number 1.0.0: it's actually a pre-alpha stage WIP; no    acceleration (nor for 2d neither for 3d which is totally unimplemented).

If you dare to try I have weekly build of the driver taken from git on my site, you can find the latest debs (for gutsy) at: [http://opensystems.ath.cx/radeonhd/](http://opensystems.ath.cx/radeonhd/)

8.2 it's a bugfix release, no new feature, but I've seen no regressions too. If you are not experiencing problems keep 8.1, otherwise give 8.2 a go.

---

