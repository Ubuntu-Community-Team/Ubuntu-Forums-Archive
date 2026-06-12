---
title: "Show Applications no longer in the absolute bottom left"
date: 2021-10-15
forum: Desktop Environments
---

### Post by albatorsk2 on 2021-10-15
Hi,

I just upgraded to Ubuntu 21.10 from 21.04 and have come across something very annoying. The Show Applications grid icon in the bottom left of the desktop s now one pixel raised from the bottom of the screen. Now, if it was just aesthetics I wouldn't mind (not even noticeable), but that also means I can't quickly drag my mouse pointer down to the corner of the screen and click the icon, now I have to aim carefully when I want to click Show Applications.

Is this a bug, or a misconfiguration I could have made somewhere in GNOME? Is there a way for the end user to adjust it and place it firmly in the bottom left corner again?

Thank you.

---

### Post by vanadium on 2021-10-17
In vanilla Gnome Shell, the dash is shown leaving some space to the bottom. Still, there, the icons are still active when the cursor is at the full bottom of the page, thus outside of the slightly lighter colored box. This is, therefore, not a Gnome misconfiguration (they do that "right" – even though that is not consistent with the visual appearance), and likely also not a misconfiguration from your part. Likely, it is an  issue with the Dash to Dock extension (which the Ubuntu dock is based upon).

---

### Post by monkeybrain20122 on 2021-10-18
This is gnome 40. You can restore the vertical dock layout with either dash to dock or dash to panel extension. Since you did an "upgrade" the ubuntu dock that was left over no longer works (d to d has been broken for gnome 40 for a while, it seems that it has only updated to work for gnome 40 very recently, the "ubuntu dock" is a crippled version of d to d), just uninstall  ubuntu dock (or dash to dock if it was installed and remove all its files in ~/.local/share/gnome-shell/extensions), then install dash to dock from the genome extension website.

---

### Post by ActionParsnip on 2021-10-20
You can press Windows Key + A to show the applications window. Much faster than swinging a mouse down to the bottom of the screen

---

