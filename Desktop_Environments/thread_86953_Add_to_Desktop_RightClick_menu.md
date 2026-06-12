---
title: "Add to Desktop RightClick menu?"
date: 2005-11-06
forum: Desktop Environments
---

### Post by NewWithoutClue on 2005-11-06
I want to add to the "Create New" section of the right click menu.
I would like to add an option to create a new shell script ( .sh ), i know it doesn't have to have that extension to be labled a shell script, but it would be nice to have automatic syntax highlighting when opening the file.

Does anyone know how to add to the rightclick menu?

Regards,
Paul.

---

### Post by audax321 on 2005-11-06
I use Gnome, so I might not be of much help, but if you type:

kde-config --path templates

you should get a path to your templates folder. This might be global (requires root access), but there could be a local one under /home/username/.kde/<whatever the rest of the path returned by the above is>

You would create the file in there. But to see how its done check the global path  that was returned and just copy the way KDE's default templates were put in. In Gnome you just make a Templates folder in your home directory and throw whatever empty files you want in it...but KDE has to go and complicate everything :razz:

---

### Post by NewWithoutClue on 2005-11-07
All is working as expected, thanks.

Paul.

---

