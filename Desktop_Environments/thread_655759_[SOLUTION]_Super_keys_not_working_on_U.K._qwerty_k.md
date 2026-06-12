---
title: "[SOLUTION] Super keys not working on U.K. qwerty keyboard"
date: 2008-01-01
forum: Desktop Environments
---

### Post by heffo on 2008-01-01
I don't know what causes this bug, I believe it is using sudo dpkg-reconfigure xserver-xorg while using a U.K. QWERTY keyboard.

This post will hopefully fix your U.K. QWERTY keyboard's super keys if they have stopped working with the error:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70200000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

If you don't get that error then theres no harm in trying anyway!

I've seen a few forum posts with people having the same problem but no solutions, however here is your lucky day! The way I worked around it was going to system<preferences<keyboard

Then went to the layouts tab and clicked the Add... button, then set the drop down menu for layouts to U.S. English and left the other drop down as default.

Now the super keys should work but the @ and " keys will be switched round, (2 and ' should be in the same place still). The way I fixed this is by remapping those 2 keys in the configuration files in 
/usr/share/X11/xkb/symbols
and editing the "us" file.

I'll upload a copy of the file that you can use with the re-mapped keys.

Just download the file then backup your original with:
sudo cp /usr/share/X11/xkb/symbols/us /usr/share/X11/xkb/symbols/us.bak
Then put the new file in:
sudo mv /path/to/downloaded/file/us /usr/share/X11/xkb/symbols/us

Then just restart and it should be working fine!

Not a perfect fix but it works well for me!

If this doesn't work for you or you need to switch back simply run:
sudo mv /usr/share/X11/xkb/symbols/us.bak /usr/share/X11/xkb/symbols/us

---

