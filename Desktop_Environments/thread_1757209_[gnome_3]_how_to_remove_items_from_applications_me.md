---
title: "[gnome 3] how to remove items from applications menu?"
date: 2011-05-13
forum: Desktop Environments
---

### Post by u-noob-tu on 2011-05-13
in gnome 3, when i go to activities>applications i either have duplicates (sometimes i do and sometimes i dont) of some programs or no icons for the ones i uninstalled, but they are still there. how do i hide/delete them?

---

### Post by maximo1010 on 2011-05-17
> **u-noob-tu said:**
> in gnome 3, when i go to activities>applications i either have duplicates (sometimes i do and sometimes i dont) of some programs or no icons for the ones i uninstalled, but they are still there. how do i hide/delete them?

In the ALT+F2 box, type "alacarte" (without quotes, of course) and uncheck what you don't want. Navigate around alacarte, check and uncheck items and close after satisfaction. Test it after changing so you know that you have what you want.
This star will help you: [:KS]("http://tinyurl.com/65ftd4u") [FONT="Georgia"]*<(click me!*)[/FONT]

---

### Post by tlhl28 on 2011-05-17
> **u-noob-tu said:**
> in gnome 3, when i go to activities>applications i either have duplicates (sometimes i do and sometimes i dont) of some programs or no icons for the ones i uninstalled, but they are still there. how do i hide/delete them?

First, I'm using Archlinux, gnome3.
I got the same problem.
I have found the file just now. In this way( at HOME ):

```

chord@chord ~ $ find . -name *.desktop
./.config/autostart/bluetooth-applet.desktop
./.config/autostart/workrave.desktop
./.local/share/applications/chrome-http___192.168.1.222_droid_guide_topics_media_index.html.desktop

```

---

### Post by Dlambert on 2011-10-25
Doesn't work in Sabayon

---

### Post by dniolet on 2012-05-27
I'm having this same problem in 12.04.  I'm using the default gnome shell.  When I go to the top left corner and then select applications, there are many duplicate icons of apps, some clear, some pixelated.  If/when I go into "alacarte" there are no duplicates there.  Any suggestions on how to remove the pixelated ones?  I'd assume those are the bad ones.

---

### Post by dniolet on 2012-05-27
> **dniolet said:**
> I'm having this same problem in 12.04.  I'm using the default gnome shell.  When I go to the top left corner and then select applications, there are many duplicate icons of apps, some clear, some pixelated.  If/when I go into "alacarte" there are no duplicates there.  Any suggestions on how to remove the pixelated ones?  I'd assume those are the bad ones.
It's fixed!  While doing something completely unrelated (browsing the Ubuntu Software Center and trying out different apps), the applications menu corrected itself.  While apps were installing, the menu would sometimes revert back to duplicated icons, but then return to being correct.  So far it is staying as it should.

---

### Post by mixoff on 2012-07-26
**alacarte** for menu items, and
```
$sudo update-menus
``` to remove the accumulated duplicate icons.

Cheers!

---

### Post by trondhuso on 2012-09-05
Worked like a charm here.
Ubuntu 12.04
Gnome 3

---

### Post by brookchef on 2012-12-24
I have come across this as well.  The update-menus command will clear the duplicate entries, but they return when I reboot.  How can I get the menu to remain duplicate free?

---

### Post by Frogs Hair on 2012-12-25
Open the main menu and remove the unwanted items. This will not work with Unity. Install alacarte if the main menu does not appear

---

### Post by Colin Keenan on 2013-01-19
I have gnome-shell 3.6.2 and it seems to completely ignore alacarte and update-menus, so that advice is no good. However, there is a good answer here, but it's just not obvious what to do with it. 

tlhl28 has the correct answer:

> **tlhl28 said:**
> First, I'm using Archlinux, gnome3.
I got the same problem.
I have found the file just now. In this way( at HOME ):

```

chord@chord ~ $ find . -name *.desktop
./.config/autostart/bluetooth-applet.desktop
./.config/autostart/workrave.desktop
./.local/share/applications/chrome-http___192.168.1.222_droid_guide_topics_media_index.html.desktop

```

Once you've found all the desktop files in your home folder, look through them for the stuff that you don't want, and delete them. 

For example, I had a top-level "Enthought" category showing up between "Accessories" and "Games" even though I had deleted the Enthought folder so all the links were nonexistent. By looking through all the .desktop files though, I discovered a whole bunch of them started with "Enthought..". I went into that directory and deleted them with "rm Enthought*". Problem solved.

Even better, I figured out how to get applications to show up that weren't before or in better locations. All you do is edit the .desktop file (usually located in /usr/share/applications) and edit or add a "categories" line. For example, if you want a game that you installed in wine to show up in Games, just put "Categories=Game;" in that desktop file. If you want Virtualbox to show up under Office because you've got some office application that won't run under linux, not even with wine, then just edit the Categories line and add Office like this: "Categories=Office;Emulator;System;X-MandrivaLinux-System;Application;" (everything was there already - I just added Office to the beginning of the list).

---

