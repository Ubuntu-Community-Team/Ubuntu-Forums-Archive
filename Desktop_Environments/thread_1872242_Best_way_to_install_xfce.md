---
title: "Best way to install xfce"
date: 2011-10-30
forum: Desktop Environments
---

### Post by physic.dude on 2011-10-30
I have seen both the use of 'apt-get install xfce4' and 'apt-get install xubuntu-desktop'. Whitch of these two would be the best way to obtain the xfce desktop environment after a clean install of Ubuntu 11.10?

---

### Post by Lars Noodén on 2011-10-30
xubuntu-desktop will give you everything you would have gotten from an installation of the Xubuntu CD.  You can then remove the things you don't want or need manually.

---

### Post by mikewhatever on 2011-10-30
I believe the first way would be better, but most importantly, you should not start with 'a clean install of Ubuntu 11.10'. You should start with the command line installation, and then add xfce4 and the other packages you need. If that sounds complicated, just use the Xubuntu live CD.

---

### Post by physic.dude on 2011-10-30
Ok, I figured it out, I didn't realise Xubuntu was up to date with an 11.10 release. I just tried it out on a VM and it's perfect.

I just have one question before I make the switch. Are there any known serious problems when using xubuntu's xfce environment and compiz?

---

### Post by 3Miro on 2011-10-30
> **physic.dude said:**
> Ok, I figured it out, I didn't realise Xubuntu was up to date with an 11.10 release. I just tried it out on a VM and it's perfect.

I just have one question before I make the switch. Are there any known serious problems when using xubuntu's xfce environment and compiz?

If you want to have both Xfce and Gnome, then install 11.10 and add just xfce4. You can add a few extra applets and such if you need them.

If you start with Xubuntu, this will not be needed of course.

For compiz and xfce4, both work quite well together, the only issue is with the windows decorations. Compiz comes with a decorator that mimics Gnome2 metacity themes. In order to change themes under Compiz, you will need to install gnome-control-center (plus quite a few Gnome dependencies). Only then would you be able to adjust the decoration theme.

---

### Post by physic.dude on 2011-10-30
@3Miro, Well I'm in Xubuntu now, Do you mind explaining how to get this window decoration thing fixed with compiz. I got gnome-control-center and its dependencies installed.

---

### Post by physic.dude on 2011-11-05
bump

---

### Post by physic.dude on 2011-11-07
bump

---

### Post by 3Miro on 2011-11-07
> **physic.dude said:**
> @3Miro, Well I'm in Xubuntu now, Do you mind explaining how to get this window decoration thing fixed with compiz. I got gnome-control-center and its dependencies installed.

Compiz has no tool for adjusting the decorations, it just reads the Gnome settings. Xfce4 on the other hand doesn't have a tool to adjust the Gnome settings. You should be able to go to the Appearance part of Gnome Control Center and select the decorations theme. Under Gnome 3 (i.e. 11.10) it is possible that you may have to adjust the Metacity settings directly from gconf editor.

---

### Post by BobMarleyy on 2011-11-08
If I understand correctly, you want to change the way windows look.
Open xfce4 settings manager, applications-> settings-> settings manager, or from a terminal
```
xfce4-settings-manager
```
Click on window manager and there you go.
Perhaps this has solved your problem, if not I do not really get what your problem is. Anyway, I would recommend anyone on Xubuntu to just check out the settings manager.

Cheers,
Bob

---

### Post by LewisTM on 2011-11-08
If you don't mind a bit of gconf editing, you don't need to install  Gnome Control Center.
All you need to do is install some Metacity theme, like Ambiance from the light-themes package, then go to gconf-editor /apps/metacity/general/theme and add Ambiance. You can also move the buttons around to your liking.
To autostart Compiz, follow this [guide]("https://wiki.archlinux.org/index.php/Compiz#Xfce_autostart_.28without_.22fusion-icon.22.29").
You can then start cleaning up GNOME packages, which takes patience but is kind of rewarding.

---

