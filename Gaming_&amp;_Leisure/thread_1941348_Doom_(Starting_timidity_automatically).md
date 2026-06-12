---
title: "Doom (Starting timidity automatically)"
date: 2012-03-15
forum: Gaming &amp; Leisure
---

### Post by christopher.mountford on 2012-03-15
I was wondering if anyone could help me, I have recently installed the original doom using Dosbox and I'm using timidity for MIDI emulation, as far as I know both the game and timidity are configured properly but each time i want to run the game i have to start timidity manually from the commandline using ```
timidity -iA -B2,8 -Os -EFreverb=0 2>&1 &
```

Does anyone know of a way of adding a script to the game's shortcut that will check the status of timidity and start it automatically if it isn't running? 

I know this is probably very amateurish stuff but I haven't really had much experience with shell scripting.

---

### Post by lite1979 on 2012-03-19
Depending on which one you want to run first, I would modify whatever you use to launch Doom with "&&" and the code you posted above either before or after the Doom command (not sure which should come first)

---

