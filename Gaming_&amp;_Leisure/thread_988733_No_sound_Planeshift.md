---
title: "No sound Planeshift"
date: 2008-11-20
forum: Gaming &amp; Leisure
---

### Post by Alvinius on 2008-11-20
I am running 64 bit intrepid, I get no sound in planeshift, sound is fine in other programs, running alsa.

Your configuration files are in... /home/james/.PlaneShift
DEBUG: Sound System Software Renderer Initializing...

planeshift.application.client:
  PlaneShift Steel Blue (0.4.01)
  This game uses Crystal Space Engine created by Jorrit and others
  1.4.0 [Unix-x86-GCC]
Thu Nov 20 18:29:28 2008, LOG_ANY flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_WEATHER flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_SPAWN flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_CELPERSIST flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_PAWS flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_GROUP flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_CHEAT flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_LINMOVE flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_SPELLS flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_NEWCHAR flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_SUPERCLIENT flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_EXCHANGES flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_ADMIN flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_STARTUP flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_CHARACTER flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_CONNECTIONS flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_CHAT flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_NET flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_LOAD flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_NPC flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_TRADE flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_SOUND flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_COMBAT flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_SKILLXP flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_QUESTS flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_SCRIPT flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_MARRIAGE flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_MESSAGES flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_CACHE flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_PETS flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_USER flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_LOOT flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_DUELS flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, LOG_TRIBES flag deactivated with no filter.
Thu Nov 20 18:29:28 2008, All LOGS are off.
Mounting skin: /this/art/skins/elves.zip
Mounting skin: /planeshift/art/skins/base/client_base.zip
  psEngine initialized.
Using fontsize 22 for resolution 1680x1050
WARNING! Object '_s_sigil_03' is not closed!
WARNING! Object '_s_sigil_01' is not closed!
WARNING! Object '_s_sigil_02' is not closed!
WARNING! Object '_s_stairs_01' is not closed!
WARNING! Object '_s_column_01' is not closed!
WARNING! Object 'spikes_06' is not closed!
...
  PSLoader: step 2: success
Thu Nov 20 18:29:40 2008, <src/client/pscharcontrol.cpp:879 LoadKeys SEVERE>
Thu Nov 20 18:29:40 2008, Failed to map 'F10' to 'Brightness reset'
  PSLoader: step 3: success
Thu Nov 20 18:29:41 2008, <src/common/util/psxmlparser.cpp:282 ParseFile SEVERE>
Thu Nov 20 18:29:41 2008, Could not find file: /planeshift/world/terr_common/sound.xml
Thu Nov 20 18:29:41 2008, <src/common/util/psxmlparser.cpp:282 ParseFile SEVERE>
Thu Nov 20 18:29:41 2008, Could not find file: /planeshift/world/hydlaa_jayose/sound.xml
  PSLoader: step 4: success
Map hydlaa_common loaded successfully in 98ms

crystalspace.mesh.anim.pdlight:
  Could not find light with ID '4831bf6f6f7453e7ad13cf536c263180'
  Could not find light with ID '4831bf6f6f7453e7ad13cf536c263180'
  Could not find light with ID '4831bf6f6f7453e7ad13cf536c263180'
  Could not find light with ID '4831bf6f6f7453e7ad13cf536c263180'
Map tutorial loaded successfully in 712ms
Thu Nov 20 18:29:42 2008, <src/client/psclientdr.cpp:248 HandleStatsUpdate SEVERE>
Thu Nov 20 18:29:42 2008, Stat request failed because CelClient not ready for 31486
Thu Nov 20 18:29:42 2008, <src/client/psclientdr.cpp:248 HandleStatsUpdate SEVERE>
Thu Nov 20 18:29:42 2008, Stat request failed because CelClient not ready for 31486

planeshift.application.client:
  PSLoader: step 5: success
  PSLoader: step 6: success

---

