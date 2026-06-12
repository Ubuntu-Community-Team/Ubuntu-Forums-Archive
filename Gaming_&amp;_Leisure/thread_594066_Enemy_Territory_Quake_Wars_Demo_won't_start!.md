---
title: "Enemy Territory Quake Wars Demo won't start!"
date: 2007-10-27
forum: Gaming &amp; Leisure
---

### Post by quadomatic on 2007-10-27
I can't start the demo for some reason. After it's installed, and I got to the folder and run ./etqw in the terminal, I get this:

```

aneesh@aneesh-desktop:~/ETQW$ ./etqw
ETQW 1.0.11144.11144  linux-x86 Oct 15 2007 10:32:37
found interface lo - loopback
found interface eth0 - 192.168.1.88/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2
ETQW using generic code for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Loaded pk4 /home/aneesh/ETQW/base/game000.pk4 with checksum 0xe9a0d58a
Loaded pk4 /home/aneesh/ETQW/base/game002.pk4 with checksum 0x77a60ea7
Loaded pk4 /home/aneesh/ETQW/base/pak000.pk4 with checksum 0xb48bb812
Loaded pk4 /home/aneesh/ETQW/base/pak001.pk4 with checksum 0xde1cb42c
Loaded pk4 /home/aneesh/ETQW/base/zpak_english000.pk4 with checksum 0x575930bc
Current search path:
/home/aneesh/.etqw/base
/home/aneesh/ETQW/base
/home/aneesh/ETQW/base/zpak_english000.pk4 (670 files)
/home/aneesh/ETQW/base/pak001.pk4 (1775 files)
/home/aneesh/ETQW/base/pak000.pk4 (6062 files)
/home/aneesh/ETQW/base/game002.pk4 (3 files)
/home/aneesh/ETQW/base/game000.pk4 (3 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------

Running in restricted mode.

----- Initializing Decls -----
Decompressing the global token cache...2849Kb
...loading binary 'generated/declb/templates/effects.templateb'
...loading binary 'generated/declb/templates/imposters.templateb'
...loading binary 'generated/declb/templates/vehicles.templateb'
...loading binary 'generated/declb/templates/water.templateb'
...loading binary 'generated/declb/templates/wind.templateb'
...loading binary 'generated/declb/materials/blendlights.mtrb'
...loading binary 'generated/declb/materials/botclip.mtrb'
...loading binary 'generated/declb/materials/boxcover.mtrb'
...loading binary 'generated/declb/materials/cargo.mtrb'
...loading binary 'generated/declb/materials/characters.mtrb'
...loading binary 'generated/declb/materials/cockpits.mtrb'
...loading binary 'generated/declb/materials/collision.mtrb'
...loading binary 'generated/declb/materials/commandmaps.mtrb'
...loading binary 'generated/declb/materials/concrete.mtrb'
...loading binary 'generated/declb/materials/concrete_new.mtrb'
...loading binary 'generated/declb/materials/decals.mtrb'
...loading binary 'generated/declb/materials/decals_new.mtrb'
...loading binary 'generated/declb/materials/draska.mtrb'
...loading binary 'generated/declb/materials/dummy.mtrb'
...loading binary 'generated/declb/materials/editor.mtrb'
...loading binary 'generated/declb/materials/engine.mtrb'
...loading binary 'generated/declb/materials/fogs.mtrb'
...loading binary 'generated/declb/materials/frankies.mtrb'
...loading binary 'generated/declb/materials/generic.mtrb'
...loading binary 'generated/declb/materials/gfx.mtrb'
...loading binary 'generated/declb/materials/glass.mtrb'
...loading binary 'generated/declb/materials/guis_assets.mtrb'
...loading binary 'generated/declb/materials/id_andy.mtrb'
...loading binary 'generated/declb/materials/id_base_trim.mtrb'
...loading binary 'generated/declb/materials/id_kentest.mtrb'
...loading binary 'generated/declb/materials/id_lights.mtrb'
...loading binary 'generated/declb/materials/id_seneca.mtrb'
...loading binary 'generated/declb/materials/id_vp_materials.mtrb'
...loading binary 'generated/declb/materials/id_weapons.mtrb'
...loading binary 'generated/declb/materials/id_zgraeme.mtrb'
...loading binary 'generated/declb/materials/imposters.mtrb'
...loading binary 'generated/declb/materials/invisible.mtrb'
...loading binary 'generated/declb/materials/items.mtrb'
...loading binary 'generated/declb/materials/karateka_temp.mtrb'
...loading binary 'generated/declb/materials/levelshots.mtrb'
...loading binary 'generated/declb/materials/lights.mtrb'
...loading binary 'generated/declb/materials/mapobjects.mtrb'
...loading binary 'generated/declb/materials/massive.mtrb'
...loading binary 'generated/declb/materials/megatextures.mtrb'
...loading binary 'generated/declb/materials/metal.mtrb'
...loading binary 'generated/declb/materials/metal_new.mtrb'
...loading binary 'generated/declb/materials/metal_trim.mtrb'
...loading binary 'generated/declb/materials/particles.mtrb'
...loading binary 'generated/declb/materials/particles_penta.mtrb'
...loading binary 'generated/declb/materials/particles_peppi.mtrb'
...loading binary 'generated/declb/materials/penta.mtrb'
...loading binary 'generated/declb/materials/pipes.mtrb'
...loading binary 'generated/declb/materials/postprocess.mtrb'
...loading binary 'generated/declb/materials/sd_decals.mtrb'
...loading binary 'generated/declb/materials/sd_guis.mtrb'
...loading binary 'generated/declb/materials/sd_sfx.mtrb'
...loading binary 'generated/declb/materials/sdpatd.mtrb'
...loading binary 'generated/declb/materials/sewer.mtrb'
...loading binary 'generated/declb/materials/sfx.mtrb'
...loading binary 'generated/declb/materials/sfx_multiplayer.mtrb'
...loading binary 'generated/declb/materials/shaderdemo.mtrb'
...loading binary 'generated/declb/materials/strogg.mtrb'
...loading binary 'generated/declb/materials/strogg_base.mtrb'
...loading binary 'generated/declb/materials/structures.mtrb'
...loading binary 'generated/declb/materials/stuff.mtrb'
...loading binary 'generated/declb/materials/tables.mtrb'
...loading binary 'generated/declb/materials/techkits.mtrb'
...loading binary 'generated/declb/materials/tools.mtrb'
...loading binary 'generated/declb/materials/water.mtrb'
...loading binary 'generated/declb/materials/weapons.mtrb'
...loading binary 'generated/declb/materials/window.mtrb'
...loading binary 'generated/declb/materials/atmospheres/atmosphere.mtrb'
...loading binary 'generated/declb/materials/atmospheres/lights.mtrb'
...loading binary 'generated/declb/materials/atmospheres/skydomes.mtrb'
...loading binary 'generated/declb/materials/atmospheres/skydomes_old.mtrb'
...loading binary 'generated/declb/materials/atmospheres/skydomes_templates.mtrb'
...loading binary 'generated/declb/materials/edf/hud/hud.mtrb'
...loading binary 'generated/declb/materials/edf/players/edf_player.mtrb'
...loading binary 'generated/declb/materials/edf/structures/cc.mtrb'
...loading binary 'generated/declb/materials/guis/commandmap.mtrb'
...loading binary 'generated/declb/materials/guis/crosshairs.mtrb'
...loading binary 'generated/declb/materials/guis/cursors.mtrb'
...loading binary 'generated/declb/materials/guis/deploy_icons.mtrb'
...loading binary 'generated/declb/materials/guis/endscreen.mtrb'
...loading binary 'generated/declb/materials/guis/firesupport.mtrb'
...loading binary 'generated/declb/materials/guis/hud.mtrb'
...loading binary 'generated/declb/materials/guis/icons.mtrb'
...loading binary 'generated/declb/materials/guis/logos.mtrb'
...loading binary 'generated/declb/materials/guis/main_menu.mtrb'
...loading binary 'generated/declb/materials/guis/mission_icons.mtrb'
...loading binary 'generated/declb/materials/guis/models.mtrb'
...loading binary 'generated/declb/materials/guis/targeting.mtrb'
...loading binary 'generated/declb/materials/guis/vehicles.mtrb'
...loading binary 'generated/declb/materials/guis/weapon_icons.mtrb'
...loading binary 'generated/declb/materials/guis/hud/gdf.mtrb'
...loading binary 'generated/declb/materials/guis/hud/strogg.mtrb'
...loading binary 'generated/declb/materials/mapobjects/automobiles.mtrb'
...loading binary 'generated/declb/materials/mapobjects/billboard_roadsign.mtrb'
...loading binary 'generated/declb/materials/mapobjects/cmarker.mtrb'
...loading binary 'generated/declb/materials/mapobjects/office.mtrb'
...loading binary 'generated/declb/materials/mapobjects/tanks.mtrb'
...loading binary 'generated/declb/materials/mapobjects/valley.mtrb'
...loading binary 'generated/declb/materials/particles/violator.mtrb'
...loading binary 'generated/declb/materials/particles/weapons.mtrb'
...loading binary 'generated/declb/materials/particles/debris/debris.mtrb'
...loading binary 'generated/declb/materials/particles/explosion/gen_explosion.mtrb'
...loading binary 'generated/declb/materials/particles/explosion/plasmamortar.mtrb'
...loading binary 'generated/declb/materials/particles/flash/muzzleflash.mtrb'
...loading binary 'generated/declb/materials/particles/flash/tracer.mtrb'
...loading binary 'generated/declb/materials/particles/projectiles/missiles.mtrb'
...loading binary 'generated/declb/materials/particles/projectiles/plasmamortar.mtrb'
...loading binary 'generated/declb/materials/particles/projectiles/ssm.mtrb'
...loading binary 'generated/declb/materials/particles/smoke/smoke.mtrb'
...loading binary 'generated/declb/materials/particles/water/splash.mtrb'
...loading binary 'generated/declb/materials/raven/raven.mtrb'
...loading binary 'generated/declb/materials/textures2/henning.mtrb'
...loading binary 'generated/declb/materials/texturesheets/valley.mtrb'
...loading binary 'generated/declb/materials/vegetation/trees/ash_test.mtrb'
...loading binary 'generated/declb/materials/vegetation/trees/pine_test.mtrb'
...loading binary 'generated/declb/materials/vehicles/lights.mtrb'
...loading binary 'generated/declb/materials/vehicles/vehicles_gdf.mtrb'
...loading binary 'generated/declb/materials/vehicles/vehicles_strogg.mtrb'
...loading binary 'generated/declb/materials/weapons/grenades.mtrb'
...loading binary 'generated/declb/materials/weapons/items_gdf.mtrb'
...loading binary 'generated/declb/materials/weapons/shells.mtrb'
...loading binary 'generated/declb/materials/weapons/weapons_gdf.mtrb'
...loading binary 'generated/declb/materials/weapons/weapons_strogg.mtrb'
...loading binary 'generated/declb/skins/deployables.skinb'
...loading binary 'generated/declb/skins/skins_characters_player.skinb'
...loading binary 'generated/declb/skins/vehicles/gdf/anansi.skinb'
...loading binary 'generated/declb/skins/vehicles/gdf/badger.skinb'
...loading binary 'generated/declb/skins/vehicles/gdf/bumblebee.skinb'
...loading binary 'generated/declb/skins/vehicles/gdf/husky.skinb'
...loading binary 'generated/declb/skins/vehicles/gdf/magog.skinb'
...loading binary 'generated/declb/skins/vehicles/gdf/mcp.skinb'
...loading binary 'generated/declb/skins/vehicles/gdf/titan.skinb'
...loading binary 'generated/declb/skins/vehicles/gdf/trojan.skinb'
...loading binary 'generated/declb/sounds/ambience.sndshdb'
...loading binary 'generated/declb/sounds/ambient_events.sndshdb'
...loading binary 'generated/declb/sounds/amt_gdf.sndshdb'
...loading binary 'generated/declb/sounds/anansi.sndshdb'
...loading binary 'generated/declb/sounds/apt_gdf.sndshdb'
...loading binary 'generated/declb/sounds/apt_strogg.sndshdb'
...loading binary 'generated/declb/sounds/artillery.sndshdb'
...loading binary 'generated/declb/sounds/assaultrifle.sndshdb'
...loading binary 'generated/declb/sounds/avt_gdf.sndshdb'
...loading binary 'generated/declb/sounds/avt_strogg.sndshdb'
...loading binary 'generated/declb/sounds/badger.sndshdb'
...loading binary 'generated/declb/sounds/blaster.sndshdb'
...loading binary 'generated/declb/sounds/bumblebee.sndshdb'
...loading binary 'generated/declb/sounds/chat.sndshdb'
...loading binary 'generated/declb/sounds/cinematics.sndshdb'
...loading binary 'generated/declb/sounds/deployables.sndshdb'
...loading binary 'generated/declb/sounds/desecrator.sndshdb'
...loading binary 'generated/declb/sounds/explosions.sndshdb'
...loading binary 'generated/declb/sounds/fafff.sndshdb'
...loading binary 'generated/declb/sounds/flyerhive.sndshdb'
...loading binary 'generated/declb/sounds/footsteps.sndshdb'
...loading binary 'generated/declb/sounds/forwardspawn.sndshdb'
...loading binary 'generated/declb/sounds/gatling.sndshdb'
...loading binary 'generated/declb/sounds/gdf_botchat.sndshdb'
...loading binary 'generated/declb/sounds/gdf_highcommand.sndshdb'
...loading binary 'generated/declb/sounds/gdf_highcommand_objectives.sndshdb'
...loading binary 'generated/declb/sounds/gdf_highcommand_valley.sndshdb'
...loading binary 'generated/declb/sounds/gdf_npc.sndshdb'
...loading binary 'generated/declb/sounds/gdf_player.sndshdb'
...loading binary 'generated/declb/sounds/gdf_quickchat.sndshdb'
...loading binary 'generated/declb/sounds/goliath.sndshdb'
...loading binary 'generated/declb/sounds/gpmg.sndshdb'
...loading binary 'generated/declb/sounds/grenades.sndshdb'
...loading binary 'generated/declb/sounds/guis.sndshdb'
...loading binary 'generated/declb/sounds/haw.sndshdb'
...loading binary 'generated/declb/sounds/hog.sndshdb'
...loading binary 'generated/declb/sounds/hornet.sndshdb'
...loading binary 'generated/declb/sounds/husky.sndshdb'
...loading binary 'generated/declb/sounds/hyperblaster.sndshdb'
...loading binary 'generated/declb/sounds/icarus.sndshdb'
...loading binary 'generated/declb/sounds/impacts.sndshdb'
...loading binary 'generated/declb/sounds/jotun.sndshdb'
...loading binary 'generated/declb/sounds/knife.sndshdb'
...loading binary 'generated/declb/sounds/lacerator.sndshdb'
...loading binary 'generated/declb/sounds/law.sndshdb'
...loading binary 'generated/declb/sounds/lightningpistol.sndshdb'
...loading binary 'generated/declb/sounds/machinepistol.sndshdb'
...loading binary 'generated/declb/sounds/magog.sndshdb'
...loading binary 'generated/declb/sounds/mcp.sndshdb'
...loading binary 'generated/declb/sounds/misc.sndshdb'
...loading binary 'generated/declb/sounds/movement.sndshdb'
...loading binary 'generated/declb/sounds/music.sndshdb'
...loading binary 'generated/declb/sounds/nailgun.sndshdb'
...loading binary 'generated/declb/sounds/object_ambience.sndshdb'
...loading binary 'generated/declb/sounds/obliterator.sndshdb'
...loading binary 'generated/declb/sounds/pistol.sndshdb'
...loading binary 'generated/declb/sounds/plasmacannon.sndshdb'
...loading binary 'generated/declb/sounds/plasmamortar.sndshdb'
...loading binary 'generated/declb/sounds/players.sndshdb'
...loading binary 'generated/declb/sounds/psi.sndshdb'
...loading binary 'generated/declb/sounds/radar.sndshdb'
...loading binary 'generated/declb/sounds/railgun.sndshdb'
...loading binary 'generated/declb/sounds/railhowitzer.sndshdb'
...loading binary 'generated/declb/sounds/repairdrone.sndshdb'
...loading binary 'generated/declb/sounds/rockets.sndshdb'
...loading binary 'generated/declb/sounds/sbc.sndshdb'
...loading binary 'generated/declb/sounds/shieldgenerator.sndshdb'
...loading binary 'generated/declb/sounds/shotgun.sndshdb'
...loading binary 'generated/declb/sounds/slamship.sndshdb'
...loading binary 'generated/declb/sounds/sniperrifle.sndshdb'
...loading binary 'generated/declb/sounds/soundscapes.sndshdb'
...loading binary 'generated/declb/sounds/spikes.sndshdb'
...loading binary 'generated/declb/sounds/ssg.sndshdb'
...loading binary 'generated/declb/sounds/ssm.sndshdb'
...loading binary 'generated/declb/sounds/strogg_botchat.sndshdb'
...loading binary 'generated/declb/sounds/strogg_nexus.sndshdb'
...loading binary 'generated/declb/sounds/strogg_nexus_objectives.sndshdb'
...loading binary 'generated/declb/sounds/strogg_nexus_valley.sndshdb'
...loading binary 'generated/declb/sounds/strogg_npc.sndshdb'
...loading binary 'generated/declb/sounds/strogg_player.sndshdb'
...loading binary 'generated/declb/sounds/strogg_quickchat.sndshdb'
...loading binary 'generated/declb/sounds/structures.sndshdb'
...loading binary 'generated/declb/sounds/titan.sndshdb'
...loading binary 'generated/declb/sounds/tools.sndshdb'
...loading binary 'generated/declb/sounds/trojan.sndshdb'
...loading binary 'generated/declb/sounds/ui.sndshdb'
...loading binary 'generated/declb/sounds/valley_sounds.sndshdb'
...loading binary 'generated/declb/sounds/vampire.sndshdb'
...loading binary 'generated/declb/sounds/vehicles.sndshdb'
...loading binary 'generated/declb/sounds/violator.sndshdb'
...loading binary 'generated/declb/sounds/wav.sndshdb'
...loading binary 'generated/declb/sounds/weapons.sndshdb'
...loading binary 'generated/declb/sounds/world.sndshdb'
...loading binary 'generated/declb/atmosphere/cockpits.atmb'
...loading binary 'generated/declb/atmosphere/limbo.atmb'
...loading binary 'generated/declb/atmosphere/main_menu.atmb'
...loading binary 'generated/declb/atmosphere/valley.atmb'
...loading binary 'generated/declb/stuff/valley.stuffb'
...loading binary 'generated/declb/surfacetypes/types.stpb'
...loading binary 'generated/declb/surfacetypes/models/mapobjects/valley/valley_mapobjects01.stmapb'
...loading binary 'generated/declb/surfacetypes/texturesheets/valley/valley08.stmapb'
...loading binary 'generated/declb/surfacetypes/texturesheets/valley/valley_assault_bridge.stmapb'
...loading binary 'generated/declb/surfacetypes/texturesheets/valley/valley_jetty.stmapb'
...loading binary 'generated/declb/surfacetypes/texturesheets/valley/valley_wall_1.stmapb'
...loading binary 'generated/declb/surfacetypes/texturesheets/valley/valley_wall_2.stmapb'
...loading binary 'generated/declb/surfacetypes/texturesheets/valley/valley_wall_3.stmapb'
...loading binary 'generated/declb/surfacetypes/texturesheets/valley/valley_wall_4.stmapb'
...loading binary 'generated/declb/surfacetypes/texturesheets/valley/valley_wall_5.stmapb'
...loading binary 'generated/declb/surfacetypes/texturesheets/valley/valley_wall_6.stmapb'
...loading binary 'generated/declb/surfacetypes/texturesheets/valley/valley_wall_7.stmapb'
...loading binary 'generated/declb/renderprogs/atmosphere.rprogb'
...loading binary 'generated/declb/renderprogs/coverage.rprogb'
...loading binary 'generated/declb/renderprogs/depth.rprogb'
...loading binary 'generated/declb/renderprogs/foglights.rprogb'
...loading binary 'generated/declb/renderprogs/heathaze.rprogb'
...loading binary 'generated/declb/renderprogs/imposters.rprogb'
...loading binary 'generated/declb/renderprogs/occlusion.rprogb'
...loading binary 'generated/declb/renderprogs/portals.rprogb'
...loading binary 'generated/declb/renderprogs/renderbindings.rprogb'
...loading binary 'generated/declb/renderprogs/sfx.rprogb'
...loading binary 'generated/declb/renderprogs/sfx2.rprogb'
...loading binary 'generated/declb/renderprogs/shadow.rprogb'
...loading binary 'generated/declb/renderprogs/skies.rprogb'
...loading binary 'generated/declb/renderprogs/stuff.rprogb'
...loading binary 'generated/declb/renderprogs/trivial.rprogb'
...loading binary 'generated/declb/renderprogs/water.rprogb'
...loading binary 'generated/declb/renderprogs/game/railgunscope.rprogb'
...loading binary 'generated/declb/renderprogs/game/sniperscope.rprogb'
...loading binary 'generated/declb/renderprogs/interaction/basic.rprogb'
...loading binary 'generated/declb/renderprogs/interaction/basic_alphatest.rprogb'
...loading binary 'generated/declb/renderprogs/interaction/basic_detail.rprogb'
...loading binary 'generated/declb/renderprogs/interaction/basic_detailwm.rprogb'
...loading binary 'generated/declb/renderprogs/interaction/foliage.rprogb'
...loading binary 'generated/declb/renderprogs/interaction/parallax.rprogb'
...loading binary 'generated/declb/renderprogs/interaction/self_illum.rprogb'
...loading binary 'generated/declb/renderprogs/interaction/separate_depth.rprogb'
...loading binary 'generated/declb/renderprogs/interaction/strogg.rprogb'
...loading binary 'generated/declb/renderprogs/interaction/translucent.rprogb'
...loading binary 'generated/declb/renderprogs/megatexture/ambient.rprogb'
...loading binary 'generated/declb/renderprogs/megatexture/glslambient.rprogb'
...loading binary 'generated/declb/renderprogs/megatexture/glslinteraction.rprogb'
...loading binary 'generated/declb/renderprogs/megatexture/interaction.rprogb'
...loading binary 'generated/declb/renderprogs/postprocess/glare.rprogb'
...loading binary 'generated/declb/renderprogs/skinning/skinning_matrix.rprogb'
...loading binary 'generated/declb/imposters/imposters.impb'
...loading binary 'generated/declb/localization/locstr/default.locstrb'
...loading binary 'generated/declb/localization/locstr/engine/keys.locstrb'
...loading binary 'generated/declb/localization/locstr/engine/misc.locstrb'
...loading binary 'generated/declb/localization/locstr/engine/sdnet.locstrb'
...loading binary 'generated/declb/localization/locstr/game/achievements.locstrb'
...loading binary 'generated/declb/localization/locstr/game/chat_gdf.locstrb'
...loading binary 'generated/declb/localization/locstr/game/chat_gdf_bot.locstrb'
...loading binary 'generated/declb/localization/locstr/game/chat_strogg.locstrb'
...loading binary 'generated/declb/localization/locstr/game/chat_strogg_bot.locstrb'
...loading binary 'generated/declb/localization/locstr/game/classes.locstrb'
...loading binary 'generated/declb/localization/locstr/game/default.locstrb'
...loading binary 'generated/declb/localization/locstr/game/intros.locstrb'
...loading binary 'generated/declb/localization/locstr/game/loadtips.locstrb'
...loading binary 'generated/declb/localization/locstr/game/obituaries.locstrb'
...loading binary 'generated/declb/localization/locstr/game/ranks.locstrb'
...loading binary 'generated/declb/localization/locstr/game/rewards.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tasks.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tooltips.locstrb'
...loading binary 'generated/declb/localization/locstr/game/votes.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tasks/solo_aggressor.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tasks/solo_all.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tasks/solo_common.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tasks/solo_constructor.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tasks/solo_covertops.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tasks/solo_engineer.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tasks/solo_fieldops.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tasks/solo_gdf.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tasks/solo_infiltrator.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tasks/solo_medic.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tasks/solo_oppressor.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tasks/solo_soldier.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tasks/solo_strogg.locstrb'
...loading binary 'generated/declb/localization/locstr/game/tasks/solo_technician.locstrb'
...loading binary 'generated/declb/localization/locstr/guis/admin.locstrb'
...loading binary 'generated/declb/localization/locstr/guis/bindings.locstrb'
...loading binary 'generated/declb/localization/locstr/guis/game.locstrb'
...loading binary 'generated/declb/localization/locstr/guis/global.locstrb'
...loading binary 'generated/declb/localization/locstr/guis/hud.locstrb'
...loading binary 'generated/declb/localization/locstr/guis/limbo.locstrb'
...loading binary 'generated/declb/localization/locstr/guis/mainmenu.locstrb'
...loading binary 'generated/declb/localization/locstr/guis/maps.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/area22.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/ark.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/canyon.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/island.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/locations.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/objectives.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/outskirts.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/quarry.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/refinery.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/salvage.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/sewer.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/slipgate.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/valley.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/volcano.locstrb'
------------------------------
couldn't exec 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
couldn't exec 'etqwbinds.cfg'
execing 'autoexec.cfg'
TODO: Sys_GetGfxDeviceIdentification
Vendor: Device:
/proc/cpuinfo CPU frequency: 2400 MHz
parse /proc/cpuinfo for CPU information
parse had a problem
detecting video ram (set sys_videoRam on command line to override) ..
trying /proc/dri/0/umm
'total      LFB  =' not matched in /proc/dri/0/umm
guess failed, return default low-end VRAM setting ( 128MB VRAM )
Detected
        1 2.40 GHz CPU
        752 MB of System memory
        128 MB of Video memory on an optimal video architecture

This system qualifies for Low quality.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
WARNING: SDL_GL_LoadLibrary libGL.so.1 failed: Couldn't open ./etqw.bmp

execing 'specs/minspec.dat'
execing 'specs/minspec_cpu.dat'
execing 'specs/minspec_gamedetail.dat'
execing 'specs/minspec_gpu.dat'
execing 'specs/minspec_gpudetail.dat'
execing 'specs/minspec_lighting.dat'
execing 'specs/minspec_foliage.dat'
TODO: Sys_GetGfxDeviceIdentification
Vendor: Device:
execing 'specs/recspec_foliage.dat'
Opening IP socket: localhost:-1
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
WARNING: SDL_GL_LoadLibrary libGL.so.1 failed: Couldn't open ./etqw.bmp

------- Initializing renderSystem --------
----- R_InitOpenGL -----
signal caught: 'Segmentation fault', si_code 1
callstack:
0x0
[0x082cc6d1]
[0x082bc82f]
[0xffffe600]
Trying to exit gracefully..
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()
thread priority set to 0

```

