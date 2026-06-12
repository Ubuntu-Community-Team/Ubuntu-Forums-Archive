---
title: "Reverting to an older xorg package"
date: 2009-04-28
forum: Desktop Environments
---

### Post by handsomeDave on 2009-04-28
The other night I updated 8.04 and the next morning the x server would freeze after running less than a minute. The only thing I can think of is that it must be something graphics card-wise incompatible with an xrog-server package that updated.
How can I revert it back to the older package from the terminal?

---

### Post by Zorael on 2009-04-28
Well, you need to know the package name, and obviously the older package must still reside on one of the repositories.

First use **apt-cache policy** to divine the package version number you want to install, and then **aptitude install *package*=*version***. I've marked an example up with some coloring, should be self-explanatory enough.
```
$ **apt-cache policy [COLOR="DeepSkyBlue"]xserver-xorg-video-intel[/COLOR]**
[COLOR="DeepSkyBlue"]xserver-xorg-video-intel[/COLOR]:
  Installed: [COLOR="Red"]2:2.6.99.1+git20090402.fad714c4-0ubuntu0tormod2[/COLOR]
  Candidate: [COLOR="Red"]2:2.6.99.1+git20090402.fad714c4-0ubuntu0tormod2[/COLOR]
  Version table:
 *** [COLOR="Red"]2:2.6.99.1+git20090402.fad714c4-0ubuntu0tormod2[/COLOR] 0
        500 http://ppa.launchpad.net jaunty/main Packages
        100 /var/lib/dpkg/status
     **[COLOR="Lime"]2:2.6.3-0ubuntu9[/COLOR]** 0
        500 http://archive.ubuntu.com jaunty/main Packages

$ sudo aptitude install [COLOR="DeepSkyBlue"]xserver-xorg-video-intel[/COLOR]=**[COLOR="Lime"]2:2.6.3-0ubuntu9[/COLOR]**
```

---

