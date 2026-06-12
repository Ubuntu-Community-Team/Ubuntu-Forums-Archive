---
title: "Do I Really Need the Session Manager?"
date: 2011-07-31
forum: Desktop Environments
---

### Post by neu5eeCh on 2011-07-31
I'm thinking of removing Xubuntu's (XFCE's) Session Manager. It seems to be causing me nothing but trouble? If I save a Session, XFCE never seems to remember it. When I start fresh, XFWM4 frequently doesn't start (so I struggle to start it). The session manager also boots up Nautilus (which I've installed) even when I specifically specify **Never** in session manager.

I'm wondering if removing Session Manager will solve all this crap?

---

### Post by jerrrys on 2011-07-31
don't know if you can or not, but you can try this:

open a terminal and enter

killall session-manager (if thats is its actual name)

system still work?  if not a reboot will restore it.

also check in your system monitor to be sure it didn't just automatically restore it

EDIT: forgot the dash

---

### Post by cmcanulty on 2011-07-31
Why not try firefox's session manager, works great

---

### Post by neu5eeCh on 2011-07-31
> **cmcanulty said:**
> Why not try firefox's session manager, works great

I do. XFCE's session manager and firefox's session manager do two different things though. XFCE's session manager is, in theory, meant to be a session manager for the entire OS, not just the browser. It works great **when** it works.

---

### Post by neu5eeCh on 2011-07-31
> **jerrrys said:**
> don't know if you can or not, but you can try this:

open a terminal and enter

killall session manager (if thats is its actual name)

system still work?  if not a reboot will restore it.

also check in your system monitor to be sure it didn't just automatically restore it

Thanks. XFCE is modular so it's easy enough to remove the "session manager" via Synaptic's Package manager. I know XFCE will run without it, I'm just wondering if removing it messes with suspend or hibernate.

---

### Post by cmcanulty on 2011-07-31
That sounds cool is there a similar package for gnome?

---

### Post by jerrrys on 2011-07-31
gnome session manager is just called gnome-session and not removable unless i am missing something

---

### Post by cmcanulty on 2011-07-31
OK I found it is installed on my laptop but how do I use it, I checked all the menus and didn't see any session manager options

---

### Post by neu5eeCh on 2011-07-31
> **cmcanulty said:**
> OK I found it is installed on my laptop but how do I use it, I checked all the menus and didn't see any session manager options

If you're asking **me**, I don't know. I don't use Gnome anymore. I prefer a menu driven OS on a computer.

---

### Post by enimeizoo on 2011-07-31
I see no reason why it would mess with suspend or hibernate. I think that the acpi manager is independent from the session manager. At least, it should be. There is only one way to make sure, though.

---

