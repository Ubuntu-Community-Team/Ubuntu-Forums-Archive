---
title: "Spring not working."
date: 2010-01-09
forum: Gaming &amp; Leisure
---

### Post by bobmatino17 on 2010-01-09
i reacently installed the Lobby and Engine for Spring, then downloaded Kernal Panic for it. It says the game crashed. I then downloaded 1944 to see if that worked and it crashed.

these are the contents of infolog.txt

```

```

yes, that is blank.

any suggestions???

---

### Post by bobmatino17 on 2010-01-09
```
LogOutput initialized.
Spring 0.80.5.0
Available log subsystems: mapinfo, CollisionVolume, unit, VFS-detail, VFS, ArchiveScanner, Sound
Enabled log subsystems: Sound
Enable or disable log subsystems using the LogSubsystems configuration key
  or the SPRING_LOG_SUBSYSTEMS environment variable (both comma separated).
using configuration source "/home/link/.springrc"
[CMyMath::Init] CPU SSE mask: 124, flags:
	SSE 1.0:  1,  SSE 2.0:  1
	SSE 3.0:  1, SSSE 3.0:  1
	SSE 4.1:  0,  SSE 4.2:  0
	SSE 4.0A: 0,  SSE 5.0A: 0
	using streflop SSE FP-math mode, CPU supports SSE instructions
OS: Linux
OS: 32bit native mode
Using read-only  data directory: /usr/games/
Using read-write data directory: /home/link/.spring/
Using read-only  data directory: /usr/share/games/spring/
Scanning: /usr/share/games/spring/maps
Scanning: /usr/share/games/spring/base
Scanning: /usr/share/games/spring/mods
Scanning: /usr/share/games/spring/packages
Scanning: /home/link/.spring/maps
Scanning: /home/link/.spring/base
Scanning: /home/link/.spring/mods
Scanning: /home/link/.spring/packages
Scanning: /usr/games/maps
Scanning: /usr/games/base
Scanning: /usr/games/mods
Scanning: /usr/games/packages
Video mode set to  1024 x 768 / 32 bit
SpringApp::InitWindow(): 3928259400 ms
[      0] SDL:  1.2.13
[      0] GL:   2.1.2 NVIDIA 185.18.36
[      0] GL:   NVIDIA Corporation
[      0] GL:   GeForce 6200 LE/PCI/SSE2
[      0] GLEW: 1.5.1
[      0] Joysticks found: 0
[      0] Joystick 0 not found
[      0] Connecting to local server
[      0] Sound: OpenAL info:
[      0] Sound:   Vendor:     OpenAL Community
[      0] Sound:   Version:    1.1 ALSOFT 1.8.466
[      0] Sound:   Renderer:   OpenAL Soft
[      0] Sound:   AL Extensions: AL_EXTX_buffer_sub_data AL_EXT_EXPONENT_DISTANCE AL_EXT_FLOAT32 AL_EXT_IMA4 AL_EXT_LINEAR_DISTANCE AL_EXT_MCFORMATS AL_EXT_OFFSET AL_EXTX_source_distance_model AL_LOKI_quadriphonic
[      0] Sound:   ALC Extensions: ALC_ENUMERATE_ALL_EXT ALC_ENUMERATION_EXT ALC_EXT_CAPTURE ALC_EXT_EFX
[      0] Sound:   Device:     ALSA Software
[      0] Sound:   Available Devices:  
[      0] Sound:                       ALSA Software
[      0] Sound:                       OSS Software
[      0] Sound:                       PortAudio Software
[      0] Sound:                       PulseAudio Software
[      0] Sound:                       Wave File Writer
[      0] Starting GameServer: 501 ms
[      0] Starting demo recording
[      0] Using map Data Cache L1.smf
[      0] Recording demo demos/local_20100109_203134_Data Cache L1_0.80.5.sdf
[      0] Using script Commanders
[      0] Using mod Kernel Panic 3.6
[      0] Using mod archive Kernel_Panic_3.6.sd7
[      0] Loading client data: 9 ms
[      0] User number 0 (team 0, allyteam 0)
[      0] Loading console: 0 ms
[      0] Sound:  parsed 4 sounds from gamedata/sounds.lua
[      0] Loading sounds: 17 ms
[      0] Sound: WAV file sounds/button9.wav has data length 291939 greater than actual data length 16388
[      0] Camera and mouse: 164 ms
[      0] Parsing unit icons
[      0] Parsing definitions
[      0] removing homebaseshieldgood from Security Hole
[      0] removing homebaseshieldbad from Security Hole
[      0] removing minifacshieldgood from Window
[      0] removing minifacshieldbad from Window
[      0] removing minifacshieldgood from Small Circle
[      0] removing minifacshieldbad from Small Circle
[      0] removing homebaseshieldgood from Carrier
[      0] removing homebaseshieldbad from Carrier
[      0] removing minifacshieldgood from socket
[      0] removing minifacshieldbad from socket
[      0] removing minifacshieldgood from Window
[      0] removing minifacshieldbad from Window
[      0] removing minifacshieldgood from Port
[      0] removing minifacshieldbad from Port
[      0] removing homebaseshieldgood from Magical Circle
[      0] removing homebaseshieldbad from Magical Circle
[      0] removing homebaseshieldgood from Security Hole
[      0] removing homebaseshieldbad from Security Hole
[      0] removing minifacshieldgood from obelisk
[      0] removing minifacshieldbad from obelisk
[      0] removing homebaseshieldgood from kernel
[      0] removing homebaseshieldbad from kernel
[      0] removing minifacshieldgood from Firewall
[      0] removing minifacshieldbad from Firewall
[      0] removing minifacshieldgood from terminal
[      0] removing minifacshieldbad from terminal
[      0] Loading all definitions:  0.146000
[      0] Loading defs: 153 ms
[      0] You are missing the "ARB_shadow_ambient" extension (this will probably make shadows darker than they should be)
[      0] Loading map informations
[      0] Opening map file
[      0] Loading Map
[      0] Loading detail textures
[      0] Creating overhead texture
[      0] Creating ground shading
[      0] Loading .smt tile-file "maps/Data Cache L1.smt" (0/1, 41 tiles)
[      0] Reading tiles
[      0] Reading tile map
[      0] Creating projectile texture
[      0] Number of damage types: 10
[      0] Loading weapon definitions
[      0] Could not load sound from def: Explosion5
[      0] Could not load sound from def: Explosion5
[      0] Could not load sound from def: Explosion5
[      0] Loading unit definitions
[      0] Loading feature definitions
[      0] Generating trees
[      0] Creating unit textures
[      0] Initializing map features
[      0] Unknown map feature type 
[      0] Reading estimate path costs
[      0] Error opening maps/paths/Data Cache L1.3612088074.pe.zip
[      0] Analyzing map accessibility [8]
[      0] Block offset: 0 of 3072 (size 8)
[      0] Block offset: 1000 of 3072 (size 8)
[      0] Block offset: 2000 of 3072 (size 8)
[      0] Path cost: 0 of 3072 (size 8)
[      0] Path cost: 1000 of 3072 (size 8)
[      0] Path cost: 2000 of 3072 (size 8)
[      0] Writing path data file...
[      0] Reading estimate path costs
[      0] Error opening maps/paths/Data Cache L1.3612088098.pe2.zip
[      0] Analyzing map accessibility [32]
[      0] Block offset: 0 of 192 (size 32)
[      0] Path cost: 0 of 192 (size 32)
[      0] Writing path data file...
[      0] Pathing data checksum: 8a9e83c7
[      0] Creating sky
[      0] Loading LuaRules
[      0] gf1 = LuaRules/Gadgets/airstrike.lua
[      0] gf1 = LuaRules/Gadgets/areadenial.lua
[      0] gf1 = LuaRules/Gadgets/autohold.lua
[      0] gf1 = LuaRules/Gadgets/bug_bombard.lua
[      0] gf1 = LuaRules/Gadgets/burrow.lua
[      0] gf1 = LuaRules/Gadgets/colorwars.lua
[      0] gf1 = LuaRules/Gadgets/evilless.lua
[      0] gf1 = LuaRules/Gadgets/infection.lua
[      0] gf1 = LuaRules/Gadgets/kernelboost.lua
[      0] gf1 = LuaRules/Gadgets/kpai.lua
[      0] gf1 = LuaRules/Gadgets/kpai_fair.lua
[      0] gf1 = LuaRules/Gadgets/kpunittypes.lua
[      0] gf1 = LuaRules/Gadgets/launcher.lua
[      0] gf1 = LuaRules/Gadgets/luacob.lua
[      0] gf1 = LuaRules/Gadgets/luaui_force.lua
[      0] gf1 = LuaRules/Gadgets/metaltogeo.lua
[      0] gf1 = LuaRules/Gadgets/network_arceffect.lua
[      0] gf1 = LuaRules/Gadgets/network_buffer.lua
[      0] gf1 = LuaRules/Gadgets/network_build.lua
[      0] gf1 = LuaRules/Gadgets/network_dispatch.lua
[      0] gf1 = LuaRules/Gadgets/network_enter.lua
[      0] gf1 = LuaRules/Gadgets/network_flowspeed.lua
[      0] gf1 = LuaRules/Gadgets/network_reflectorshield.lua
[      0] gf1 = LuaRules/Gadgets/new_cmd_id.lua
[      0] gf1 = LuaRules/Gadgets/ons.lua
[      0] gf1 = LuaRules/Gadgets/pseudo_orders.lua
[      0] gf1 = LuaRules/Gadgets/regenai.lua
[      0] gf1 = LuaRules/Gadgets/screensaver.lua
[      0] gf1 = LuaRules/Gadgets/set_alpha_threshold.lua
[      0] gf1 = LuaRules/Gadgets/sos.lua
[      0] gf1 = LuaRules/Gadgets/spawn_units.lua
[      0] gf1 = LuaRules/Gadgets/specialattack.lua
[      0] gf1 = LuaRules/Gadgets/touhou_build.lua
[      0] gf2 = LuaRules/Gadgets/airstrike.lua
[      0] gf2 = LuaRules/Gadgets/areadenial.lua
[      0] gf2 = LuaRules/Gadgets/autohold.lua
[      0] gf2 = LuaRules/Gadgets/bug_bombard.lua
[      0] gf2 = LuaRules/Gadgets/burrow.lua
[      0] gf2 = LuaRules/Gadgets/colorwars.lua
[      0] gf2 = LuaRules/Gadgets/evilless.lua
[      0] gf2 = LuaRules/Gadgets/infection.lua
[      0] gf2 = LuaRules/Gadgets/kernelboost.lua
[      0] gf2 = LuaRules/Gadgets/kpai.lua
[      0] gf2 = LuaRules/Gadgets/kpai_fair.lua
[      0] gf2 = LuaRules/Gadgets/kpunittypes.lua
[      0] gf2 = LuaRules/Gadgets/launcher.lua
[      0] gf2 = LuaRules/Gadgets/luacob.lua
[      0] gf2 = LuaRules/Gadgets/luaui_force.lua
[      0] gf2 = LuaRules/Gadgets/metaltogeo.lua
[      0] gf2 = LuaRules/Gadgets/network_arceffect.lua
[      0] gf2 = LuaRules/Gadgets/network_buffer.lua
[      0] gf2 = LuaRules/Gadgets/network_build.lua
[      0] gf2 = LuaRules/Gadgets/network_dispatch.lua
[      0] gf2 = LuaRules/Gadgets/network_enter.lua
[      0] gf2 = LuaRules/Gadgets/network_flowspeed.lua
[      0] gf2 = LuaRules/Gadgets/network_reflectorshield.lua
[      0] gf2 = LuaRules/Gadgets/new_cmd_id.lua
[      0] gf2 = LuaRules/Gadgets/ons.lua
[      0] gf2 = LuaRules/Gadgets/pseudo_orders.lua
[      0] gf2 = LuaRules/Gadgets/regenai.lua
[      0] gf2 = LuaRules/Gadgets/screensaver.lua
[      0] gf2 = LuaRules/Gadgets/set_alpha_threshold.lua
[      0] gf2 = LuaRules/Gadgets/sos.lua
[      0] gf2 = LuaRules/Gadgets/spawn_units.lua
[      0] gf2 = LuaRules/Gadgets/specialattack.lua
[      0] gf2 = LuaRules/Gadgets/touhou_build.lua
[      0] Loaded gadget:  Color Wars!         <colorwars.lua>
[      0] Loaded gadget:  Force LUA UI        <luaui_force.lua>
[      0] Loaded gadget:  Kernel Panic S.O.S.  <sos.lua>
[      0] Loaded gadget:  Screensaver         <screensaver.lua>
[      0] Loaded gadget:  Spawn Units         <spawn_units.lua>
[      0] Loaded gadget:  kpunittypes.lua     <kpunittypes.lua>
[      0] Loaded gadget:  new_cmd_id.lua      <new_cmd_id.lua>
[      0] Loaded gadget:  Touhou Build        <touhou_build.lua>
[      0] Loaded gadget:  Metal To Geo converter  <metaltogeo.lua>
[      0] Loaded gadget:  set Alpha Threshold  <set_alpha_threshold.lua>
[      0] Loaded gadget:  Pseudo Orders       <pseudo_orders.lua>
[      0] Loaded gadget:  Burrow              <burrow.lua>
[      0] Loaded gadget:  UnitAutoHold        <autohold.lua>
[      0] Loaded gadget:  Airstrike           <airstrike.lua>
[      0] Loaded gadget:  Area Denial         <areadenial.lua>
[      0] Loaded gadget:  Bombard             <bug_bombard.lua>
[      0] Loaded gadget:  Infection           <infection.lua>
[      0] Loaded gadget:  Kernel boost        <kernelboost.lua>
[      0] Loaded gadget:  LuaCOB              <luacob.lua>
[      0] Loaded gadget:  Network Arc Effect  <network_arceffect.lua>
[      0] Loaded gadget:  Network Buffer      <network_buffer.lua>
[      0] Loaded gadget:  Network Build       <network_build.lua>
[      0] Loaded gadget:  Special Attack      <specialattack.lua>
[      0] Loaded gadget:  Launcher            <launcher.lua>
[      0] Loaded gadget:  Network Dispatch    <network_dispatch.lua>
[      0] Loaded gadget:  Network Enter       <network_enter.lua>
[      0] Loaded gadget:  Flow Speed          <network_flowspeed.lua>
[      0] Loaded gadget:  Network Reflectorshield  <network_reflectorshield.lua>
[      0] Loaded gadget:  Kernel Panic O.N.S.  <ons.lua>
[      0] Loaded gadget:  Kernel Panic AI     <kpai.lua>
[      0] Loaded gadget:  Fair KPAI           <kpai_fair.lua>
[      0] Loaded gadget:  Regenerative AI     <regenai.lua>
[      0] Loaded gadget:  Evilless            <evilless.lua>
[      0] gf1 = LuaRules/Gadgets/airstrike.lua
[      0] gf1 = LuaRules/Gadgets/areadenial.lua
[      0] gf1 = LuaRules/Gadgets/autohold.lua
[      0] gf1 = LuaRules/Gadgets/bug_bombard.lua
[      0] gf1 = LuaRules/Gadgets/burrow.lua
[      0] gf1 = LuaRules/Gadgets/colorwars.lua
[      0] gf1 = LuaRules/Gadgets/evilless.lua
[      0] gf1 = LuaRules/Gadgets/infection.lua
[      0] gf1 = LuaRules/Gadgets/kernelboost.lua
[      0] gf1 = LuaRules/Gadgets/kpai.lua
[      0] gf1 = LuaRules/Gadgets/kpai_fair.lua
[      0] gf1 = LuaRules/Gadgets/kpunittypes.lua
[      0] gf1 = LuaRules/Gadgets/launcher.lua
[      0] gf1 = LuaRules/Gadgets/luacob.lua
[      0] gf1 = LuaRules/Gadgets/luaui_force.lua
[      0] gf1 = LuaRules/Gadgets/metaltogeo.lua
[      0] gf1 = LuaRules/Gadgets/network_arceffect.lua
[      0] gf1 = LuaRules/Gadgets/network_buffer.lua
[      0] gf1 = LuaRules/Gadgets/network_build.lua
[      0] gf1 = LuaRules/Gadgets/network_dispatch.lua
[      0] gf1 = LuaRules/Gadgets/network_enter.lua
[      0] gf1 = LuaRules/Gadgets/network_flowspeed.lua
[      0] gf1 = LuaRules/Gadgets/network_reflectorshield.lua
[      0] gf1 = LuaRules/Gadgets/new_cmd_id.lua
[      0] gf1 = LuaRules/Gadgets/ons.lua
[      0] gf1 = LuaRules/Gadgets/pseudo_orders.lua
[      0] gf1 = LuaRules/Gadgets/regenai.lua
[      0] gf1 = LuaRules/Gadgets/screensaver.lua
[      0] gf1 = LuaRules/Gadgets/set_alpha_threshold.lua
[      0] gf1 = LuaRules/Gadgets/sos.lua
[      0] gf1 = LuaRules/Gadgets/spawn_units.lua
[      0] gf1 = LuaRules/Gadgets/specialattack.lua
[      0] gf1 = LuaRules/Gadgets/touhou_build.lua
[      0] gf2 = LuaRules/Gadgets/airstrike.lua
[      0] gf2 = LuaRules/Gadgets/areadenial.lua
[      0] gf2 = LuaRules/Gadgets/autohold.lua
[      0] gf2 = LuaRules/Gadgets/bug_bombard.lua
[      0] gf2 = LuaRules/Gadgets/burrow.lua
[      0] gf2 = LuaRules/Gadgets/colorwars.lua
[      0] gf2 = LuaRules/Gadgets/evilless.lua
[      0] gf2 = LuaRules/Gadgets/infection.lua
[      0] gf2 = LuaRules/Gadgets/kernelboost.lua
[      0] gf2 = LuaRules/Gadgets/kpai.lua
[      0] gf2 = LuaRules/Gadgets/kpai_fair.lua
[      0] gf2 = LuaRules/Gadgets/kpunittypes.lua
[      0] gf2 = LuaRules/Gadgets/launcher.lua
[      0] gf2 = LuaRules/Gadgets/luacob.lua
[      0] gf2 = LuaRules/Gadgets/luaui_force.lua
[      0] gf2 = LuaRules/Gadgets/metaltogeo.lua
[      0] gf2 = LuaRules/Gadgets/network_arceffect.lua
[      0] gf2 = LuaRules/Gadgets/network_buffer.lua
[      0] gf2 = LuaRules/Gadgets/network_build.lua
[      0] gf2 = LuaRules/Gadgets/network_dispatch.lua
[      0] gf2 = LuaRules/Gadgets/network_enter.lua
[      0] gf2 = LuaRules/Gadgets/network_flowspeed.lua
[      0] gf2 = LuaRules/Gadgets/network_reflectorshield.lua
[      0] gf2 = LuaRules/Gadgets/new_cmd_id.lua
[      0] gf2 = LuaRules/Gadgets/ons.lua
[      0] gf2 = LuaRules/Gadgets/pseudo_orders.lua
[      0] gf2 = LuaRules/Gadgets/regenai.lua
[      0] gf2 = LuaRules/Gadgets/screensaver.lua
[      0] gf2 = LuaRules/Gadgets/set_alpha_threshold.lua
[      0] gf2 = LuaRules/Gadgets/sos.lua
[      0] gf2 = LuaRules/Gadgets/spawn_units.lua
[      0] gf2 = LuaRules/Gadgets/specialattack.lua
[      0] gf2 = LuaRules/Gadgets/touhou_build.lua
[      0] Loaded gadget:  Color Wars!         <colorwars.lua>
[      0] Loaded gadget:  Force LUA UI        <luaui_force.lua>
[      0] Loaded gadget:  Kernel Panic S.O.S.  <sos.lua>
[      0] Loaded gadget:  Screensaver         <screensaver.lua>
[      0] Loaded gadget:  Spawn Units         <spawn_units.lua>
[      0] Loaded gadget:  kpunittypes.lua     <kpunittypes.lua>
[      0] Loaded gadget:  new_cmd_id.lua      <new_cmd_id.lua>
[      0] Loaded gadget:  Touhou Build        <touhou_build.lua>
[      0] Loaded gadget:  set Alpha Threshold  <set_alpha_threshold.lua>
[      0] Loaded gadget:  Pseudo Orders       <pseudo_orders.lua>
[      0] Loaded gadget:  Burrow              <burrow.lua>
[      0] Loaded gadget:  UnitAutoHold        <autohold.lua>
[      0] Loaded gadget:  Airstrike           <airstrike.lua>
[      0] Loaded gadget:  Area Denial         <areadenial.lua>
[      0] Loaded gadget:  Bombard             <bug_bombard.lua>
[      0] Loaded gadget:  Infection           <infection.lua>
[      0] Loaded gadget:  LuaCOB              <luacob.lua>
[      0] Loaded gadget:  Network Arc Effect  <network_arceffect.lua>
[      0] Loaded gadget:  Network Buffer      <network_buffer.lua>
[      0] Loaded gadget:  Network Build       <network_build.lua>
[      0] Loaded gadget:  Special Attack      <specialattack.lua>
[      0] Loaded gadget:  Launcher            <launcher.lua>
[      0] Loaded gadget:  Network Dispatch    <network_dispatch.lua>
[      0] Loaded gadget:  Network Enter       <network_enter.lua>
[      0] Loaded gadget:  Network Reflectorshield  <network_reflectorshield.lua>
[      0] Loaded gadget:  Kernel Panic O.N.S.  <ons.lua>
[      0] Loaded gadget:  Kernel Panic AI     <kpai.lua>
[      0] Loaded gadget:  Fair KPAI           <kpai_fair.lua>
[      0] Loaded gadget:  Regenerative AI     <regenai.lua>
[      0] Loaded gadget:  Evilless            <evilless.lua>
[      0] Loading LuaGaia
[      0] Loading LuaUI
[      0] Using LUAUI_DIRNAME = LuaUI/
[      0] Reloaded ctrlpanel with: LuaUI/ctrlpanel.txt
[      0] LuaUI: bound F11 to the widget selector
[      0] LuaUI: bound CTRL+F11 to tweak mode
[      0] Loaded widget from mod:   Dump Units          <dump_units.lua>
[      0] Loaded widget from mod:   Keep Morpheds Selected  <kp_keep_morphed_selected.lua>
[      0] Loaded widget from mod:   Kernel Panic Build Bar  <kp_buildbar.lua>
[      0] Loaded widget from mod:   Kernel Panic Console Commands  <kp_cnslcmd.lua>
[      0] Loaded widget from mod:   Kernel Panic Hotkeys  <kp_hotkeys.lua>
[      0] Loaded widget from mod:   Kernel Panic MidKnight's tooltip background  <kp_midknight_bg.lua>
[      0] Loaded widget from mod:   Kernel Panic autospam  <kp_autospam.lua>
[      0] Loaded widget from mod:   Kernel Panic Default Commands  <kp_defaultcommands.lua>
[      0] movewarnings disabled
[      0] Loaded widget from mod:   noResBar NoMoveWarnings  <noresbar.lua>
[      0] Loaded widget from mod:   Kernel Panic Geos Highlight  <kp_geoshighlight.lua>
[      0] movewarnings disabled
[      0] Enable some widgets
[      0] Loading:  LuaUI/Widgets/noresbar.lua
[      0] movewarnings disabled
[      0] Loading:  LuaUI/Widgets/kp_hotkeys.lua
[      0] Removed:  LuaUI/Widgets/kp_settings.lua
[      0] Spring settings changed to fit K.P. taking effect next game
[      0] Loaded widget from mod:   Set Spring-wide settings and Lua WhiteList  <kp_settings.lua>
[      0] Loaded widget from mod:   Kernel Panic Automatic Tip Dispenser  <kp_automatic_tip_dispenser.lua>
[      0] Reloaded ctrlpanel with: LuaUI/Widgets/KP_CtrlPanel.txt
[      0] Loaded widget from mod:   Kernel Panic Tooltip  <kp_tooltip.lua>
[      0] Loaded widget from mod:   Kernel Panic O.N.S. help tips  <kp_onshelp.lua>
[      0] Loaded widget from mod:   Spring Direct Launch 2  <kp_spring_direct_launch.lua>
[      0] LuaUI v0.3
[      0] Finalizing...
[      0] Spring 0.80.5.0
[      0] Build date/time: Oct 26 2009 06:55:41
[      0] Player added point: Start 0
[      0]  -> connection established (given id 0)
[      0] Player Player finished loading and is now ingame
[      0] Switching to Overhead (TA) style camera
[      0] GameID: ff2d494b7f46f1f004bacb6bc51a3332
[      0] Player added point: Start 0
[     76] Game has ended
[    132] Switching to Total War style camera
[    709] Path cache hits 0 0%
[    709] Path cache hits 0 0%
[    709] Statistics for local connection:
Received: 1662 bytes
Sent: 6867 
```

well i tried saving the blank infolog.txt file, and it worked, this is what i got.

---