Can someone help?

---

### Post by aephoenix on 2007-10-30
I have what I feel is exactly the same problem as you.. and yet a google search for "./etqw.bmp" returns nothing.. What's so uncommon about our problem? :|

edit: oops duh, of course you do you have a signature D:

---

### Post by The Populist on 2007-11-03
I agree:

I have surfed this forum, and enemy territory forums, and there are people who just cant get the damn demo to install. It's driving me nuts. I really wan to play this game.

...

---

### Post by B0rsuk on 2007-11-03
Are your drivers installed properly ? Can you run other games like Wolfenstein:Enemy Territory , UT2004 , Quake4 , Doom3 , Neverball (in repositories) ?

If you run glxgears do you get fluid motion ?

---

### Post by aoanla on 2007-11-03
The error in the log clearly shows that SDL couldn't load libGL.so.1

libGL.so.1 is normally a link to libGL.so.1.2, and that link clearly hasn't been created on your system.

Are you, by any chance, running an ATI graphics card? I know that the installer for fglrx drivers often "forgets" to generate these symlinks, especially on Ubuntu. (Aha, and, looking at your sig, I see you are using such a card).

in that case, in a terminal, type:

locate libGL.so.1

You should see lots of copies of libGL libraries:
For each directory, there should be a libGL.so, libGL.so.1 and a libGL.so.1.2
This is especially important for the /usr/lib/ and /usr/lib32/ directories.
One of those two paths will be missing a libGL.so.1
You need to make the correct link, for the directory which is missing that libGL.so.1 by typing either:
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

or

sudo ln -s /usr/lib32/libGL.so.1.2 /usr/lib32/libGL.so.1

depending on which directory is missing a libGL.so.1, of course.
(If both are missing one, then do both lines).

Tell me if this doesn't work.

---

