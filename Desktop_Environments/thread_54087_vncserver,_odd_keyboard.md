---
title: "vncserver, odd keyboard?"
date: 2005-08-03
forum: Desktop Environments
---

### Post by eriksays on 2005-08-03
i'm using vncserver to access my desktop; and, all of a sudden, the keyboard layout is off [click g, get j]

odd thing is, it was working fine yesterday?

suggestions?

---

### Post by TheYetiMan on 2006-11-18
*BUMP*.... dude exaclty the same thing has just happened to me. I've had xtightvncserver running on my linux box for like 4 weeks with no problem what so ever. Then yesterday, out of the f****ng blue the keyboard layout has just totally changed to totally TOTALLY random - I can't use it any more!

Here is what I get when I type "qwertyuiop" (top row of keyboard):

"c.gvnmlzx"

Seriously - WTF? I don't even think it's a different country's keyboard layout, its just utterly f***ed. I've restarted the entire computer, restarted the vnc server. Tried connecting from different clients (windows and linux) but they are all the same.

I've tried changing the gnome keyboard layout but it has NO effect.

It's driving me totally potty, so if anyone could help I'd be really grateful.

Thanks in advance to anyone who responds,

Yeti

---

### Post by Lindhardsen on 2007-01-03
Did any of you resolve this issue?

I'm experiencing the exact same keyboard bullshit. But online when running as myself, and not when running as root.

Extremely irritating!

Please help

Regards,
Jan

---

### Post by jsalin on 2008-04-12
Same thing on my new Ubuntu server. Just starting VNC with a command "vncserver -depth 16 -geometry 1024x768", it finds the Xsession file and starts up gnome fine. Keyboard is however wrong with the previously described behaviour when trying to type QWERTY. This has never happened to me on any other distro or ubuntu version, wonder what's wrong.

---

### Post by jsalin on 2008-04-12
This was Gnome related, since removing gnome-session and using another (a simple WM) instead fixed the keyboard.

---

### Post by IronWolve on 2008-06-23
Humm, Just switched to gnome-session from twm, and exact same issue.

Any ideas?

---

