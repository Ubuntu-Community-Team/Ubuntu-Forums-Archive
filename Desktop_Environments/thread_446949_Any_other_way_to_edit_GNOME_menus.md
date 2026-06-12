---
title: "Any other way to edit GNOME menus?"
date: 2007-05-17
forum: Desktop Environments
---

### Post by botulismo on 2007-05-17
The built in Alacarte menu editor that comes with GNOME either does not work correctly for me or I am stupid... I think it's the former rather than the later, because when I click to "Delete" something, it won't delete... all the time. Sometimes it will. I know I could just uncheck it, but when I tried to drag something into a subfolder I'd made, and it didn't show up, I kept trying... Well, on reboot, I discovered that it had. I've had it show up immediately on occasion, but this is no way for me to have to organize the programs I use unless I go crazy. Is this a bug that I can correct, or is there another way I can edit the GNOME menu? Even if it involves going into a configuration file or five and doing it by hand and I have to teach myself a scripting language, I imagine that this would still be easier than me mucking around in Alacarte and HOPING that the drag and drop I did worked...
Not to mention delete.

---

### Post by FuturePilot on 2007-05-17
Sometimes the changes aren't visible right away. In that case just press <Alt><F2> and type
```
killall gnome-panel
```
When it reloads the changes should be there.

---

### Post by hikaricore on 2007-05-17
The linux standard menu system could use a serious overhaul.  In both KDE and Gnome the menu is actually just a set of .desktop files that are supposed to be stored in:

/usr/share/applications

But this is not always the case which causes problems.  Some distros have a specific location(s) they store their .desktop files, but along with that the gnome menu has to search the /usr/share/applications directory as well.  On top the this the "folders" you find in these menus are either named by ["vfolders"]("http://www.gnome.org/start/2.0/menuediting.html#howdoesitwork") as well as tags in the individual .desktop files or the gnome or kde menu configuration files.  These are a nightmare to modify by hand.

The only thing I will ever miss about the ***dows line of OSs is the simple (yet sometimes problematic) method of simply storing the menu files in a directory.  This way you can manually edit, add, remove, etc for a single user or all users.

The linux standards are evolving, but not fast enough for most.

I know this doesn't really solve your problem but it atleast gives you some more info on the situation.

Here's some more in depth reading on how the gnome menu system works:

[http://www.gnome.org/start/2.0/menuediting.html](http://www.gnome.org/start/2.0/menuediting.html)

p.s. in my personal experience with gnome, I've found that moving menu items whose names contain spaces causes the behavior you mentioned as not moving.  exiting and restarting alacarte or in some cases relogging into gnome (or killing gnome-panel)  showed the missing item, but it also still existed in it's original category.

---

### Post by botulismo on 2007-05-17
Well, this makes me feel a little better - at least I know I'm not letting something glaringly obvious go over my head... It seemed to me like a menu editor should be a pretty straightforward thing. It would be ideal, really, if you didn't even need a separate menu editor - IE you right click to add a launcher, drag a program over to a different folder if you wanted to replace it, right click to clone a launcher to the desktop, etc;

I believe Windows has most of these options and it's one of the small things that I miss most. I recently installed Ubuntu Studio and while I love it for the most part - stylistically it's great but there's a great deal more programs installed than I need (I went for all of the packages to see if I could teach myself some new programs while I'm using the ones I actually need) and I need to organize them into coherent groups so I can quickly find things! This may take all night.

I'm going to try killing the panel to see if this helps as I edit and if not... we'll see.

---

### Post by hikaricore on 2007-05-17
The panel will respawn.  I was just suggesting killing it after moving a launcher that doesn't seem to move.  :)

This forces the menu to update obviously as the panel has to reload.

---

### Post by botulismo on 2007-05-18
That's what I thought you meant, and yes, it allowed me to edit the menus quite a bit faster as four out of five menu items were "sticking"... thems bad odds.

---

