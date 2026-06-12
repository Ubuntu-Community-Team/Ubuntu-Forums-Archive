---
title: "Cannot change to Unity 3D!"
date: 2013-05-16
forum: Desktop Environments
---

### Post by Samuel H on 2013-05-16
Hi everyone!  Major problem here and I'd appreciate some help!

I was installing WINE and Steam to get my games running.  Got everything installed and configured, and my games were working.  However after that, the Update Manager popped up to say that I needed to update my system.  I ran the updates, and then the cogwheel in the corner of the screen turned red, because I needed to reboot.  I rebooted, and now I cannot change the size of my Unity Launcher, and none of my WINE applications will run!!

I logged out and actually selected Ubuntu 3D from the login menu, then logged in again, but I STILL cannot change the size of my launcher, and my WINE apps will not work!  I even tried CCSM and changed the size manually, but it didn't work.  Also noticing that when I click on Dash it takes a long time to actually open, which it wasn't doing before.

If it helps I now have two extra options when I choose Ubuntu 3D - I have "Gnome Classic" and "Gnome Classic (no effects)", but where these came from I have no idea.

What the hell have I done to mess up my system? :(:confused:

Someone please help me because I am seriously just considering a reinstall of Ubuntu which I don't want to do! :(

---

### Post by grahammechanical on 2013-05-16
At least you are not threatening to go back to Windows. :) You do not say what version of Ubuntu you are using. So, I am assuming that it is 13.04. We nearly always need to reboot when we get an update to the Linux kernel and it often conflicts with the proprietary video driver that we are using. On 13.04 you need to go to System Settings>Software & Updates>Additional Drviers tab. You will see a list of video drivers. You may need to experiment. Select a driver and click apply. You may need to reboot or at least log out and log back in.

In the past when there was a conflict between the kernel and the video driver ubuntu would load without activating a video driver. Now, I think Ubuntu loads using something called llvmpipe. It is an open source driver that is supposed to give the Ubuntu 3D effect on hardware that do not support Ubuntu 3D. This is what you are seeing. It is why things are moving slow. I think. This is why I am recommending re-activating a video driver.

As for Gnome classic and Gnome Classic (no effects) - you must have done something to install them. Have you installed Gnome 3 shell? Have you been trying out other desktops?

Regards.

---

### Post by Samuel H on 2013-05-16
Hi grahammechanical - You were right about the video drivers!  I did a sudo apt-get remove fglrx, and then reinstalled the latest ATI driver.  Then I rebooted and lo and behold - everything worked!

As for the Gnome desktop stuff - no idea where that came from, I certainly didn't install it!

And don't worry, certainly not thinking of going back to Windows just yet ;)

---

