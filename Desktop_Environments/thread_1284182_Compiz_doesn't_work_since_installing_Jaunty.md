---
title: "Compiz doesn't work since installing Jaunty"
date: 2009-10-06
forum: Desktop Environments
---

### Post by yknivag on 2009-10-06
I've just resurrected an old PC which was running Gutsy.  As that release is no longer supported I wiped it off and installed Jaunty.  Before I did, Compiz was working perfectly (I had glassy wobbly windows, trasparency, a rotating cube etc).

Now I've installed Jaunty (on exactly the same hardware) it wont start.

The graphics are provided by an onboard Intel device, as below:
```

gavin@wrist:~$ sudo lshw -C video
[sudo] password for gavin: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
gavin@wrist:~$ 

```

Have the minimum requirements for Compiz changed? :(

---

### Post by oldos2er on 2009-10-06
There are issues with Intel video drivers under Jaunty. See [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by yknivag on 2009-10-06
Thanks oldos2er.

This seems a very backward step as the hardware was fully supported in Gutsy! Looks like it's back to Hardy! :(

---

### Post by yknivag on 2009-10-07
I followed the steps in [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) but far from improving the situation, it stopped my graphics card working completely.

Guess I'm going to have to drop back to Hardy or Intrepid.

Anyone know which release broke these cards?

EDIT: I've filed [Bug #445874](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/445874).  I hope there is a chance of fixing this for Karmic!

---

