---
title: "HOWTO: Bug workaround for slow responsiveness of Ubuntu 8.10 (display refresh bug)"
date: 2008-12-25
forum: General Help
---

### Post by Colt45 on 2008-12-25
Posted this to launchpad and over at videolan.org earlier tonight. Hopefully this workaround can help some people who may be experiencing a very laggy/slow desktop in Ubuntu 8.10 or are experiencing problems with video playback using X11/XVideo or VLC.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972)



The issue of "General System Sluggishness" may be due to a bug with autodetection of display refresh rate in Compiz or Ubuntu. This would explain why both Nvidia and ATi users are effected.

Example: If refresh rate is being polled at 59.88Hz, Ubuntu or Compiz is rounding down to 50Hz instead of setting refresh to 60Hz.

The Nvidia steps only need to be done by Nvidia users to fix tearing/VSync issues for video playback. Follow the steps and see if it solves the problem...




Credit goes to shaundennie 
[http://www.nvnews.net/vbulletin/showthread.php?t=106746](http://www.nvnews.net/vbulletin/showthread.php?t=106746)


**UPDATE**: *12/26/08*
The steps in this post fix tearing in XVideo/X11 and improve desktop responsiveness, but they do not fix the skipping issue in VLC.



Problems with desktop responsiveness mainly appear to be attributed to Compiz or Ubuntu's autodetection of refresh rate.  Compiz or Ubuntu will round down display refresh from 59.99Hz to 50Hz instead of setting it to 60hz.  This rounding down of 10Hz seems to cause  the slowdown that many people are experiencing with Ubuntu desktop performance.   To overcome this, you need to manually set your display refresh rate to 60Hz in CompizConfig Settings Manager.


**Fore note**:
----------------------------------------------------------------------------------------------------------------------
A few days before executing the steps below, I reverted to Nvidia 173.14.12 and VLC 0.8.6h
It's entirely possible that you may be fine using Nvidia 177.80 or 177.82 with VLC 0.9.4
or later after following the steps below.  I have not tested further. If you encounter success
with newer drivers or newer vlc, please post results.



----------------------------------------------------------------------------------------------------------------------
**STEPS**: *Compiz Configuration*

1. Download CompizConfig Settings Manager from Ubuntu repository.
2. Navigate to.. System --> Prefences --> CompizConfig Settings Manager
3. Navigate to.. General --> General Options
4. Click "General Options" to open window
5. Click "Display Settings" tab
6. Uncheck "Detect Refresh Rate"
7. Move "Refresh Rate" slider to 60, or set 60 in the box
8. Check "Sync to VBlank"
9. Click back button to move back to main CompizConfig window
10. Navigate to.. Utility --> Video Playback
11. Uncheck "Video Playback" then exit the CompizConfig Settings Manager.


**STEPS**: *Nvidia Configuration*

1. Pull up nvidia-settings
.. Navigate to.. Applications --> System Tools --> nvidia-settings
.. or open a terminal, type "nvidia-settings" , press enter
2. Click "X Server XVideo Settings"
3. Check "Sync to VBlank" _IF_ not checked
4. Click "OpenGL Settings"
5. Uncheck "Sync to VBlank" _IF_ checked
6. click quit button
7. click quit button
8. Reopen nvidia-settings to verify that config changes were saved.
.. IF they were saved, you are done with step 8.
.. IF they were not saved, ~/.nvidia-settings-rc in your home directory
.. may be under root permissions. You will need to chown chgrp for the file.
.. Then you will need to start back at Step 1 and repeat all steps.

**IMPORTANT**: Reboot your machine when finished. The driver changes won't function correctly until you reboot

---

### Post by Colt45 on 2008-12-25
Also, an interesting observation after executing the steps above and rebooting.

Ubuntu's "Monitor Resolution Settings" still show a display refresh rate of 50Hz. This is why it may be a bug in Ubuntu?

I forgot to add that while this solution may fix "general system sluggishness" it does not fix high CPU usage by Xorg observed in Ubuntu 8.10

---

### Post by Colt45 on 2008-12-26
I may have spoken too soon .. =/

There still remains some very infrequent video playback skipping that coincides with Xorg CPU spikes of 10-20%.

---

### Post by andybunted on 2008-12-26
Interesting.

This has improved the 'feel' of the GUI markedly.  The difference with video playback (including flash based rubbish such as Youtube) is night and day!  

Thankyou!

Something else I discovered earlier today - the SWFDEC plugin was causing massive CPU usage on my system when browsing Flash heavy sites, and wasn't loading Flash properly at all.  Uninstalling and installing the Adobe version made a massive improvement.


One thing I will note - the built in 'Screen Resolution' applet was showing a 60Hz refresh rate before I made these changes, however Compiz was definitely showing 50... Possible bug?

Cheers,
Andrew.

---

### Post by mac21 on 2009-01-11
hi, thx for the tut 

it seems to have removed the majority of the tearing i was experincing in video playback (only with video the video player set to opengl though)

thx

---

### Post by jevchance on 2009-05-04
Just wanted to chime in that this also solved my horizontal tearing problem. Thanks for the information.

---

