---
title: "how to edit the popup window when you right-click"
date: 2009-01-05
forum: Desktop Environments
---

### Post by hbral on 2009-01-05
hi everyone.

does anyone know how to edit the popup-menue when you do a right-click.
the default menue only contains like creating a new folder or a document
but i want also to launch applications (for example a terminal) from this menue.

best regards

---

### Post by mcduck on 2009-01-05
There really isn't any easy way to freely configure the right-click menu, but you can add a couple of useful features as Nautilus extensions.

First, installing the "nautilus-open-terminal"-package from repositories will add option to open current directory in a terminal.

Then, any scripts you put into /home/*username*/.gnome2/nautilus-scripts/ will be added to a submenu in the right-click menu. Anything in /home/*username*/Templates/ will appear in the right-click menu under the "Create Document"-option.

Nautilus-image-converter adds option to compress, resize and rotate images from the right-click menu.

Nautilus Actions extension allows creating custom actions that appear in the right-click menu depending on what type of files/directories you have selected.

---

