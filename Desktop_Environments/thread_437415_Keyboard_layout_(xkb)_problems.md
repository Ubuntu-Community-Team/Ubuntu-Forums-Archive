---
title: "Keyboard layout (xkb?) problems?"
date: 2007-05-08
forum: Desktop Environments
---

### Post by lerra on 2007-05-08
Hi, i have installed ubuntu dapper base-system with debootstrap and after that gained a shell/system where i did a apt-get install ubuntu-desktop.
After that i did a vnc installation to be able to get graphical access outside the machine because it is based in a xen guest, no problems there and i join the session but i cant change my keyboard layout from the english to swedish. When i go to (gnome) system-> preference -> keyboard and in the tab layout, in the keyboard model i have "Unknown", in the layout list i have US and i cant add anything. I changed the xorg.conf so it looks like this now:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "se"
EndSection


But it did not work (yes i have rebooted), i did add a panel named keyboard indicator but when i have the mouse over it, it says: "Error loading xkb configuration registry". I reinstalled the package (and deleted the /etc/X11/xkb dir) and restarted but nothing. I have even configured the console to match my keybord layout (it should not be necessary) to qwerty and sv-latin1.

 I am out of ideas now, is there anybody out there that could help me or have experience the same problem?

---

### Post by lerra on 2007-05-10
Interesting, so i am the only one with this problem or is there no help to get?

---

