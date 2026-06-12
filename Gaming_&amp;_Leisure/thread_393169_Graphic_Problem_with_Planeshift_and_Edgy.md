---
title: "Graphic Problem with Planeshift and Edgy"
date: 2007-03-25
forum: Gaming &amp; Leisure
---

### Post by eaglesfan17 on 2007-03-25
I'm having a strange problem with Planeshift. The game installed just fine (binary version), but when I load it, it looks like this:

[IMG]http://img340.imageshack.us/img340/6631/mainxb9.th.jpg[/IMG]
[IMG]http://img179.imageshack.us/img179/9776/setupfq8.th.jpg[/IMG]

I'm sure it's some kind of font issue but I have no clue as to what it could be.

Has anyone encountered this before?

Also, here is the output from psclient when it is run:

```

joseph@joseph-desktop:~/games/PlaneShift$ ./psclient
DEBUG: Sound System Software Renderer Initializing...
ATTENTION: default value of option force_s3tc_enable overridden by environment.
libGL warning: 3D driver claims to not support visual 0x4b

crystalspace.canvas.openglcommon:
  Driver database lacks <gldriverdb> node
*********************************WARN_ONCE*********************************
File radeon_mm.c function radeon_mm_alloc line 216
Ran out of GART memory (for 33554432)!
Please consider adjusting GARTSize option.
***************************************************************************

planeshift.application.client:
  PlaneShift Crystal Blue
  This game uses Crystal Space Engine created by Jorrit and others
  1.1dev [Unix-x86-GCC]
LOG_ANY flag deactivated with no filter.
LOG_WEATHER flag deactivated with no filter.
LOG_SPAWN flag deactivated with no filter.
LOG_CELPERSIST flag deactivated with no filter.
LOG_PAWS flag deactivated with no filter.
LOG_GROUP flag deactivated with no filter.
LOG_CHEAT flag deactivated with no filter.
LOG_LINMOVE flag deactivated with no filter.
LOG_SPELLS flag deactivated with no filter.
LOG_NEWCHAR flag deactivated with no filter.
LOG_SUPERCLIENT flag deactivated with no filter.
LOG_EXCHANGES flag deactivated with no filter.
LOG_ADMIN flag deactivated with no filter.
LOG_STARTUP flag deactivated with no filter.
LOG_CHARACTER flag deactivated with no filter.
LOG_CONNECTIONS flag deactivated with no filter.
LOG_CHAT flag deactivated with no filter.
LOG_NET flag deactivated with no filter.
LOG_LOAD flag deactivated with no filter.
LOG_NPC flag deactivated with no filter.
LOG_TRADE flag deactivated with no filter.
LOG_SOUND flag deactivated with no filter.
LOG_COMBAT flag deactivated with no filter.
LOG_SKILLXP flag deactivated with no filter.
LOG_QUESTS flag deactivated with no filter.
LOG_SCRIPT flag deactivated with no filter.
LOG_MARRIAGE flag deactivated with no filter.
LOG_MESSAGES flag deactivated with no filter.
LOG_CACHE flag deactivated with no filter.
LOG_PETS flag deactivated with no filter.
LOG_USER flag deactivated with no filter.
LOG_LOOT flag deactivated with no filter.
LOG_DUELS flag deactivated with no filter.
LOG_TRIBES flag deactivated with no filter.
All LOGS are off.
Mounting skin: /this/art/skins/elves.zip
Mounting skin: /planeshift/art/skins/base/client_base.zip
Skipping 'ButtonTutorial' because it's already loaded
  psEngine initialized.
Using fontsize 16 for resolution 1024x768

crystalspace.maploader.parse.image:
  Could not open image file '/planeshift/models/clacker/clacker_2.dds' on VFS!

crystalspace.maploader.parse.texture:
  Could not load texture 'clacker_texture2', using checkerboard instead
  [node: library,textures,texture(name=clacker_texture2)]

crystalspace.maploader.parse.image:
  Could not open image file '/planeshift/models/clacker/clacker_3.dds' on VFS!

crystalspace.maploader.parse.texture:
  Could not load texture 'clacker_texture3', using checkerboard instead
  [node: library,textures,texture(name=clacker_texture3)]

crystalspace.maploader.parse.image:
  Could not open image file 'Trepor_texture2' on VFS!

crystalspace.maploader.parse.texture:
  Couldn't load image 'Trepor_texture2', using checkerboard instead!

crystalspace.maploader.parse.image:
  Could not open image file 'Trepor_texture3' on VFS!

crystalspace.maploader.parse.texture:
  Couldn't load image 'Trepor_texture3', using checkerboard instead!

```

---

### Post by fender1212 on 2007-03-27
Im having the same problem! any help?

---

### Post by eaglesfan17 on 2007-03-28
Looks like we are alone on this one fender...

I have tried re-installing, installing as root or not as root, etc. I guess it just wasn't meant to be.

I may try it out again in Feisty or something. I can't get any support on the Planeshift forums.

---

### Post by fender1212 on 2007-03-29
lol, tried it in feisty.  no use.  maybe if we compile it from source?  i do recall in the back of my mind this font problem being something common, cuz i played planeshift over a year ago, but i can't remember the fix.  i think there was some sort of patch

---

### Post by fender1212 on 2007-03-29
i tried running the updater in non-graphical mode, got this

```
peter@peter-desktop:~/planeshift$ ./updater -auto
Critical files (<critical>) not found (Server only)
NOTIFY: psUpdaterEngine initialized.
Checking registry version...
Server error 404 (http://65.90.250.154/~psmirror/psupdater/version.dat)
Couldn't connect to mirror mir2!
Trying mirror mir1..
Server error 404 (http://planeshift.mirror.thumbnail.cz/psupdater/version.dat)
Bad version info in file: /this/updatertemp/mir1.dat
Mirror lacks a version file; can't use it
Trying mirror mir2..
Server error 404 (http://www.psmirror.org/psupdater/version.dat)
Bad version info in file: /this/updatertemp/mir2.dat
Mirror lacks a version file; can't use it
Trying mirror backup..
Server error 404 (http://laanx.fragnetics.com/updater_hidden/version.dat)
Bad version info in file: /this/updatertemp/backup.dat
Mirror lacks a version file; can't use it
Ran out of mirrors! Game cannot be updated.

```

---

### Post by eaglesfan17 on 2007-03-29
Weird dude, I just ran the same exact command and got the exact same output! Hmm....

---

### Post by eaglesfan17 on 2007-03-29
I was considering compiling it from source, found a little guide here:

```

http://planeshift.cvs.sourceforge.net/*checkout*/planeshift/planeshift/docs/compiling.html

```

Probably will take a whack at it some time this weekend.

---

### Post by OldSpiceAP on 2007-04-07
[http://vaalnor.mine.nu/psdoc](http://vaalnor.mine.nu/psdoc)

I independently maintain ubuntu build guides for dapper, edgy, and feisty.  PlaneShifts official compile docs are lacking.  Mine are even specific for specific ubuntu versions, so these would work better for you. I know the guides are awsome.. cause I wrote them! Whoo!!

---

