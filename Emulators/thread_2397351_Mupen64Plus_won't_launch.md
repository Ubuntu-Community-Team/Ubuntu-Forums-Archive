---
title: "Mupen64Plus won't launch"
date: 2018-07-28
forum: Emulators
---

### Post by dexterisawesome on 2018-07-28
mupen64plus isn't launching. I rightclick my rom, and i select "Open with Mupen64Plus". Mupen64plus opens and closes in i could say one milisecond. :mad:

---

### Post by deadflowr on 2018-07-28
*Thread moved to **Emulators***

Open a terminal and run the command
```
mupen64plus /path/to/file
```
replacing /path/to/file with the path to a rom file.
Click ESC to quit and post back the output from the command.

---

### Post by dexterisawesome on 2018-07-28
THank you!
Wait... i tryed that before. 
Mupen does not work on the terminal.
I'm 7, so i might have been doing it wrong, but i did what you said  earlier and it did'nt work.
It might have been a virus.

---

### Post by deadflowr on 2018-07-28
I asked for the output from the command I posted.
Whether or not it works is irrelevant.

---

### Post by dexterisawesome on 2018-07-28
I have a possible idea why it isn't working. [FONT=microsoft sans serif]it could be the memory, not enough slots to run mupen64plus. i only have a like 300 gigabyte harddrive[/FONT]

---

### Post by alcagenericpyro on 2018-08-14
Alright. First: Try running it in terminal, then tell me the error. I might know enough to fix it, but most likely will redirect you to a fix somewhere else. Also sorry for being a necromancer and necromancing this thread. I also want to see the error.

EDIT: I think I know the error, I've been getting this error too.
It's the following error:
> dlopen('libmupen64plus.so.2') error: libpng12.so.0: cannot open shared object file: No such file or directory
dlopen('./libmupen64plus.so.2') error: libpng12.so.0: cannot open shared object file: No such file or directory
AttachCoreLib() Error: failed to find Mupen64Plus Core library

Am I correct? (ascii art and other stuff removed for clarity)

---

