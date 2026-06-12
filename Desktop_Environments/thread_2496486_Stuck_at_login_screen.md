---
title: "Stuck at login screen"
date: 2024-03-30
forum: Desktop Environments
---

### Post by marsdenf on 2024-03-30
Using Xubuntu 22.04 on a laptop.  After entering login password,  the password box and the options on top right disappear, but nothing else happens.  It just stays at the wallpaper screen with nothing else.
(The mouse pointer moves, but no click functions.)
At the login screen, am able to get a full screen terminal by pressing ctrl-alt-f5, and then I can successfully login to a full terminal.  Then entered command "startx" and got a black screen (backlit, not pure black) and
nothing else. Is there another command to get graphics?  Any ideas on how I can get the login screen to work properly?

Update:  After waiting a few minutes on the black backlit screen,  the graphical os shows up normal after moving the mouse.  (ie it looks like the login was successful).  But there are problems with internet access.  For example, when Skype is opened
there is an error message:  "the login keyring did not get unlocked when you logged into your computer".  Internet does not work for any program, even though the laptop is connected via wifi.

---

### Post by Rubi1200 on 2024-03-31
Do you have the same issues if you try booting an older kernel?

---

### Post by marsdenf on 2024-03-31
I tried and earlier kernel, made no difference

---

### Post by marsdenf on 2024-03-31
Update:  I tried again, and after entering password,  got the wallpaper screen with nothing else again, but this time I waited a bit longer , and the desktop showed up normal, except the same problem with internet.  So it seems the bootup is very slow.

---

### Post by marsdenf on 2024-03-31
Boot-info summary at [http://*******.us/OOxbQg](http://*******.us/OOxbQg) or [URL="http://*******.us/vz2BYU"]http://*******.us/vz2BYU
[/URL]Update:  did recommended boot repair, report at [http://*******.us/TTdTmc](http://*******.us/TTdTmc) 
It did not work, same problems as before.

---

### Post by MAFoElffen on 2024-03-31
> **marsdenf said:**
> Boot-info summary at [http://*******.us/OOxbQg](http://*******.us/OOxbQg) or [URL="http://*******.us/vz2BYU"]http://*******.us/vz2BYU
[/URL]Update:  did recommended boot repair, report at [http://*******.us/TTdTmc](http://*******.us/TTdTmc) 
It did not work, same problems as before.
The Boot-Repair report has nothing to do with the graphics not coming up.

The 'system-info' report would be more relatable.

That would at least tell us your hardware and what graphics drivers you might be using so we can direct you into some focused diagnostics.

---

