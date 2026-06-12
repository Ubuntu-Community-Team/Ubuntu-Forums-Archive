---
title: "Default icons on panels, pixelated in shift switcher"
date: 2008-12-19
forum: General Help
---

### Post by N00b-un-2 on 2008-12-19
These are a few issues that have been bugging me for a while now.  I've applied a custom icon theme, and the icons that I want to see show up in Avant Dock and in the Main Menu, but any time I open a program like Firefox for example, the icon that shows up in the title bar of the window and on the panel are the stock icons.
It seems as though this is the same icon that is used in the Compiz effect "Shift Switcher", which I greatly prefer to the stock window switcher and the "Ring Switcher", except for this bug.
What icons are being displayed here so I can replace them with ones from my custom theme?  I don't like the stock "tango" or "GNOME" icon theme, I think it looks very childish and tacky.  I much prefer the sleeker look of my custom icon set.
see the attached screen shots for examples.
Any one know where the default icons are stored so I can change them?

---

### Post by fuzZzball on 2008-12-19
Hi, same problem here, been trying to figure this out for the last few hours, I think it has something to do with the gtk-update-icon-cache, but the thing is, it's not updating .. hmm .. well .. if someone has a clue, be happy to post it here :D

---

### Post by fuzZzball on 2008-12-23
Okidoki,
Anyone bugging with the pixel rated stuff, old icon sets, etc.

First of all, it's not really clear to me which or what uses the icons or pixmaps, if you want to use new themes, icons, etc. 
A lot of icons are replaced, but for some icons GNOME still uses old icons, located in different locations.
Some are because old themes are not yet modified for GNOME v2.22 and for the applications part, well .. I have to found out why :). 

The firefox icon displayed on the GNOME-panel or the Ring-Switcher is located in ```
/usr/lib/firefox-3.0.5/chrome/icons/default
``` with the names 
[LIST]
[*]defualt16.png [*]default32.png [*]defualt48.png
[/LIST]
I'm using 3.0.5, just find the directory in */usr/lib* matching firefox and take the latest version. 
I've managed to increase the size of the PNG thumbs to 96 pixels and renamed the PNG to default48.png so
it replaces the old default48.png.

Resizing a PNG can be done with the **convert** command 
```
convert -resize 96 firefox.png default96.png
```

If the command **convert** is not recognized, install *imagemagick*
```
apt-get install imagemagick
```

I will reply later on with a detailed list of the default folders where the icons are used. 
A lot of icons are in program folders, don't really get why, but ok..

---

