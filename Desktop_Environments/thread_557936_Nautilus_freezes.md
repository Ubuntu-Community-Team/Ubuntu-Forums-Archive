---
title: "Nautilus freezes"
date: 2007-09-23
forum: Desktop Environments
---

### Post by howardf42 on 2007-09-23
I have recently encountered this problem when I attemp to open Nautilus.  I have the same results no matter what folder or partition I'm trying to open.  I am running Feisty Fawn and have been running successfully fot quite some time.  

When I open, for instance the File System folder, Nautilus opens with all the folders and files listed, but everything is frozen in the window with the exception of the window control buttons at the upper right corner.  When I click on the Close (X) button, I get a "File Browser is not responding" message.  I click on Force Quit and the window closes and is replaced with a new Nautilus window opening the Home folder with the same results.  

Following an earlier thread, I tried ```
gksudo nautilus
``` and got the following results :```
(nautilus:26088): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing nautilus-open-terminal extension
Initializing gnome-mount extension
Initializing nautilus-image-converter extension
Initializing nautilus-share extension
Nautilus-Share-Message: REFRESHING SHARES
Nautilus-Share-Message: ------------------------------------------
Nautilus-Share-Message: spawn arg "net"
Nautilus-Share-Message: spawn arg "usershare"
Nautilus-Share-Message: spawn arg "info"
Nautilus-Share-Message: end of spawn args; SPAWNING
``` and another freezing Nautilus window.

All suggestions are welcome.

---

