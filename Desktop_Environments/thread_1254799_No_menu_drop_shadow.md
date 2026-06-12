---
title: "No menu drop shadow"
date: 2009-08-31
forum: Desktop Environments
---

### Post by Orange Kingdom on 2009-08-31
Hi,

I noticed that when i open a menu (nautilus Firefox) there is no shadow.
However there is a shadow drawn when i open the menu's at the panel, like applications places and system.

Is there a way to enable this, cant find it within the compizconfig manager.

---

### Post by Orange Kingdom on 2009-08-31
I found it: Compiz manager settings the "windows decoration" to "any".

---

### Post by steveneddy on 2009-08-31
More settings:
```

## removing gnome panel drop shadow
You can set the Shadow Windows (Windows Decoration)option in CCSM Window Decorations from "any" to "any & !(type=dock)" to remove the shadow from the panel

## Also make panel and menus transparent

Open CCSM

Go to General Settings

Go to Tab - Opacity Settings

Settings as follows:

dock 67
Menu 90
DropdownMenu 92
popupmenu 93

Link: http://wiki.compiz-fusion.org/WindowMatching

## make gnome bar true transparent

if you are using compiz (desktop effects), you can add true transparency.
go to System->Prefs->Advanced desktop effects settings
Click on General opts.->Opacity settings, and add the following entry at top of the list:
Opacity windows: type=dock
Opacity windows values: 80 (adjust this to your like)

if you dont have the advanced desktop settings util, just install it:
sudo apt-get install compizconfig-settings-manager

this will make entire panel transparent

```

These are old settings but still work.

I actually kept these from the Beryl years.

---

