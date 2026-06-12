---
title: "V7 R19WPS 19&quot; WideScreen monitor not useable above 800x600 resolution in Ubuntu 9.04"
date: 2009-04-21
forum: Desktop Environments
---

### Post by grungedoobie on 2009-04-21
I have been unsuccessful in getting a resolution better than 800x600 with Xorg, or a resolution better than 640x480 with NVidia.

On a box with an AMD Athlon 1800+, an NVidia 5200 FX card /w 128MB RAM, and 1.5GB System RAM @ 333MHz.

This is using the Jaunty 9.04 32Bit install.  I tried getting decent resolution before and after making the updates.  Neither worked.  At best, the software says it is unable to detect the monitor and uses a generic driver with minimal resolution settings.

I have tried using Jockey and Envy.  I've tried using the suggested NVidia driver (173) and the lesser driver (180 is not an option for the hardware).

I've tried changing to the xserver-xorg-video-nv package.

I've tried doing a number of other things like editing xorg.conf to force the resolution.  Forcing the resolution at best just gets reset on next boot, and at worst trashes the XServer and I have to reconfigure.

I know the monitor works.  I had just wiped a working install of Hardy 8.04 32Bit using proprietary NVidia driver.

Has anybody come across this?  Is it possible that the hardware is too old for Jaunty?  If it is, then why was a 32Bit version of Jaunty even an option?

I guess I'll just put Hardy back on there and wait for Jaunty to age a little more.  Unless anyone has better suggestion.


The Grunge

---

### Post by grungedoobie on 2009-04-22
Ok, I believe I've found the hang-up with the monitor.

It's two-fold.

First, the monitor is either non-compliant, or its built-in auto-detection service has failed.  It is a fully functional monitor, but neither the Linux nor the NVidia drivers are able to detect it properly.

Second, the NVidia card also seems to be either non-compliant, or its built-in auto-detection service has failed.  It is a fully functional card, but neither Linux nor the NVidia drivers are able to detect it properly.

I was able to find this out while re-installing Hardy.  I have to use the oldest available NVidia driver that allows me to force proper settings through the Linux xorg.conf script.

With this knowledge, I'll try re-installing Jaunty and post again with the outcome.

The Grunge.

---

### Post by grungedoobie on 2009-04-22
For those of you who have wondered, the native resolution of the monitor is 1440x900 WideScreen.

Ok, I've re-installed Jaunty and tried the Envy-NG package as I did on Hardy.  Unfortunately, the screen settings package has been redone, so I have no power to set the screen properties manually.  The xorg.conf file is no longer a configuration file but more like a re-route for other configuration files.

In short, the xorg.conf is now just a dummy file that says "Pre-Configured Device" for everything.  This being the case, there is no help for users to fix the config without someone at Linux HQ spilling the beans on what to do.

Well, here I go...  Back to Hardy.

The Grunge.

---

