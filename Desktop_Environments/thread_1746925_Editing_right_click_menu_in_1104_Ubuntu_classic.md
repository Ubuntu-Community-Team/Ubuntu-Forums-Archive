---
title: "Editing right click menu in 1104 Ubuntu classic"
date: 2011-05-02
forum: Desktop Environments
---

### Post by SpeedyGonsales on 2011-05-02
As Unity have too much serious regressions to be usable desktop (I'll list some so maybe somebody could get an idea what to change for Ocelot 1110 edition):
[LIST]
[*]desktop switcher is obnoxious for somebody who is used to having 8-12 virtual desktops and to see in system tray what desktop is taken and what desktop is free
[*]I do not see Pidgin icon in system tray anymore. And I hate (not dislike, but hate) Empathy, so I do not want to hear "Install Empathy". Have empathy for users who just want their apps in system tray!
[*]Launcher is bugged. I added Synaptic to it, place in launcher was taken, but there was no icon until restart. I added dconf-editor, there was no icon for it also after restart.
[*]weather applet is no more part of date/time tray indicator, but you can install it separately. Yes, you can install it separately, but you can not add your location, and that applet is not smart enough to read your old settings of weather and 1-5 locations for time zones
[*]should I go further?
[/LIST]
In short, 1104 is stable but default login (Unity) is not functional. It is better than M$ Vista which was not stable, but I expected that Ubuntu would adhere to higher standards than one shitty commercial company which wants only money of users and therefore rushed non-functional software to market.

My question (finally):

In Ubuntu classic items I added to right click menu using nautilus-actions are not there anymore. They are still present in Nautilus, but not in desktop right-click menu. I googled a bit and found zilch, so I ask here. Please share how to do it (scripts folder is still there, but that would be regression to be unable to edit right click menu, FFS Ubuntu is not proprietary software so we would be helpless and could not tweak our favorite OS how we like it). Thanks in advance!

---

### Post by wyth on 2011-05-04
You may be running into the same problem [a lot of other people are having with nautilus-actions 3.0.5]("http://ubuntuforums.org/showthread.php?t=1744144&highlight=nautilus+actions"). Maverick's version was 2.30.2-1, had fewer configurations, and actually worked. It seems 3.0.5 just doesn't seem to run like it used to. 

Seems the fix (for now) is to [download the 2.30.2-1 deb]("http://packages.ubuntu.com/maverick/nautilus-actions"), install that over the 3.0.5 version, and maybe pin it in Synaptic so it doesn't automatically update. 

Unfortunately, that doesn't seem to be working for me yet, but maybe I just need to do a little more than restart nautilus. I *do* get my nautilus-actions entries in my right-click menu, nothing happens when I click on one.

The other option would be to use the nautilus scripts manager and run it that way. I messed with that a bit, but quickly tired of tweaking scripts to get them to do what nautilus-actions did.


**EDIT**
Rebooted and all is right again with nautilus-actions.

---

### Post by ZeroFossilFuel on 2011-05-10
Count me in as a hater of Unity. First thing I did when upgrading all of my machines was change the default desktop back to classic at the logon screen.

I also have the right-click missing actions problem in Nautilus. My Wipe utility is installed but will not appear on the context menu. Regression is not a suitable option.

---

