---
title: "Menu Editor: Eliminate Uninstalled Wine Apps"
date: 2007-02-10
forum: Desktop Environments
---

### Post by tylersticka on 2007-02-10
Greetings,

I recently saved a laptop computer from the clutches of obsolescence, installing Xubuntu 6.10 (Edgy) and setting it up with everything necessary.

I initially installed Photoshop 5.5 under WINE, but uninstalled the app when it wasn't working properly.

The problem is that the Program now appears under a Wine submenu in my Applications drop-down. If I select "Adobe Photoshop 5.5" or "Uninstall Adobe Photoshop 5.5," I get an error saying the file isn't found.

The Menu Editor isn't any help, because all it has in place of most of the submenus is an "include" linking to an external system list of applications I can't find.

Does anyone know how I can edit this so the Wine menu doesn't think it still has Photoshop installed? Any help would be very appreciated.

Alternatively, if anyone has a link to a really good tutorial on installing Photoshop 5.5 (or any older version) to work with Wine, I would appreciate it. I love GIMP, but I'm a designer and at times I require native PSD support.

Thanks for your time, let me know if you need more information!

---

### Post by tylersticka on 2007-02-11
Bump!

---

### Post by Ryan_B on 2007-02-13
Did anyone find an answer to this? I installed Sketch up and uninstalled it but it remains in my drop down menu.

Any ideas?

---

### Post by oscarmeyer51 on 2007-04-18
Just ran into this myself. If you managed to uninstall the app correctly within wine or in a terminal window and the app is still showing up in the drop down Applications menu under wine, you can do the following (this is for the Gnome Desktop):

1)  Select System-Menu Layout from the main panel.
2)  Find your wine folder in the left pane of the Menu Layout window
3)  Expand the wine folder to see any/all the orphaned apps (uninstalled, but still showing up in the wine menu)
4)  Select each uninstalled program in the left pane so that it shows up in the right pane (you have to do this one at a time for each app).
5)   You have to deselect each individual item (I had an uninstall and a program in one folder).
6)   Once the item(s) are deselected (the Show column), you should be able to right click on the item and select the 'Delete' option from the popup window.
7)  Be patient, for some reason this is fairly slow (You may have to restart the Desktop after you are done).
8)  This worked about 50% of the time for me, the last resort is to remove the wine package and then reinstall it.

Not to knock wine, but this is just one more reason to find native apps that will do what you need. (I unfortunately have to use some remote connection software into work and Infernal Exploder is the required interface, and I do mean required!).

Good Luck!

---

### Post by YokoZar on 2007-04-19
In the future, if you want to uninstall a Wine program, you can use Wine's built in uninstaller application by running **wine uninstaller** from a terminal.  If the Wine start menu isn't cleared up yet, you can then run **wineboot** to simulate a Windows reboot.

Yes, I know there should be shortcuts to these two applications in the Wine menu, I'm working on it ;)

---

### Post by sergius248 on 2008-06-24
I just went in the "edit menu" (right click in "Applications") selected Wine and deselected the relevant (Wine menu)programs.
I could noterase them, but the entries will not show up.
Use Ubuntu 8.04.

---

