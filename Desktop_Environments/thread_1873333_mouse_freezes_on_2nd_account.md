---
title: "mouse freezes on 2nd account"
date: 2011-11-01
forum: Desktop Environments
---

### Post by simon heimbach on 2011-11-01
Hello altogether,

after many years of confident work with ubuntu (and other linux) systems I experienced a peculiar problem today.

I basically have two accounts on my system. One for basic computer use (internet, email, photos, music, etc) and a second one for development. So I switch a lot between these two accounts.

When I log into my development-account, the mouse (PS2-Touchpad) freezes. The system-preferences do recognize it. I tried to plug an external USB-mouse and it works like a charm. Amazingly the touchpad also works perfectly under my standard-account.

Now I never had any problems with my touchpad so far and I wonder where to start my research.

System:
Asus Eee PC 1001HA (Atom N270, GMA945, 1GB RAM, Ubuntu 11.10 [clean install])

It could be, that I switched off the computer yesterday with "sudo shutdown -now" from the shell with an active X11-session as developer.

Any idea is very appreciated
Simon

---

### Post by simon heimbach on 2011-11-02
Hello altogether,

I just solved the problem my self - stupid me. It seems as if the newest kernel supports the function-keys of asus' eee pc. The comination Fn+F2 disables and enables the trackpad.

Maybe someone else's tumbles over the same problem some time =).

Greetings, Simon

---

