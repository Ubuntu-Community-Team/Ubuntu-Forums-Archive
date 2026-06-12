---
title: "Tremulous HUD not working???"
date: 2010-06-25
forum: Gaming &amp; Leisure
---

### Post by creative31 on 2010-06-25
Hi, I've just downloaded a new HUD for tremulous, the impulse HUD, 1st version, and I did the instructions, and I ran tremulous, It worked for one game, then then it reset to the default next game?? anyone know how to fix this

Edit: You can find the HUD here.

PS: For some reason, My fps drops down real low, even with default HUD, any suggestions? I'm not using compiz.

thx
Creative

---

### Post by HoKaze on 2010-06-25
I haven't really used any mods with Tremulous but you may have to either choose it from "mods" each time or set up a script that launches Tremulous with the mod.
Also, as far as FPS go, have you tried adjusting settings (e.g. reducing effects, lower quality textures, etc) and also try running in windowed mode at a lower resolution? What graphics card are you using?

---

### Post by creative31 on 2010-06-25
Its not a MOD, Its a HUD, But scripts I dont know. Ive tryed from the console,
```
/cg-hudfiles''ui/impulse.cfg
```  
and
```
/exec ui/impulse.cfg
```

---

### Post by creative31 on 2010-06-25
As for video card I have radeon 5670 1gb, so it can handle effects, and ive got the drivers.

---

### Post by HoKaze on 2010-06-25
Although Tremulous makes a distinction between HUDs and other mods, a different HUD is still a mod <_<;
Anyway, I've looked into this and I'm not 100% sure if these instructions are relevant to your version (which appears to be old seeing Impulse version 6 is now over 2 years old...) but here they are: 
1. Extract the HUD into the tremulous base folder (/home/user/.tremulous/base)
2. Edit the file /home/user/.tremulous/autogen.cfg with the text editor of your choice
3. Replace the line that starts with ```
seta cg_hudfiles
``` with ```
seta cg_hudfiles "ui/Impulse.cfg"
``` (or create this line if it doesn't exist)
4. Replace the line that starts with ```
cg_drawcrosshair
``` with ```
cg_drawcrosshair 4
``` (again, if it doesn't exist, add this line, but it should exist)

You shouldn't have to run any commands in-game to change the HUD if you do this. Hope this helps.

---

### Post by creative31 on 2010-06-25
Ive done this, still doesn't work, though my bigger concern is my fps doesn't go above 30, and i have max fps set to 85?any one know whats up

---

### Post by creative31 on 2010-06-26
noone can answer why my fps is so low!

---

