---
title: "File manager question"
date: 2008-02-15
forum: Desktop Effects &amp; Customization
---

### Post by kiwited on 2008-02-15
Is there anything similar to the Xandros File Manager in Ubuntu?
I have found equivalents for pretty much everything else, but would love to have a tool similar to the Xandros one, in particular can rip mp3 by drag and drop and create and burn cd's and view images all from within the file manager.

Kiwited

---

### Post by jan quark on 2008-02-15
I like worker very much

just search in synaptic

---

### Post by ajgreeny on 2008-02-15
Sounds just like konqueror, but I've never used Xandros so don't know.  Konqueror is available for ubuntu and can even be set as the default file manager if you want.

It doesn't come up very often, but every now and then, someone on the Ubuntu Forums wants to know how to change the default file manager in Gnome from Nautilus to something else. It's all been a big mystery until now. Special thanks to forum member ciscosurfer for starting to unravel the mystery. I'm hoping these scripts will finish the job, even though they don't work perfectly.

Changing from Nautilus to Thunar
Step 1: Download this script to your Downloads. Now in Downloads

Step 2: Paste these commands in the terminal:
cd ~/Downloads
chmod +x defaultthunar.sh
./defaultthunar.sh

Changing from Nautilus to Konqueror
Step 1: Download this script to your Downloads. Now in Downloads

Step 2: Paste these commands in the terminal:
cd ~/Downloads
chmod +x defaultkonqueror.sh
./defaultkonqueror.sh

Restoring Nautilus as the default
If you wish to restore Nautilus as the default file manager in Gnome, download this script to your Downloads and paste these commands in the terminal:
cd ~/Downloads
chmod +x restorenautilus.sh
./restorenautilus.sh

---

