---
title: "Import Mupen64Plus save to Project 64?"
date: 2011-05-24
forum: Gaming &amp; Leisure
---

### Post by JellyBeanRacer on 2011-05-24
So I have a file in Majora's Mask in Mupen64Plus on my Ubuntu machine which I would love to have work in Project 64 in Windows 7.

(1) I don't know where save files are kept or which files to use
(2) I don't know if Project 64 will even be able to read save files created by Mupen
(3) Google provided no help

All help very much appreciated.

---

### Post by doorknob60 on 2011-05-24
Look in ~/.mupen64plus/save, copy the .eep file to wherever the Project64 save files are stored, and it should work. If you start the game in PJ64 and it creates a new savefile and ignores the one you put there, delete the one it created and rename the one you want to use to whatever it was called. That's what I always do, and it works just fine. Also, symlinking works quite nicely if you want to be able to switch back and forth :D

---

### Post by JellyBeanRacer on 2011-05-26
Hey, thanks for the reply.

I got to the directory, and a few of the roms have an .eep file in there, but Majora's Mask does not ...

The two files relating to Majora's Mask have .fla and .st0

Is there someway I can force Majora's Mask to output an .eep file?

---

### Post by JellyBeanRacer on 2011-05-27
Bump. =(

---

### Post by doorknob60 on 2011-05-27
If it doesn't have a .eep file, maybe it saves differently than other games. Copy (or symlink) the other files, see what happens. From googleing, looks like the .fla file is just a different format of savefile that certain games use (there's also .sra, maybe some others), that's probably the right one, and should work the same. I think the .st0 might just be a savestate or something, can't tell, but the .fla is probably what you want.

---

### Post by MalGaniz on 2011-08-30
Interestig questin! I have done that many times and it's easy.

Fist of all, Open a new game and save it with PJ64, go to te directory and see the saved saved. Take the Mupen64 saved file and move to that directory, but, here's the trick;

assuming you have saved the same game, you'll notice the difference between the 2 files names, you can simply rename your Mupen64 saved file (eve the extension).

---

