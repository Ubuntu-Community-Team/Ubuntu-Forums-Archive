---
title: "Compiz freezes during scale effect : Ubuntu 9.04"
date: 2009-04-30
forum: General Help
---

### Post by radsqd on 2009-04-30
Compiz fusion freezes when using the scale plugin. Specs include a intel gma 3500 video card. Jaunty, Core2 duo processor, compiz .82 installed

Anyone either have this happen to them or better yet know a solution. I have listed two launchpad pages that refer to simillar problems

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353514](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353514)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/356951](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/356951)

---

### Post by densou on 2009-04-30
Are you using UXA+xf86-video-intel 2.7.0 ?

well, shame on who made up to adopt 2.6.28 Kernel instead of .29 (less tearing, overall better for Intel GPU's owners, imo)


I doubt it could be a bug related to Compiz only, maybe you can read [this]("http://ubuntuforums.org/showthread.php?t=1130582") first :popcorn:

---

### Post by everythingsround on 2009-05-24
I think it is a bug with compiz scale plugin or something with Jaunty, but I'm guessing it is simply the compiz version currently in jaunty.  I say that because it has only started, for me, since I've upgraded to jaunty and I began jaunty using my onboard nvidia 7150 and just upgraded to a new nvidia gts250.  I still get the occasional freeze while using the scale plugin.  How can I debug this?  Better yet, fix this without rebooting.  I
ve tried other ttys and ssh-ing in to restart compiz to no avail.  

I'm using nvidia repo driver 180.44, planning on upgrading to 180.51. I'll post back for any nvidia users having the same problem.  ALL other compiz plugins have no noticable bugs causing freezing like scale is.  I have had others in the past freeze machines with a variety of historical ubuntu versions.

---

### Post by densou on 2009-05-24
Enable _Compiz SVN_ repository from *Ubuntu Tweak*, then report any issue to developers ;)

---

