---
title: "Blank Desktop in Gnome Shell after Upgrade to 12.10"
date: 2013-02-10
forum: Desktop Environments
---

### Post by kendoori on 2013-02-10
Unity and Cinnamon Desktops work properly, but Gnome Shell presents me with wallpaper and one of my startup apps with undecorated windows (e.g. no controls and title bar/borders). I can log out using keyboard shortcut (ctrl+alt+del) but can do nothing else but move my mouse around the screen.

Things I've tried:

1) completely removing and reinstalling gnome-shell
2) manually removing all remnants of gnome shell configuration files
3) deleting various compiz config files

.compiz
.config/.compiz-1
.gconf/apps/compizconfig-1
.gconf/apps/compiz-1

None of this works.  I was previously running 3.5.4 under 12.04 and prior to upgrade gnome shell was working.

I'm about ready to either reinstall (and preserve existing home), or wipe a restore home after clean install. Would love to not have to go through that.

P.S. am running a Thinkpad X201 w/Intel components and no alternative drivers.

---

### Post by meteorrock on 2013-02-10
Could be a bad or corrupted file for that gnome shell you have. Did you do a complete purge of the gnome shell and then re-installed it? 

Run this command in the terminal.

```
 sudo apt-get update
```

```
sudo apt-get purge alacarte cups-pk-helper gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-folks-0.6 gir1.2-gconf-2.0 gir1.2-gdesktopenums-3.0 gir1.2-gee-1.0 gir1.2-gjsdbus-1.0 gir1.2-gkbd-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-panelapplet-4.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-applets gnome-applets-data gnome-contacts gnome-icon-theme-full gnome-panel gnome-panel-data gnome-session-fallback gnome-shell gnome-shell-common gnome-themes-standard indicator-applet-complete libcaribou-common libcaribou0 libclutter-1.0-0 libclutter-1.0-common libcogl-common libcogl-pango0 libcogl9 libgjs0c libmozjs185-1.0 libmutter0 libpanel-applet-4-0 mutter-common python-gmenu
```

Also remove the gnome classic shell that comes with gnome 3.

```
sudo apt-get purge alacarte cups-pk-helper gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-panel gnome-panel-data gnome-session-fallback indicator-applet-complete libpanel-applet-4-0 python-gmenu
```

The above codes should totally purge all of that gnome shell along with its settings and other packages that go along with it. Source here. [http://askubuntu.com/questions/65200/remove-gnome-shell-completely-after-installing-it](http://askubuntu.com/questions/65200/remove-gnome-shell-completely-after-installing-it)



~~~~~~~~~~~~~

Then try to re-install it and see if that helps. The new gnome 3 shell uses graphical hardware acceleration so if your computer specs are on the old side, it might not work correctly for you. 

To reinstall it use these commands. 

```
sudo apt-get update && sudo apt-get install ubuntu-gnome-desktop ubuntu-gnome-default-settings
```

Its a good idea to uninstall the ubuntu settings also.

```
sudo apt-get remove ubuntu-settings
```

Then install optional settings for gnome 3 using ubuntu. 

```
sudo apt-get install gnome-documents gnome-boxes
```

The ppa, which you will want to keep gnome 3 updated is this code here. 

```
sudo add-apt-repository ppa:gnome3-team/gnome3
```

Source here for the guide. [http://www.webupd8.org/2012/10/how-to-get-complete-gnome-3-desktop-in.html](http://www.webupd8.org/2012/10/how-to-get-complete-gnome-3-desktop-in.html)

~~~~~~~~~~~~

Hope that helps. :)

---

### Post by kendoori on 2013-02-10
Thanks for all of that, but still no go... I have tested this with LiveCD, so my hardware definitely supports this...

I will probably have to bite the bullet and reinstall from scratch... Upgrades are always a crap shoot.

BTW, any advice on further diagnosing why Gnome Shell won't load properly?

---

### Post by djhawk on 2013-03-28
I had the same issue when logging into the gnome session and this worked like a charm. Thanks!

---

