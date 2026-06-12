---
title: "Missing panels...aka panel death!"
date: 2007-10-12
forum: Desktop Environments
---

### Post by willpower232 on 2007-10-12
I'm running the default xfce4 desktop on my xubuntu (7.04) box which im using primarily as a file server to my windows hell computers.

I was looking for a way to play media with a decent library on it on my xubuntu box and i thought I would try amarok. I decided I was not a fan of amarok and I used the synaptic log to uninstall amarok and all the packages that came with it.

Having shutdown after the package removal and rebooted, I logged in today to discover that my panels were missing. Both the application launcher and tray had simply disappeared from my screen.

I right clicked and altered Desktop Settings to change the right click to show desktop menu to regain some functionality. Going into the Settings Manager, I click on the Panel button but nothing happens. All the others work fine, its just the panel button.

Reinstalling the xfce4-panel package had no effect so I used apt-get remove to remove xfce4 (and the rest of the desktop environment), rebooted and used PuTTY to reinstall everything that had been removed.

But the problem remains.

Do I hope that the gutsy gibbon upgrade will repair the panels or do I go for a full reinstall now? Any ideas?

wp

---

