---
title: "TwinView + Dual Monitor + Disable Problem - Seeking Help"
date: 2009-12-30
forum: Desktop Environments
---

### Post by andddlay on 2009-12-30
Hello.  I just installed Ubuntu on my parents computer for they haven't had the greatest luck with Windows.  They have dual monitors, and I want Ubuntu to use them properly.  

I have it set up *right now* and it is working great, but once I restart the computer, the right screen displays the main login screen, but the black one is turned off.  I see in the NVIDIA X Server Settings that after restarting the computer, the left one becomes disabled.  To make it working like it was before the restart, I had to fiddle with the Position option on NVIDIA X Server Settings.  I want the left screen to stay on after boot, obviously, with the panels on the left side.

The left screen is a Dell monitor 1280x1024 (I checked the box making this the primary display for the X screen), and the right is a Gateway monitor 1024x768.

Should have the latest drivers, and I'm running Ubuntu 9.10.  Visual Effects is set to normal (should this be set to none? - the problem persists whether or not that change is applied). 

I tried to be as specific as I can, but if more information is required, I will be glad to explain.  Help would be much appreciated.

Thank you :)

---

### Post by andddlay on 2009-12-30
I'd like to add that when I click, "Save to X Configuration File," it gives the the error, "Failed to parse existing X config file '/etc/X11/xorg.conf'!"

---

### Post by andddlay on 2009-12-30
I searched a lot before, but some more searching lead me to this thread:

[http://ubuntuforums.org/showthread.php?t=1101445&page=2](http://ubuntuforums.org/showthread.php?t=1101445&page=2)

What I think fixed my problem was this:

[http://ubuntuforums.org/showpost.php?p=7273190&postcount=20](http://ubuntuforums.org/showpost.php?p=7273190&postcount=20)

---

