---
title: "Installing xserver no backfill version"
date: 2010-01-30
forum: Desktop Environments
---

### Post by Rule2 on 2010-01-30
Hey,
I am experiencing noticeable delays while maximising or restoring windows. My video card is ATI Mobility Radeon HD 4530. CPU is core 2 duo @ 2.2 Ghz. When I browsed through this forum, I bumped into a thread which said that installing the xserver with no backfill, using 
[https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill]("https://launchpad.net/%7Eubuntu-x-swat/+archive/xserver-no-backfill")

But, nothing seems to happen when I add the ppa, and sudo apt-get update.
Thanks in advance.

---

### Post by Rule2 on 2010-01-31
bump

---

### Post by vladilinsky on 2010-02-24
This repo used to work for me but now it does not.

from what I can tell, (which may be completely wrong) the x server in that repo is older than the one which I am using so it will not use the patched version.   I would assume you have the same problem.  

fortunately it sounds like this will be fixed in the new fglrx 
[http://www.phoronix.com/forums/showthread.php?t=21846](http://www.phoronix.com/forums/showthread.php?t=21846)

---

### Post by latebeat on 2010-04-29
> **vladilinsky said:**
> This repo used to work for me but now it does not.

from what I can tell, (which may be completely wrong) the x server in that repo is older than the one which I am using so it will not use the patched version.   I would assume you have the same problem.  

fortunately it sounds like this will be fixed in the new fglrx 
[http://www.phoronix.com/forums/showthread.php?t=21846](http://www.phoronix.com/forums/showthread.php?t=21846)

I just added the repo and it doesnt work any more (404 error). Also I'm using version 10.3 of the ati catalyst drivers and the no-backfill problem is still there so all the speculations about being fixed in the new versions are bogus...

---

### Post by wardy277 on 2010-04-30
I am too getting this message. I get an error that i cant find ```
http://ppa.launchpad.net/launchpad-weyland/xserver-nobackfill/ubuntu/dists/lucid/main/binary-amd64/Packages.gz
``` I went to it and there is only a karmic version not a lucid one.

Are they not supporting lucid or will it just be a while before they release a lucid one. (Resizing windows in compiz is really slow without it again!)

---

### Post by latebeat on 2010-04-30
FYI.. this **[post]("http://phoronix.com/forums/showpost.php?p=125120&postcount=11")** had a ppa that did the trick for me.

```
ppa:info-g-com/xserver-xorg-1.7.6-gc
```
you can also try
```
ppa:bryceharrington/violet
```

---

### Post by screaminj3sus on 2010-05-01
I am using the violet one with no issues.

---

### Post by ttfung on 2010-05-01
I think you don't need the nobackfill things anymore
all you need to do is update your catalyst and 
```
sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE
```
the restart xserver / reboot 
which fix the maximize and minimize problem

ref:
[http://ubuntuforums.org/showthread.php?p=9207152]("http://ubuntuforums.org/showthread.php?p=9207152")

---

