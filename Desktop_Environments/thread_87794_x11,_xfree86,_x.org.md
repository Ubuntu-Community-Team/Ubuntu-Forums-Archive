---
title: "x11, xfree86, x.org???"
date: 2005-11-08
forum: Desktop Environments
---

### Post by jimmygoon on 2005-11-08
Whats the difference between the 3 and what exactly are they?

thanks

---

### Post by mlomker on 2005-11-08
If I'm wrong someone will correct me.  X11 is a protocol for displaying screen information, Xfree is a server that provides X11, and X.org is an offshoot (fork) of the Xfree project.

---

### Post by kairu0 on 2005-11-08
From xfree86.org ("XFree86 is an open source X11-based desktop infrastructure.")

X11 = the X windowing system available for Unix, BSD, etc.

Xfree86 = an open-source implementation of it.

X.org = the X11 implementation that Ubuntu uses

All 3 are client and servers "provide a client/server interface between display hardware (the mouse, keyboard, and video displays) and the desktop environment" (also xfree86.org homepage). In other words, they give you the graphical display that lets Gnome/KDE/whatever draw your windows (no pun intended.)

Someone else can probably define it better, but that's my understanding.

---

### Post by jimmygoon on 2005-11-08
[QUOTE=kairu0]From xfree86.org ("XFree86 is an open source X11-based desktop infrastructure.")

X11 = the X windowing system available for Unix, BSD, etc.

Xfree86 = an open-source implementation of it.

X.org = the X11 implementation that Ubuntu uses

All 3 are client and servers "provide a client/server interface between display hardware (the mouse, keyboard, and video displays) and the desktop environment" (also xfree86.org homepage). In other words, they give you the graphical display that lets Gnome/KDE/whatever draw your windows (no pun intended.)

Someone else can probably define it better, but that's my understanding.[/QUOTE]
I can't help myself.... why is there three of them?? thanks

---

### Post by bryan986 on 2005-11-09
[QUOTE=jimmygoon]I can't help myself.... why is there three of them?? thanks[/QUOTE]

Same reason there is gnome,kde and xfce

Each believe they can do it better than the others

---

### Post by jimmygoon on 2005-11-09
[QUOTE=bryan986]Same reason there is gnome,kde and xfce

Each believe they can do it better than the others[/QUOTE]

So why does ubuntu use x.org???

---

### Post by NewWithoutClue on 2005-11-09
[QUOTE=jimmygoon]So why does ubuntu use x.org???[/QUOTE]
Choice.

---

### Post by 23meg on 2005-11-09
xorg performs better than xfree86 and has more development going on.

---

### Post by DrBair on 2005-11-09
X11 is the protocol that the latter two use.  Xfree was THE open source version for a few years but due to constant bickering, nothing much got done.  

Then a license change happened which clamped down on the openness of the source code.  Many of best developers got fed up and left to form X.org, most of the other developers were soon to follow.  X.org started with the version just before the license change (since the new license prohibited a fork essentially).  The licensing issue is a BIG reason why most linux distros use X.org, not to mention that it has a few more improvements on it.

Since X.org has started, the X server has made much better progress and we're soon to see a very big leap forward with the new modularized 7.0 version which will pave the way for even more improvements.

---

### Post by pravuil on 2006-08-22
Licensing problems with Xfree86. that's why

---

