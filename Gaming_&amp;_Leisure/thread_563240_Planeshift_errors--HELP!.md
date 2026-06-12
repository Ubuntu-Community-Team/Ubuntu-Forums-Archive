---
title: "Planeshift errors--HELP!"
date: 2007-09-29
forum: Gaming &amp; Leisure
---

### Post by oneadvent on 2007-09-29
I installed Planeshift on my box, and I got the install working great, and started the game, and it started....flashing....

I tried to take a screenshot, but it kept just catching the black part of the flash...maybe I can video capture it if anyone thinks that will help. Anyway, I can play CS fine, as well as ActionCube without much trouble, so this should play, albeit slow. Here is what the terminal spit out:
```
jwelch@jwelch-laptop:~/Desktop$ sudo planeshift
DEBUG: Sound System Software Renderer Initializing...
ATTENTION: default value of option force_s3tc_enable overridden by environment.

planeshift.application.client:
  PlaneShift Crystal Blue
  This game uses Crystal Space Engine created by Jorrit and others
  1.1.0 [Unix-x86-GCC]
     379 LOG_ANY flag deactivated with no filter.
     379 LOG_WEATHER flag deactivated with no filter.
     379 LOG_SPAWN flag deactivated with no filter.
     379 LOG_CELPERSIST flag deactivated with no filter.
     380 LOG_PAWS flag deactivated with no filter.
     380 LOG_GROUP flag deactivated with no filter.
     380 LOG_CHEAT flag deactivated with no filter.
     380 LOG_LINMOVE flag deactivated with no filter.
     380 LOG_SPELLS flag deactivated with no filter.
     381 LOG_NEWCHAR flag deactivated with no filter.
     381 LOG_SUPERCLIENT flag deactivated with no filter.
     381 LOG_EXCHANGES flag deactivated with no filter.
     381 LOG_ADMIN flag deactivated with no filter.
     381 LOG_STARTUP flag deactivated with no filter.
     381 LOG_CHARACTER flag deactivated with no filter.
     382 LOG_CONNECTIONS flag deactivated with no filter.
     382 LOG_CHAT flag deactivated with no filter.
     382 LOG_NET flag deactivated with no filter.
     382 LOG_LOAD flag deactivated with no filter.
     382 LOG_NPC flag deactivated with no filter.
     383 LOG_TRADE flag deactivated with no filter.
     383 LOG_SOUND flag deactivated with no filter.
     383 LOG_COMBAT flag deactivated with no filter.
     383 LOG_SKILLXP flag deactivated with no filter.
     383 LOG_QUESTS flag deactivated with no filter.
     383 LOG_SCRIPT flag deactivated with no filter.
     384 LOG_MARRIAGE flag deactivated with no filter.
     384 LOG_MESSAGES flag deactivated with no filter.
     384 LOG_CACHE flag deactivated with no filter.
     384 LOG_PETS flag deactivated with no filter.
     386 LOG_USER flag deactivated with no filter.
     386 LOG_LOOT flag deactivated with no filter.
     387 LOG_DUELS flag deactivated with no filter.
     387 LOG_TRIBES flag deactivated with no filter.
     387 All LOGS are off.
Mounting skin: /this/art/skins/elves.zip
Mounting skin: /planeshift/art/skins/base/client_base.zip
  psEngine initialized.
Using fontsize 16 for resolution 1024x768

crystalspace.maploader.parse.image:
  Could not open image file 'tlo-ke_1.dds' on VFS!

crystalspace.maploader.parse.texture:
  Couldn't load image 'tlo-ke_1.dds', using error texture instead!

crystalspace.maploader.parse.image:
  Could not open image file '/planeshift/items/spoon_wooden01a.dds' on VFS!

crystalspace.maploader.parse.texture:
  Couldn't load image '/planeshift/items/spoon_wooden01a.dds', using error
  texture instead!
psEngine destroyed.
Segmentation fault (core dumped)

```

Anyone got any ideas? I'm stuck on this one.

Thanks in advance.

---

### Post by oneadvent on 2007-09-29
Update: I tried to run the set up, but I cannot read any of the fonts....

I will attach a screenshot, I hope this helps any gurus out there.

---

### Post by Ripfox on 2007-09-29
Font multitexturing has been broken, try the following:
Open up the file Planeshift3D/data/config/r3dopengl.cfg in a text editor, and find this line:
Video.OpenGL.FontCache.UseMultiTexturing = yes
and change yes to no.

---

### Post by oneadvent on 2007-09-29
Ok, font problem fixed, but it still seems like it is SLOWLY refreshing or something. It flashes black and regular, totally unplayable. It isn't slow though...just really annoying.

---

### Post by oneadvent on 2007-09-29
maybe there is a way to increase the refresh rate or maybe it doesn't auto start in opengl or something?

---

### Post by oneadvent on 2007-09-29
Oh, another thing is that it seems to run fine in everything except the actual game, for instance the updater runs fine, and so does the config utility for it.

---

### Post by appleipod30 on 2008-01-20
im having the same problem + i cant even open the game or updater because whenever i try to open the updater or client even uninstaller it gives me this error

---

### Post by dtgolder on 2008-03-08
Try putting a symbolic link to opt from you home directory:

ln -s /opt ./opt

---

