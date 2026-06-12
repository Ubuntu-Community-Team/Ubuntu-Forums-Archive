---
title: "Video display screws up, then it won't boot!"
date: 2009-06-14
forum: General Help
---

### Post by Nintendo01 on 2009-06-14
I'm not sure what is wrong, but as of a couple of days ago something started glitching my display. The first time it happened my screensaver seemed to not want to unblank, but switching to a different session (ctrl+alt+F1) and switching back (ctrl+alt+F7) would give me my desktop back, but it would never prompt for the password to unlock from the screen saver. The screensaver was set to blank after 10 minutes. After switching back to the Gnome session the display was workable, but bringing up windows or menu lists would cause the display to create random rectangles of either blackness or patches of random stuff on the screen at the moment. I uninstalled gnome-screensaver, thinking it was having the problem, and didn't have xscreensaver installed, then rebooted to try to fix the remaining graphics issues.

After rebooting, I watched it sit idle and after about 5 minutes (before the screensaver would have kicked in) the screen flashed darker a few times, like it was trying to blank, and my gnome-panel menus (only the drop down menus, not any icons) became graphically glitched, but still worked and opening windows gave the same results as above. I rebooted again to clear everything and let it sit for about an hour, and when I came back the display was blank, and no keyboard or mouse movement would work. Even switching sessions wouldn't work, so I had to do a hard shutdown, after which the computer wouldn't boot! The lighted external fans would turn on and the HD activity light would be lit, but my lighted keyboard was still dark, there was no signal to the monitor, and pressing the power button immediately powered it down. I discovered that leaving the computer powered down for a few minutes then trying again let it boot like normal.

Every time I let it sit for about 5 minutes the video glitched and wouldn't be useable until after switching sessions or doing "compiz --restart" and "emerald --restart". It seems the wierd glitch is compiz and/or emerald related, but I don't know why. If it sat long enough to freeze it wouldn't reboot until after sitting for a few minutes.

I'm running 64 bit Jaunty, Gnome, Compiz, Emerald, NVidia drivers 180.44 from repos, kernel 2.6.28-12-generic, GeForce 8600 GT graphics card, 2 gigs ram, and Pentium Core 2 duo processor @ 2.53 GHz. I haven't made any changes to any system configurations in weeks, so it either has to be a recent update (I have security, main, proposed, and backports enabled and I can't remember exactly what packages were updated last time, but I don't remember anything dealing with video) or something hardware failing. This is a custom build that I've only had just over a year now, with no problems in the past.

If anyone has any suggestions I'm open to try anything.

Thank you.

Edit:
I've been letting it sit for a while now and something successfully blanked the screen, but I don't have a screensaver installed. There is something running that is blanking like a screensaver, but causing compiz to glitch. The weird thing is it didn't glitch this past time, but the computer was frozen when I came home from work and started on this post, so something has to still be wrong.

---

