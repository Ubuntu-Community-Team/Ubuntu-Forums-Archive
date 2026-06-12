---
title: "Disable Desktop Icons in Unity"
date: 2011-05-17
forum: Desktop Environments
---

### Post by impendingVOID on 2011-05-17
I hate desktop icons, can't find an easy way to hide/disable them.

Suggestions appreciated.

Cheers,

VOID.

---

### Post by Copper Bezel on 2011-05-17
The method from ordinary Gnome isn't working for you? That is, in gconf-editor, navigating to apps -> nautilus -> desktop and unchecking everything?

---

### Post by fjgaude on 2011-05-17
Here' the command line code that worked for me. In a terminal:

```
gconftool-2 -s -t boolean /apps/nautilus/desktop/volumes_visible false
```

Give it a try and see.

---

### Post by impendingVOID on 2011-05-17
Command line worked perfectly.

Cheers.

---

### Post by Krytarik on 2011-05-17
If you don't even use the desktop to create launchers for your Unity Launcher, you may want to disable Nautilus' handling of the desktop completely, to spare system resources. As a bonus, you can set different wallpapers for either workspace with Compiz' "Wallpaper" plugin without any loss of features, therefore you need the package "compiz-plugins-extra", it's in the official repos.
```
gconftool-2 /apps/nautilus/preferences/show_desktop --type bool --set false
```Greetings.

---

### Post by psypher on 2012-02-13
I am running 12.04 precise and none of these commands have worked to hide anything. Any other ideas?

---

### Post by Krytarik on 2012-02-13
> **psypher said:**
> I am running 12.04 precise and none of these commands have worked to hide anything. Any other ideas?
For Oneiric 11.10 and later - since based on Gnome 3, not Gnome 2 - it's instead:
```
gsettings set org.gnome.nautilus.desktop volumes-visible false
```respectively:
```
gsettings set org.gnome.desktop.background show-desktop-icons false
```Regards.

---

### Post by psypher on 2012-02-14
> **Krytarik said:**
> For Oneiric 11.10 and later - since based on Gnome 3, not Gnome 2 - it's instead:
```
gsettings set org.gnome.nautilus.desktop volumes-visible false
```respectively:
```
gsettings set org.gnome.desktop.background show-desktop-icons false
```Regards.

Brilliant, it worked! Thanks

---

### Post by markbl on 2012-02-14
Surely the clearest way is to install+run gnome-tweak-tool and disable "Have file manager manage the desktop".

---

