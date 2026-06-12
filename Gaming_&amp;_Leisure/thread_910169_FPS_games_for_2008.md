---
title: "FPS games for 2008"
date: 2008-09-04
forum: Gaming &amp; Leisure
---

### Post by dope540 on 2008-09-04
I am looking for a couple FPS's but the one's I find are either unavailable or run with no sound.

I currently have Assaultcube and Nexuiz, only gripe about nexuiz is that there is no crosshair.

alien arena worked but without sound, tremulous would only work if i play online.

warsow is the same.

i can't get urban terror, truecombat elite as the websites either only have a windows download or do not exists, which is the case for truecombat.

i am running hardy heron, on a 64bit.

---

### Post by Eren on 2008-09-04
what is your pc's specs bro? write here. and are your configs correct? did you correctly installed your graphic card etc? write here than the answers will come.

---

### Post by dope540 on 2008-09-04
> **Eren said:**
> what is your pc's specs bro? write here. and are your configs correct? did you correctly installed your graphic card etc? write here than the answers will come.

i have a compaq presario v3000, amd turion64, nvidia graphics card. the actual models i'm not sure of but the laptop is only a few months old, so should be able to support the games.

i assume that ubuntu installed my graphics card correctly when i installed it. the games i either downloaded from getdeb.net or via synaptic which all the relevant files were installed aswell.

---

### Post by Catalyst2Death on 2008-09-04
You should install the nvidia proprietary drivers: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

also, make sure you have direct rendering:

```
$ glxinfo | grep render

```
Should output: 
Direct Rendering: yes
Render String: nvidia blah blah

---

### Post by dope540 on 2008-09-04
> **Catalyst2Death said:**
> You should install the nvidia proprietary drivers: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

also, make sure you have direct rendering:

```
$ glxinfo | grep render

```
Should output: 
Direct Rendering: yes
Render String: nvidia blah blah

just tried the rendering you posted and its just says command not recognised.

and my nvidia drivers are installed and enabled.

---

### Post by Irritant on 2008-09-04
Try using the sdl versions of each of these game's binaries.

---

