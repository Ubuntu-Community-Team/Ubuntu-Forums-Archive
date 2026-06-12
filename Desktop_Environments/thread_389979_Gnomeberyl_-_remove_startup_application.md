---
title: "Gnome/beryl - remove startup application"
date: 2007-03-21
forum: Desktop Environments
---

### Post by justleen on 2007-03-21
Hey there Ubuntus

I just installed Beryl, which work brilliantly. Until i decided i wanted it to start automaticly when GDM starts. So, i created a new session, for beryl.
That worked, but the ubuntu splash screen hung for several minutes (which is a known issue, apperently) so i added beryl to the startup application in gnome itself.

This is where everything went downhill. I logged out, logged in... and...
I can see the splash screen loading nautilus, and then i get a blank background. i left it there for a few minutes, but nothing happend.

i restarted GDM  in a terminal and tried to launch a fail safe gnome: same thing.
i can logon to a fail safe terminal, but i dont know which app runs the startup manager.

Ive already removed the beryl packages, to no avail.
Ive also removed the gnome setting in my home dir (rm -rf .gnome*), which didnt help either..

Can anyone point me to the settings file where gnome keeps the startup apps?
Or help me out in another way?

An help would be greatly appreciated!

---

### Post by Waappu on 2007-03-21
Hi

In Gnome startup applications are```
~/.config/autostart
```

---

### Post by justleen on 2007-03-21
> **Waappu said:**
> Hi

In Gnome startup applications are```
~/.config/autostart
```


Great, that worked... Cheers!

---

