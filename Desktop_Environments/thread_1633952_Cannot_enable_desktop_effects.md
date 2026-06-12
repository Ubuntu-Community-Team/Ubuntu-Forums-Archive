---
title: "Cannot enable desktop effects"
date: 2010-11-29
forum: Desktop Environments
---

### Post by Raugturi on 2010-11-29
For some reason I cannot enable desktop effects.  When I try to enable from the Appearance settings it actually turns on and I can see the effects, but then it pops up a message saying "Desktop effects could not be enabled" and then it turns them back off.

I saw a thread suggesting I run compiz from the command line and check the output.  But when I do that it works fine and gives no errors.

I also tried downloading compiz-check and here's the output of that:

```
Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 3650
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
```

I can't seem to get AIGLX enabled.  I tried re-installing the driver multiple times, I also ran sudo aticonfig --initial, which generated a new xorg.conf.  I have tried with and without Option "AIGLX" "True" in the ServerLayout section (and in a ServerFlags section), also have tried with and without Option "Composite" "Enabled" in the Extensions section.  The only line in /var/log/Xorg.0.log that mentions AIGLX says:

```
[    27.118] (II) AIGLX: Loaded and initialized /usr/lib64/dri/fglrx_dri.so
```

Update: I have now also installed the latest driver from the ATI website, still exactly the same.

---

### Post by Raugturi on 2010-12-14
I completely purged the proprietary driver from my system and now this is the output of compiz-check:

```
Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 3650
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```

However, I still have the same issue.  If I start compiz manually it starts and works perfectly.  If I enable desktop effects (Normal or Extra either one) it starts them, then gives the error that they could not be enabled and turns them off again.  Does anyone know what it is checking after it turns them on that might be telling it to turn them back off?

---

### Post by Raugturi on 2010-12-14
Output of 'compiz --replace':

```
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
IRQ's not enabled, falling back to busy waits: 2 0
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing zoom options...done
Initializing scale options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
Initializing wall options...done
Initializing staticswitcher options...done
Initializing resize options...done
Starting gtk-window-decorator
```

---

### Post by Krytarik on 2010-12-15
How did you install the driver in the first place, via "System -> Administration -> Additional Drivers"? If not, try that.

Is your video card still covered by the drivers build by ATI/AMD, or is it a so-called "legacy"-card?

---

### Post by Raugturi on 2010-12-15
> **Krytarik said:**
> How did you install the driver in the first place, via "System -> Administration -> Additional Drivers"? If not, try that.

Is your video card still covered by the drivers build by ATI/AMD, or is it a so-called "legacy"-card?

Initially I installed it via the Additional Drivers indicator that came up in the Indicator Applet of gnome-panel to let me know it was available.  After completely purging it I have since reinstalled it from the ATI website and then after that didn't work either I installed fglrx via Synaptic.

