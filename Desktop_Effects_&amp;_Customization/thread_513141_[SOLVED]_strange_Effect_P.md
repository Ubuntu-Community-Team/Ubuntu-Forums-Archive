---
title: "[SOLVED] strange Effect :P"
date: 2007-07-30
forum: Desktop Effects &amp; Customization
---

### Post by nowshining on 2007-07-30
yep, messed with my system at first a bit earlier last night, well fixed the xserver thing, after booting from a live CD and using that to fix it in the live cd terminal, well odd thing is that The cd ejected as usual when rebooting, nothing no reboot, pushed in the CD tray with cd in it, it ejected it again and then remembered the livd cd reboot didn't work on my computer, so hard rebooted..well now compiz won't even show up in the system prefs or whatever after uninstall and re-install completely did the apt remove cache files, same thing.. :P well since  i got nothing even no effects, just installed beryl - reinstalled the manager, and changed the manger to compiz - effects such as wobbly are still there, however now when I go to the bottom left screen by even touching it with my mouse - yep just by going there, the open windows suddenly become transparent - then scoll to the top of the screen - i mean move up to the top of the screen to just where the bottom is showing, moving back to the edge brings them right back down..  cool, but now I can't move desktops with the key command like I had... so any fixes for this??


EDIT: solved it was in /home/nowshining/.local/share/applications/gnome-compiz-preferences.desktop

where gnome-compiz-preferences.desktop was the application... :) altho I still have some issues to sort out...

---

