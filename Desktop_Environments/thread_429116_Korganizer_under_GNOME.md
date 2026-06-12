---
title: "Korganizer under GNOME"
date: 2007-04-30
forum: Desktop Environments
---

### Post by mcgirvanmedia on 2007-04-30
I like Korganizer for managing myself and have used it for a while.

I have recently moved from Fedora to Ubuntu, and would like to stick with GNOME for the moment (was using KDE under fedora).

I installed KOrganizer which worked fine, although there is no menu entry for it.

What i would like to do is have the reminder daemon running at login that way i can just click on the reminder icon and Korganizer opens for me. I added an entry to System/Preferences/Sessions and KOrganizer starts fine, except it is the full application, not just the minimized tray icon.

Is there either a command line parameter i should be using, or is the reminder daemon a seperate program i should be running instead.

Regard

Glen

---

### Post by mcgirvanmedia on 2007-04-30
OK, i just found it myself.

I just run korgac and that is just the tray icon.

---

### Post by mcgirvanmedia on 2007-04-30
OK, problem back.

That doesn't work properly, it doesn't put the icon into the tray next to the clock as it does when i run from a command prompt, insted it shows in the task list down the bottom like all other running programs.

---

### Post by mcgirvanmedia on 2007-05-02
Anybody come across this before?

---

### Post by StrayCat on 2007-06-22
Came across the same phaenomenon... Still no idea about this?

---

### Post by Acksys on 2007-08-22
I have this problem too. If you right click the tray icon, there is an checkbox called "Start Reminder Daemon at Login." Ticking this box does not, however, cause the daemon to start when I login.

Anyone have a solution to this?

---

### Post by Acksys on 2007-09-05
Bump.

---

### Post by areteichi on 2007-09-15
I fixed the problem by starting up the followings (adding to the Auto Startup Sessions):

```
kded
kdeinit
klauncher
knotify
korgac
```

---

