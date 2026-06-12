---
title: "KDE hijacks sound system?"
date: 2005-11-09
forum: Desktop Environments
---

### Post by nrwilk on 2005-11-09
I couldn't get any streaming audio to work until I finally got realplayer to do it.  Except, it wouldn't do anything at first.  I found an option in the system settings which controls the amount of idle time KDE leaves before dropping it's deathgrip on the audio system.  Once I put that slider to 1 second, the streaming audio worked.

* Is this bad to have KDE set up this way?
* Should I give it more than 1 second before it lets the sound system go?
* Is it normal to have to work around the problem like this?
* Why does KDE do this?

---

### Post by mlomker on 2005-11-10
I've never had that problem and mine is set at the default of 60 seconds.  I mostly use amaroK with the Xine engine.  I imagine it'd vary depending upon what application your are using (and what sound engine that application uses).

---

### Post by nrwilk on 2005-11-10
Shiver me Timbers!

Switching Amarok to Xine worked!

Thanks a lot.  I hated using Real player, it was my last resort.  On the other hand I love Amarok.

---

### Post by Navyblue on 2005-11-11
I use XMMS and I don't have this problem, but I have this problem on enemy territory. I set the timeout to be 15 sec btw.

---

### Post by nrwilk on 2005-11-11
[QUOTE=Navyblue]I use XMMS and I don't have this problem, but I have this problem on enemy territory. I set the timeout to be 15 sec btw.[/QUOTE]


Is there any drawback to setting it lower than the default of 60 seconds?  If not, why wouldn't they just set it as low as possible by default?

---

### Post by Navyblue on 2005-11-12
[QUOTE=Fealos]Is there any drawback to setting it lower than the default of 60 seconds?  If not, why wouldn't they just set it as low as possible by default?[/QUOTE]

I am a newbie myself so I don't know. I guess it makes the next sound within the idle time limit more responsive by not needing to load ARTS again?

---

### Post by nrwilk on 2005-11-13
[QUOTE=Navyblue]I am a newbie myself so I don't know. I guess it makes the next sound within the idle time limit more responsive by not needing to load ARTS again?[/QUOTE]
makes sense.

---

