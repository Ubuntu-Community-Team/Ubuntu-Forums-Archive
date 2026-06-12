---
title: "Xinerama and kscreensaver"
date: 2006-08-25
forum: Desktop Environments
---

### Post by cypher35 on 2006-08-25
So i recently set up my second cheap lcd 1024x768 monitor with TwinView so that i could perhaps use it to play videos or something while doing work on my main monitor.

I followed [this](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html) very helpful guide to set up my xorg.conf and get everything working.  Here is a small section:

```
[FONT="Courier New"]Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
    VendorName "Videocard vendor"
    BoardName "NVIDIA GeForce 6600 GT"
    Option "NvAGP" "2"
    Option "NoLogo" "1"
    Option "RenderAccel" "1"
#   Option "CursorShadow" "1"
    Option "Coolbits" "1"
    Option "ConnectedMonitor" "dfp, dfp"
    Option "NoPowerConnectorCheck"
    Option "TwinView" "1"
    Option "Metamodes" "1280x1024,1024x768; 1024x768,1024x768;"
    Option "SecondMonitorHorizSync" "31-82"
    Option "SecondMonitorVertRefresh" "56-76"
#   Option "NoTwinViewXineramaInfo"
EndSection[/FONT]
```

Following the tutorial's recommendation, I commented out the NoTwinViewXineramaInfo option to allow Kwin and other Xinerama-aware apps to know there are actually two monitors here.  I am assuming that by doing so, TwinView emulates an Xinerama setup and that to any application that tries to access information about the monitor setup, it would appear to be so.

It all works as expected.  Maximizing windows works as it should (expanding into one window and not both), the desktop Background widget in the settings recognizes two monitors, et cetera.  The only program that does not appear to recognize (or care perhaps) that I am running two monitors is Kscreensaver.  Instead of being run on the windows separately, it treats them as one screen and displays the screensaver accordingly.

This is fine for many screensavers where there's just some stream of colors floating around, but for many of them (like slide shows) I would prefer the way xscreensaver handles it by playing separate instances of the same screensaver on each monitor.

Is this by design or is it simply an overlooked feature?  Is there any way to change the implementation aside from recompiling kscreensaver myself?

---

