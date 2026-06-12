---
title: "Remove network locations from desktop"
date: 2007-03-13
forum: Desktop Environments
---

### Post by MattNuzum on 2007-03-13
I have a lot of "network locations" saved. Every time I create a new one it is added as a shortcut to my desktop. The only way I can get rid of them is to remove the network location, which cripples this feature. I can't seem to move them to a folder or hide them.

Anyone know a way to get these off of my desktop?

I also have a cd icon and icons for my sd card and usb thumb drive. I don't mind them being there, but I rarely use them from my desktop. More often, I just go to the "places" menu. Therefore it would be OK if they left my desktop too.

---

### Post by daengbo on 2007-03-13
This is probably configurable if you go deep inside the Gnome configurations, but you'll need to use a GConf editor for that. I don't thinks it can be disabled in the standard interface.

---

### Post by MattNuzum on 2007-03-13
Ah, beautful idea, thanks.

/apps/nautilus/desktop/volumes_visible

Fixes that problem nicely. What am I going to do with all this new space now... :-)

---

