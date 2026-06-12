---
title: "ezQuake install script"
date: 2009-08-11
forum: Gaming &amp; Leisure
---

### Post by homerhomer on 2009-08-11
I was bored and decided to make a ezQuake install script. It's sort of ugly but should work. The script will download ezQuake and the shareware version of Quake and install the game. It also adds an icon to the Gnome Menu subsection Games

Prerequisites
In order to run this script you'll need to install the lha library. This is used to extract the PAK files from the original shareware game.

To install just open Synaptic and look for lha or you can go to command prompt and type.

sudo apt-get install lha

Steps to use the installer
Extract quakeinstaller from the quakeinstaller.tar file
Make the file executable (either right click or from CLI type "chmod +x quakeinstaller"
And run from commandline

When it's finished you should have a new entry in the gnome menu subsection Games called ezQuake

New with 1.3 
* Easy unisntaller if ezQuake is already installed. 

New with 1.2
* updated script downloads to a easier more reliable mirror 
* script now detect Xorg and runs a xterm

new with 2.0

* works with lucid
* updated ezQuake to 2.0

---

### Post by Brebs on 2009-08-11
All the echo lines can be simplified by this BASH method - example:

```
cat > paintown.desktop << EOF
[Desktop Entry]
Name=Paintown
Comment=Side-scrolling beat-em-up in the style of Beats of Rage
Icon=paintown
Exec=paintown
Categories=Game;ActionGame;
Terminal=false
Type=Application
EOF
```

The first line should be **#!/bin/bash**, otherwise people will submit crazy-sounding bug reports, because their [default sh](http://en.wikipedia.org/wiki/Unix_shell) is something exotic.

---

### Post by commodore256 on 2009-08-12
There's no sound

---

### Post by homerhomer on 2009-08-16
> **commodore256 said:**
> There's no sound


Did you get it working?

I've noticed that sound it really touchy with paulse audio. Try changing the sound setting in the config.  

[install dir]/ezquake/configs/config.cfg

maybe changing 
s_khz		"48"

to someting like 

//Sound Settings 
s_khz		"44"

good luck

---

### Post by homerhomer on 2009-08-17
Thanks

I updated the script

---

### Post by commodore256 on 2009-08-20
Thanks, Bro. I only wish it ran perfectly "out of the box".

---

### Post by ruzkie on 2009-08-21
sounds like a tiny version of nQuake, trying it out right now.

---

### Post by homerhomer on 2009-08-23
> **commodore256 said:**
> Thanks, Bro. I only wish it ran perfectly "out of the box".

Let me know if you get the sound working. Maybe I can modify the script.

Thanks

---

