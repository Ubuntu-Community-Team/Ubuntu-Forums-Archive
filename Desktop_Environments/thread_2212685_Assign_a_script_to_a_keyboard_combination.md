---
title: "Assign a script to a keyboard combination"
date: 2014-03-22
forum: Desktop Environments
---

### Post by Francis4344 on 2014-03-22
Hello!

On Ubuntu 12.04 (with gnome classic desktop, not Unity), I am trying to assign a script (to send pdf file straight to the printer without opening them) to a keyboard combination (CRTL-P).

I edited the keyboard through gnome config editor, (apps, metacity, global_keybinding) and so forth. But it does not work. 
I am following these instructions :[http://ubuntuguide.net/assign-custom-keyboard-shortcuts-on-ubuntu](http://ubuntuguide.net/assign-custom-keyboard-shortcuts-on-ubuntu)

The script works perfectly from the mouse right-click routine. What am I missing?

This is the script 
#!/bin/bash


IFS_BAK=$IFS
IFS="
"


for line in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
   if [[ "$line" = "" || "$line" = " " ]]; then
      exit
   fi
   lpr "$line"
   sleep 1;
done


IFS=$IFS_BAK
IFS_BAK=




Francis

---

