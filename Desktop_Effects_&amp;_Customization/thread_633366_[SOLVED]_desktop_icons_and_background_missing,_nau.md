---
title: "[SOLVED] desktop icons and background missing, nautilus appears not to work"
date: 2007-12-06
forum: Desktop Effects &amp; Customization
---

### Post by Pitt Stains on 2007-12-06
Hi, I was messing around with Compiz, and now I have problems.  I'll list the problems first, then what I did that might have caused the problems.

Problems:
[LIST]
[*]desktop wallpaper gone -- replaced with black
[*]desktop icons gone
[*]desktop not interactive -- no right-click
[*]show desktop button causes items to disappear from status bar as well as from desktop area
[*]nautilus appears dead -- can't get into any of my "places" or use the GUI to connect to a server
[*]my system menu has changed, and I can't seem to figure out how to turn off desktop effects
[/LIST]

How I got here:
[LIST]
[*]installed gnome-compiz-manager, made some changes through the GUI
[*]had trouble with this (but I don't think I lost my desktop here), removed package -- tried to "purge" (remove config files) but these apparently stayed in place
[*]installed compizconfig-settings-manager, made some changes through the GUI
[*]uninstalled compiz (and all related packages) and attempted to purge (again, apparently unsuccessfully)
[*]reinstalled compiz (and all related package), as well as compizconfig-settings-manager
[/LIST]

I am happy to edit/delete whatever config files I need to manually, if I only knew where they were and what to change.  I've looked around on the forum and though some have had similar issues, none of their solutions worked for me (e.g., start nautilus through CLI).

Any help at all is appreciated.
-Pitt

---

### Post by Pitt Stains on 2007-12-06
I managed to solve most of my problems.  This fix was simple as could be.

**The solution:**
We need to edit the config file for compizconfig-settings-manager.  From the command line, type:
```
sudo nano /etc/compizconfig/config
```

You should see (at least I did) a file that looks like this:
```

[general]
integration = true
backend = ini

[gnome_session]
integration = true
backend = gconf

[kde_session]
integration = true
backend = kconfig

```

I changed all the true values to false, and saved the file.  I'm not sure if that they all need to be set, but that's what I did and it worked for me.

Once you've saved the file, make sure to close and save anything you're working on, then press "Alt + Ctrl + Backspace" to restart your session (thereby reloading the config file).  When you log in, your desktop should be restored.  Interestingly, you can still use the settings manager to optimize your desktop experience.

**Side note:**
This probem:
> show desktop button causes items to disappear from status bar as well as from desktop area
...if it can be called a problem, was specific to my configuration.  I had the "Enable Show desktop" plugin enabled, with the "Movement Direction" set to "To Corners" and the "Window Part Size" set to 0.  Apparently this is a deadly combination for your status bar.  I set the Window Part Size to 4 and got the desired effect.

**Remaining issues:**
> 
my system menu has changed, and I can't seem to figure out how to turn off desktop effects

I don't think this is a "bug" so much as the way compizconfig-settings-manager works... or maybe I'm just misremembering the menu layout.  In any case, it turns out you can turn off visual effects here: System > Preferences > Appearance

---

