---
title: "Compiz disables Window Borders"
date: 2010-11-19
forum: Desktop Environments
---

### Post by Vi3GameHkr on 2010-11-19
Hello,

I haven't used Ubuntu much, so I'm still a little bit of a newbie.  I decided to install Compiz so I opened the Software Center and searched for 'compiz' and found Compiz, Advanced Desktop Effects Settings, Emerald Theme Manager, Compiz Fusion Icon and Simple CompizConfig Settings Manager.  I installed each of those.

When I run Compiz Fusion Icon and then switch to compiz, by window borders disappear.  When I switch from terminal by typing "compiz --replace" I get "compiz (core) - Warn: Unable to parse XML metadata from file "core.xml""

Following some suggestions I found around the Web, I checked to make sure "Window Decoration" was checked in ccsm, and then opened up /etc/X11/xorg.conf and found the lines "    DefaultDepth    24" and "    Option         "AddARGBGLXVisuals" "True"" both under Section "Screen"

At this point I have no clue what to do to fix it.  If it should prove helpful to anyone, I am using Ubuntu 10.10 32-bit.  Also I have a GeForce 9800 GT graphics card.

---

### Post by Purplerob on 2010-11-19
Get advanced desktop effects settings (ccsm) if you don't have it installed. Then you can look through all your settings for compiz. I had a similar problem and for me it was the reflection effect. Try checking ccsm for it, if it is selected, deselect it if that plug-in is not the problem try to deselect all the enabled plug-ins until it is fixed.

Hope I helped! :D

---

### Post by ajgreeny on 2010-11-19
> **Purplerob said:**
> Get advanced desktop effects settings (ccsm) if you don't have it installed. Then you can look through all your settings for compiz. I had a similar problem and for me it was the reflection effect. Try checking ccsm for it, if it is selected, deselect it if that plug-in is not the problem try to deselect all the enabled plug-ins until it is fixed.

Hope I helped! :D
Make sure "Window decoration" is enabled as well.

---

### Post by Vi3GameHkr on 2010-11-19
Actually, I already have ccsm, and confirmed Window Decoration is enabled.  I tried disabling and re-enabling most of the features (reloading the window manager in between) but to no avail.

---

### Post by stinkeye on 2010-11-20
In the window decoration plugin you should have in the command box
```
gtk-window-decorator --replace
```

This should also bring your borders up if run with Alt+F2.

---

### Post by Vi3GameHkr on 2010-11-20
Well here's another thing.  Alt-F2 doesn't work in Compiz.  I checked the GNOME compatibility plugin, and Alt<F2> was programmed to Run Dialog, but nothing happens when I press it in Compiz.  Also gtk-window-decorator --replace is the command in the window decorator plugin but still nothing.

---

### Post by Vi3GameHkr on 2010-11-20
Well here's another thing.  Alt-F2 doesn't work in Compiz.  I checked the GNOME compatibility plugin, and Alt<F2> was programmed to Run Dialog, but nothing happens when I press it in Compiz.  Also gtk-window-decorator --replace is the command in the window decorator plugin but still nothing.

---

### Post by Vi3GameHkr on 2010-11-20
Well here's another thing.  Alt-F2 doesn't work in Compiz.  I checked the GNOME compatibility plugin, and Alt<F2> was programmed to Run Dialog, but nothing happens when I press it in Compiz.  Also gtk-window-decorator --replace is the command in the window decorator plugin but still nothing.

---

### Post by Vi3GameHkr on 2010-11-20
Well here's another thing.  Alt-F2 doesn't work in Compiz.  I checked the GNOME compatibility plugin, and Alt<F2> was programmed to Run Dialog, but nothing happens when I press it in Compiz.  Also gtk-window-decorator --replace is the command in the window decorator plugin but still nothing.

---

### Post by Vi3GameHkr on 2010-11-20
Well here's another thing.  Alt-F2 doesn't work in Compiz.  I checked the GNOME compatibility plugin, and Alt<F2> was programmed to Run Dialog, but nothing happens when I press it in Compiz.  Also gtk-window-decorator --replace is the command in the window decorator plugin but still nothing.

---

