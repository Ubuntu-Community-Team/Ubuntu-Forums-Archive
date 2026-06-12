---
title: "Setting automatic lock on automatic login"
date: 2009-03-23
forum: General Help
---

### Post by wersdaluv on 2009-03-23
I want to enable automatic login because that allows my computer to load my desktop environment even if I leave it unattended so it wont get stuck on GDM while I'm away from my computer. The use case is I turn my computer on and leave it loading while I'm doing other things so when I go back, I have a ready to use desktop environment. The thing is, it is a security issue because other people can use my desktop without entering a password.

Is there a way to enable automatic lock screen whenever I turn my computer on with automatic login enabled? This way, my desktop session loads but a password would still be required at startup.

---

### Post by peterLinux on 2009-03-24
Not sure if this would work but you could issue something 
to lock the screen from a batch script that get called (rc.local)

I belive the cmd is
xscreensaver-command -lock 
There must be a screensaver running for this to work. 

Have Fun

PeterLinux

---

### Post by peterLinux on 2009-03-24
And of course...
sudo apt-get install xtrlock

It does not start a screensaver but it requires your password before you can unlock...

(run xtrlock from the command line)

---

### Post by mocoloco on 2009-03-24
System -> Preferences -> Sessions
Add a new startup program.  Call it whatever you want
Command is
```
 gnome-screensaver-command --lock
```
Now that will run every time you log in.

The track peterLinux was on would work too, but I think this is easier if you prefer GUI.

---

### Post by wersdaluv on 2009-03-24
> **mocoloco said:**
> System -> Preferences -> Sessions
Add a new startup program.  Call it whatever you want
Command is
```
 gnome-screensaver-command --lock
```
Now that will run every time you log in.

The track peterLinux was on would work too, but I think this is easier if you prefer GUI.
Hmm. Adding it to gnome's autorun apps doesnt work. I'll try the xtrlock path when I get home :)

---

### Post by Yashiro on 2009-03-24
Just run: 
> xdg-screensaver lock
From the Sessions (Startup Apps) panel.

---

### Post by wersdaluv on 2009-03-24
Both codes do the same thing. However, they only work if the session is started by logging in GDM. They don't run in a newly-booted, automatic login-enabled session.

---

### Post by wersdaluv on 2009-03-24
xtrlock works on autorun! Thanks, peterLinux! :)

---

### Post by Yashiro on 2009-03-24
> Both codes do the same thing. However, they only work if the session is started by logging in GDM. They don't run in a newly-booted, automatic login-enabled session.
Adding xdg lock to sessions works fine in a newly-booted, automatic login-enabled session. I run it myself.

---

### Post by wersdaluv on 2009-03-24
> **Yashiro said:**
> Adding xdg lock to sessions works fine in a newly-booted, automatic login-enabled session. I run it myself.
Aw. I don't know why it doesn't work for me :( Oh well. xtrlock is fine and it's even better because it doesn't have to blacken the screen. Thus, eats less cpu power.

---

