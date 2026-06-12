---
title: "Gnome Settings not &quot;Sticking&quot;"
date: 2006-11-03
forum: Desktop Environments
---

### Post by napsilan on 2006-11-03
Gnome seems to not be saving my settings that I set using the system->preferences menu.  So far, I know that it has not saved session->startup changes, as well as keyboard changes.  For the startup changes, I had to manually sudo gedit a file in ~/.config/autostart ([http://www.ubuntuforums.org/showpost.php?p=1707258&postcount=4)](http://www.ubuntuforums.org/showpost.php?p=1707258&postcount=4)).  For the keyboard settings, I was trying to get rid of the international keymap that needed 2 hits to type "'" and "~".  Changing the settings in keyboard->layouts did not seem to have any effect.  I had to manually edit my /etc/X11/xorg.conf files and change pc105 intl to pc101. Gnome then complained that the gnome keyboard settings didn't map the Xserver settings.  

My end question is this--

Is something in my gnome settings hosed to the point where it does not have root privelages when it should?

Edit:  Edgy x64

---

