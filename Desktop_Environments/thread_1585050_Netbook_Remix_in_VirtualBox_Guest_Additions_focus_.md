---
title: "Netbook Remix in VirtualBox Guest Additions focus problem"
date: 2010-09-30
forum: Desktop Environments
---

### Post by DrJohn999 on 2010-09-30
I am supporting several users with UNR on their laptops, so on my AMD-64 machine I installed UNR 10.04 in VirtualBox 3.2.8r64453, updated upgraded, installed DKMS and gcc, then added the Linux-x86 Guest Additions from the supplied Guest Additions iso. So far so good.

But, there is a problem with the UNR desktop: whenever I try to run anything, for example FireFox, the app starts and then the focus immediately switches back to the desktop. Clicking on the app's icon in the top left panel, or using alt+tab to switch causes the selected app to draw on the screen for a moment, then the focus switches back to the desktop. If I'm fast I can get a character to appear on the command line in terminal, but that's it.

Result: I can get nowhere. This behavior only began after rebooting after installing the guest additions. It occurs whether in normal, fullscreen, or seamless mode. Uninstalling guest additions doesn't seem easy since I can't get to a console. Nothing in this install yet, so I'll nuke it and reinstall w/o the Guest Additions but it's a shame not to have the GA's available.

---

### Post by DrJohn999 on 2010-09-30
Further information: reinstalled, but activated user logins so I can choose Gnome or UNR at login. Installed DKMS and Guest Additions from a Gnome session, rebooted, no problem with focus in Gnome.

Same problem found in UNR (focus keeps popping back to desktop) but by choosing 'switch from <username>...' and switching back to the UNR session the problem does not occur; can switch between apps without loosing the focus. Logging out and in with a UNR session the problem appears again; choosing 'switch from <username>..' and switching back fixes it. Nice and repeatable.

What th' ??

---

### Post by P4man on 2010-09-30
Im guessing this is somehow related to "maximus", its part of the default UNR and is used to force maximize all windows and remove window decorations and such. Try disabling it (should be in the startup app lists, just uncheck it there).

---

