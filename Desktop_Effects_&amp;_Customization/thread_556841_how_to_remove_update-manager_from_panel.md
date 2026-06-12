---
title: "how to remove update-manager from panel?"
date: 2007-09-21
forum: Desktop Effects &amp; Customization
---

### Post by malspa on 2007-09-21
In Dapper, is it possible to remove the update-manager from the the top panel?  If so, how?

I thought about uninstalling it but Synaptic says it will uninstall gnome-app-install, ubuntu-desktop, and update-notifier.

---

### Post by dcstar on 2007-09-22
> **malspa said:**
> In Dapper, is it possible to remove the update-manager from the the top panel?  If so, how?

I thought about uninstalling it but Synaptic says it will uninstall gnome-app-install, ubuntu-desktop, and update-notifier.

The thing in the top panel is the update-notifier, not the update-manager. You can (probably) safely remove that (although why you would not want to know about updates is baffling..................)

---

### Post by Forlong on 2007-09-22
> **malspa said:**
> In Dapper, is it possible to remove the update-manager from the the top panel?  If so, how?
Do a right-click on the icon next time it shows up and uncheck *Show notifications*

---

### Post by malspa on 2007-09-22
> The thing in the top panel is the update-notifier, not the update-manager. You can (probably) safely remove that (although why you would not want to know about updates is baffling..................)

When I right-click on it and go to Preferences, then click on Help, what comes up is the Update Manager Manual, so this is why I assumed that it is the update-manager.

The reason that I want to remove it is because I don't need it.  I can go to Synaptic and find out what updates are available, so it's not necessary for me to have this show up on the desktop.  Maybe you are baffled because you need this reminder, but I don't need it.  Linux is supposed to be about choice, right?  I have also removed the similar "apt-notify" desktop icons from the KDE desktops in Mepis and PCLOS and it's as simple as right-clicking on the icon and removing it.  

> Do a right-click on the icon next time it shows up and uncheck Show notifications

When I right-click on it, the "Show notifications" box is already unchecked.

To be more specific:  Since this is an item that appears on the Notification Area Applet part of the panel, is there a way to control which items show up on the Notification Area Applet?

---

### Post by Forlong on 2007-09-22
Ah, OK... I just thought you were annoyed by the balloon popping up.

If you don't need it at all, you can disable that feature in Synaptic. I'm not on Dapper, so I can't tell you where exactly.
It should be there in *Settings &#8594; Repositories &#8594; Updates* (or something similar).

---

