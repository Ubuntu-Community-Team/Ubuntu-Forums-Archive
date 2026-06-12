---
title: "Steam AMD driver update"
date: 2013-03-25
forum: Gaming &amp; Leisure
---

### Post by verymadpip on 2013-03-25
Hi there.
Has anybody successfully used the Steam AMD driver update utility?

There is also a new option available in "Additional Drivers".  Would upgrading by installing that driver work?

Thanks for any help.

---

### Post by tjeremiah on 2013-03-25
i've always tried to update via STEAM but it never worked. As for the updated in "Additional Drivers", I dont bother to do it there. I just looked up the AMD website and they have a new driver 13.3 BETA 3 that seems to fix a lot of issues with Tf2 in linux. Im going to download from there and install on my Ubuntu 12.10 . 

[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx)

---

### Post by verymadpip on 2013-03-25
Thanks for the response.
I'm trying to avoid doing the AMD website thing as I ended up with serious headaches, resulting in my reverting to 12.04.

I may try via Steam & Additional Drivers anyway.
Mainly, what I don't want is to bork my system as I already have dealing with this graphics thing.

---

### Post by tjeremiah on 2013-03-26
by the way i updated with the newest beta and have zero problems with it.

---

### Post by verymadpip on 2013-03-27
Hi again.
H'mmm.  Ok.

Here's the story:-
I was using 12.10 with drivers from AMD's website & everything was ticking over okay.  I had to reinstall the drivers with every kernel update, but that wasn't a problem.  I suspect I had to do this because I'd not done something I should have - clearly I hadn't done my homework properly.
At some point the drivers would not reinstall due to a previous install, or remnants thereof, causing a problem.  At this point I found I couldn't uninstall whatever drivers I'd previously installed & consequently couldn't move forward.
Hence rolling back to 12.04 & trying for an easy life.

---

### Post by tjeremiah on 2013-03-27
> **verymadpip said:**
> Hi again.
H'mmm.  Ok.

Here's the story:-
I was using 12.10 with drivers from AMD's website & everything was ticking over okay.  I had to reinstall the drivers with every kernel update, but that wasn't a problem.  I suspect I had to do this because I'd not done something I should have - clearly I hadn't done my homework properly.
At some point the drivers would not reinstall due to a previous install, or remnants thereof, causing a problem.  At this point I found I couldn't uninstall whatever drivers I'd previously installed & consequently couldn't move forward.
Hence rolling back to 12.04 & trying for an easy life.

I am new to this stuff as I've purchased my first graphic card not to long ago. The re-installs after every kernel update seems to be a normal thing. But from what I remember, the last update I didnt have to reiinstall the graphic drivers but my wireless drivers. This is how I do the installs for the graphic drivers.

I follow this post (bookmark it), [http://ubuntuforums.org/showthread.php?t=1999119&p=12008178#post12008178](http://ubuntuforums.org/showthread.php?t=1999119&p=12008178#post12008178) . Post number 3 and please read the steps carefully so that you dont end up installing the wrong packages for your system. This post shows you how to remove everything so that you can upgrade without problems. I reboot, install the drivers from AMD site, make sure I ```
sudo amdconfig --initial
``` in the terminal before rebooting. Reboot and everything works just fine. This while using the newest drivers with Ubuntu 12.10. The new driver suppose to work with 13.04 when you do decide to upgrade to that next month.

IF things break after yet another Kernel update, just log into your desktop and press alt+ctrl+t to launch the terminal and do this process again.

---

### Post by verymadpip on 2013-03-28
Hi tjeremiah.
Thanks for the response & the help, yet again.

I've bookmarked the link (nice one) ready for an attempt when 13.04 comes out.
I think I can be patient for a few weeks.

I'm sure I didn't install the mesa libs & what have you while trying this previously.  Probably where it all went wrong.
I also recall NOT having to reinstall the driver after one kernel update.  It was the next one when things got very broken.  Weird.

I'm inclined to leave this as unsolved until I try in April, which will also give me time to find out where the new "Solved" button is ;)

---

