---
title: "XFCE Corrupt Settings"
date: 2011-01-13
forum: Desktop Environments
---

### Post by MrTuring on 2011-01-13
Hi there all, so I just installed Xubuntu 10.10 64-bit on a new Lenovo Ideapad Z565 earlier this week, got it all working just dandy, but now have a problem.  I was using VLC player, it froze, and the system became very sluggish.  I had trouble moving the mouse even to the menus, but after finally clicking the Log Out, everything froze on me.  So I restarted, logged back in just fine, but now all my settings related to XFCE are gone.  The Applications and Places menu text have been replaced by XFCE Menu and simply a folder icon.  Many other settings have reverted to I assume XFCE defaults, as they are not even Xubuntu defaults.  I've linked to a screenshot [explained below] of what happened to the menu bar.  Is there any way to get at the very least the Xubuntu default settings back, as I was considering just reinstalling...but I'd really rather not.  Furthermore, what files can I backup in case this happens in the future?  Any help greatly appreciated!

[http://img337.imageshack.us/img337/3131/menubarq.jpg](http://img337.imageshack.us/img337/3131/menubarq.jpg)

The 3 box icons on the left near the folder icon (which itself is right next to the Xfce Menu text) were application icons that turned into boxes.  All the little applets--cpu, notepad, were all on the very right of the bar.  The settings for those little applets were reverted to defaults.  The Applications and Places menu texts were replaced by Xfce Menu and the folder icon.  The settings for the file manager are gone.  There's more, but that should give you an idea.

---

### Post by bobcollard on 2011-01-14
Use Synaptic Pkg. Mgr. and reinstall xfce4 and xfce4-goodies.  This problem happens when you have a crash and have to do a hard shutdown to restart.  When you get things running again, Open VLC, go into Tools>Preferences>Inputs & Codecs and change the Default Optical Device from /dev/dvd to: /dev/sr0  this should work around the crash.

---

