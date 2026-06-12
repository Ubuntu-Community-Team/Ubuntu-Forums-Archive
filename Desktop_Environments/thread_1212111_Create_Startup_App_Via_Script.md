---
title: "Create Startup App Via Script"
date: 2009-07-13
forum: Desktop Environments
---

### Post by Trapper on 2009-07-13
U-904-64
Gnome

Does anyone know how to add an application to a users startup applications list via a bash script rather than using the gui tool?

---

### Post by ajgreeny on 2009-07-13
Do you mean using the cli, because you don't have a gui installed?  If so, I think you would just write your script, save it as an executable shell script and add the shell script to /etc/init.d/filename, then run ```
sudo /etc/init.d/filename start
```in the same way as you can for things like gdm.  Just allow others to support my thoughts before you rush into this, as I'm not absolutely sure.

If you want to know how to add something to the gnome-session-properties startup list, I think you need to copy the shell script to **~/.config/autostart**

---

### Post by Trapper on 2009-07-13
Thanks ajgreeny. You resolved my problem. I have a script a user can run to do an auto setup of a custom app. Just utilizing a copy of the .desktop file for that app that I have in my own ~/.config/autostart and copying it in the user's ~/.config/autostart, as part of the setup script, seems to work to autostart the app at login.

---

