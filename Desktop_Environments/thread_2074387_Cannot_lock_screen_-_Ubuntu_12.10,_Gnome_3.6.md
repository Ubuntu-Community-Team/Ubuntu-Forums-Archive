---
title: "Cannot lock screen - Ubuntu 12.10, Gnome 3.6"
date: 2012-10-21
forum: Desktop Environments
---

### Post by dandaman96 on 2012-10-21
After upgrading from 12.04 and Gnome 3.4 to 12.10 and Gnome 3.6, I have lost the ability to "Lock" my screen.  Using either keyboard shortcuts (Super + L, Alt+Ctrl+L) or the menu option (user menu in top right of screen, "Lock"), nothing happens.  

Can anyone suggest a solution or a log file in which to begin researching a solution?

---

### Post by toobuntu on 2012-10-22
You can lock the screen manually from a terminal.
```
$ gnome-screensaver-command -l
```

-l Tells the running screensaver process to lock the screen immediately

---

### Post by dandaman96 on 2012-10-22
Shamefully, I have to report that part of my problem has been solved.  As it turns out, gnome-screensaver was not installed on my machine.  I don't know why I didn't check that before anything else.  

I can now lock the screen via command line as noted above and via the user menu.  

The keybindings are still an issue though.  Ctrl+Alt+L as well as Super+L do nothing.

---

### Post by rk0r on 2012-10-22
> **dandaman96 said:**
> Shamefully, I have to report that part of my problem has been solved.  As it turns out, gnome-screensaver was not installed on my machine.  I don't know why I didn't check that before anything else.  

I can now lock the screen via command line as noted above and via the user menu.  

The keybindings are still an issue though.  Ctrl+Alt+L as well as Super+L do nothing.

It seems that gnome 3 and 12.10 are having a load of issues, i have had them non stop since the upgrade.

I am unable to use Unity, gnome 3 worked great in the 12.04LTS

---

### Post by Mr.JJ on 2012-10-23
R u using gdm? If u r using GDM, the lock screen will not work. I guess u don't need gnome screensaver for lock screen if you have GDM installed and enabled.

---

### Post by dandaman96 on 2012-10-23
No, using lightDm

---

### Post by ArgAthens on 2012-10-26
The ctrl-alt-l works.  That's what I'm using until this gets sorted out.

---

### Post by dandaman96 on 2012-10-26
> **ArgAthens said:**
> The ctrl-alt-l works.  That's what I'm using until this gets sorted out.

Even that does not work on my machine.

---

### Post by asalapi on 2012-11-20
In my case, the keyboard shortcut didn't work either.

I installed xscreensaver. Then, edited the keyboard shortcuts adding a "personalized" one named screensaver wich command "xscreensaver-command -lock" (without quotes). Assigned to it the keys ctrl-alt-l and confirmed it when a warning screen told me that the shortcut was already in use (indeed, I knew, so I told ubuntu to discard the previous use of the keys).

Now the keyboard brings up xscreensaver. Menu not working, anyway.

---

### Post by Luigi2012SM64DS on 2012-11-20
> **dandaman96 said:**
> After upgrading from 12.04 and Gnome 3.4 to 12.10 and Gnome 3.6, I have lost the ability to "Lock" my screen. Using either keyboard shortcuts (Super + L, Alt+Ctrl+L) or the menu option (user menu in top right of screen, "Lock"), nothing happens. 
 
Can anyone suggest a solution or a log file in which to begin researching a solution?
 Try using a live cd (so you have a clean version of ubuntu)

---

### Post by grege on 2012-11-23
This is now a weeks old thread, But I would create a new user and log into a clean setup and see what happens. If the new user works properly then you can rebuild your home folder. Log into a recovery session, rename your home folder to whatever, then make a new home folder with the same name as the old one, set the permissions so the new home folder is owned by you. Then log in and use Nautilus to move all your documents, music etc the the new home. As all the files still have your ownership the moving should be seamless. I install and use Midnight Commander to use in the recovery session, that way you do not have to remember all the syntax for creating folders and setting permissions. 

I have clean installed UGR 12.10 (Ubuntu Gnome Remix) and added the Gnome PPA. My Gnome 3.6 is rock solid and lock works every way it should.

---

