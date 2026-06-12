---
title: "How to save a game in progress using Mednaffe emulator?"
date: 2024-01-10
forum: Gaming &amp; Leisure
---

### Post by joep991 on 2024-01-10
Anyone know how to save a game in progress (emulating the PS1) using the Mednaffe emulator?

---

### Post by jimmyrus on 2024-01-11
> **joep991 said:**
> Anyone know how to save a game in progress (emulating the PS1) using the Mednaffe emulator?
did you try the extreme measure of reading the docs?  [https://mednafen.github.io/documentation/](https://mednafen.github.io/documentation/)   [https://github.com/AmatCoder/mednaffe/wiki](https://github.com/AmatCoder/mednaffe/wiki)  

These idiots have been using that stuff for a while why don't you pm them?
[https://ubuntuforums.org/showthread.php?t=2492450](https://ubuntuforums.org/showthread.php?t=2492450)  [https://ubuntuforums.org/showthread.php?t=2251228](https://ubuntuforums.org/showthread.php?t=2251228)  [https://ubuntuforums.org/showthread.php?t=2195338](https://ubuntuforums.org/showthread.php?t=2195338)

---

### Post by Holger_Gehrke on 2024-01-12
You can either use the (emulated) memory card which is stored in ~/.mednafen/sav/, one 128 KB card per game, named after the game with extensions *.[01].mcr and use whatever option for saving the game offers. Or you can use save states, keys '1' to '0' select a save 'slot', F5 saves the current state to the selected slot, F7  load the state from the currently selected slot. Save states are stored in files in ~/.mednafen/mcs/.

Holger

---

### Post by jimmyrus on 2024-01-13
> **Holger_Gehrke said:**
> You can either use the (emulated) memory card which is stored in ~/.mednafen/sav/, one 128 KB card per game, named after the game with extensions *.[01].mcr and use whatever option for saving the game offers. Or you can use save states, keys '1' to '0' select a save 'slot', F5 saves the current state to the selected slot, F7  load the state from the currently selected slot. Save states are stored in files in ~/.mednafen/mcs/.

Holger
ya, all in the docs. especially since the op's been using this stuff for about 10yrs now. Loads of different id's here.

---

### Post by martacostello on 2024-01-16
Hey, 

Aaving your game in Mednaffe for a PS1 emulation is pretty simple. Just hit the 'Esc' key to open the menu while your game is running. Look for the 'Save State' option and choose a slot to save your game. Later, you can load it from the same menu by selecting 'Load State.' Make sure to save often for a smooth gaming experience!"

---

### Post by stdhamza on 2024-03-17
To save a game in progress using Mednaffe emulator, press the F5 key to create a save state, and press F7 to load a previously saved state. These shortcuts allow you to easily save and resume your game progress at any time.

---

### Post by stdhamza on 2024-03-17
And also you can navigate to the File menu, select "Save State" to save your game progress, and choose "Load State" to resume from a previously saved point.

---

