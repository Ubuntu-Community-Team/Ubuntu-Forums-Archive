---
title: "Add/Remove programs auto-starts at boot"
date: 2009-01-14
forum: General Help
---

### Post by Bucky Ball on 2009-01-14
Hi all.

Running xfce on my laptop and every time I boot, Add/Remove programs auto-starts, checks for installed and new packages and opens. Checked in Applications/Settings/Auto-started apps and no sign of Add/Remove there.

May have started happening after an update but admit I didn't really notice. Wondering if there is a directory where commands for apps intended to auto-start at boot are kept. System seems to be working fine despite this new 'feature'! :)

Tnx in advance and as always, all suggestions appreciated.

---

### Post by redilyn on 2009-01-16
I've never used xfce but if it has a sessions menu you should check there as well

---

### Post by Bucky Ball on 2009-01-16
Thanks for the suggestion. Xfce doesn't have 'sessions' as such, but on this box I have about 6 different desktop managers including Gnome, so I will drop into one of the others and see if the same problem is occurring, which was my next step. Let you know. (I was using Fluxbox last night and no problems, but that is very different to Xfce and Gnome and not sure there is Add/Remove programs as such).

Anyone else??

---

### Post by Bucky Ball on 2009-01-16
Currently in Gnome/Openbox and no problem with 'Add/Remove' auto-starting after login. Only in Xfce so must be a setting there. But as I mentioned in my first post, where would this setting be, what directory/file?

---

### Post by urukrama on 2009-01-17
Are you sure you did not save a previous session where you had the Add/Remove application open? I believe XFCE automatically saves the session by default when you log out (or shutdown, etc.), and will therefore when it starts reload all the applications that were running when you logged out. 

To disable this feature, you have to untick the "Save Session" box that is just under the buttons to restart, shutdown, hibernate, etc. in the log out dialog. If you are not looking for it, it is easy not to notice it. I've had similar issues because of this in the past. You could just load a new session, close the Add/Remove application, and log out while saving the (now 'empty') session. 

Alternatively, I believe the session details are stored in ~/.config/xfce4-session. The other Xfce settings are stored in ~/.config/xfce4

---

### Post by Bucky Ball on 2009-01-17
> **urukrama said:**
> Are you sure you did not save a previous session where you had the Add/Remove application open? I believe XFCE automatically saves the session by default when you log out (or shutdown, etc.), and will therefore when it starts reload all the applications that were running when you logged out. 

To disable this feature, you have to untick the "Save Session" box that is just under the buttons to restart, shutdown, hibernate, etc. in the log out dialog. If you are not looking for it, it is easy not to notice it. I've had similar issues because of this in the past. You could just load a new session, close the Add/Remove application, and log out while saving the (now 'empty') session. 



Yes, I am aware of that elusive little checkbox. Such a simple fix, why didn't I think of that! Booted, closed Add/Remove, Logout after ticking save session, log back in and problem solved. Thanks! Too easy.

---

