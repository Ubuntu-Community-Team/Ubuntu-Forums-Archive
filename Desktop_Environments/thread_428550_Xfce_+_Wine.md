---
title: "Xfce + Wine?"
date: 2007-04-30
forum: Desktop Environments
---

### Post by mechanic on 2007-04-30
Changing to Xubuntu (installed xubuntu-desktop), Wine seems to have developed a problem rendering the window border and title+icons. They are all scrambled up! The rest of the window displays as it should. Logging out and logging into the Gnome desktop shows the window perfectly normal. Only a problem with the xfce desktop.

Any thoughts?

Thanks, m.

---

### Post by mechanic on 2007-05-04
Well what seems to be happening is that the filemanager from the Gnome install and the xfce filemanager I've been trying out have been fighting each other to render some of the windows surrounds (title bar,scroll bars and so on). I bit the bullet and installed a fresh copy of Xubuntu, preserving the old /home partition to save personal data and settings. That seemed to solve the immediate issue, the windows are now rendered perfectly in all cases. One or two issues relating to the old Gnome settings in ~/.config and elsewhere remain to be sorted out, but by and large it solved the problem. The xfce desktop is remarkably customisable, by the way, even more so than the Gnome desktop/window manager, and more attractive visually. I've lost gdesklets which is a pity, can't get adesklets to play properly. Nautilus was quite good, but takes the icon rendering over completely so I don't miss that. The other current issue to do with settings in .gtk...rc allowing the icon text to be set against a transparent background, etc., is easy to fix in xfce, as it's gtk based. Xubuntu installed better than Gnome/Ubuntu as well, the LCD screen set itself up without intervention, and to the right resolution.

Regds, m.

---

### Post by tyk on 2007-11-06
yea to Xubuntu and Xfce :) prefer over G and K somehow

---

### Post by TeaSwigger on 2007-11-06
Hello mechanic, if you want to use Gnome / Nautilus again without it taking over your settings, you'd open Nautilus with the command 'no desktop' like so:

```
nautilus --no-desktop
```

Also in a pinch, you can configure WINE to kind of bypass the window manager - open

```
winecfg
```

and you'll find the option under graphics. Just fyi :) 

If you feel you're getting the hang of things and want to try more stuff, try some of the other window managers like Fluxbox, IceWM, WindowMaker, jwm etc. They're even lighter than xfce, and though not as extensively featured are highly customizeable, usually by editing just a few text files, and as such can often be made just your style so to speak. A snap to install and remove from your Xubuntu install without messing things up.

Enjoy :)

---

