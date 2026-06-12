---
title: "N64 emulation and Intel Graphics card"
date: 2006-12-30
forum: Gaming &amp; Leisure
---

### Post by Junk_head on 2006-12-30
I wanna play n64 roms on my ubuntu machine as i did in my windows setup which worked pretty well, but it seems mupgen64 is just slow, or the sacrifice of graphics to attain an ok framerate. The guides ive read speak of ati configs or nvidia card, i dont have a graphics card like that, any intergrated card users who use n64 emulation have any tips ? i810 is the card on ubuntu but i think it was 845

---

### Post by play0r on 2006-12-31
do you have direct rendering?

```
glxinfo | grep direct
```

if not... try uncommenting the following in your xorg.conf.

```
    
Load       "glx"
Load       "dri" 

Section "DRI"
    Mode 0666
EndSection
```

you may also want to add these options to your device section.

```

VideoRam <your video ram size here>
Option  "DRI"                           "true"

```

for the videoram, if you had a 32mb card the size would be 32768. check your documentation...

hope this helps,
play0r

p.s.
i use "mupen64_nogui --interactive /pathto/romdir/rom.z64" to play n64 games, it seems to lessen the ram usage that's created by running the gui.

---

### Post by Sklasko on 2007-01-01
I would recommend upgrading, an Intel chipset is usually regarded as the bare minimum when it comes to gaming. And emulators don't go easy on requirements, alot of the time even with a high-end GFX card you have to do some tweaking within the emulator to get good frame rates.

---

### Post by Junk_head on 2007-01-02
> **play0r said:**
> do you have direct rendering?

```
glxinfo | grep direct
```

if not... try uncommenting the following in your xorg.conf.

```
    
Load       "glx"
Load       "dri" 

Section "DRI"
    Mode 0666
EndSection
```

you may also want to add these options to your device section.

```

VideoRam <your video ram size here>
Option  "DRI"                           "true"

```

for the videoram, if you had a 32mb card the size would be 32768. check your documentation...

hope this helps,
play0r

p.s.
i use "mupen64_nogui --interactive /pathto/romdir/rom.z64" to play n64 games, it seems to lessen the ram usage that's created by running the gui.

It seems like i had DRI enabled already, but i didnt have the video ram set up so I'll try 64 mb

---

### Post by Junk_head on 2007-01-03
aww man adding that ram in the system messed up the x-server... aww man can someone help now i cant get to the xorg.conf file in this terminal fullscreen setup

---

### Post by hikaricore on 2007-01-03
ctrl+alt+f1

....

login...


sudo pico /ect/X11/xorg.conf


fix it....

---

### Post by Junk_head on 2007-01-04
thanks hikaricore
man was a little worried there.

---

### Post by hikaricore on 2007-01-04
Hehehe np, sorry for the grumpy reply.  I'm bad when I'm half awake.  >.<

---

