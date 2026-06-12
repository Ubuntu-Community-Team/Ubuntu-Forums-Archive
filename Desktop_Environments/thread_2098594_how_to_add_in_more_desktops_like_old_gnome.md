---
title: "how to add in more desktops like old gnome"
date: 2012-12-27
forum: Desktop Environments
---

### Post by james2b on 2012-12-27
My question is how to add in more desktop managers like the old style gnome which has that basic layout. Do I add in specific software sources into the updater, then use the package manager to search for one like gnome or XFCE ? I have Ubuntu 12.04 32 bit standard. Or is the only way to install that Ubuntu gnome shell remix version ?

---

### Post by ibjsb4 on 2012-12-27
Gnome Classic desktop

```
sudo apt-get install gnome-session-fallback
```

XFCE

```
sudo apt-get install xfce
```

And chose at boot (login).

---

### Post by kansasnoob on 2012-12-27
I made some notes about using the classic (no effects) session here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by james2b on 2012-12-28
Okay then and thanks, will there be very much cross over between the different desktops, so some from one into the other (mixed)?

---

### Post by zombifier25 on 2012-12-28
> **james2b said:**
> Okay then and thanks, will there be very much cross over between the different desktops, so some from one into the other (mixed)?

If you install Xfce (or LXDE, KDE), then some Xfce apps may show up in your menus and clutter them. Other than that no.
GNOME Classic itself is only a shell.

---

### Post by cmcanulty on 2012-12-28
that depends. On my laptop the panels carry over and I get hybrids of each. In Unity I get no launcher. A desktop seems more able to keep them separate.

---

### Post by james2b on 2012-12-28
Okay I see then and thanks, I just did install that gnome fallback, and looks fine except it has only applications and places on the main menu. If I install Debian will that be the good old style gnome desktop ?

---

### Post by zombifier25 on 2012-12-29
> **james2b said:**
> Okay I see then and thanks, I just did install that gnome fallback, and looks fine except it has only applications and places on the main menu. If I install Debian will that be the good old style gnome desktop ?

1. All the preferences are moved to a dedicated System Settings window. Click the top right icon and choose it.

2. If you move to Debian stable, you to trade modern software for rock solid stability and GNOME 2. Just want to make sure you want to do it, since GNOME Classic is almost identical to old GNOME 2, and if you don't like it, you can switch to MATE (which is essentially a GNOME 2 fork), Xfce, LXDE, ...

---

### Post by cmcanulty on 2012-12-29
you can add whatever you want to the panels by clicking alt+rt cl or alt+super+ rt cl. Also you can have several panels same way

---