As for the legacy status, I do not think so, but my reason for not thinking so is that when I went to ATI's site and selected my card it took me to the download for the driver.  If there's a list somewhere that you can point me to I will check.  (I'm also searching for a list now to see if I can find it)

As a side note, I'm not sure it's the driver causing the issue, but rather some check that is being done after enabling the effects, because I can Alt-F2 and run compiz --replace after I login and it runs fine all day with no issues.

---

### Post by Krytarik on 2010-12-16
I've checked AMDs driver-download-site and it seems that your card isn't legacy.

I indeed recommend using the proprietary drivers build by AMD, they should deliver the best performance.

I searched a little around and found this HowTo:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Another hint: Before doing "sudo aticonfig --initial" I would ensure that the xorg.conf is a default one, means not already altered by earlier driver installations. There are backups in the /etc/X11-dir.

EDIT: When following the guide you have to replace "Ubuntu/karmic" by "Ubuntu/maverick" of course.

---

### Post by Raugturi on 2010-12-17
Thank you so much for your help.  Unfortunately that didn't work either.

It appears the problem is with gnome-appearance-properties.  I tried running it from the command line and after I enable desktop effects this error is repeated over and over in the output until it reverts:

```
(gnome-appearance-properties:2395): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
```

I found [this bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/518368") for it, so I will have to try and follow up there.

---

### Post by Krytarik on 2010-12-17
I don't think it's a bug, at least not this (even though mentioned in one of your outputs).

EDIT: Why? The reported bug is about getting an error by just opening the appearance-properties-window.

According to this guide both "AIGLX" and "Composite" have to be enabled:
[http://wiki.compiz.org/ATI%20with%20AIGLX]("http://wiki.compiz.org/ATI%20with%20AIGLX")

Please post your "xorg.conf".

You may also try the Ubuntu-X-Team-drivers or the Open Source Edge drivers:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

Does it work when using the default "radeon"-drivers?:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Raugturi on 2010-12-17
> I don't think it's a bug, at least not this (even though mentioned in one of your outputs).

EDIT: Why? The reported bug is about getting an error by just opening the appearance-properties-window.
The error does come up as soon as a run gnome-appearance-properties, just not very frequently.  Then when trying to enable the effects is when it comes up all at once.  It's possible though that it's just throwing more at once because it's redrawing every window and therefore the error itself has nothing to do with my issue.

> According to this guide both "AIGLX" and "Composite" have to be enabled:
[http://wiki.compiz.org/ATI%20with%20AIGLX](http://wiki.compiz.org/ATI%20with%20AIGLX)
Please post your "xorg.conf".
Since it is on my work machine I don't have the xorg.conf handy until Monday most likely, but I have read that already and did what it says.  There was no change in behavior.

> You may also try the Ubuntu-X-Team-drivers or the Open Source Edge drivers:
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

Does it work when using the default "radeon"-drivers?:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I've tried with the default radeon driver.  Same behavior.  I have not yet tried the xorg-edgers ppa though, so I will try that on Monday.

---

### Post by Krytarik on 2010-12-17
> **Raugturi said:**
> The error does come up as soon as a run gnome-appearance-properties, just not very frequently.  Then when trying to enable the effects is when it comes up all at once.  It's possible though that it's just throwing more at once because it's redrawing every window and therefore the error itself has nothing to do with my issue.
Ok, I've checked that now at my own machine, when calling from terminal I get the same error message (twice), however when switching desktop effects between "None" and "Normal" I also get just a few.
>  I've tried with the default radeon driver.  Same behavior.  I have not yet tried the xorg-edgers ppa though, so I will try that on Monday.
Sorry, the output you posted in post #2 was generated while using the "radeon"-driver, I overlooked that. At least there are no errors reported from compiz-check for this driver.

Did you make a dist-upgrade or however use an old user-profile, which may have settings for Compiz and are maybe causing this trouble?

---

### Post by Raugturi on 2010-12-20
> Did you make a dist-upgrade or however use an old user-profile, which may have settings for Compiz and are maybe causing this trouble?

Yes.  I used dist-upgrade.  I will try to clear all compiz settings and see if that solves it.

Also, here's the current content of my xorg.conf file:
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Option         "AIGLX" "true"
EndSection

Section "Module"
    Load  "dri"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
    Option     "Composite" "Enable"
EndSection
```

---

### Post by Raugturi on 2010-12-20
Removed all compiz configuration files and settings and still the same.  I even completely removed compiz and reinstalled it, no change.  If I can find a disk to back up my larger files I'm going to just try a fresh install and see how that goes.

---

### Post by Krytarik on 2010-12-21
Try to enable the effects 

- with a new user

- with a LiveCD

Please post the output of
```
fglrxinfo
```

and the content of "/var/log/Xorg.0.log"

---

### Post by Raugturi on 2011-04-19
Just wanted to give an update here.

With a new user I get the same issue.

With the Live CD it starts with the desktop effects already on Normal using the radeon driver.

I have switched back to radeon now and removed fglrx so I can't post the output of fglrxinfo, but here is the output of glxinfo | grep render

```
IRQ's not enabled, falling back to busy waits: 2 0
direct rendering: Yes
OpenGL renderer string: Mesa DRI R600 (RV635 9591) 20090101  TCL
```

I'm at a total loss here for what else to check.  "compiz --replace &" still works perfectly fine, so I still don't think it's a driver issue, especially considering the issue is exactly the same whether I use fglrx or radeon.  It even enables the effects right before it turns them off again and tells me it couldn't enable them.

I guess I'll have to try looking through the source for the Appearance application to see exactly what it checks for after it enables them.

---

### Post by Krytarik on 2011-04-19
So, the conclusion is that at least the default "radeon" driver works fine with your video chip when run from within a LiveCD, but not within your installed system.

Since you did at least one time a manual installation of the proprietary "fglrx" driver, try reinstalling some packages those may have altered:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

Please try running all of these commands, although you may get error messages for some of them. You didn't say that you removed the manually installed driver mentioned in post #5. So, hopefully we get your drivers in order by carefully running these commands, please post any error messages you may get.

---

### Post by Raugturi on 2011-04-20
The only errors I got was when trying to run the first two commands.  I got this from the first:

```
sh: Can't open /usr/share/ati/fglrx-uninstall.sh
```

That's because there is no /usr/share/ati directory.

And this from the second:

```
Virtual packages like 'xorg-driver-fglrx' can't be removed
Package fglrx is not installed, so not removed
Package fglrx-amdcccle is not installed, so not removed
Package fglrx-dev is not installed, so not removed
The following packages will be REMOVED:
  fglrx-modaliases*
```

I checked Synaptic and I don't even see xorg-driver-fglrx anyway.  fglrx package is not installed.

The rest went as would be expected.  However, the issue still persists.

This is the output of compiz-check now:

```
Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 3650
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```

Output of glxinfo | grep render:

```
direct rendering: Yes
OpenGL renderer string: Mesa DRI R600 (RV635 9591) 20090101  TCL
```

And it still works using "compiz --replace".  It only fails when starting it via gnome-appearance-properties.

---

### Post by Raugturi on 2011-04-20
Ok, there's a new twist.  I ran compiz --replace & from a terminal and after about 25-30 minutes it randomly restarted X.

Which log file do I look at to see what happened, and how can I start compiz in a way that will make sure if that happens again it tells me what went wrong?  The info about that may explain what the issue is.

---

### Post by Krytarik on 2011-04-20
Try setting Compiz directly:
```
gconftool-2 /desktop/gnome/session/required_components/windowmanager --type string --set compiz
gconftool-2 /desktop/gnome/applications/window_manager/current --type string --set /usr/bin/compiz
gconftool-2 /desktop/gnome/applications/window_manager/default --type string --set /usr/bin/compiz
```
The values for Metacity are "metacity" and "/usr/bin/metacity" respectively.

Then relogin.

---

### Post by Krytarik on 2011-04-20
> **Raugturi said:**
> 
Which log file do I look at to see what happened
The relevant log files are "/var/log/Xorg.0.log" and "~/.xsession-errors", respectively each one's *.old file for the previous xserver session.

---

### Post by Raugturi on 2011-04-20
Well now this is just getting bizarre.  When I enable compiz that way, or just by running it as before, and then open Chromium, put in a URL and hit Enter, X crashes.

---

### Post by Krytarik on 2011-04-20
Maybe it's time for more brute force methods, try

- reinstalling "compiz":
```
sudo apt-get install --reinstall compiz
```
- resetting all Compiz settings:
```
gconftool-2 --recursive-unset /apps/compiz
rm -rf ~/.compiz
```
Relogin after either of those operations.

---

### Post by Raugturi on 2011-04-20
No change after doing both.

---

### Post by Krytarik on 2011-04-20
So, the only remaining way out of this seems to be fresh reinstall of Ubuntu.

You could install the latest beta of Natty 11.04 right away:
[http://www.ubuntu.com/testing/natty/beta](http://www.ubuntu.com/testing/natty/beta)

---

### Post by Raugturi on 2011-04-20
Yeah, I'll have to give that a shot this weekend.  I'm a bit wary of going to 11.04 during the beta in the middle of the week, because this is my work laptop.  I'd hate to lose essential functionality over a minor cosmetic issue.  So I'll have to wait until this weekend when I have time to make a backup image of the whole disk first.  That way if something doesn't work I can rollback to what I have before work on Monday.

Thank you for all your help.  I'll come back after I've got 11.04 on it to let you know if it resolved it (and update the thread status).

---

### Post by Krytarik on 2011-04-20
Then you could also wait until its final release at 28th of this month.

I just yet noticed that we ruled out a misconfiguration in the user profile before.

But you could try 'purging' "compiz", then reinstalling it, maybe that makes a difference:
```
sudo apt-get purge compiz
sudo apt-get install compiz
```
Also, you could try upgrading the "radeon" driver through Xorg-Edgers' PPA, it offers more recent drivers than the offical repos (although the official driver version apparently works within a LiveCD):
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```
If you need/want to remove those PPA and downgrade the concerning packages again:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```

---

### Post by Raugturi on 2011-04-26
Well I never did find out the cause of the problem, but I'm now running 11.04 and it is working perfectly so far (in Unity at least, haven't tried gnome-panel again yet).  Thank you again for all your help.

---

### Post by Krytarik on 2011-04-26
> **Raugturi said:**
> I'm now running 11.04 and it is working perfectly so far (in Unity at least, haven't tried gnome-panel again yet).  Thank you again for all your help.
Glad to hear! Then it will work in "Ubuntu Classic" as well, see here on how to enable Compiz in it:
[http://ubuntuforums.org/showthread.php?t=1730485](http://ubuntuforums.org/showthread.php?t=1730485)

You're welcome!

---

