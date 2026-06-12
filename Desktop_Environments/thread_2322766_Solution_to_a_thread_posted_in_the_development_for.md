---
title: "Solution to a thread posted in the development forum - User switching"
date: 2016-04-30
forum: Desktop Environments
---

### Post by kurt18947 on 2016-04-30
As is usually the case there's a solution, I just had to find it. The question was how to restore user switching that had been present in previous Ubuntu-Gnome releases but appears to be MIA in 16.04. The solution I came up with is a .desktop file that runs this:  
```
dm-tool switch-to-greeter. 
```
I also discovered an extension that works something like the 'drawers' app in Gnome 2 - QuickLaunch. There's only one 'drawer' but I find that enough. Drop a .desktop file into its folder and the app is available via the QuickLaunch icon.

Edit: This appears to only works with lightDM according to Ubuntu Manpages.

Edit2: This is working great on a desktop with AMD graphics. I just reinstalled 16.04 on a Thinkpad (Intel graphics) and when I switch users, the cursor disappears. I can log out then log back in and the cursor re-appears. It does the same thing when using the lock screen method of switching users. I've found threads on the Fedora forums talking about this. I wonder if it's a gnome thing?

---

