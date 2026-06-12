---
title: "GNOME not loading properly"
date: 2007-12-11
forum: Desktop Environments
---

### Post by IndyNosebone on 2007-12-11
Hey Everyone,

Recently, for whatever reason, whenever I boot Ubuntu and login to my (or any) account, the GUI improperly loads. Icons are gray, color schemes are dull, and everything seems very... Windows95-esque. The current solution to my problem is to run the command "gnome-settings-daemon" after login and *poof!* the problem is instantly solved.

My issue is that I would like to understand (1.) why this is happening, and (2.) how to prevent having to manually executing the "gnome-settings-daemon" command in the future, essentially automating it, and (3.) knowing the differences between X and GNOME (to my knowledge, they are both GUIs from different developers, and seem to both exist and compete on Ubuntu..)

Thanks In Advance,
Ed

---

### Post by PeterJS on 2007-12-11
> **IndyNosebone said:**
>  
My issue is that I would like to understand (1.) why this is happening, and (2.) how to prevent having to manually executing the "gnome-settings-daemon" command in the future, essentially automating it, and (3.) knowing the differences between X and GNOME (to my knowledge, they are both GUIs from different developers, and seem to both exist and compete on Ubuntu..)

Thanks In Advance,
Ed

3) Gnome and X are just different layers of the same system. At the very bottom of the stack are the graphics drivers, loading them doesn't do anything particularly impressive, but is essential for the upper layers. On top of the graphics drivers is X itself, X is what actually manages keyboard and mouse input, drawing the most basic "desktop" it's just a gray hash pattern, and drawing the cursor. On top X sits the Gnome Desktop environment, which is made up of a bunch of sub components, nautils is both the file browser and draws the actual desktop with the icons, the panels, the metacity window manager, the GTK tool kit, and a bunch of helper apps. What metacity does is draw the close buttons, and borders around all your windows. And GTK draws all the various widgets, like buttons and scroll bars of each program.

1) The gnome-settings-daemon isn't loading up automatically like it should, this is a problem because it's function is to load the users settings including the theme that should be used.

2)If you go to System > Preferences > Session.  There's a button to add a  new application to load with the desktop. If you add a new entry for the command *gnome-settings-daemon* that should start it when you log in. This isn't the Right Way(tm), but it should fix the problem.

---

### Post by IndyNosebone on 2007-12-11
Awesome! Worked flawlessly!

Thank you very much PeterJS. :)

---

