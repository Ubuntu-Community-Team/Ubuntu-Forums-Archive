---
title: "Notification Area (System Tray) Icons gone"
date: 2006-11-09
forum: Desktop Environments
---

### Post by impactdni on 2006-11-09
Recently (unsure how recently unfortunately), all of my notification area icons are gone.  An easy example of this is my gaim icon.  Plugin is set up and was working up until around a week ago or so.

Things that might be related:
I Upgraded from 6.06 --> 6.10 using dist-upgrade
I installed XGL/Beryl (on a different session)

I'm running 6.10 (Edgy), on an AMD64 machine.  Everything was working at one point.  Gaim and Skype are two examples of programs that _should_ but do not put icons in the Notification area.

I have tried removing, and re-adding the notification area to my panel.

I am running dual-monitors with two separate Screens in xorg (non Twinview/Xinerama), each monitor is their own desktop entirely, only the mouse crosses the boundaries.

The icons do not show up in either desktop when launched.

Any thoughts?

---

### Post by cemptor on 2006-11-09
Sorry I don't have a solution, but a similar problem.

I added compiz using one of the howtos in the forums. Was really slow for my machine, so I removed it.

My notification area disappeared. Loked at a thread in the forums, and was able to add it back using "Add to Panel". So Firestarter and Gaim show up.

However, I have Amule, which appears on the top left of the desktop, instead of in the notificaiton area on the taskbar. Have trie enabling and disabling, to no effect.

How do I get it to show in the task bar?

Running Ubuntu 6.10 i386 on an AMD64 processor machine

---

### Post by impactdni on 2006-11-13
Bump?

---

### Post by Psquared on 2006-11-13
> **impactdni said:**
> Bump?

Same problem here; waiting on someone with an answer.

---

### Post by CatKiller on 2006-11-13
> **impactdni said:**
> I am running dual-monitors with two separate Screens in xorg (non Twinview/Xinerama), each monitor is their own desktop entirely, only the mouse crosses the boundaries.

The icons do not show up in either desktop when launched.

I'm doing the same, and found that it got easily confused, having two notification areas. I removed the Notification Area from the panel on one of the screens, and all is well for the other screen.

---

### Post by impactdni on 2006-11-15
Didn't do it unfortunately.  At least, not after just removing one and restarting AIM, might have to relog...

Anyone have other ideas?

---

### Post by CatKiller on 2006-11-15
> **impactdni said:**
> Didn't do it unfortunately.  At least, not after just removing one and restarting AIM, might have to relog...

I'd imagine that a **killall gnome-panel**, at least, would be necessary.

---

### Post by p3d4l on 2006-11-16
I seem to have fixed the problem.. (I too am running edgy btw) I did "killall gnome-panel" then right clicked the notification area, which for me was at the top right of my screen, removed it, then right clicked the panel and did "add to panel" and add the notification area again. 

Hope this helps..

---

### Post by Psquared on 2006-11-16
> **p3d4l said:**
> I seem to have fixed the problem.. (I too am running edgy btw) I did "killall gnome-panel" then right clicked the notification area, which for me was at the top right of my screen, removed it, then right clicked the panel and did "add to panel" and add the notification area again. 

Hope this helps..

Worked for me too. Thanks.

---

### Post by mbertini on 2006-11-17
> **p3d4l said:**
> I seem to have fixed the problem.. (I too am running edgy btw) I did "killall gnome-panel" then right clicked the notification area, which for me was at the top right of my screen, removed it, then right clicked the panel and did "add to panel" and add the notification area again. 

Hope this helps..


I have the same problem: Ubuntu 6.10 + ATI drivers 8.28.08, and this solution unluckily did not work for me.

I do not remind what changed when the tray disappeared...

I hope that someone will have some other solution ](*,)

---

### Post by impactdni on 2006-11-17
Hmmm, worked _somewhat_

Now if I launch gaim on my right (main) monitor, I get the system tray icon (in the right monitor)

However, if I launch it on the left monitor, still nothing....

---

### Post by mbertini on 2006-11-23
> **impactdni said:**
> Hmmm, worked _somewhat_

Now if I launch gaim on my right (main) monitor, I get the system tray icon (in the right monitor)

However, if I launch it on the left monitor, still nothing....

Exactly what is happening to me.

The notification area in the right monitor (external LCD) works, but my left monitor (portable LCD) doesn't work. It justs sits there empty.

---

