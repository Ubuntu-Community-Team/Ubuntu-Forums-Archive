---
title: "Can't change desktop environment settings away from default"
date: 2015-03-20
forum: Desktop Environments
---

### Post by Utnubu42 on 2015-03-20
I use Ubuntu 14.04 with GNOME 3.10.4.

For some reason, I am now unable to change my desktop background or any other desktop environment settings. This problem isn't unique to GNOME; when I switch into a Unity session, I still cannot change these settings.

When I click on a menu item in GNOME Tweak Tool or Unity Tweak Tool, for example, the selected setting does not change (even in the settings panel). When I try to change my desktop background, I can "select" a new background in the wallpaper program, but the previewed wallpaper doesn't change. I can't even change the date and time settings at all.

A few restarts before this problem emerged, I followed the instructions given in the top solution on [this page]("http://askubuntu.com/questions/86977/how-to-correctly-enable-desktop-cube-in-unity-3d") in order to enable the Desktop Cube in Unity (through compiz). It worked for a bit, but after a few restarts the Cube effect was disabled and my present situation emerged. Please help. I suspect this has something to do with permissions.

---

### Post by dino99 on 2015-03-20
what you describe let me think about your profile, as is it has lost its rights (like a guest)

---

### Post by Utnubu42 on 2015-03-20
Well, the problem is specific to my user account (which is still listed as an Administrator). I made a new account and the problem didn't persist. It would be great to be able to fix the problem without migrating to a new account.

---

### Post by Frogs Hair on 2015-03-20
If the version of the Gnome Tweak Tool in use has a setting under desktop that reads "Let File Manger Handle the Desktop", Make sure it is enabled.

---

### Post by Utnubu42 on 2015-03-20
My Gnome Tweak Tool does not have that setting.

---

### Post by Frogs Hair on 2015-03-20
Check under the extensions list and see if user themes is enabled .

---

### Post by Utnubu42 on 2015-03-20
User themes is disabled. I can't enable it because of my problem.

---

### Post by Frogs Hair on 2015-03-21
You can try resetting Compiz from the _Unity_ desktop . The gnome shell uses a different window manager and a sign that it has crashed is that extensions will be disabled automatically. As you wrote you suspect  Compiz so try the following while logged in to Ubuntu.

If not installed```
 sudo apt-get install dconf-tools
``` 
Reset Compiz```
 dconf reset -f /org/compiz/
```

---

### Post by Utnubu42 on 2015-03-21
I tried to reset Compiz, and got this error:
```
GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dfile_2derror_2dquark.Code17: Cannot open dconf database: invalid gvdb header
```

I looked up the error; apparently it means my dconf files are corrupted. I followed the instructions on [this thread]("https://bbs.archlinux.org/viewtopic.php?id=165485")—in which my exact problem is described—and my problem was solved. Apparently it was caused by a faulty shutdown, which probably occurred after my fiddling with Compiz caused the computer to crash. Thanks.

---

### Post by CantankRus on 2015-03-22
If you follow tutorials to customize Ubuntu search for and use guides for your release.
Applications and desktop environments continually evolve and previous guides may not work.
[**_[COLOR="#B22222"]How To Install CCSM And Enable the Desktop Cube on Ubuntu 14.04[/COLOR]_**]("http://www.n00bsonubuntu.net/content/install-ccsm-enable-desktop-cube-ubuntu-14-04/")

---

