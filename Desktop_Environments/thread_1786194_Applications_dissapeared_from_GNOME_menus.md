---
title: "Applications dissapeared from GNOME menus"
date: 2011-06-19
forum: Desktop Environments
---

### Post by stingray69 on 2011-06-19
Basically my problem is that the Applications menu is empty and Preferences and Administration no longer appear under the System menu.

I'm running 11.04 and I use Ubuntu Classic because I prefer the GNOME interface.

The other day I was trying out various audio/multimedia players so I was installing and uninstalling several programs with the Software Center. I started to play a CD in Audacious when the system crashed. The screen went dark but the computer kept running. I ended up doing a hard reset.

Everything booted up normally and everything seems to run fine except my GNOME menu is messed up. The Applications menu is empty and Preferences and Administration no longer appear under the System menu. (I realize I can get to these through System Settings but I want the menus back) Furthermore alacarte will not run so that I can edit the menu contents.

I've tried using one of the old menu versions in /home/dan/.config/menus but they are all outdated and I cannot edit them. It also doesn't bring back Preferences and Administration.

I've tried reinstalling alacarte and that doesn't do anything.
I've tried using other panel programs like Docky and AWN but I have the same menu problem.
I also tried resetting the panels to defaults but that doesn't fix the problem.

Any advice?

---

### Post by jerrrys on 2011-06-20
when you say reset to default, was that with alacarte?  if so you can try

sudo apt-get remove gnome-panel

sudo apt-get install install gnome-panel

if you have custom setting, you will be prompted to keep them

---

### Post by stingray69 on 2011-06-20
> **jerrrys said:**
> when you say reset to default, was that with alacarte?

Thanks for responding. In answer to your question, no I didn't use alacarte. I haven't been able to do anything with alacarte since this problem began. Nothing happens when I try to launch it. Here is what I did to reset the panel:

```
gconftool-2 --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
killall gnome-panel
```

---

