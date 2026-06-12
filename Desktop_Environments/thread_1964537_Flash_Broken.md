---
title: "Flash Broken"
date: 2012-04-24
forum: Desktop Environments
---

### Post by hartz on 2012-04-24
I expect this is on all variants, but I have the issue specificaly on Kubuntu 11.10.

Flash applications causes terrible screen distortion, flickering, and redraw problems.  It is so bad that, switching to another virtual desktop and working in a VirtualBox system is also affected.  I'll try to get a screenshot!

As soon as the browser tab with the affected flash application is closed, the screen recovers.

It seems to happen for all flash apps.

I suspect it is related to the latest Flash-for-linux garbage-ware.

Any ideas how to get it working again?  Go back to a manual instaled flash player?  Lock it's version?  A PPA somewhere with a working flash player?


Searching for problems with flash brings up many old reports, but I'm not hitting the right search terms to find a solution to this new mess, even though I suspect many are facing something similar right now!

Thanx,
  _J

---

### Post by Krytarik on 2012-04-24
> **hartz said:**
> Go back to a manual instaled flash player?  Lock it's version?
Yeah, this. This post describes well enough how to get the library file of an old version of the Flash Player plugin - specifically the one that is mentioned there, 11.1.102.63; at least that's the last version that is working on my Lucid 10.04 with the proprietary nvidia-96 driver:

[http://ubuntuforums.org/showthread.php?p=11803061#post11803061](http://ubuntuforums.org/showthread.php?p=11803061#post11803061)

Then, you only need to replace the currently installed version with that one, in my case in the directory "/usr/lib/adobe-flashplugin", but that might be different in your case, depending on how you installed it in the first place. And to protect it against updates, you need to lock the version of the package-based installation, of course, as you said, for example with Synaptic.

Hope that works for you.

Regards.

---

### Post by lovinglinux on 2012-04-26
> **Krytarik said:**
> Yeah, this. This post describes well enough how to get the library file of an old version of the Flash Player plugin - specifically the one that is mentioned there, 11.1.102.63; at least that's the last version that is working on my Lucid 10.04 with the proprietary nvidia-96 driver:

[http://ubuntuforums.org/showthread.php?p=11803061#post11803061](http://ubuntuforums.org/showthread.php?p=11803061#post11803061)

Then, you only need to replace the currently installed version with that one, in my case in the directory "/usr/lib/adobe-flashplugin", but that might be different in your case, depending on how you installed it in the first place. And to protect it against updates, you need to lock the version of the package-based installation, of course, as you said, for example with Synaptic.

Hope that works for you.

Regards.


[http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

