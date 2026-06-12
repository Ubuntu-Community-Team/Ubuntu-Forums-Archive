---
title: "Panel Spawning Madness!"
date: 2005-06-24
forum: Desktop Environments
---

### Post by chaumurky on 2005-06-24
Here's what happened: 

My main panel crashed and I chose the option to restart it. The thing is another one started up automatically at the same time and so another error came up saying "I've detected a panel already running, and will now exit." When I click ok ANOTHER panel starts up and gives me the same message. I can't get out of this loop! I tried ending/killing the process but another is spawned right afterwards. So I log out - to find 2 instances immediately fighting each other again. 

I guess a config somewhere is calling 2 instances of this panel on login. If that is the case, where should I be looking? Maybe it's something else. I really want to get it solved before the wife gets home as I'm trying to convince her that Ubuntu causes less hassles than her old XP install. Any takers?

EDIT: Oh yeah, we're talking Gnome here...

---

### Post by elvis on 2005-06-24
Did this happen out of the blue, or after an upgrade?

A recent upgrade of GNOME for me also broke most of my desktop and panels.  To fix it, I killed X, and from a non-GUI CLI I moved all my ~/.g* files and directories (essentially .gnome, .gstreamer, .gconf, .gtk, etc) to a temporary folder (nuking most of my custom desktop preferences) and then fired up X and GNOME again, and all was working well.  Obviously during the upgrade, some of my preferences weren't compatible with the new version.

Ensuring you move them somewhere and not delete them means if it doesn't solve your issues, you can move them back again without destorying anything. :)

---

### Post by chaumurky on 2005-06-24
[QUOTE=elvis]Did this happen out of the blue, or after an upgrade?

A recent upgrade of GNOME for me also broke most of my desktop and panels.  To fix it, I killed X, and from a non-GUI CLI I moved all my ~/.g* files and directories (essentially .gnome, .gstreamer, .gconf, .gtk, etc) to a temporary folder (nuking most of my custom desktop preferences) and then fired up X and GNOME again, and all was working well.  Obviously during the upgrade, some of my preferences weren't compatible with the new version.

Ensuring you move them somewhere and not delete them means if it doesn't solve your issues, you can move them back again without destorying anything. :)[/QUOTE]
 I was just trying to move or unlock an item on the panel. Nothing out of the ordinary.

---

### Post by chaumurky on 2005-06-24
Well as what often happens I eventually sorted it out. I went to System >Preferences>Sessions and in the 'Current Session' section there they were: 2 gnome panels with the 'restart' option set. I deleted one, clicked OK on the error message window and it didn't come back. Perhaps in future there should be some option in the error message to remove the offending item. Oh well, the wife needn't know...   :wink:

---

