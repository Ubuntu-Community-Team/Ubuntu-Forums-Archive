---
title: "Belgian keyboard layout in KDM and TTY's?"
date: 2005-05-03
forum: Desktop Environments
---

### Post by greatshape on 2005-05-03
Hi, I 'm running kubuntu and everything (also keyb layout)is working fine in kde.
But how do i set the default language in kdm and the tty's to a belgian layout?
I already STF and changed in /etc/X11xorg.conf the keyboard language to be and restarted the system, but the problem remains. 
 :-? It stays querty and i need azerty

Any suggestions? ( i already tried be-latin1 but that didn't work also)

xorg.conf:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "be"
EndSection


Regards, steve

---

