---
title: "nm-applet eth0 grayed out"
date: 2011-08-17
forum: Desktop Environments
---

### Post by solamour on 2011-08-17
I installed a minimal system using the "Alternate" method with Fluxbox, NetworkManager, and nm-applet. Everything works OK, except that the "Edit" button for "Auto eth0" is grayed out. I can add/edit/delete a new connection, but "Auto eth0" is not editable even if I do "su nm-applet". Any suggestions on what to look for?
__
sol

---

### Post by fdrake on 2011-08-17
maybe the device is busy thats why you cannot edit it.. try to disable the network first.

---

### Post by solamour on 2011-08-18
One thing I noticed is that when I click on nm-applet's status icon in a standard installation of Xubuntu, "Enable Networking" is checked. And when I select "Edit Connections..." from the menu, I can select "Auto eth0" and edit it as well.

But on my system (bare installation with Fluxbox), "Enable Networking" is checked, but it's grayed out. I think that might have something to do with "Auto eth0"'s not being editable.

I verified the following files from Xubuntu, but they were identical.

/etc/NetworkManager/NetworkManager.conf
/etc/dbus-1/system.d/NetworkManager.conf
/etc/dbus-1/system.d/nm-applet.conf

I'd appreciate any suggestions.
__
sol

---