### Post by Vi3GameHkr on 2010-11-20
Well here's another thing.  Alt-F2 doesn't work in Compiz.  I checked the GNOME compatibility plugin, and Alt<F2> was programmed to Run Dialog, but nothing happens when I press it in Compiz.  Also gtk-window-decorator --replace is the command in the window decorator plugin but still nothing.

---

### Post by Vi3GameHkr on 2010-11-20
Well here's another thing.  Alt-F2 doesn't work in Compiz.  I checked the GNOME compatibility plugin, and Alt<F2> was programmed to Run Dialog, but nothing happens when I press it in Compiz.  Also gtk-window-decorator --replace is the command in the window decorator plugin but still nothing.

---

### Post by stinkeye on 2010-11-20
> **Vi3GameHkr said:**
> Well here's another thing.  Alt-F2 doesn't work in Compiz.  I checked the GNOME compatibility plugin, and Alt<F2> was programmed to Run Dialog, but nothing happens when I press it in Compiz.  Also gtk-window-decorator --replace is the command in the window decorator plugin but still nothing.

OK, I think I've got that one.
Try going in ccsm preferences and setting back to default.
There is an option to save your current settings if you want.

---

### Post by realzippy on 2010-11-20
> **Vi3GameHkr said:**
> Well here's another thing.  Alt-F2 doesn't work in Compiz.  I checked the GNOME compatibility plugin, and Alt<F2> was programmed to Run Dialog, but nothing happens when I press it in Compiz.  Also gtk-window-decorator --replace is the command in the window decorator plugin but still nothing.

Does emerald work then?

---

### Post by Vi3GameHkr on 2010-11-20
Ohh crap! I am soooo sorry I did NOT mean to post like 10 times!!! The page froze so I went back to the thread to make sure my message didn't post before clicking submit again!  How do you delete posts?  Can users do it?

Anyways, reset the settings: nothing; Used emerald as the window decorator, and it didn't work, but I don't have any themes imported, so I don't know if that would change anything.  I wouldn't think so though.

---

### Post by stinkeye on 2010-11-20
Try this in terminal to see if your missing anything.
```
sudo apt-get install compiz compiz-fusion-plugins-main compizconfig-backend-gconf compizconfig-settings-manager python-compizconfig compiz-dev compiz-plugins compiz-core
```

---

### Post by Vi3GameHkr on 2010-11-20
Umm I feel kinda stupid now, because compiz wasn't actually installed... I only had the icon and the settings manager which is kinda weird and confusing.  Well now I think gnome crashed or something because my taskbars disappeared entirely, along with all the titlebars.

I have a build currently running in terminal so I'll wait for that to finish up then I'll have to reboot.

---

### Post by Vi3GameHkr on 2010-11-22
I am still having problems.  So far, there is no foreseeable option to correcting this by some stupid setting (and I know I'm generally smarter than to start asking questions before checking out all the settings, although I understand that is typically a first resort to fixing a problem)

I've restarted, I've uninstalled and reinstalled compiz and all the packages listed by stinkeye above ```
sudo apt-get install compiz compiz-fusion-plugins-main compizconfig-backend-gconf compizconfig-settings-manager python-compizconfig compiz-dev compiz-plugins compiz-core

```

The main problem I am still having is that when I switch to compiz, my title bars all disappear.

---

### Post by Vi3GameHkr on 2010-11-24
Well I'm not getting anywhere far.  I've read a few places that several other people are experiencing the same problems, and it's happened as of the upgrade to 10.10, but it also sounds like a couple 10.10 users are using compiz just fine.

A tutorial at [http://www.webupd8.org/2010/11/install-compiz-0921-in-ubuntu-1010.html](http://www.webupd8.org/2010/11/install-compiz-0921-in-ubuntu-1010.html) shows you how to download the compiz 9.2.1 packages, which aren't fully tested or ready for release.  After playing around with that, I decided I can wait for a stable release.

---

### Post by skauber on 2010-12-06
Window decorations disappeared here after some update, not sure which one....

```
gtk-window-decorator --replace
```


This did the trick for me.. :) Thanks!

---

### Post by Vi3GameHkr on 2011-01-09
New info! The problem must have been in ~/.config/compiz/compizconfig or some other compiz-related configuration file in the home directory.  Upon accidentally deleting my home directory, compiz began to work.

---

