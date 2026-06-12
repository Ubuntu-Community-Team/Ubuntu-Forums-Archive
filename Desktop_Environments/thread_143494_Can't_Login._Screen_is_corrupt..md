---
title: "Can't Login. Screen is corrupt."
date: 2006-03-12
forum: Desktop Environments
---

### Post by Dakaru on 2006-03-12
Ok, So I installed a new login theme, restarted and turns out it was corrupt, so now I cant type in my Username/password. 

So I rebooted into failsafe mode as root, and it wont let me open the login screensetup through this, Is there any terminal command to restore it to default, or did I completely ruin my install?

---

### Post by bscbrit on 2006-03-12
I find it hard to imagine that you have completely screwed your install simply by changing theme.  But I'm not sure how you fix your problem because I have never experienced this before.  I'll go away and do some thinking but you might get a better answer from someone else in the meantime.:D

---

### Post by Kevinator on 2006-03-12
You should be able to get to a terminal any time by pressing Ctrl-Alt-F1 (or F2, F3, F4, F5, F6). My suggestion is to start up normally (not in failsafe), switch to a terminal, log in there, then run startx. This skips the graphical login screen. I'm not sure it will all work properly if GDM (the thing that creates the graphical login screen) is running, so you might try

sudo killall gdm

before startx.

---

### Post by Kevinator on 2006-03-12
Oh, and the other thing I was going to mention: While Ctrl-Alt-F1 through F6 are text terminals, Ctrl-Alt-F7 is usually where you'll find your X (graphical) session. So you can switch back and forth.

---

