---
title: "Only one program can use my sound card at the time."
date: 2006-01-03
forum: Desktop Environments
---

### Post by Hoxzer on 2006-01-03
I'm having wierd problem on my ubuntu system. Sounds work propelly but when I already have on program using my sound card other one can't put sound out. 

For example if I have xmms running and I try to use team speak I can't hear anything peapol are speaking.

Edit:

I forgot to say that when I go to the sound setup my default sound card is named as "Nvidia CK8S" in ubuntu 5.04 I remeber the name was "esd"

---

### Post by rubinstein on 2006-01-03
Maybe esd (the sound daemon) isn't running. Check gnome-system-monitor if esd is running; if not, start it in a terminal with esd and test your sound.

---

### Post by Hoxzer on 2006-01-03
esd is running and I also tried to restart it but the problem stays.

Edit:
I forgot to say that when I go to the sound setup my default sound card is named as "Nvidia CK8S" in ubuntu 5.04 I remeber the name was "esd"

---

