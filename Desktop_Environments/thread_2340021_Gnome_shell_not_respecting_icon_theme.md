---
title: "Gnome shell not respecting icon theme"
date: 2016-10-15
forum: Desktop Environments
---

### Post by hmw2 on 2016-10-15
hey guys. im using the latest gnome shell and im having an issue with changing my ison theme. ive got the arc theme installed and it works in nautilus but gnome shell isnt picking it up. the indicator icons have changed but everything in the app menu and quick launch is still using adwaita. ive checked what theme dconf is using and it says Arc so im stumped as to whats causing this. here a pic : [http://pasteboard.co/f7uUGfMLn.png](http://pasteboard.co/f7uUGfMLn.png)

---

### Post by buzzingrobot on 2016-10-15
Arc's developer says the Arc icon theme does not "[COLOR=#333333][FONT=-apple-system]provide application icons, it needs another icon theme to inherit them".  By default, this is the Moka icon theme.  If that's not installed, Gnome's default set will be used. ([https://github.com/horst3180/arc-icon-theme](https://github.com/horst3180/arc-icon-theme))[/FONT][/COLOR]

---

