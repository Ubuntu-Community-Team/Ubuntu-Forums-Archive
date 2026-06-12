---
title: "Fully uninstall of KDE"
date: 2005-03-29
forum: Desktop Environments
---

### Post by Diego F. on 2005-03-29
I'm deciding migrate to Hoary, but I wan't to do it from Warty. I installed KDE, but I couldn't start it, so I want to uninstall it. There are a lot of packages. How I can ensure that all is removed?

---

### Post by ubuntu_demon on 2005-03-29
[QUOTE=Diego F.]I'm deciding migrate to Hoary, but I wan't to do it from Warty. I installed KDE, but I couldn't start it, so I want to uninstall it. There are a lot of packages. How I can ensure that all is removed?[/QUOTE]
 install debfoster
start it up and purge kde (kubuntu-desktop for hoary) and all packages that depend on it.

Most kde-packages need kdebase so make sure that one is removed.

I use debfoster and deborphan to keep my system clean,lean and mean :)

---

### Post by Diego F. on 2005-03-29
I'm thinking about waiting with Warty, now that I solved my problems with resolution.

Now that I have KDE installed, how should I start it?

---

### Post by ubuntu_demon on 2005-03-29
[QUOTE=Diego F.]I'm thinking about waiting with Warty, now that I solved my problems with resolution.

Now that I have KDE installed, how should I start it?[/QUOTE]
 I'm assuming you have gdm as your display manager. Go to your login screen. Choose session -> KDE and login.

to choose which displaymanager to use (gdm or kdm) do :
sudo dpkg-reconfigure kdm

---

### Post by Glanz on 2005-03-29
[QUOTE=Diego F.]I'm deciding migrate to Hoary, but I wan't to do it from Warty. I installed KDE, but I couldn't start it, so I want to uninstall it. There are a lot of packages. How I can ensure that all is removed?[/QUOTE]
 Synaptic will also come in handy for getting rid of KDE and all its residual configuration files.
I have uninstalled KDE for folks using only Synaptic too.
Whichever method you use, check Synaptic afterwards for residuals.
STATUS (on the bottom on the left)> "not installed (residual config)"
You will be surprised how many files remain. Since KDE fundamentally is an agglomeration of more or less workable applications, many will remain no matter which method you use other than Synaptic, which has the advantage of a GUI that will let you SEE, in list form, just what is installed. KDE applications are not only under "KDE DesktopEnvironment" in the Synaptic list. KDE apps, utilities, and libraries are scattered all over the place. Look under "k", but be careful not to delete any kernel stuff because "k" also refers to "kernel"... hehehe

---

### Post by az on 2005-03-29
True to open source software form, here is another way to achieve the goal of removing kde from one's system:

sudo apt-get remove kdelibs4 libqt3c102-mt arts

---

### Post by Diego F. on 2005-03-29
[QUOTE=azz]True to open source software form, here is another way to achieve the goal of removing kde from one's system:

sudo apt-get remove kdelibs4 libqt3c102-mt arts[/QUOTE]

Thank you. I used that way and I suppose everything is removed. I'll stay with warty and gnome for a while  ;-)

---

### Post by ubuntu_demon on 2005-03-29
[QUOTE=Glanz]Synaptic will also come in handy for getting rid of KDE and all its residual configuration files.
I have uninstalled KDE for folks using only Synaptic too.
Whichever method you use, check Synaptic afterwards for residuals.
STATUS (on the bottom on the left)> "not installed (residual config)"
You will be surprised how many files remain. Since KDE fundamentally is an agglomeration of more or less workable applications, many will remain no matter which method you use other than Synaptic, which has the advantage of a GUI that will let you SEE, in list form, just what is installed. KDE applications are not only under "KDE DesktopEnvironment" in the Synaptic list. KDE apps, utilities, and libraries are scattered all over the place. Look under "k", but be careful not to delete any kernel stuff because "k" also refers to "kernel"... hehehe[/QUOTE]
 synaptic uses deborphan for this I think

I prefer that commandline for my package-management because it is faster. But sometimes synaptic can be very handy indeed.

---

