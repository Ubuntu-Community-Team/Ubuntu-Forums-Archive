---
title: "Gnome Flashback Metacity alt+click functionality"
date: 2015-08-14
forum: Desktop Environments
---

### Post by namrbius on 2015-08-14
Trying to get my settings for ubuntu flashback metacity (under new 14.04.3 install) to match my centos 6 gnome 2 settings in regards to disabling alt+click window moves (because all pro apps have some sort of alt+click functionality).  In centos I would open gconf-editor and go to apps.metacity.general and remove <Alt> under mouse-button-modifier.  The equivalent for ubuntu seems to be in dconf-editor under org.gnome.desktop.wm.preferences.  When I remove the <Alt> from mouse-button-modifier, the alt+click window move behavior still persists, but I lose the ability to edit the top panel settings using alt+right click.  In order to change window move settings, I have to use the compizconfig settings manager (which is weird in that I'm using metacity) and change it to something like <Alt><Ctrl><Shift><Super> because completely disabling it doesn't seem to actually do anything and keeps it at the default <Alt>.  

After doing this, the mouse-button-modifier settings in dconf-editor say <Alt><Shift><Ctrl><Super>.   The end result of this is no alt+click window move (good), window moves with alt+shift+ctrl+super+click (with some sort of added desktop edge snapping functionality), and no ability to change the top panel settings using either alt+right click or alt+shift+ctrl+super+right click.  

Is there any way to get the functionality that I want? i.e. No window moves as well as retaining the ability to alt+right click the top panel and change its settings.

---

### Post by namrbius on 2015-08-17
I guess an easier question would be: is there a way to change the panel settings by just right clicking and not alt-right clicking so that it's not reliant on the mouse button modifier?

---

