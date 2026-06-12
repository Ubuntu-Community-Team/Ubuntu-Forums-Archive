---
title: "Macbuntu used to work, now it doesn't..."
date: 2011-03-12
forum: Desktop Environments
---

### Post by burimin on 2011-03-12
Well like last week, I had Macbuntu. Worked perfectly. Long story, but I had to uninstall and reinstall Ubuntu. The OS works fine now, but Macbuntu doesn't work anymore. I mean it slightly does, but the visual effects that make it feel like a real Mac don't work anymore. And the dock doesn't show up as well, so I keep on losing my windows. Basically the only things that do change is the color, the minimize, exit, maximize, and the taskbar. The wobbly effect (even though I did put yes in terminal) doesn't work, nor does the splash effects in the startup screen, etc.

If this is any help, now when I install it, half of the time I get this error that says:

"The panel encountered a problem while loading "OAFIID:GlobalMenu_PanelApplet""

Please help! And I'm totally new to Linux, so if there's any small step I need to do, please explain :D

---

### Post by Copper Bezel on 2011-03-12
Macbuntu is just a package to download an configure a bunch of applications that coincidentally do Mac-like things. They can all be installed individually and configured as you like.

To change visual effect settings (like Wobbly Windows) and hot corners (like the Show Desktop toggle in the lower left) make certain that you have the package CCSM installed:

```
sudo apt-get install ccsm
```

You can change the settings from Preferences -> Compiz Config Settings Manager.

The dock is, I believe, Cairo Dock. Install it and configure it to your liking.

```
sudo apt-get install cairo-dock
```

I've never played with the Global Menu panel applet, but it looks as if it's causing you some trouble. That's the panel applet that moves your menus from the windows to the panel. Its 
package name is gnome2-globalmenu. Try reinstalling it. First, remove it with

```
sudo apt-get purge gnome-globalmenu
```

Then you can get it back here:

[http://code.google.com/p/gnome-globalmenu/wiki/Installation](http://code.google.com/p/gnome-globalmenu/wiki/Installation)

It looks like yours is a common problem, so you could also search with the output of your error and see if anyone has a quick solution.

Thanks!

---

### Post by Spyderkid on 2011-03-27
its docky not cario dock

---

