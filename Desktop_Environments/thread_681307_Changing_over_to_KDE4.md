---
title: "Changing over to KDE4"
date: 2008-01-28
forum: Desktop Environments
---

### Post by baracuda68 on 2008-01-28
Hi.
What is the easiest way to change Kubuntu from KDE 3.5 to 4, 
while keeping my desktops icons, toolbars and toolbar settings, menu settings, or do I have to start from scratch and put my icons back onto kde4?
Is there just an "upgrade"?
I have the kde4 packages installed, but when I boot into it, everything is a fresh new desktop with no personal settings from my kde3.
should I just apt-remove all kde3.5 packages?

Thanks.:guitar:

---

### Post by luisromangz on 2008-01-29
With the packages that are provided currently, that isn't possible, because all packages are configured to use ~/.kde4 and not ~/.kde as its config files root path. You shouldn't uninstall your kde3.5 packages, at least with the purpouse of being able to load the settings in KDE4. You would only lose KDE3.5

I think that not using the same config folder is wise, as it is a major update, not a minor one, so programs are so different that the settings files' structures wouldn't be compatible without many problems (possibly breaking your KDE3.5 install).

---

