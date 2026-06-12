---
title: "Gnome Extensions in 20.04"
date: 2020-06-02
forum: Desktop Environments
---

### Post by johnnymcc on 2020-06-02
In researching another problem with another users help, I found another more important issue.  I can't get gnome extensions to work.

I did a fresh install of 20.04 LTS about a week ago.  Gnome is version 3.36.2.  Firefox version is 76.0.1.  I installed chrome-gnome-shell and the web site at [https://extensions.gnome.org](https://extensions.gnome.org) functions and offers to install the "Applications Menu" extension.  It does something because it's added to the installed extensions list.  I reboot and then try to turn the extension on.  The switch turns on in the web site but if I switch pages and come back, it's off again.  There's still no evidence of the extension working.  In the Extensions desktop app, the extension is listed, but the on/off switch shows off and is not "clickable".  Is this still the preferred way to do this?  Is this supposed to work?

The gnome site says something about click-to-play, but I can't figure out how it relates to the current version of Firefox.  After Googling the most recent article I found was supposed to be for 20.04 but it was using gnome 3.34.2, so  I don't know if I can totally trust that it showed the right procedure.  Either way, it didn't work.

Any ideas?  Is there any way to diagnose this?

Thanks

---

### Post by Dennis N on 2020-06-03
> I can't get gnome extensions to work...
There is an extensions "master switch" at the top of the Extensions app that controls them all. If none of your extensions work, it might be that it's set to "OFF". (screenshot attached).

---

### Post by johnnymcc on 2020-06-03
That was it!   With all the installing and uninstalling of stuff for both issues, the Extensions app was uninstalled, so I didn't see the master switch.  I installed "gnome-shell-extension-prefs", ran the Extensions app and saw that the switch was off.  Thank You!

---

### Post by johnnymcc on 2020-06-04
I wonder why this switch can't be on the extensions web site.

---

### Post by Dennis N on 2020-06-04
If you're interested, there is also a terminal command to manage extensions: **gnome-extensions [command]**

Example - show your installed extensions:
```
dmn@Tyana-vm:~$ gnome-extensions list
user-theme@gnome-shell-extensions.gcampax.github.com
drive-menu@gnome-shell-extensions.gcampax.github.com
all-windows@ezix.org
dash-to-dock@micxgx.gmail.com
apps-menu@gnome-shell-extensions.gcampax.github.com
panel-osd@berend.de.schouwer.gmail.com
places-menu@gnome-shell-extensions.gcampax.github.com
workspace-indicator@gnome-shell-extensions.gcampax.github.com
desktop-icons@csoriano
ubuntu-appindicators@ubuntu.com
ubuntu-dock@ubuntu.com
```
But the names here do not always correspond exactly with the names on the gnome-shell extensions web site. (For example: above is "apps-menu" but it's "Applications Menu" in the Extensions GUI and on the web site.) Neither does is always show the author.

Use **gnome-extensions help** to see available commands.

---

