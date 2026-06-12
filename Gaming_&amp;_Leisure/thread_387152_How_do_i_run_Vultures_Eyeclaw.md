---
title: "How do i run Vultures Eye/claw"
date: 2007-03-17
forum: Gaming &amp; Leisure
---

### Post by mesach on 2007-03-17
I appear to have installed it correctly, but vultureseye and vulturesclaw do nothing in terminal, and they dont exist on the menu anywhere...

Anyone have any insight on how to start the game?

---

### Post by Perfect Storm on 2007-03-18
How did you install it? 

also 
```
whereis  vultures
locate vultures
```

---

### Post by mesach on 2007-03-18
First i had some issues with one package so i had to downgrade following these instructions here [http://ubuntuforums.org/showthread.php?p=2004663](http://ubuntuforums.org/showthread.php?p=2004663)

then I installed it by following this [http://ubuntuforums.org/showthread.php?t=335262](http://ubuntuforums.org/showthread.php?t=335262)

so its in ~/vultures folder but i dont know of any command that will run it, vulture isnt in any tab completion and the documentation just says

Great now it's installed, just run it and have fun... RUN WHAT?

---

### Post by Perfect Storm on 2007-03-18
Normally it's a bad idea to downgrade (there's situations where if you installed an unofficial libs and it breaks your system).

well lets see;
```
 cd /into/vultures/folder
ls -a
```

---

### Post by mesach on 2007-03-18
ls -a just gives me 

.   ..   vulturesclaw   vulturesclawdir   vultureseye   vultureseyedir

both claw and eye are green therefore i thought they were executable, but i cant get bash to recognise them

whereis vultures just returnes
vultures:

and locate finds all directories and such but i cant figure out what the executable is...

should i upgrade the file i downgraded earlier, i only did it, because libglu1-mesa refused to install with the newer version of libgl1-mesa

---

### Post by mesach on 2007-03-18
BTW thanks for your help!

---

### Post by Perfect Storm on 2007-03-18
Just leave the libs as they are now (as long it doesn't mess your system up).

okay try this;
```
chmod +x vultureseye
chmod +x vulturesclaw
./vultureseye
```

---

### Post by mesach on 2007-03-18
YOU ARE SOOOOOO SMART!!!!

That worked! Thanks!

---

### Post by Perfect Storm on 2007-03-18
You might want to make a launcher script for them so you don't have to **cd** into the folder a launch it manually.

```
cd /into/the/vulture/folder
nano Startvultureseye.sh
```

add:

[b]#!/bin/bash

cd /into/the/vulture/folder
./vultureseye[/b]

save [ctrl]+[o] and exit [ctrl]+[x]

```
chmod +x Startvultureseye.sh
alacarte
```

Name: Vultures Eye
Comment: *Whatever you like*
Command: sh <distination>/Startvultureseye.sh


You might want to do the same with vulturesclaw

---

