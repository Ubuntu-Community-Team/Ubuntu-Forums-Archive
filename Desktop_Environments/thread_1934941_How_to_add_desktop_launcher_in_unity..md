---
title: "How to add desktop launcher in unity."
date: 2012-03-03
forum: Desktop Environments
---

### Post by usalabs on 2012-03-03
This is for those that use the unity desktop on Ubuntu version 11.x up to 12.04 and beyond.

Personally, I find not being able to create a desktop launcher for programs is the dumbest move that's ever been made, as some programs are created as a binary file and can only be executed either by directly double clicking and selecting 'Run', or using './<name>' in a terminal.

First open a terminal and type this:-

sudo apt-get install --no-install-recommends gnome-panel

then in the same terminal window, create a bash script using any of your favorite CLI text editors,,,(for this example I use nano).

nano create-launcher.sh

then in the editor type this:-
```

#! /bin/bash

gnome-desktop-item-edit ~/Desktop/ --create-new

```then save and exit the editor, then make the bash script executable using:-

chmod +x create-launcher.sh

then the most important step, is to create a desktop launcher to this script so that you would not have to keep opening a terminal,,,,at the terminal prompt, type:-

./create-launcher.sh

a pop up window will appear,,, in the 'Name' box enter the name of the launcher, (I used Create Launcher),,, then click on 'Browse' and browse to your home folder where you created the bash file, and select the bash script, then click 'Ok'

This will create a launcher on your desktop, ready for you to simply double click and create any launchers straight to your desktop.

You can now exit the terminal,,, job done.

---

