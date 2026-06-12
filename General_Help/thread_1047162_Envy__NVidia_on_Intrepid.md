---
title: "Envy:  NVidia on Intrepid"
date: 2009-01-22
forum: General Help
---

### Post by VanillaMozilla on 2009-01-22
I need a confirming opinion about using Envy to install an NVidia driver.

Envy supposedly makes it easy, BUT it comes with the following warning:

"you will have to remove the driver you installed with Envy before upgrading Debian or Ubuntu to a newer release (e.g. upgrading Ubuntu Edgy to Ubuntu Feisty or Debian Etch to Debian Lenny)."

Urk.  Does that preclude minor security updates, or do they just mean major upgrades every 6 months?


In case you were wondering, I updated to Intrepid, thinking it was OK if there is no driver for NVidia TNT2, because a third-party driver is available.  Big mistake!  These drivers are NOT easy to install on Intrepid.

---

### Post by thegreenblob on 2009-01-22
Pretty sure that warning is just talking about the 6 month releases. Such as Hardy (8.04) to Intrepid (8.10).

---

### Post by VanillaMozilla on 2009-01-22
Thanks.  I'll give it a try and hope I don't nuke my computer.

---

### Post by redilyn on 2009-01-22
I use envy with the ATI driver and never remember to remove the driver before upgrading to a new ubuntu version. So far I haven't had any troubles.

Just FYI if it helps.

---

### Post by dabl on 2009-01-22
I think it only means to use "remove/uninstall" _before_ you use "install the driver".  It's a little more obvious when you run envyng in text mode on the console

```
sudo envyng -t
```


On the "version upgrade", it means the proprietary driver is non-functional on the new kernel that comes with a new version.

:)

---

### Post by stchman on 2009-01-22
> **VanillaMozilla said:**
> I need a confirming opinion about using Envy to install an NVidia driver.

Envy supposedly makes it easy, BUT it comes with the following warning:

"you will have to remove the driver you installed with Envy before upgrading Debian or Ubuntu to a newer release (e.g. upgrading Ubuntu Edgy to Ubuntu Feisty or Debian Etch to Debian Lenny)."

Urk.  Does that preclude minor security updates, or do they just mean major upgrades every 6 months?


In case you were wondering, I updated to Intrepid, thinking it was OK if there is no driver for NVidia TNT2, because a third-party driver is available.  Big mistake!  These drivers are NOT easy to install on Intrepid.

What kind of nvidia card do you have?  Most nvidia cards are supported under Intrepid.

---

### Post by sandyd on 2009-01-22
it doesn't really do any damage not to remove it - if theirs any problems later, you can just recover them.

For example when i upgraded, i had too much on my mind (kde 4 garbage) and i forgot to remove it..

next thing i knew, when i restarted, the only thing that was there when i rebooted was a terminal.

So i just go and type in envyng -t and uninstall, then install the envyng drivers and everything worked fine .:)

---

### Post by Yoodle on 2009-01-22
I'm having problems getting the nVidia drivers to work on my system too.

I have a fresh install of Ubuntu 8.10, and I can't get it to show any resolution higher than 800 x 600.  My video card is a RIVA TNT2 Model 64/Model 64 Pro.  If I go to "Hardware Drivers", it says that I don't have any proprietary drivers installed.

So, I installed EnvyNG, and tried to use it to install the drivers.  It shows that the 71.86.04 drivers are the only ones that are compatible (which agrees with the list from [http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-a.html)).  So, I enable them, it installs them, then recommends I reboot.  So, I do.  When I reboot, it fails when it's trying to load the nVidia 71.86.04 drivers.  Anyone have any idea why?

I have tried running envyng -t and un-installing the drivers, then re-installing them.  Same thing.  I've tried going into recovery mode and selecting the XFIXIT (or something like that?) option.  That just puts me back to the generic video drivers.

This is getting really frustrating, and I'm not sure what else to try.  Anyone have any ideas?

Thanks!

---

### Post by VanillaMozilla on 2009-01-22
> **stchman said:**
> What kind of nvidia card do you have?  Most nvidia cards are supported under Intrepid.
Huh???  Are you sure?  I just updated about two days ago, and it specifically told me no drivers were available.

Tell me how.  I have a RIVA TNT2.


Yoodle, I'll try to help you out a little.  Let's see, what's the file name?  I think /etc/X11/xorg.conf or something like that.  Sorry, I can't look right now.  Google it and you'll get more information.  You should be able to get at least 1280x1024 with just a generic driver, I think.

---

### Post by VanillaMozilla on 2009-01-25
Well, this is interesting!  I ran EnvyNG, but the driver is not running.  Nevertheless, everything seems to work, and I now have my 1680x1050 resolution, automatically configured with completely generic drivers.

EDIT:  Next sentence is not correct after all.==>  Not only that, but for the first time it correctly determines the resolution and aspect ratio even if the monitor is not connected!


So I'm going to uninstall all that garbage.  Just for my information, in case of disaster, does ALL the video configuration take place in xorg.conf, or is there something else?


For those who want details:
I installed and ran EnvyNG.  Envy did whatever it does, and claims it installed the (correct) driver.  But I received an error on bootup.  I was offered the chance to repair video settings and took it.  It put me in an infinite loop, presenting the same dialog repeatedly.  Somehow I got out of the loop, and I HAVE MY 1680x1050 RESOLUTION!

However, the NVIDIA driver is NOT running, and no video driver is shown.  This according to Administration > Hardware Drivers, the NVIDIA X Server Settings application, and the screen resolution UI.

---

### Post by VanillaMozilla on 2009-01-25
Yoodle,
That is exactly the experience I had.  I can give you a suggestion, however.

1. Back up xorg.conf.
2. This is from xorg.conf:

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

I did my automatic reconfiguration by some brain-damaged, automagic method, but it probably did the same thing.  And my computer works.  Good luck.

---

### Post by Yoodle on 2009-01-26
Well, I ended up swapping out the video card with what I think is an older nVidia card.  I'm now getting 1024 x 768 with the generic driver.  The nVidia drivers still won't load, but this is at least a little better than where I was.

I'm going to be swapping out some other hardware (hard drives, DVD burner, etc), so I think I'm going to just do a fresh install of Ubuntu and see if it works any better.  I hadn't really configured anything on it yet, so I'm not really losing anything.

---

### Post by rbmorse on 2009-01-26
look at /var/log/xorg.0.log with any text editor. That will tell you what driver is actually loaded (probably VESA right now). Scroll down about 1/4th of the way and you'll see the driver name in the listing. 

/var/log/xorg.0.old is the immediately preceding version of the log. It gets overwritten quickly and on every reboot (actually, every time the x-server starts) but if you haven't restarted the system it may contain hints about what went wrong before.  Use the search function of the editor to find the string "EE" (without quotes) to quickly find the errors.

---

### Post by VanillaMozilla on 2009-01-26
Oh.  Here is what I found.

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
...but later:
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)

So EnvyNG seems to have failed completely.

But:

(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.1.10
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1

***********************************************************************
*****  Does that mean I have a non-proprietary driver?  Woohoo!  ******
***********************************************************************

---

### Post by VanillaMozilla on 2009-01-27
The only problem is that it seems to redetect the monitor at boot time AND on logging out.  I have a KVM switch.  So if I log off and switch to another computer, IT SWITCHES TO 800x600.  Ouch!  Is there a way to prevent that?

---

