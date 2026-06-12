---
title: "mine craft 1.8/1.9 fglrx graphic fix mien craft now playable"
date: 2011-09-25
forum: Gaming &amp; Leisure
---

### Post by markg48 on 2011-09-25
If you where like me u cudnt play mine craft on fglrx driver or open source(to slow 10 fps) here quicks fix till its been patched open terminal in put in :

env LIBGL_ALWAYS_INDIRECT=1 java -Xmx1024M -Xms512M -cp /home/yourusername/Desktop/Minecraft.jar net.minecraft.LauncherFrame

change directory to where your mine craft launcher is mine is on desktop

mine craft 1.8 :minor graphic glitches some blocks turn black and animals (40-70 fps)

mine craft 1.9pre:nearly perfect blocks flash sometimes (40-70fps)

mien craft on xf86-ati-driver: 2-12 fps

---

### Post by markg48 on 2011-09-25
EDIT: miss spell mine (mien)

---

### Post by markg48 on 2011-09-25
mark executing in file properties if it isnt and edit to file to
change where your mine craft launcher is enjoy (not in ./minecraft)

---

### Post by WesleyAaron on 2011-09-26
when i put that in the terminal i get this


"env: java-Xmex1024m-Xms512M: No such file or directory"

---

### Post by markg48 on 2011-09-27
you have to point it to the directory u have minecraft.jar or (minecraftSP.jar)

---

