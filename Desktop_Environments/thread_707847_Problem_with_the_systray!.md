---
title: "Problem with the systray!"
date: 2008-02-25
forum: Desktop Environments
---

### Post by h4p0 on 2008-02-25
Hello everyone!
I've a problem with the systray in gnome-panel.
I cannot click any icon to access any menu with right or left click!
The only menu I could see (clicking with the right button ) is the systray menu [help,report a bug, remove from panel,lock to panel]

But when I click with the left button (for example on nm-applet to select a wireless network) the only thing I obtain is that the cursor changes to the "all-side resize" shape (do you know what I mean?)
The one with the crossed four arrows...like I could to move around the selected item...
That's make me very bad! :mad:
I cannot select a wifi, i cannot change amarok's song, and many more operations are unaccessibles...
Some help?

---

### Post by bruno9779 on 2008-02-25
I had a similar problem, and this command line helped:

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by h4p0 on 2008-02-25
:KS:KS:KS Simply LOVELY! :KS:KS:KS
Thank's a lot!!

h4p0

---

### Post by Locutus_of_Borg on 2008-02-25
I have that same problem, but it is only affecting my trash applet, I added that to the disabled applets in the panel section of gconf, but I would like to be able to view/empty my trash folder without having to navigate to ~/.trash

that command did not solve this.


Oh, and I cannot seem to click on anything in the window list either, but I use AWN to navigate amongst open applications so that is not such an issue

Any other solutions though would be welcome.

---

