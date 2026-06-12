---
title: "Nautilus script to create .rar archive from directory?"
date: 2006-04-02
forum: Desktop Environments
---

### Post by mmcmonster on 2006-04-02
This may be a stupid question, but:

Does anyone have a script (that I can put in ~/gnome2/nautilus-scripts/ ) that will take a directory (or maybe a file) that I right-click on and change it into a .rar achive with the same name (so it doesn't need any user input)?

ie: I open nautilus, right-click on a folder "folder1", and run the script.  The script creates a fie "folder1.rar", with the compressed contents of the folder in it.

---

### Post by jamesford on 2006-04-02
you will find some like that here i think [http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

---

### Post by Gustav on 2006-04-02
It should probably work with something like this:
```
#!/bin/bash
#

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	rar a -r "$uri".rar "$uri"
done
```
If you have installed the package rar. 
(it works for single files as well)
(if you mark several directories (or files) and start the script there will be a single archive created for each)

edit:added "'s so it will work on directories with spaces in the name

---

