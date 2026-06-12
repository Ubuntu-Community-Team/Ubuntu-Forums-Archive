---
title: "Beryl-manager start dm as metacity"
date: 2006-09-30
forum: Desktop Environments
---

### Post by dentaku65 on 2006-09-30
Hi to all,
I've updated compiz/cwgd to beryl and works great!
Only one thing: when I reboot the machine beryl-manager the default desktop manager is metacity and not beryl as I set up, and every time I'm booting the machine I have to do this manually via beryl tray icon options; is there any way to set this as default?

TIA

---

### Post by djRobbieF on 2006-09-30
I've never tried it, and I don't have the problem you have... but does this work?

Replace your startup beryl-manager with this:
beryl-manager --replace gnome-window-decorator &

It's a long shot... but worth a try.

---

### Post by orb9220 on 2006-09-30
Did you add beryl-manger in your sessions startup?
That is what you do to get it to boot on startup.

Mine works great.

---

### Post by djRobbieF on 2006-09-30
> **orb9220 said:**
> Did you add beryl-manger in your sessions startup?
That is what you do to get it to boot on startup.

Yeah it sounds like what they're saying is beryl-manager DOES load, but it defaults to metacity for the default window manager.

---

### Post by dentaku65 on 2006-09-30
> **orb9220 said:**
> Did you add beryl-manger in your sessions startup?
That is what you do to get it to boot on startup.

Mine works great.

Yes it is in the session startup and is loaded correctly, the strange thing that it loads metacity as wm instead of beryl as I selected prevously.

---

### Post by djRobbieF on 2006-09-30
and my suggestion didn't work?

---

### Post by orb9220 on 2006-09-30
[http://forum.beryl-project.org/](http://forum.beryl-project.org/)

---

### Post by dentaku65 on 2006-09-30
> **djRobbieF said:**
> and my suggestion didn't work?

Hi RobbieF, sorry for the delay; no I got the same "issue".
I was thinking about compiz, is compiz (and derivates) must be removed once beryl is installed?

---

### Post by dentaku65 on 2006-09-30
uh uh, "fixed" after a personal workaround....
I disabled Crash Handler plugin and now beryl loads as Beryl, in fact when I'm entering in the session (I don't know why) beryl loads itself twice (two times splash screen) and I think that with that plugin enebled beryl recognized this behaviour as "crash".... I don't but now working perfect :-D

---

