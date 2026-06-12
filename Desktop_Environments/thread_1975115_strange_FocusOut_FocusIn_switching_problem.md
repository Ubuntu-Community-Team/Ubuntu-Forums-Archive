---
title: "strange FocusOut FocusIn switching problem"
date: 2012-05-06
forum: Desktop Environments
---

### Post by cnbiz850 on 2012-05-06
The symptom of the problem is that the pulldown/popup menus often disappear quickly before I make an action with the mouse.  I checked with xev, and got the following strange things showing up very often withou my touching of anything.

> FocusOut event, serial 31, synthetic NO, window 0x6a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 31, synthetic NO, window 0x6a00001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 31, synthetic NO, window 0x6a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   



I am running XUbuntu 12.04 64bits on Dell XPS L501X.  It didn't have this problem on 11.10.

Does anyone know what is wrong and how to fix it, please?

---

### Post by cnbiz850 on 2012-05-10
Any ideas please?

---

### Post by rai4shu2 on 2012-05-13
You have a wireless mouse?

---

### Post by cnbiz850 on 2012-05-13
> **rai4shu2 said:**
> You have a wireless mouse?

No, Just a USB mouse.  But I have also tested without the external mouse, and the case is the same.
 
Very annoying.

---

### Post by rai4shu2 on 2012-05-13
You could just hold down the mouse button and then release when it gets to the option you want. That is a weird problem, though.

---

### Post by cnbiz850 on 2012-05-14
I think I nailed the problem, but can hardly believe what I found.

It was GKrellM system monitor!  I can't imagine how it did it, but turning it off got rid of the long-time problem I had.

Guess not many people use GKrellM.  What else can be used to monitor system activities?

---

### Post by rai4shu2 on 2012-05-14
A lot of people like conky, but I just use htop whenever I want to check out whatever I'm running.

---

