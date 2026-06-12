---
title: "suddenly my sound doesnt work"
date: 2006-01-24
forum: Desktop Environments
---

### Post by Brando569 on 2006-01-24
yesterday around 3 pm my sound worked perfectly, then hours later (around midnight or so) i decided to compile a new kernel, 2.6.15 (vanilla) and patch it with ArchCK2, eveything went fine and i booted into the new kernel. to my suprise the sound didnt work, i thought maybe this was a bug with the kernel since i read people were having strange problems with it. i planned on dealing with it later and went to sleep. today i booted into 2.6.12-9 and the same thing, no sound. i tried all of the kernels i have installed and i dont have sound in any of them, KDE doesnt give me any errors about something not loading, no errors during boot up, and when i try to play a song in amarok it goes along like it usually would but theres no sound comming from my speakers. i know my speakers are connected cuz my mother board is screwed up and the POST reporter tells me that the boot process failed due to cpu overclocking (wich neither happend, it still boots and the cpu isnt overclocked). i have no idea on how to fix this. i really didnt change anything in KDE between 3pm and midnight so idk what could have caused this. any suggestions?

---

### Post by otake-tux on 2006-01-24
type ```
sudo /etc/init.d/alsa-utils restart 
```

post what happens.

---

### Post by franklee on 2006-01-24
I have the same problem, in that there is no sound, but the alsa sound server seems to be functioning fine. I restarted Alsa using the command you posted and it simply said ok, ok. Stopped and restarted alsa, without any sound.

Any ideas?

---

### Post by Brando569 on 2006-01-24
same thing:

* Shutting down ALSA...                                                 [ ok ]
* Setting up ALSA...                                                      [ ok ]

its wierd it happened randomly

---

### Post by otake-tux on 2006-01-24
did you run the command in the old kernel?

---

### Post by Brando569 on 2006-01-24
i am running the old kernel :-/

---

### Post by otake-tux on 2006-01-24
run alsamixer and make sure everything is above 0%.

---

### Post by Brando569 on 2006-01-25
they are, that was the second thing i checked, cuz im known for overlooking the stupid things. a few times on my surround sound system i thought a peice of it was broken when in reality either a fuse blew or something came unplugged...

---

### Post by otake-tux on 2006-01-25
strange, did you enable  alsasound when you compiled your kernel?

---

### Post by Brando569 on 2006-01-26
im pretty sure i did, i used the config from one of the ubuntu kernels but i dont see how not enabling it in one kernel would effect all of them... this is really starting to make me mad cuz i wanna listen to music

---

### Post by Brando569 on 2006-01-26
found this in my bootlog:

```
 * Setting up ALSA...
/etc/init.d/alsa-utils: Warning: 'alsactl restore' failed with error message 'alsactl: set_control:894: warning: name mismatch (Stereo Mic/Headphone Jack Sense) for control #44
: alsactl: set_control:896: warning: index mismatch (0/0) for control #44
: alsactl: set_control:894: warning: name mismatch (Exchange Center/LFE/Line Jack Sense) for control #45
: alsactl: set_control:896: warning: index mismatch (0/0) for control #45
: alsactl: set_control:898: failed to obtain info for control #45 (Operation not permitted)'. 
```

i tried uninstalling alsa-utils and then reinstalling it but that didnt help... if i cant get this fixed im gonna have to reinstall... :(

---

