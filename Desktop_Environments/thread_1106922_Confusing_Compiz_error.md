---
title: "Confusing Compiz error"
date: 2009-03-26
forum: Desktop Environments
---

### Post by xJoo Unitx on 2009-03-26
Hi, I simply logged into my computer today and now I have an error in Compiz and I can't even enable desktop effects.. this is the output of "compiz" in the terminal

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "activate_window_menu"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_on_all_workspaces"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_group"
Window manager warning: "" found in configuration database is not a valid value for keybinding "cycle_windows"
Window manager warning: "" found in configuration database is not a valid value for keybinding "run_command_terminal"


Any help would be appreciated

---

### Post by zolek78 on 2009-03-26
It seems like i have the same problems. Something happened to me today as well. I can log in and thing looked normal except i cant see anything. My desktop was completely black. Someone helps pls

---

### Post by xJoo Unitx on 2009-03-27
a kind of unsatisfactory fix for me.  I updated the nvidia drivers from 180.22 to 180.29 and I was able to enable the visual effects through "change desktop" again.

Probably reinstalling the drivers if you already have them will fix it, but I still want to know why restarting a computer would make parts of my computer disappear.

---

