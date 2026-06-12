---
title: "Broken Gnome Menu Bar"
date: 2006-09-27
forum: Desktop Environments
---

### Post by Iskra on 2006-09-27
Somehow I have managed to lose the access to the applications section on my main menu panel applet. When I tried to use an alternative menu bar applet I got the error "Failure loading -- applications.menu".

The strange thing is, this menu along with all of its components are still visible (and presumeably editable) in Allacarte. Is there anyway I can fix this? Thanks in advance :)


Kevin

---

### Post by Robor on 2006-09-27
> **Iskra said:**
> Somehow I have managed to lose the access to the applications section on my main menu panel applet. When I tried to use an alternative menu bar applet I got the error "Failure loading -- applications.menu".

The strange thing is, this menu along with all of its components are still visible (and presumeably editable) in Allacarte. Is there anyway I can fix this? Thanks in advance :)


Kevin
Maybe try creating a new panel and adding all of the desired features you want then delete the old panel that's not functioning properly.

---

### Post by Iskra on 2006-09-27
> **Robor said:**
> Maybe try creating a new panel and adding all of the desired features you want then delete the old panel that's not functioning properly.

No, unfortunately it seems to have nothing to do with the panel itself--the menu bar is broken no matter what panel I put it on and I am not having any trouble with any other aspect of the GNOME panel. It seems to me that the data files contain the menu data for the applications menu (both the places and system menus work fine) are corrupted. Is there any way I can rebuild this?

---

### Post by Robor on 2006-09-29
Tried changing sessions (try default Gnome) before logging in with your current username?  If that doesn't work try creating another user and log in as it and see if you get the same issue.

If it's a corruption in your 'profile' I can send you a document to help clean things up.  Speaking of that...  credit to 'drag' on AnandTech Forums.  :)

---

### Post by Iskra on 2006-09-29
> **Robor said:**
> Tried changing sessions (try default Gnome) before logging in with your current username?  If that doesn't work try creating another user and log in as it and see if you get the same issue.

If it's a corruption in your 'profile' I can send you a document to help clean things up.  Speaking of that...  credit to 'drag' on AnandTech Forums.  :)

That seems to be the case. Changing sessions has no effect. It works fine with other the users.

---

### Post by Iskra on 2006-10-03
Any ideas short of creating a new user? I'd really like to fix this.

---

### Post by ayllu on 2006-11-09
To fix this use yor live cd and copy the files etc/xdg/*.menu and copy in the same directory in yor file system. If you dont have the live cd try to find applicatios.menu, preferences.menu, settings.menu

Good Luck

---

