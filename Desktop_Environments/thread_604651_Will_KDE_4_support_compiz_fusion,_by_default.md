---
title: "Will KDE 4 support compiz fusion, by default?"
date: 2007-11-06
forum: Desktop Environments
---

### Post by creeco on 2007-11-06
Does anybody know if kde4 will support compiz fusion by default? I tried to search for this but could'nt find any answer to my question.

---

### Post by GeneralZod on 2007-11-06
I'm not sure if there are any specific plans for this, as KDE4's window manager (kwin) will have its own built-in compositor.  I wouldn't rule it out, though :)

---

### Post by creeco on 2007-11-06
I hope you're right

---

### Post by SteFaNweI on 2007-11-06
Q: Will KDE 4 support compiz fusion
A: yes - if you want to use it, it will work as it does now :)

Q ..., by default?
A: no - by default it will use its own window manager - kwin.

this has two important advantages. 
[LIST]
[*] kwin can flawlessly switch between accelerated 3d desktop to, a non accelerated 3d desktop or a 2d desktop. compiz in contrast (currently at least) will only work if your hardware supports it. that means if it doesn't, you have to use the "fallback" window manager which may lead to different functioning (e.g. different keystrokes) and other issues.
[*] additionally, kwin is a mature wm that has seen a lot of improvements and bugfixing whereas compiz is new and sometimes does not behave as intended (e.g. focus steeling prevention). by the way: i use compiz all the time and it is great (except focus steeling prev.) and the sentence above does not come from me but from some kde-dev - i forgot where i got it from.
[/LIST]

if you look at the 3d plugins that are currently there for kwin, it won't be long until it has the same things to offer as compiz.

hope that helped ;)

---

### Post by creeco on 2007-11-07
> **SteFaNweI said:**
> Q: Will KDE 4 support compiz fusion
A: yes - if you want to use it, it will work as it does now :)

Q ..., by default?
A: no - by default it will use its own window manager - kwin.

this has two important advantages. 
[LIST]
[*] kwin can flawlessly switch between accelerated 3d desktop to, a non accelerated 3d desktop or a 2d desktop. compiz in contrast (currently at least) will only work if your hardware supports it. that means if it doesn't, you have to use the "fallback" window manager which may lead to different functioning (e.g. different keystrokes) and other issues.
[*] additionally, kwin is a mature wm that has seen a lot of improvements and bugfixing whereas compiz is new and sometimes does not behave as intended (e.g. focus steeling prevention). by the way: i use compiz all the time and it is great (except focus steeling prev.) and the sentence above does not come from me but from some kde-dev - i forgot where i got it from.
[/LIST]

if you look at the 3d plugins that are currently there for kwin, it won't be long until it has the same things to offer as compiz.

hope that helped ;)

I already know about kwin, by default KDE 3.X handles compiz horribly, because its default WM kwin (you probhably havent heard of it :P) don't use a big desktop (like metacity) but serveral virtual desktops. When i fire up compiz in kde, its pager gets completely messed up, and i can't have more than 2 dekstops in compiz.

---

### Post by roderick on 2007-11-07
> **creeco said:**
> I already know about kwin, by default KDE 3.X handles compiz horribly, because its default WM kwin (you probhably havent heard of it :P) don't use a big desktop (like metacity) but serveral virtual desktops. When i fire up compiz in kde, its pager gets completely messed up, and i can't have more than 2 dekstops in compiz.

Kwin does not handle it horribly, just different from what Metacity does.

Kwin has the concept of 1 desktop and multiple viewports, whereas Metacity and Compiz both define multiple desktops and viewports. So, when in KDE you define your 4 viewports, it's actually on one desktop. Then in compiz, if you increase/change the desktop (not viewport) the kde pager gets confused. 

I'm not sure how Kwin will handle this in the future, and whether or not it will take the concept of desktops and viewports to the same level and degree that Metacity/Compiz has.

By the way, one should note that Compiz was originally developed under GTK/Gnome and not Qt/KDE, so there was no original thought put towards the potential limitations that could exist under other toolkits and wm's like Qt/KDE. In fact, Compiz was never meant to last as a WM - It was a proof-of-concept originally, and Metacity/Kwin were meant to incorporate the "ideas" of compiz into their compositing engines (which is what is/has happened).

Cheers.

---

