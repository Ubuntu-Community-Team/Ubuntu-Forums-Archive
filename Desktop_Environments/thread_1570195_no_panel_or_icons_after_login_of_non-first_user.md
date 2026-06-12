---
title: "no panel or icons after login of non-first user"
date: 2010-09-07
forum: Desktop Environments
---

### Post by memphisrich on 2010-09-07
First user, everything still normal. All other users and any added users basically have no desktop now. Background and arrow are there, but no right-click no panels. Have tried every option in other similar posts including deleting .config, .gnome2, etc files. Also tried all the commands at [http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html), to no avail.

.xsession-errors log reports :

gnome-session[26291]: WARNING: Unable to find provider 'gnome-panel' of required component 'panel'
gnome-session[26291]: WARNING: Unable to find provider 'nautilus' of required component 'filemanager'
___________________________________________________

I cannot locate the particular script the /etc/Xsessions runs to launch these commands, but first (still working) user does not get these errors in log.

I can login user with xterm session and launch gnome-panel, which provides some functionality, but this basically sucks, because there is no window manager. I have tried changing themes and various compiz stuff, but no success yet. Even removed and reinstalled compiz.

Any help is much appreciated.

---

### Post by memphisrich on 2010-09-08
Solved!
Don't know why but /usr/share/applications/nautilus.desktop & gnome-panel.desktop were gone. I would blame it on an upgrade, but no related applications are in the current upgrade history, so I don't know how they were lost. 

The reason that first user worked, was because .local/share/applications for this user had these files. Temp solution was to copy .local ones to another user to test. It worked.



Permanent solution: reinstall nautilus, and gnome-panel data, which I did via Synaptic. The missing files are restored.

---

### Post by arrange on 2011-10-11
Thanks man, that saved me from headaches.

In my case I was playing with ```
xdg-desktop-menu uninstall
``` and forgot to revert that back.

Thanks again.

---

