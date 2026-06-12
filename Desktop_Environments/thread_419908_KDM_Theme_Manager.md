---
title: "KDM Theme Manager"
date: 2007-04-23
forum: Desktop Environments
---

### Post by Scheater5 on 2007-04-23
According to kde-look.org, the KDMThemeManager is supposedly in the Universe Repository since Dapper.  So, I fired up a terminal and installed kdmtheme via

> sudo aptitude install kdmtheme

to no immediately apparent effect, but after a reboot it appeared under System Settings.  But there's a problem - there's no button to enter Administrator Mode.  Entering System Settings through "sudo systemsettings" doesn't work either, as when I do that the kdmthememanager doesn't appear at all.  I could edit this by hand if necessary - I've recently become adept at changing the grub bootsplash - but this seems something that Kubuntu should be able to do through a GUI.  Anyone have any ideas?

---

### Post by Scheater5 on 2007-04-23
Mark it resolved.  Apparently it's a known bug with an unknown cause.  Fortunately there's a workaround, as the button appears normally under KControl.

---

