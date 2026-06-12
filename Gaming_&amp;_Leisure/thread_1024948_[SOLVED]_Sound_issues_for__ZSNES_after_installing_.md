---
title: "[SOLVED] Sound issues for  ZSNES after installing KDE over GNOME"
date: 2008-12-29
forum: Gaming &amp; Leisure
---

### Post by Sol401 on 2008-12-29
Hey.. This is a strange problem. I downloaded ZSNES a while back (while using GNOME) and eventually got everything working properly. There WERE sound issues at that time, but I resolved them through these forums by using the command  

zsnes -ad sdl

and everything worked beautifully. However, recently I got the urge to try the KDE desktop for Ubuntu Hardy 8.04. So I installed KDE 4 desktop environment. Sound seems to be working fine in all applications. The only exception is ZSNES... Sound is now NOT working. Sound works in all my other emulators (for example, PCSX) but not ZSNES... 

I'm quite stumped! Any suggestions from the experts out there? Much appreciated, thanks...:D

EDIT...
The sound still works if I change sessions and go back to GNOME... But I would still like a fully functional KDE environment (with sound in ZSNES!)

---

### Post by Sol401 on 2008-12-30
NEvermind.. I solved it. Sound now working in both GNOME and KDE4

---

### Post by Vadi on 2008-12-30
Would be great if you posted how so others know :P

Also click on Thread Tools&#8594;Mark thread as solved

---

### Post by Sol401 on 2009-01-02
My apologies for not including this! It was actually just something silly. GNOME uses the sdl sound system, while KDE uses alsa. So all you have to do is install the alsa Debian sound package. Run a terminal and do:

```
sudo apt-get install libsdl1.2debian-alsa
```

Things should now work. If they do not, try this in addition at the terminal:

```
export SDLAUDIODRIVER=alsa
```

Everything should work fine!

---

