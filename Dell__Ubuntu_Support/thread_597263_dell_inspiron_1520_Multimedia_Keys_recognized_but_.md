---
title: "dell inspiron 1520: Multimedia Keys recognized but dont affect ALSAMIXER"
date: 2007-10-30
forum: Dell  Ubuntu Support
---

### Post by cellerit on 2007-10-30
Title says nearly everything. Basically, when i press the multimedia keys i see nice graphjcs on my screen telling me i lowered the volume / muted etc... but in practice it doesnt affect the real sound output, it doesnt act on alsamixer.
Any idea how to fix it?
Thanks alot!

---

### Post by rockin_goliath on 2007-10-30
Are you trying to control the volume of the internal speakers or the headphone volume? Usually the multimedia keys are bound to the Master Volume, which only controls the internal speakers, and not headphone volume. Headphone volume is done with a separate level in Alsamixer. Are you able to control the volumes you want by clicking on the volume icon and moving the sliders?

If it is a key binding issue, refer to this post. It describes using the application "xbindkeys" to change what volume levels the multimedia keys control. This person used it to bind his keys to link the headphone and master volume.

[http://ubuntuforums.org/archive/index.php/t-79717.html](http://ubuntuforums.org/archive/index.php/t-79717.html)

Good luck!

---

### Post by cellerit on 2007-10-30
Thanks but xbindkeys config doesnt take my input when i press a media key (although like i said i see the nice drawings on the screen corresponding to the media key) and they control neither the master volume nor the PCM. All they do that i know of is nice GUI animations that do correspond to the right key. Maybe im missing some package?
thanks again.

edit:
Oh and i recently reistalled Ubuntu with exactly the same CD, but the first time the keys did work and controlled the master volume and the headphones and i had compiz fusion installed, this time neither of the 2 worked, i installed compiz fusion just fine. .. its just its weird since i used the same cd...

---

### Post by rockin_goliath on 2007-10-30
Interesting. Try and burn the Gutsy LiveCD at the slowest speed possible. I've run into installation troubles that way as well.

---

### Post by Qinjuehang on 2007-11-01
I have that on a compaq multimedia keyboard. It only happened AFTER i used the alsamixer config utility...so...I think it is a configuration problem

Edit:I realised that it controls my PC Speaker volume, not the Master Volume. And the PC Speaker seems only to affect the "beeps" when there is an error. I think I'll go edit the config file if I can find it.

Edit2:Got it to work. Go to System>Prefences>Sound and select Master volume in the Menu (for me). Assuming you use gnome.

---

### Post by cellerit on 2007-11-01
wow thanks alot it worked! easy as that :)!
it was actually changing the recording volume! when my microphone doesnt even work (thats another problem) ...
thanks again!

---

### Post by Qinjuehang on 2007-11-01
np :D Maybe Dell thinks everyone's a DJ :P

---

### Post by ashdezign on 2007-11-10
Qinjuehang: Thanks!

> Got it to work. Go to System>Prefences>Sound and select Master volume in the Menu (for me). Assuming you use gnome

I was having the same problem and that fixed it.

---

