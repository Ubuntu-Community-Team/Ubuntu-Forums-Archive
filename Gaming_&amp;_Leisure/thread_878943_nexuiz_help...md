---
title: "nexuiz help.."
date: 2008-08-03
forum: Gaming &amp; Leisure
---

### Post by zerkk on 2008-08-03
Well, I've searched far and wide for a good tutorial for Nexuiz Dedicated Server setup and use.. Well, either I'm just not looking hard enough, my computer hates me or There isn't a good tutorial to begin with.

On to the question..

Stating the obvious.. I need help with getting my server setup and running, I have followed the Readme.txt and ever link on the first two pages of google.:(

I followed the directions, Moving the *server_linux.sh* to the main directory, and moving the *server.cfg* to the data folder. when I alter the settings in the *server.cfg* and I run the server, first I get some errors

```
Nexuiz Linux 15:46:59 May 11 2008
Trying to load library... "libz.so.1" - loaded.
Added packfile data/common-spog.pk3 (26 files)
Added packfile data/data20080511.pk3 (4076 files)
Trying to load library... "libcurl.so.4" - loaded.
execing quake.rc
execing default.cfg
execing physicsQBR.cfg
execing newhook.cfg
execing weapons.cfg
execing normal.cfg
Warning: Could not expand $r_showsurfaces
Warning: Could not expand $gl_finish
Warning: Could not expand $v_kicktime
execing config.cfg
execing config_update.cfg
couldn't exec data/campaign.cfg
couldn't exec autoexec.cfg
execing server.cfg
Shader 'textures/Reaptxt/sun' already defined
Server using port 26000
LHNET_OpenSocket_Connectionless: bind returned error: Address already in use
Server failed to open socket on address 0.0.0.0:26000
LHNET_OpenSocket_Connectionless: bind returned error: Address already in use
Server failed to open socket on address 0.0.0.0:26001
LHNET_OpenSocket_Connectionless: bind returned error: Address already in use
Server failed to open socket on address 0.0.0.0:26002
LHNET_OpenSocket_Connectionless: bind returned error: Address already in use
Server failed to open socket on address 0.0.0.0:26003
LHNET_OpenSocket_Connectionless: bind returned error: Address already in use
Server failed to open socket on address 0.0.0.0:26004
LHNET_OpenSocket_Connectionless: bind returned error: Address already in use
Server failed to open socket on address 0.0.0.0:26005
LHNET_OpenSocket_Connectionless: bind returned error: Address already in use
Server failed to open socket on address 0.0.0.0:26006
LHNET_OpenSocket_Connectionless: bind returned error: Address already in use
Server failed to open socket on address 0.0.0.0:26007
LHNET_OpenSocket_Connectionless: bind returned error: Address already in use
Server failed to open socket on address 0.0.0.0:26008
LHNET_OpenSocket_Connectionless: bind returned error: Address already in use
Server failed to open socket on address 0.0.0.0:26009
LHNET_OpenSocket_Connectionless: bind returned error: Address already in use
Server failed to open socket on address 0.0.0.0:26010
LHNET_OpenSocket_Connectionless: bind returned error: Address already in use
Server failed to open socket on address 0.0.0.0:26011
LHNET_OpenSocket_Connectionless: bind returned error: Address already in use
Server failed to open socket on address 0.0.0.0:26012
LHNET_OpenSocket_Connectionless: bind returned error: Address already in use
Server failed to open socket on address 0.0.0.0:26013
Server listening on address 0.0.0.0:26014
Loaded maps/aggressor.ent
models/weapons/g_gl.md3: could not load texture "glaunch.tga"
models/weapons/g_gl.md3: could not load texture "glaunch.tga"
models/grenademodel.md3: could not load texture "grenademodelskin.tga"
models/weapons/v_gl.md3: could not load texture "glaunch.tga"
models/weapons/v_gl.md3: could not load texture "glaunch.tga"
models/weapons/w_gl.zym: could not load texture "glaunch"
models/weapons/g_rl.md3: could not load texture "textures/rl2.tga"
models/weapons/g_rl.md3: could not load texture "textures/rl.tga"
models/weapons/g_rl.md3: could not load texture "textures/rl2.tga"
models/flash.md3: could not load texture "f_shotgun.jpg"
models/rocket.md3: could not load texture "textures/rl2.tga"
models/rocket.md3: could not load texture "textures/rl2.tga"
models/rocket.md3: could not load texture "textures/rl2.tga"
models/rocket.md3: could not load texture "textures/rl2.tga"
models/weapons/v_rl.md3: could not load texture "textures/rl2.tga"
models/weapons/v_rl.md3: could not load texture "textures/rl.tga"
models/weapons/v_rl.md3: could not load texture "textures/rl2.tga"
models/weapons/w_rl.zym: could not load texture "rl2"
models/weapons/w_rl.zym: could not load texture "rl"
models/items/a_rockets.md3: could not load texture "rocketam.tga"
models/items/a_cells.md3: could not load texture "cellammoskin.tga"
models/items/a_shells.md3: could not load texture "shellsamm.tga"
models/weapons/g_uzi.md3: could not load texture "textures/uzi.tga"
models/weapons/g_uzi.md3: could not load texture "textures/uzi.tga"
models/tracer.mdl: could not load texture "models/bulcore.tga" (frame 0) for shader "models/bulcore"
models/tracer.mdl: could not load texture "models/bultrail.tga" (frame 0) for shader "models/bultrail"
models/uziflash.md3: could not load texture "textures/muzzle2"
models/uziflash.md3: could not load texture "textures/muzzle1"
models/weapons/v_uzi.md3: could not load texture "textures/uzi.tga"
models/weapons/v_uzi.md3: could not load texture "textures/uzi.tga"
models/weapons/w_uzi.zym: could not load texture "uzi"
models/items/g_a25.md3: could not load texture "saskin.tga"
models/items/g_a25.md3: could not load texture "laskin.tga"
models/items/g_h100.md3: could not load texture "lhskin.tga"
models/items/g_h100.md3: could not load texture "50hpskin"
models/weapons/g_hagar.md3: could not load texture "hagar.tga"
models/weapons/g_hagar.md3: could not load texture "hagar.tga"
models/weapons/v_hagar.md3: could not load texture "hagar.tga"
models/weapons/v_hagar.md3: could not load texture "hagar.tga"
models/weapons/w_hagar.zym: could not load texture "hagar"
models/items/g_h25.md3: could not load texture "mhskin.tga"
models/weapons/g_nex.md3: could not load texture "nexgun.tga"
models/nexflash.md3: could not load texture "nexflash.tga"
models/weapons/v_nex.md3: could not load texture "nexgun.tga"
models/weapons/w_nex.zym: could not load texture "nexgun"
models/weapons/g_electro.md3: could not load texture "electroskin.tga"
models/weapons/g_electro.md3: could not load texture "electroskin.tga"
models/ebomb.mdl: could not load texture "models/eleccore.tga" (frame 0) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/eleccore2.tga" (frame 1) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/eleccore3.tga" (frame 2) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/eleccore4.tga" (frame 3) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/eleccore5.tga" (frame 4) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/eleccore6.tga" (frame 5) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/eleccore7.tga" (frame 6) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/eleccore8.tga" (frame 7) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/elecbeam.tga" (frame 0) for shader "models/elecbeam"
models/ebomb.mdl: could not load texture "models/elecglass.tga" (frame 0) for shader "models/elecglass"
models/weapons/v_electro.md3: could not load texture "electroskin.tga"
models/weapons/v_electro.md3: could not load texture "electroskin.tga"
models/weapons/w_electro.zym: could not load texture "electroskin"
models/items/g_a1.md3: could not load texture "shard"
models/items/g_h1.md3: could not load texture "shskin.tga"
NOTE: crashed before even initializing the world, not saving persistent data
Shader 'textures/Reaptxt/sun' already defined
Loaded maps/warfare.ent
"fraglimit" changed to "30"
"timelimit" changed to "20"
models/laser.mdl: could not load texture "models/ltrail.tga" (frame 0) for shader "models/lasertrail"
models/laser.mdl: could not load texture "models/lcore.tga" (frame 0) for shader "models/lasercore"
models/weapons/v_laser.md3: could not load texture "laser.tga"
models/weapons/w_laser.zym: could not load texture "laser"
models/weapons/g_shotgun.md3: could not load texture "textures/shotgun.tga"
models/weapons/v_shotgun.md3: could not load texture "textures/shotgun.tga"
models/weapons/w_shotgun.zym: could not load texture "shotgun"
models/player/carni.zym: could not load texture "carni"
models/player/carni.zym: could not load texture "carniarmor"
models/player/crash.zym: could not load texture "quark"
models/player/grunt.zym: could not load texture "grunt"
models/player/headhunter.zym: could not load texture "headhunter"
models/player/insurrectionist.zym: could not load texture "insurrectionist"
models/player/jeandarc.zym: could not load texture "heroine"
models/player/lurk.zym: could not load texture "lurk"
models/player/lurk.zym: could not load texture "reptile"
models/player/lycanthrope.zym: could not load texture "lycanthrope"
models/player/marine.zym: could not load texture "marine"
models/player/nexus.zym: could not load texture "nexus"
models/player/nexus.zym: could not load texture "mulder"
models/player/nexus.zym: could not load texture "xolar"
models/player/nexus.zym: could not load texture "fbgreen"
models/player/nexus.zym: could not load texture "fbred"
models/player/nexus.zym: could not load texture "fborange"
models/player/nexus.zym: could not load texture "fbcolored"
models/player/pyria.zym: could not load texture "pyria"
models/player/shock.zym: could not load texture "shock"
models/player/skadi.zym: could not load texture "skadi"
models/player/specop.zym: could not load texture "specop"
models/player/visitant.zym: could not load texture "fricka"
models/gibs/bloodyskull.md3: could not load texture "bloodyskull.tga"
models/gibs/eye.md3: could not load texture "eye.tga"
models/gibs/eye.md3: could not load texture "eyeblood.tga"
models/gibs/gib1.md3: could not load texture "gib1.tga"
models/gibs/gib2.md3: could not load texture "textures/gib2.tga"
models/gibs/gib3.md3: could not load texture "textures/gib3.tga"
models/gibs/gib4.md3: could not load texture "textures/gib4.tga"
models/gibs/gib5.md3: could not load texture "flesh1.tga"
models/gibs/gib6.md3: could not load texture "flesh1.tga"
models/gibs/smallchest.md3: could not load texture "textures/meat.tga"
models/gibs/smallchest.md3: could not load texture "textures/meat.tga"
models/gibs/smallchest.md3: could not load texture "textures/meat.tga"
models/gibs/smallchest.md3: could not load texture "textures/meat.tga"
models/gibs/smallchest.md3: could not load texture "textures/meat.tga"
models/gibs/chest.md3: could not load texture "textures/meat.tga"
models/gibs/chest.md3: could not load texture "textures/meat.tga"
models/gibs/chest.md3: could not load texture "textures/meat.tga"
models/gibs/arm.md3: could not load texture "textures/meat.tga"
models/gibs/arm.md3: could not load texture "textures/meat.tga"
models/gibs/arm.md3: could not load texture "textures/meat.tga"
models/gibs/leg1.md3: could not load texture "textures/meat.tga"
models/gibs/leg2.md3: could not load texture "textures/meat.tga"
models/gibs/leg2.md3: could not load texture "textures/meat.tga"
models/hook.md3: could not load texture "textures/hook"
models/weapons/g_crylink.md3: could not load texture "crylink.tga"
models/plasmatrail.mdl: could not load texture "models/pcore.tga" (frame 0) for shader "models/plascore"
models/plasmatrail.mdl: could not load texture "models/ptrail.tga" (frame 0) for shader "models/plastrail"
models/weapons/v_crylink.md3: could not load texture "crylink.tga"
models/weapons/w_crylink.zym: could not load texture "crylink"

```

When I start up nexuiz, I cannot find the server... what am I doing wrong?

---

### Post by zerkk on 2008-08-03
Please?

---

### Post by vandorjw on 2008-08-03
Can I take a look at the tutorial you were following?

When I host a game, all I do is

start Nexuiz, go to Multipler, and select "create"
Configure to game to how you like it...

Then hit start.

---

### Post by zerkk on 2008-08-03
I'm trying to make a dedicated server, Sorry I should have mentioned that above :(

---

