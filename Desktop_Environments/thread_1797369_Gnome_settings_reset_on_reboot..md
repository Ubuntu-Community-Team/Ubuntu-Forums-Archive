---
title: "Gnome settings reset on reboot."
date: 2011-07-05
forum: Desktop Environments
---

### Post by u-slayer on 2011-07-05
Some of my settings don't stick after I reboot. The window list widget disappears, the buttons go back to the left side and so on. I tried inserting the following into a script that runs when I startup the machine:

```

#!/bin/bash
#Disable update manager pop up
gconftool -s --type bool /apps/update-notifier/auto_launch false

#No icons on desktop
gconftool-2 --type=Boolean --set /apps/nautilus/preferences/show_desktop false

#CTRL-ALT-DELETE
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

############################ 10.04 Fixes
#Buttons go on the right!
#http://www.ubuntugeek.com/mark-shuttleworths-response-to-left-side-button-criticisms.html
gconftool-2 --set /apps/metacity/general/button_layout --type string “menu:minimize,maximize,close,spacer”

#Text address bar
#http://www.webupd8.org/2010/05/use-text-mode-location-bar-in-nautilus.html
gconftool-2 --type=Boolean --set /apps/nautilus/preferences/always_use_location_entry true
```

But I can't get the script to run automatically correctly. I tried adding sudo -u $user myscriptname to /etc/rc.local but for some reason that doesn't do anything.

---

### Post by u-slayer on 2011-07-06
hello?

---

### Post by u-slayer on 2011-07-10
sigh

---

