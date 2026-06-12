---
title: "Top panel covering window title bars"
date: 2008-12-08
forum: General Help
---

### Post by damijit on 2008-12-08
I am using Ubuntu 8.10 Intrepid Ibex.

Recently, when many windows are created, they are created at the very top of the screen. That is, instead of being created right below the top panel, their title bars are covered up by the top panel (see screenshot).

It's not massive problem, but it's pretty annoying--especially because I can't just drag them out of the way (can't drag the title bar if it is not visible), I have to alt + right-click > move.

Does anyone have any idea what the problem is, or now to fix it?
Thanks!

---

### Post by Het Irv on 2008-12-08
Is your window manager still running? aka. when you do move the window do you have a title bar?

Based on the screenshot I would say try typing ```
metacity --replace
```
But I am not sure if that fixes your problem

---

### Post by damijit on 2008-12-08
Yes, I still have title bars after I move the window. Do you still recommend metacity --replace? What does that command do?
P.S. Also, I use compiz-fusion desktop effects, just FYI--I don't know if that matters.

---

### Post by Het Irv on 2008-12-08
nah if you still have the Title bars, it might have to do more with the resoultion of your screen.

Metacity is the default Window Decorator, meaning it handles the Title bar and all that.  Sometimes it won't load correctly because of a setting change or somthing like that and the result will look like what you posted... but the title bar isn't hidden its just not there.  Metacity --replace will start up metacity while forcing other Window Decorators, like Emerald, to quit.

If you still have the title bars, then this probably isn't the problem, I would check your screen resoution and screen size to make sure they are correct.

---

### Post by damijit on 2008-12-08
The resolution and screen size seem to be correct (see attached)
I don't know what the "Unknown" is about--I have no other monitor attached to this laptop--but the "laptop" size and resolution are correct.

---

### Post by damijit on 2008-12-14
I'm sorry to bring this back up, but it's begun to happen to nearly all my windows--it is becoming a major problem. Does anyone have any ideas about what's going on? If this isn't the right place, where should I look to get this fixed?

---

### Post by stoneage on 2008-12-14
Have you tried turning off Compiz? Sometimes it causes display troubles.

---

