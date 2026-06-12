---
title: "xubuntu lightdm gtk greeter no longer mirroring my dual monitors"
date: 2016-05-01
forum: Desktop Environments
---

### Post by ccrs8 on 2016-05-01
Running Xubuntu 16.04.  Dual monitors.  I've always had my lightdm gtk greeter login screen mirror these monitors.  I sort of like it that way, and got used to it (I then span both monitors once I log in, of course).  Anyway, after upgrading from 15.10 to 16.04, this setting remained the same.  Great.  However, then I did...something...while on the login screen and all of a sudden it changed to spanning.  But a strange type of spanning where the login box where I select the user and then enter the password and the menu bar at the top is always on the screen where my mouse is.  So if I move my mouse to the empty screen, the top panel and the login box jump to that monitor.  Very odd.  And not only that, but the monitors are swapped (I can't move my monitor from one to the other by moving normally - I need to move my mouse to the outside edge of a monitor to move to the other monitor).  Once I'm logged in, everything is fine, but the login screen is now messed up.

I've googled this, but all of the suggestions are about editing .conf files in order to get spanning to work.  I'm interested in resetting things to just mirror, and that is something I can't find.  I have no idea what exactly I did to cause this - I was just moving the mouse around while on the login screen and all of a sudden my screen was no longer mirrored, and there doesn't appear to be anything I can do on the login screen to revert it, though.

Any thoughts?

---

### Post by watchpocket on 2016-06-24
I have the opposite problem. (In Mate 16.04.)

I can span across my two monitors after login (as ccr8 says he does), but I want -- at the greeter -- to span a 5120x1600 image across my two 2560x1600 monitors, and there doesn't appear to be a way to do it in System --> Control Center --> LightDM GTK+ Greeter settings.  

Yes, I could use Gimp to chop the 5120x1600 image into two 2560x1600 halves, but no one should really have to do that.  If there's a way to span after login, there should be a way to it at the greeter stage before login.

I'd also like to know if it's possible -- in the LightDM GTK+ Greeter -- to point to a folder of images so that a different image displays on each boot.

---

