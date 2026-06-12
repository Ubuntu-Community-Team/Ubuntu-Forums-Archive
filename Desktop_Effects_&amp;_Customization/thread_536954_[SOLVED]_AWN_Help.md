---
title: "[SOLVED] AWN Help"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by Magneticgravity on 2007-08-28
When i start up Linux, i get the AWN dock, though not the apps i had put on it.

Before, i had simply dragged an app, onto the dock, and it had stayed now, but when i restart, its gone, apart from the wastebasket. I havent used the launcher in the AWN manager because it didnt work.

---

### Post by dav9000 on 2007-08-28
Ok, this is what I do to avoid losing all my launchers:

Add the ones you would like to have on AWN to the desktop via right click "add to desktop". Once you have them, move all of them to /usr/share/avant-window-navigator. From there, drop them onto  the dock at the bottom in the order you want them to appear. This way they will never disappear again.

Hope this helps!

---

### Post by b0ng0 on 2007-08-28
For mine I just created a folder in my /home path called .awn (or .avant-window-navigator I can't remember but I have both). 

Then I selected the launchers I wanted from the Gnome Menu and put them on the desktop (right-click and go add to desktop). I then dragged each one onto the AWN bar and then moved them all to the .awn folder in /home.

I know this might sems like a long-winded way of doing it but it has worked for me.

---

### Post by notwen on 2007-08-28
You may also want to try navigating in Nautilus down to usr/share/apps and once there simply drag each application you're wanting a launcher for to AWN.  Save your session, reboot and check to see if they're still there.  This way has always worked for me every time since I've learned of using this method.  Good luck. =]

---

### Post by Magneticgravity on 2007-08-28
Ahh! None of those work because either theres no an AWN file in usr/share/app or i cant make one to put the launchers in (dont have permissions!!)

Ive figured if i put the apps on the desktop, they will stay on the dock when i reboot because they're on the 'Launcher' tab in AWN manager. If i move them anywhere else, they'll disappear off the list and won't be there when i reboot.

---

### Post by Magneticgravity on 2007-08-28
Bump.

---

### Post by ayoli on 2007-08-28
you can try to add launchers using gconf-editor
first close awn, then hit alt+F2 and enter:
```
gconf-editor
```
go to :
```
/apps/avant-window-navigator/window_manager/launchers
```
and edit this key, this is a list where you add each launcher with full path, like for ex:
```
/usr/share/applications/*launcher_name*.desktop
```
just be sure that the .desktop file exists under the path you give.

---

### Post by Magneticgravity on 2007-08-28
Thx alot, done it now :)

---

