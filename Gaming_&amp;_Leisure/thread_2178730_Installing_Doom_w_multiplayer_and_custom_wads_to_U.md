---
title: "Installing Doom w/ multiplayer and custom wads to Ubuntu 12.04 LTS"
date: 2013-10-04
forum: Gaming &amp; Leisure
---

### Post by Meowcenary on 2013-10-04
I want to install a version of Doom 2 to my computer and was wondering how to go about doing this. I currently have Doom 3 BFG Edition which has Doom 2 as part of the collection, but im not sure if that will work with multiplayer and custom wads. Are there any versions of Doom or Doom 2 that will run on linux the way I would like?

---

### Post by Pako Pako on 2013-10-05
Pardon my ignorance, buy isn't Doom2 a DOS game that you could use DOSbox to emulate?

---

### Post by Rod J on 2013-10-05
I've always been a fan of Doom Legacy which improves the graphics of the Doom games a great deal. Doom Legacy is cross-platform too: [http://doomlegacy.sourceforge.net/legacy.shtml](http://doomlegacy.sourceforge.net/legacy.shtml)

I have just about all the older versions of Doom and they all run perfectly for me in Kubuntu 12.04.

---

### Post by Rod J on 2013-10-05
After some confusion trying to find the latest stable Linux version (that doesn't need to be compiled) I found the link: [http://sourceforge.net/projects/doomlegacy/files/DooM%20Legacy%20full%20version/1.42/legacy_142_linux.tar.gz/download](http://sourceforge.net/projects/doomlegacy/files/DooM%20Legacy%20full%20version/1.42/legacy_142_linux.tar.gz/download)

Just extract this file into the directory you're Doom stuff is already in. I use a startup script (DoomLegacy.sh) to run the lsdldoom file. The Windows version of Legacy includes the launcher.exe program which makes starting Doom Legacy a snap when there are multiple .wad files present (I haven't tried running Doom Legacy in Wine as I prefer to run the native Linux version). As a quick and dirty workaround I wrote the following script. The script includes code to turn off and then back on the Gnome2 screen saver (I have disabled this because it doesn't work in Kubuntu and it may not work in more recent versions of Ubuntu):

```
#!/bin/sh

# If there are multiple .wad files in this directory you need to rename all but the one you wish
# to play to something like <wad name>.wad.doom.
# To choose which .wad file to use (doom.wad, doom2.wad, plutonia.wad or tnt.wad)
# simply rename the desired .wad file. Make sure to only have one .wad file active at
# any time. Exception: Leave doom3.wad as is (it is used by Legacy in some way).

# Turn off the screensaver (in Gnome2)
# gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool false

cd "/home/rod/Games/Doom 1, 2, TNT, Final & Ultimate"
./lsdldoom -opengl &
wait

# Turn screensaver back on (in Gnome2)
# gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true

```

---

### Post by Meowcenary on 2013-10-05
This seems to be what im looking for, thanks Rod J

---

### Post by mastablasta on 2013-10-08
there are also various such crossplatform engines that run old doom and wads. jdoom, zdoom and their derivatives. i like the ones that give some openGL graphics to the game. makes it look even cooler than it was.

---

