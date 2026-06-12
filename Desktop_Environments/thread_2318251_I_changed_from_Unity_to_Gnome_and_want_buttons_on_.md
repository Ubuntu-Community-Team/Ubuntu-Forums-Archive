---
title: "I changed from Unity to Gnome and want buttons on right again"
date: 2016-03-24
forum: Desktop Environments
---

### Post by Dragonbite on 2016-03-24
I am somebody who keeps jumping around with distributions and desktop environments.

My laptop ran Ubuntu w/Unity at one point and left the window buttons on the left, but since then I switched it to a non-Ubuntu distro and running Gnome shell.  Since my /home directory is a separate partition I do not write over when switching distributions or desktop environments (I've run KDE, Xfce, Gnome and Unity on this thing) when I booted into Gnome it picked up the button setting from Unity and now the buttons on the left in Gnome.

Where can I find the setting for the window button, so I can change that to the left side again?  I dont' find anything in ~/.gnome, ~/.gnome2 or ~/.gconf.

Being a non-Ubuntu distro I cannot install Unity Tweak (as far as I know) to "set things back", and the non-Ubuntu distro group is less likely to know where this (these) settings are which is why I am asking in the Ubuntu forums.

Thanks!

---

### Post by howefield on 2016-03-24
Thread moved to the "*openSUSE and SUSE Linux Enterprise*" forum.

---

### Post by Dragonbite on 2016-03-24
> **howefield said:**
> Thread moved to the "*openSUSE and SUSE Linux Enterprise*" forum.

I think that is incorrect as the only reference to openSUSE doesn't matter.  It could be ANY non-Ubuntu distribution (Fedora, Arch, Slackware, Gentoo, etc.) and the issue being question is related to Unity, a currently-Ubuntu-only thing.

Please consider another location where I have a greater chance of getting my **Unity** question answered (config location for button location).

Thank you.

---

### Post by buzzingrobot on 2016-03-24
If by "window buttons" you mean the Launcher in Unity, and the Dash (dock) in Gnome, it is also fixed to the left screen edge in the latter.

The "Dash To Dock" Gnome extension converts the Dash into a more conventional dock and allows it to be repositioned away from the left side.

"Gnome Tweak Tool" is something you'll want to install and use, particularly to enable/disable/configure extensions.

---

### Post by Dragonbite on 2016-03-24
I'm referring to the "close" and "minimize" or "maximize" buttons in the application's title bar.

---

### Post by Frogs Hair on 2016-03-24
The gconf-editor can be installed in Suse, but I can't answer if it will move the title-bar buttons in Gnome Shell themes.

---

### Post by howefield on 2016-03-24
> **Dragonbite said:**
> Please consider another location where I have a greater chance of getting my **Unity** question answered (config location for button location).

I doubt we'll be closing the "*openSUSE and SUSE Linux Enterprise*" any time soon, until such an event happens threads regarding software run on openSUSE systems really should be posted here.

---

### Post by Dragonbite on 2016-03-25
> **Frogs Hair said:**
> The gconf-editor can be installed in Suse, but I can't answer if it will move the title-bar buttons in Gnome Shell themes.

Thanks.  I installed it and have been looking through it.  I haven't found the setting anywhere and have tried looking for "close","buttons","left" and other terms (as well as going one-by-one) and haven't found an appropriate setting yet.

I even wonder if, since it is *a non-Ubuntu distro* if the setting is not going to be included because there is no need.  Maybe if I can find the setting that Unity uses I can try manually entering it and setting it to "right" or "default"

---

### Post by QDR06VV9 on 2016-03-25
@Dragonbite I think that code has been hard coded for a more unified experience for the user.

[http://ubuntuforums.org/showthread.php?t=2255495](http://ubuntuforums.org/showthread.php?t=2255495)
I know you are not using ubuntu but I know Suse uses their code.
But have you tried the Gnome-Tweak Tool?

---

### Post by Dragonbite on 2016-03-25
> **runrickus said:**
> @Dragonbite I think that code has been hard coded for a more unified experience for the user.

[http://ubuntuforums.org/showthread.php?t=2255495](http://ubuntuforums.org/showthread.php?t=2255495)
I know you are not using ubuntu but I know Suse uses their code.
But have you tried the Gnome-Tweak Tool?

Gnome-tweak was installed and that was the first place I looked.  I'll look through the code in the other thread. Thanks.

---

