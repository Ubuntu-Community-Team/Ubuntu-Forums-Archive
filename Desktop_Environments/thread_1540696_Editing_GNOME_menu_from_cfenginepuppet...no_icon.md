---
title: "Editing GNOME menu from cfengine/puppet...no icon?"
date: 2010-07-28
forum: Desktop Environments
---

### Post by ragtag on 2010-07-28
I'm trying to add applications to the GNOME menu remotely. Creating a .desktop file in /usr/share/applications/ works just fine, but I'm having trouble getting the correct icon. The other desktop files, e.g. pitivi, just define a single name for the icon, and then presumably GNOME looks through /usr/share/icons/??? to find the one to use. The pitivi one is in hicolor/apps, in different formats...but doing the same for mine didn't seem to work.

Where do I put my icon so that it shows up correctly?

---

### Post by ragtag on 2010-07-29
I still haven't figured this out, but after installing a couple of standard programs with apt-get, the icon I had put in for my program suddenly showed up. So I'm guessing there is a command to check for changed icons, that I should run after putting my icons in place. Anyone know what this command is?

---

### Post by ragtag on 2010-08-04
I think I solved this one, so I'll just reply to my own post if someone else needs a solution for this. 

The tool I was looking for was gtk-update-icon-cache. So if your icons are in /usr/share/icons/hicolor/.... you simply run "sudo gtk-update-icon-cache /usr/share/icons/hicolor".

):P

---

