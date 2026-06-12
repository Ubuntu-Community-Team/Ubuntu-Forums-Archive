---
title: "Effect Settings Config File Locations"
date: 2008-01-06
forum: Desktop Effects &amp; Customization
---

### Post by Arcnsparc on 2008-01-06
R60 thinkpad, gutsy.  Linux noob.

I am writing my first scripts to change between appearances, I have another post going to try and figure out the commands to do this.  But instead of a big compicated script I am going to try and saving different Config files, and using the script to change between them.  

The problem is that I dont know where to find the config file I need!  I was hoping someone would know where they are.  Here are the ones I am looking for:

Panels, Panel locations & settings, Menus & menu icons.

Emerald theme settings (or which them to use) [solved: [http://forum.compiz-fusion.org/showthread.php?p=45153#post45153](http://forum.compiz-fusion.org/showthread.php?p=45153#post45153) ]
Background, splash screen, and Usplash(the very first one from boot I think)
Background [solved: gconftool-2 --type string --set /desktop/gnome/background/picture_filename "path/to/the/new/background/image.jpeg" ]

Sounds (not too important)
Compiz config (if there is a config for this one...) [solved: [http://forum.compiz-fusion.org/showthread.php?t=6511](http://forum.compiz-fusion.org/showthread.php?t=6511) ]

anything similar to above if I forgot.

Is there a config file website that tells me where they all are?

I know this is a lot, but I want to make several versions of each config file, and then have a script change them all for me in one fell swoop.  

Thanks much in advance!

---

### Post by rune0077 on 2008-01-07
Check this webpage: [http://developer.gnome.org/doc/whitepapers/SystemConfig/index.html#DOT-DESKTOP](http://developer.gnome.org/doc/whitepapers/SystemConfig/index.html#DOT-DESKTOP)

It isn't complete done yet, but there's some info on config-files.

---

### Post by Forlong on 2008-01-07
As for Compiz (I assume you have ccsm installed), you have to switch to the Flat-file Backend, then the config files will be stored at **~/.config/compiz/compizconfig/**

---

