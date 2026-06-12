---
title: "help: vanishing/crashing applications"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Slyder0244 on 2005-12-11
i've been having a problem of crashing or just losing applications whenever i switch virtual desktops it seems to happen with firefox, xchat, and firestarter does anyone know what could be causing this

---

### Post by cwaldbieser on 2005-12-11
[QUOTE=Slyder0244]i've been having a problem of crashing or just losing applications whenever i switch virtual desktops it seems to happen with firefox, xchat, and firestarter does anyone know what could be causing this[/QUOTE]
Does it happen when you change the desktop you are viewing, or when you transfer the application to another desktop?

Also, even though you can't see the window anymore, is the process still in the process table (gnome-system-monitor)?

---

### Post by Slyder0244 on 2005-12-11
it happens whenever i change from the desktop i'm viewing to a new desktop and now i'm pretty sure that it happens whenever i change to an empty desktop

and no the process isn't running in the background i checked that already plus firestarter will notify me of a crash and ask to restart 

if their is anymore info i can give let me know

---

### Post by cwaldbieser on 2005-12-11
[QUOTE=Slyder0244]it happens whenever i change from the desktop i'm viewing to a new desktop and now i'm pretty sure that it happens whenever i change to an empty desktop

and no the process isn't running in the background i checked that already plus firestarter will notify me of a crash and ask to restart 

if their is anymore info i can give let me know[/QUOTE]
That's weird-- is anything logged to the system logs (like if you run dmesg)?

---

### Post by Slyder0244 on 2005-12-11
i was wondering if there were any logs i could check and i ran that dmesg and just got tons of lines text in the console so i don't know how to make heads or tails of that are there any other logs i can check

---

### Post by Slyder0244 on 2005-12-11
now i'm also noticing it whenever i change display settings such as screen resolution

---

### Post by cwaldbieser on 2005-12-13
[QUOTE=Slyder0244]now i'm also noticing it whenever i change display settings such as screen resolution[/QUOTE]
Forgot to ask, are you using Gnome or KDE or something else?  Have you noticed the problem with any other desktop managers?

For dmesg, you might try looking for something like "Xorg", so:
```

$ dmesg | grep "Xorg"

```
or whatever other searches might make sense (video card, etc.) might turn something up.  Also there should be a hidden file called ~/.xsession-errors that might have info that is of use.

---

### Post by Slyder0244 on 2005-12-14
i'm running kde but i think i've fixed the problem i changed the use my kde style in gtk to use another style and chose qt and so far so good hopefully that will fix it for good it has been about 2 days now and i haven't had any other problems i'll have to see if the problem returns after a reboot

---

