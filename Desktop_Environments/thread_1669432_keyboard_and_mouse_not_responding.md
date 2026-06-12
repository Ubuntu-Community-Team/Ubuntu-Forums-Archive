---
title: "keyboard and mouse not responding"
date: 2011-01-17
forum: Desktop Environments
---

### Post by TheR on 2011-01-17
Kubuntu 10.04 all updates until today.

All of the sudden my keyboard and mouse are not working any more. At login window keyboard is working OK so I can login (mouse is not working), but after login, keyboard is not responding unless I press the key for few moments (perhaps a second) until a keyrepeat begins. Only then key is accepted and echoed on screen.

Funny thing is, if I login as some other user, everything works as expected. 

I have already ran Xorg -configure as su, but it didn't resolve the problem.

Help please.

by
TheR

---

### Post by inobe on 2011-01-17
sorry i never seen this before but lets start with the basics, how does it look in system settings> under> input device, does everything appear in order ?

if settings were changed they would be in there

---

### Post by Chame_Wizard on 2011-01-17
Has mostly to do with X.org .:D

---

### Post by Krytarik on 2011-01-18
What about something like "Assistive Technologies" or "Accessibility" options. There is an option "Only accept long keypresses" in Gnome, check for the equivalent in KDE, there is no such option for the mouse however.

---

### Post by TheR on 2011-01-18
Everything looks OK in settings department.

Are there per user settings for Xorg and where are they saved?

by
TheR

---

### Post by TheR on 2011-01-18
Update no. 2

Actualy there is KDE Accessibility menu, that is activated with SHIFT + NumLock. I must have accidentally poped the menu and selected wrong option.

How come this setting can not be set in Settings dialog. I wonder if there are other hidden popup options?

And now to my second problem, why my touch pad is not working. But mouse connected to USB does.

by
TheR

---

### Post by TheR on 2011-01-18
Update no. 3

It turned out that I can disable touch pad with Fn+F7 key. 

So all mysteries solved.

Thank you all
TheR

---

### Post by inobe on 2011-01-18
it's good you got it situated :)


be sure to mark your thread solved.

---

### Post by Krytarik on 2011-01-18
Amazing how many things one can accidently change by pressing the wrong shortcuts!;)

---

