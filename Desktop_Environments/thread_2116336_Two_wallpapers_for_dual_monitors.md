---
title: "Two wallpapers for dual monitors?"
date: 2013-02-15
forum: Desktop Environments
---

### Post by Rhetoric Camel on 2013-02-15
In Ubuntu 12.04 is the best way of getting two different wallpapers on a dual monitor setup still doing a screen capture of your monitors, applying images where you want them and then using that as your background? Or is there an actual method to doing this now, aside from using Nitrogen which didn't seem to work too well on my computer.

Currently using an Nvidia Quadro FX 3450 graphics card. One 24" monitor and one 22" monitor using as twin view since using them as xscreens made it show up as one monitor and labeled as "Laptop"

---

### Post by MrKaliman on 2013-02-17
Does this thread provides you a solution?

[http://ubuntuforums.org/showthread.php?t=1702100](http://ubuntuforums.org/showthread.php?t=1702100)

---

### Post by DiabolicalClaptrap on 2013-02-17
[http://www.webupd8.org/2012/10/ubuntu-multi-monitor-tweaks-full-screen.html](http://www.webupd8.org/2012/10/ubuntu-multi-monitor-tweaks-full-screen.html)
> 
**2.** Another such tool is **Nitrogen**, which **besides  being able to set the same wallpaper to extend across displays, it can  also be used to set a different wallpaper to each monitor.** 


Nitrogen is available in the  official Ubuntu repositories so to install it, search for it in Ubuntu  Software Center or use the following command:
sudo apt-get install nitrogenNitrogen doesn't have a desktop file, so run it from the command line:
nitrogen
In it's Preferences, add your  wallpaper folder, then at the bottom, select "Full Screen" to stretch  the same wallpaper across monitors or select Screen 1, 2, etc., to set a  different wallpaper for each monitor:

[CENTER][[IMG]http://2.bp.blogspot.com/-dpRQbCxE5ws/UHcrLyiE0tI/AAAAAAAAKsA/9eSnqJ-ySHE/s320/nitrogen.png[/IMG]]("http://2.bp.blogspot.com/-dpRQbCxE5ws/UHcrLyiE0tI/AAAAAAAAKsA/9eSnqJ-ySHE/s1600/nitrogen.png")[/CENTER]

To be able to set a different  wallpaper for each monitor, you must disable the file manager from  handling the desktop. This means you'll no longer have folders on the  desktop. 

In GNOME / Unity, install GNOME Tweak Tool:
sudo apt-get install gnome-tweak-tool
Then open GNOME Tweak Tool and on the "Desktop" section, set "Have file manager handle the desktop" to OFF.

And finally, to have the wallpapers restored each time you log in, add "nitrogen --restore" to your startup applications.


Hope this helps.

---

