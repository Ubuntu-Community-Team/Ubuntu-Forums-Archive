---
title: "Enemy Territory problems - GUID and more!"
date: 2009-01-08
forum: Gaming &amp; Leisure
---

### Post by spasticteapot on 2009-01-08
I installed ET, only to find that I was kicked out of each server after a few seconds. I then followed this guide:

[http://ubuntuforums.org/showthread.php?t=608466](http://ubuntuforums.org/showthread.php?t=608466)

Except that I couldn't get the .x86 files to execute after being chmodded. Now I'm getting an "invalid GUID" error and the console is telling me it can't write to files. 

What mistake did I make?

---

### Post by Cresho on 2009-01-08
```
#!/bin/bash
#Script Compiz/on/off
#killall awn
# Compiz off;
killall compiz.real &
metacity --replace &


#amixer -q set "Line Capture" 0% mute &
#amixer -q set "Synth Capture" 0% mute &
#amixer -q set "IEC958 Optical Capture" 0% mute &
#amixer -q set "Line2 Capture" 0% mute &
#amixer -q set "PCM Capture" 0% mute &
#amixer -q set "Aux2 Capture" 0% mute &
#amixer -q set "Analog Mix Capture Volume" 0% mute &
#amixer -q set "Audigy CD Capture" 0% mute &
sleep 4 && amixer -q set "Mic Capture" 100% unmute;


#run game;
cd ~/Installed_Programs/etqw
sleep 1 && ./etqw;

#Compiz on;
compiz --replace &
metacity --replace &

#sleep 4 && amixer -q set "Mic Capture" 0% mute;
#killall awn


#sleep 10 && awn
#sleep 3 && killall awn
#sleep 4 && awn
```

i slaped this one together which in conjunction of an exterior mic fix, works.  look at the run game section.  it might  help

---

### Post by spasticteapot on 2009-01-09
> **Cresho said:**
> [code]#!/bin/bash


i slaped this one together which in conjunction of an exterior mic fix, works.  look at the run game section.  it might  help

Isn't this just a sound fix?

Currently, when I try to update my GUID, it tells me that can't write to the GUID. ???

---

### Post by poisonkiller on 2009-01-09
Try "sudo nautilus" and set the "/usr/local/games/enemy-territory" folder permissions to read and write for your user. If that doesn't work, try deleting your "./.etwolf/etmain/etkey" file.

---

