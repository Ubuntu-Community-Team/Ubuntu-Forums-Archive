---
title: "I broke my gnome!"
date: 2007-03-28
forum: Desktop Environments
---

### Post by strangedezign on 2007-03-28
I am working with a new install of Ubuntu from the Ultimate Edition 1.3 cd.  I was messing with themes when I decided to choose a new icon theme.  I clicked on one of the ones that I believe came with the UE.  I guess that was a mistake since everything on the screen immediately disappeared except for the desktop.  I restarted gnome and now it just hangs at the splash screen and won't load anything even after waiting several minutes.  

I have no trouble starting KDE.  Anyone have any suggestions.  Maybe the icon set was corrupted???  This is just weird.

btw, I was running beryl at the time

---

### Post by ComplexNumber on 2007-03-28
i bet you selected a cursor theme. 

at the login screen. choose failsafe terminal as your session. then go to:
 /home/<your-username>/gconf/desktop/gnome/interface

you should a file called %gconf.xml

now type in **nano  %gconf.xml** and change the icon theme to something like 'Human'.

then type in 'exit' to go back to the login screen.





btw after you've succeeded with it, i can show you how to make the cursor themes disappear from the list of icons in gnome-theme-manager. it basically involves finding all the cursor themes in /usr/share/icons and editing the  index.theme file in each theme so that it has the following line:
**Hidden=true**

---

### Post by strangedezign on 2007-03-28
That was it!  Thanks a lot for the help.  Any idea why the cursor themes would show up there in the first place?

---

### Post by russellc on 2007-03-28
This happened to me a couple days ago when I accidentally clicked on a mouse cursor theme. Figured it out easily, but was strange how the cursor themes just decide to be there :p

Changes are, the gnome-theme-manager isn't smart enough to figure out that those themes are cursors since, after all, they are being held in the directories in which icons are kept (/usr/share/icons, ~/.icons, etc)

---

### Post by ComplexNumber on 2007-03-29
its up to the author of the cursor theme to include the line 'Hidden=true'.  but yes, i  agree. they shouldn't show up amongst the icons by default.

---

