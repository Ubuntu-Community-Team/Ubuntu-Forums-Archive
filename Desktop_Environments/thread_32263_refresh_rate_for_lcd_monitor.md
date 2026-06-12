---
title: "refresh rate for lcd monitor"
date: 2005-05-06
forum: Desktop Environments
---

### Post by hrvoje-pula on 2005-05-06
hi,

How can I increse refresh rate fro 60 Hz to 75 Hz?

Thanx in advance

---

### Post by Professor X on 2005-05-06
Preferences -> Screen Resolution in gnome (select make default for this computer to save your changes).  Also, make sure your /etc/X11/xorg.conf has the correct values for the monitor's horizontal and vertical refresh rates.

---

### Post by denzilla on 2005-05-06
I didn't think refresh rate was relevent on an LCD?

---

### Post by Bob D. on 2005-05-06
[QUOTE=denzilla]I didn't think refresh rate was relevent on an LCD?[/QUOTE]You're correct, it's not. No RGB guns scanning. The old trick of looking at the monitor from the corner of your eye will prove it. No change on a LCD. You can see the scan flicker on CRT's.

Bob

---

### Post by hrvoje-pula on 2005-05-07
hi again,

thanks for advices, but there must be something else then,

when browsing my screen (fonts) are turbid so its frustrating for my eyes.
Do you have any suggestion?

---

### Post by Bob D. on 2005-05-07
What LCD monitor (brand and model) and what resolution are you using?

Analog or DVI?

How long is the cable run?

Can you try the monitor on another computer? Can you try another monitor on your computer?

The first three will be helpful to us to help with your problem. The last one is just an idea to see if its a monitor issue or an issue with your system.

Bob

---

### Post by hrvoje-pula on 2005-05-07
I'm using 17" xerox LCD  1280x1024 60Hz, and it is working exelent on win XP (which is also installed on my pc). Grphic card is ATI radeon 9600 XT (ubuntu has recognized it)
cpu is AMD  2500+

---

### Post by hrvoje-pula on 2005-05-07
sorry, I forgot, I've installed ubuntu with another monitor first (maby that is a problem) some old one, i don't remember which type. 
btw cable is normal (came with monitor)

---

### Post by tofudrifter on 2005-07-17
i've done the same thing, when i installed ubuntu on my pc i had a 17" crt monitor connected, now i have a 19" lcd but when i look in nvidia settings i still says crt monitor connected

i ran dpkg-reconfigure xserver-xorg to try get the lcd detected

---

