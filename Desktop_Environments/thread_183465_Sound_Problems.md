---
title: "Sound Problems"
date: 2006-05-28
forum: Desktop Environments
---

### Post by CameronCalver on 2006-05-28
Hey i have been having sound problems with ubuntu for a while

i have breey 5.10 and i can run a game and the sound will be fine but if i quit the game then get back into it or get into another game i have no sound until i do killall esd can some1 plz help me

---

### Post by dmizer on 2006-05-28
try this:
```
sudo nano /etc/libao.conf
```
change esd to alsa.  hit ctrl+x ... select "y" to save it, then enter.  reboot, and all should be well.

as an asside, there should be a way to restart the sound without rebooting, but i don't know how.  if someone would come along and point that out to me, i would really appreciate it because i need to do that now on my server (which i'd rather not reboot).

---

