---
title: "Any difference in launching something from a different location?"
date: 2009-02-22
forum: General Help
---

### Post by Redalert Commander on 2009-02-22
Hi guys,

I was fiddling around with some games and wine, and I deceided to put shortcuts to them in the menu, under games, instead/next to the wine menu.
So I right click the Applications menu and select 'edit menus'.
I went to the wine menu, copied the command from the launcher and then created a new item in the games menu, with that command. For example: env WINEPREFIX="/home/username/.wine" wine "C:\Program Files\EA GAMES\Battlefield 1942\bf1942.exe" 
(I also noticed a trailing space, don't know if it matters)
Now using that launcher, the game doesn't start, using the original launcher, it does start. Also when pasting the command in a terminal window, it immediatly drops me back to my shell, just leaving 1 blank line in the terminal window.

To make it a bit more weird, some games do work fine, some other don't do anything, and others just give weird behaviour.
Metin2 for example (a free online MMORPG, it needs to check for patches first) will launch it's patcher and update normally using the original launcher, or the desktop icon, but will display an 'unknown patch version' error when using the newly created menu item.

So, any thoughts? what is the exact difference? why do some run, and some don't, and what is with the weird behaviour?
As this affects wine apps, might it also affect native linux applications? (UT2004 native linux installation runs fine with a custom menu item)

I'm using an Ubuntu 8.10 installation and tested this using gnome (kde was not tested)

---

