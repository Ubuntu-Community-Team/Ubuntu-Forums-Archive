---
title: "Gnome, Kde Settings borking XFCE!?"
date: 2006-01-05
forum: Desktop Environments
---

### Post by Joey French on 2006-01-05
I have tried to remove everything xfce related and reinstalling. It seems that settings for Gnome and KDE are carrying over to my Xubuntu desktop. What can I do? At one point I ran nautilus because I hate Rox-filer, and I think that's where the trouble started. I can click on settings from the panel (desktop and appearance) and the panel objects will change resolution, but that's it. 

Help.

Joey French

---

### Post by Joey French on 2006-01-06
Okay, now I got a mouse arrow and a brown screen, nothing else.

What gives?

---

### Post by Joey French on 2006-01-06
Anyone?

---

### Post by Clazzy on 2006-01-06
Open up a console and type:
killall nautilus

Then change the shortcut for your Nautilus to have --no-desktop at the end. The problem is that Nautilus likes to have control over your desktop, so does so when you run it. You may also want to try using [Thunar](http://www.ubuntuforums.org/showthread.php?t=95934), which is another lightweight file manager. It's rather similar to Nautilus, so you should feel right at home.

---

### Post by Suger on 2006-01-06
I was just going to say that : run Thunar, it's great.

---

### Post by Joey French on 2006-01-06
I have thunar installed and have used it. Problem is, I don't even have a desktop when I boot into xfce.
Very strange.

---

### Post by Joey French on 2006-01-06
Okay, so I tried killing all running processes that I thought might be messing up my xubuntu, but to no avail. I completely removed and reinstalled xfce and logged into it and the same problem, no panel, brown background, Alt-F2 works to pull up terminal (fonts huge!), no other desktop items. Very frustrating. Anyone got a clue, let me know, as I am using Xfce as a testing ground, and this is wasted time.
Maybe a file I can remove that will reset my beloved XFCE? It is broken, I am sad...

---

### Post by Clazzy on 2006-01-06
The best solution I can see right now is pressing Alt-F2 and running xfdesktop. This should get you back your desktop.

---

### Post by unionjak on 2006-01-06
hello,
clazzy were did you get drapper from mate ~?

---

### Post by Clazzy on 2006-01-06
Edit your /etc/apt/sources.list, changing instances of breezy to dapper, then sudo apt-get update and sudo apt-get dist-upgrade. You should just read [this](http://www.ubuntuforums.org/showthread.php?t=93157) first, though.

---

### Post by unionjak on 2006-01-06
ok, thanks for that...better leave it for now ;)

---

### Post by Joey French on 2006-01-06
I have booted into XFCE and Alt-F2, xfdesktop, to no avail. 

Why is Gnome or KDE trying to take over the XFCE desktop?

---

