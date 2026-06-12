---
title: "[SOLVED] Vega Strike won't run"
date: 2007-09-16
forum: Gaming &amp; Leisure
---

### Post by Xavier Oddmon on 2007-09-16
Alright, I downloaded Vega Strike, which looked like a fun game, kind of like a 3D version of Escape Velocity. When I try to run it, it freezes at loading "generic.png", and then quits
I ran it in terminal, and below is the output:

> 
chris@Hal:~$ vegastrike -A
Vega Strike  
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for license details.

ARG #1 = -A
GOT SUBDIR ARG = 
Found data in /usr/share/games/vegastrike
Using /usr/share/games/vegastrike as data directory
Using .vegastrike.4.x as the home directory
Found MODDIR = /usr/share/games/vegastrike/mods
USING HOMEDIR : /home/chris/.vegastrike.4.x As the home directory 
CONFIGFILE - No config found in home : /home/chris/.vegastrike.4.x/vegastrike.config
CONFIGFILE - No home config file found, using datadir config file : /usr/share/games/vegastrike/vegastrike.config
DATADIR - No datadir specified in config file, using ; /usr/share/games/vegastrike
SIMULATION_ATOM: 0.06
MISSION_NAME is empty using : explore_universe.mission
running import sys
print sys.path
sys.path = [r"/usr/share/games/vegastrike/modules/builtin/",r"/usr/share/games/vegastrike/modules/",r"/usr/share/games/vegastrike/bases/"]
['/usr/lib/python25.zip', '/usr/lib/python2.5', '/usr/lib/python2.5/plat-linux2', '/usr/lib/python2.5/lib-tk', '/usr/lib/python2.5/lib-dynload', '/usr/local/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages/Numeric', '/usr/lib/python2.5/site-packages/PIL', '/usr/lib/python2.5/site-packages/gst-0.10', '/var/lib/python-support/python2.5', '/usr/lib/python2.5/site-packages/gtk-2.0', '/var/lib/python-support/python2.5/gtk-2.0', '/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode']
testing VS randomrunning import sys
print sys.path
['/usr/share/games/vegastrike/modules/builtin/', '/usr/share/games/vegastrike/modules/', '/usr/share/games/vegastrike/bases/']
Setting Screen to w 1024 h 768 and pitch of 4096 and 32 bpp 4 bytes per pix mode
OpenGL Extensions supported: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
OpenGL::GL_EXT_compiled_vertex_array unsupported
OpenGL::Accurate Fog Distance unsupported
OpenGL::Generic Texture Compression unsupported
OpenGL::S3TC Texture Compression unsupported
OpenGL::Multitexture unsupported
OpenGL::TextureCubeMapExt unsupported
OpenGL::EXTColorTable unsupported
2 joysticks were found.

The names of the joysticks are:
    Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10
axes: 37 buttons: 42 hats: 0
    Logitech WingMan Cordless Gamepad
axes: 7 buttons: 11 hats: 0
FactionXML:LoadXML factions.xml
xyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzw
logos/mechanistSec.png, not found

logos/mechanistPri.png, not found

logos/shmrnSec.png, not found

logos/shmrnPri.png, not found

logos/rlaan_briinSec.png, not found

logos/rlaan_briinPri.png, not found
xyzwxyzwxyzwxyzwHi helper play 0
HereFound ship named : llama.begin
Found faction in save file : 0
        Exiting ReadSavedPackets
Hi helper play 0
xyzwxyzwxyzwxyzw
neutral_Asteroid.bmp, not found
xyzwxyzw
klkk_cyl.png, not found
xyzw
neutral_wh_rgb_stable.png, not found
xyzw
neutral_wh_spec_stable.png, not found
xyzwxyzwxyzwxyzwxyzwxyzw
neutral_atm.png, not found
xyzwxyzwxyzw
klkk_barracks.jpg, not found
xyzw
klkk_barracksPPL.jpg, not found
xyzw
klkk_barracksGLOW.jpg, not found
xyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzw
klkk_turret1.png, not found
xyzw
klkk_turet1ppl.png, not found

turet1ppl.png, not found

klkk_turret1ppl.png, not found

turret1ppl.png, not found

klkk_Capskn3.bmp, not found
xyzwxyzw
klkk_relay.jpg, not found
xyzw
klkk_relayPPL.jpg, not found
xyzw
klkk_relayGLOW.jpg, not found
xyzwxyzwxyzwxyzwHereUnit file rock not found
Assertion failed unit_generic.cpp:711 Unit rock not found
Warning: Cannot locate rock
xyzw
klkk_blank.png, not found
xyz palette w
klkk_mining.jpg, not found
xyzw
klkk_miningPPL.jpg, not found
xyzwxyzwxyzwMin (0.000000, 0.000000, 0.000000) Max(0.000000, 0.000000, 0.000000) MinLumin 1.000000, MaxLumin 1.000000Read In Star Count 0 used: 2000
xyzwxyzwxyzwxyzwxyzwxyzwMin (0.000000, 0.000000, 0.000000) Max(0.000000, 0.000000, 0.000000) MinLumin 1.000000, MaxLumin 1.000000Read In Star Count 0 used: 38
Loading a starsystem
WARNING: no section/variable/color named projectile_means_missile
Loading Star System Crucible/Cephid_17
 Next To: Crucible/Oldziey
 Next To: Crucible/Everett
 Next To: Crucible/Enyo
 Next To: Crucible/Cardell
 Next To: Crucible/Stirling
 Next To: Crucible/17-arWARNING: no section named terrain
WARNING: no section named terrain
WARNING: no section named terrain
FOUND MODIFICATION = test2 FOR PLAYER #0
CREATING A LOCAL SHIP : llama.begin
Hi helper play 0
xyzw
privateer_llama_connector.jpg, not found
xyzw
privateer_llama_connectorPPL.jpg, not found
xyzw
privateer_llama_catamaran.jpg, not found
xyzw
privateer_llama_catamaranPPL.jpg, not found
xyzw
privateer_llama_body.jpg, not found
xyzw
privateer_llama_bodyPPL.jpg, not found
xyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzw
neutral_laser.png, not found
xyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzw
neutral_galva.png, not found
xyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwxyzwHerepox -95124024.543917 412089916.256812 -110779667.398050
WARNING: no section named sound
SITUATION IS 1force change 1 bool 1
SITUATION IS RESET TO 1
peace
xyzwdone loading rand enc
Purging...
StartSystemCount
Current Path /usr/share/games/vegastrike
Final Path /usr/share/games/vegastrike
Using .vegastrike.4.x as the home directory
{'pirates': 31, 'forsaken': 20, 'rlaan': 771, 'ISO': 15, 'planets': 0, 'upgrades': 0, 'homeland-security': 0, 'unknown': 111, 'klkk': 17, 'unadorned': 37, 'mechanist': 29, 'LIHW': 159, 'merchant': 1, 'privateer': 0, 'aera': 705, 'dgn': 1, 'luddites': 19, 'hunter': 0, 'andolian': 149, 'rlaan_briin': 0, 'neutral': 0, 'confed': 18, 'highborn': 23, 'purist': 199, 'shaper': 98, 'shmrn': 6, 'uln': 26}
EndSystemCount
reading base names confed
Opened audio at 44100 Hz 16 bit stereo, 4096 bytes audio buffer

[CONNECTED]
i0
[SETTING FADEIN TO 0]
o1
[SETTING FADEOUT TO 1]
0
v0.500000
[SETTING VOLUME TO 0.500000]
p../music/peace2.oggreading base names aera
reading base names rlaan

[UNABLE TO PLAY ../music/peace2.ogg IN /usr/share/games/vegastrike WITH 0 FADEIN AND 1 FADEOUT]
reading base names merchant
reading base names luddites
reading base names pirates
reading base names hunter
reading base names homeland-security
reading base names ISO
reading base names unknown
reading base names andolian
reading base names highborn
reading base names shaper
reading base names unadorned
reading base names purist
reading base names forsaken
reading base names LIHW
reading base names uln
reading base names dgn
reading base names klkk
reading base names mechanist
reading base names shmrn
reading base names rlaan_briin
Second Load
init random enc
end random enc

neutral_nav.png, not found
xyzw
neutral_generic.png, not found
xyzwWARNING: no section named nav
WARNING: no section named nav
WARNING: no section named nav
WARNING: no section named nav
WARNING: color base_black not defined, using default (hexcolor)
WARNING: color base_white not defined, using default (hexcolor)
WARNING: color base_gray not defined, using default (hexcolor)
Force feedback support disabled when compiled
Loading completed, now network init
Writing Save Game test2explore_universe_difficultyHi helper play 0
HereHi helper play 0
HereHi helper play 0
yzwHereinit playerdat
done playerdat
launching bases for Crucible/Cephid_17
conditioning
nonzeroing
finding quest
quest_drone
resetting sigdist=8000.000000 detdist=40000.000000
dot 0.993099Reading from socket 17
 decrementing INSYS bounty to 1
 decrementing bounty to 1
reading company names 
generating cargo briefing
Generated defendY with insys at: 1 and outsys at 0
Generated defendY with insys at: 1 and outsys at 0
p../music/ocean.ogg
[UNABLE TO PLAY ../music/ocean.ogg IN /usr/share/games/vegastrike WITH 0 FADEIN AND 1 FADEOUT]
Generated defendY with insys at: 1 and outsys at 0
['gm', '*r'] Not in Habitable List
reading company names 
generating cargo briefing
reading company names 
generating cargo briefing
reading company names 
generating cargo briefing
Generated defendY with insys at: 1 and outsys at 0
reading company names 
generating cargo briefing
reading company names 
generating cargo briefing
 decrementing bounty to 0
reading company names 
generating cargo briefing
Generated defendY with insys at: 1 and outsys at 0
['v'] Not in Habitable List
['v'] Not in Habitable List
reading company names 
generating cargo briefing
 decrementing bounty to -1
reading company names 
generating cargo briefing
reading company names 
generating cargo briefing
reading company names 
generating cargo briefing
reading company names 
generating cargo briefing
reading company names 
generating cargo briefing
 decrementing bounty to -2
Generated defendY with insys at: 1 and outsys at 0
Generated defendY with insys at: 1 and outsys at 0
Generated defendY with insys at: 1 and outsys at 0
Generated defendY with insys at: 1 and outsys at 0
['gm', '*r', '*oa', 'gg', '*oa'] Not in Habitable List
reading company names 
generating cargo briefing
reading company names 
generating cargo briefing
Generated defendY with insys at: 1 and outsys at 0
reading company names 
generating cargo briefing
reading company names 
generating cargo briefing
 decrementing bounty to -3
reading company names 
generating cargo briefing
reading company names 
generating cargo briefing
Processing News
xyzwxyzwxyzwxyzw*** Get teh fixer to display!!!
there are 1 campagins
*** getting current node
*** read stuff from savegame
*** :-) ***
[]
['Crucible', 'Cephid_17']==?==['crucible', 'cephid_17']
*** Test if docked to: atlantis
llama.begin not docked to unit
MiningBase not docked to unit
Phillies not docked to unit
JumpToEnyo not docked to unit
JumpToCardell not docked to unit
fighter_barracks not docked to unit
Wiley not docked to unit
Broadway not docked to unit
*** Compare atlantis == atlantis
    Compare ocean == atlantis
*** inSystem return true
*** CargoSpace return true
*** cur evalutaed
*** found actuive node in campaign vega_strike_campaign
['Crucible', 'Cephid_17']==?==['crucible', 'cephid_17']
*** Test if docked to: atlantis
llama.begin not docked to unit
MiningBase not docked to unit
Phillies not docked to unit
JumpToEnyo not docked to unit
JumpToCardell not docked to unit
fighter_barracks not docked to unit
Wiley not docked to unit
Broadway not docked to unit
*** Compare atlantis == atlantis
    Compare ocean == atlantis
*** inSystem return true
*** CargoSpace return true
checking contingency: True
Nodes 1
*** display it. 
['Crucible', 'Cephid_17']==?==['crucible', 'cephid_17']
*** Test if docked to: atlantis
llama.begin not docked to unit
MiningBase not docked to unit
Phillies not docked to unit
JumpToEnyo not docked to unit
JumpToCardell not docked to unit
fighter_barracks not docked to unit
Wiley not docked to unit
Broadway not docked to unit
*** Compare atlantis == atlantis
    Compare ocean == atlantis
*** inSystem return true
*** CargoSpace return true
*** create fixer('campaign/hauler.spr', 'Talk_To_The_Hauler')
xyzwxyzwxyzwxyzwxyzwxyzwwhole list: [['Natural_Products/Food', 1.2, 0.10000000000000001, 5.0, 3.0], ['Natural_Products/Liquor', 1.1000000000000001, 0.10000000000000001, 1.0, 1.0], ['Natural_Products/Plants', 1.0, 0.10000000000000001, 2.0, 2.0], ['Natural_Products/Natural_Resources', 0.69999999999999996, 0.10000000000000001, 0.0, 0.0], ['Raw_Materials/Metals/Crude', 0.65000000000000002, 0.20000000000000001, 42.0, 15.0], ['Raw_Materials/Metals/Precious', 0.65000000000000002, 0.20000000000000001, 22.0, 5.0], ['Raw_Materials/Metals/Alloys', 0.80000000000000004, 0.20000000000000001, 0.0, 0.0], ['Raw_Materials/Metals/Radioactive', 0.65000000000000002, 0.20000000000000001, 25.0, 5.0], ['Raw_Materials/Gems/Jewelry', 1.05, 0.10000000000000001, 10.0, 0.0], ['Raw_Materials/Gems/Industrial', 0.69999999999999996, 0.20000000000000001, 22.0, 7.0], ['Raw_Materials/Stone', 0.69999999999999996, 0.10000000000000001, 7.0, 3.0], ['Fuels/Crude', 0.69999999999999996, 0.20000000000000001, 0.0, 0.0], ['Fuels/Refined', 1.1000000000000001, 0.20000000000000001, 3.0, 2.0], ['Compressed_Gasses', 1.2, 0.10000000000000001, 5.0, 5.0], ['Recycled_Products', 1.1000000000000001, 0.10000000000000001, 0.0, 0.0], ['Machinery_Goods', 1.2, 0.20000000000000001, 0.0, 0.0], ['Supplies/Aerospace_Supplies', 0.80000000000000004, 0.10000000000000001, 0.0, 0.0], ['Supplies/Agriculteral_Supplies', 0.69999999999999996, 0.10000000000000001, 0.0, 0.0], ['Supplies/Mining_Supplies', 1.3, 0.10000000000000001, 1.0, 1.0], ['Supplies/Construction_Supplies', 1.2, 0.10000000000000001, 1.0, 1.0], ['Supplies/Medical_Supplies', 1.1000000000000001, 0.10000000000000001, 5.0, 3.0], ['Electronics', 0.90000000000000002, 0.10000000000000001, 0.0, 0.0], ['Electronics/Robotics', 1.2, 0.10000000000000001, 1.0, 1.0], ['Manufactured_Goods', 0.69999999999999996, 0.20000000000000001, 0.0, 0.0], ['Entertainment', 1.2, 0.10000000000000001, 1.0, 1.0], ['Contraband', 1.1000000000000001, 0.40000000000000002, 0.0, 0.0], ['starships/Confed/Light', 1.0, 0.0, 12.0, 5.0], ['starships/Confed/Medium', 1.0, 0.0, 6.0, 3.0], ['starships/Militia/Light', 1.0, 0.0, 12.0, 5.0], ['starships/Militia/Medium', 1.0, 0.0, 6.0, 3.0], ['starships/Merchant/Light', 1.0, 0.0, 12.0, 5.0], ['starships/Merchant/Medium', 1.0, 0.0, 6.0, 3.0], ['starships/Hunter/Light', 1.0, 0.0, 12.0, 5.0], ['starships/Hunter/Medium', 1.0, 0.0, 6.0, 3.0], ['upgrades/Weapons/Mounted_Guns_Light', 1.0, 0.10000000000000001, 12.0, 5.0], ['upgrades/Weapons/Mounted_Guns_Medium', 1.0, 0.10000000000000001, 6.0, 5.0], ['upgrades/Weapons/Beam_Arrays_Light', 1.0, 0.10000000000000001, 6.0, 3.0], ['upgrades/Weapons/Beam_Arrays_Medium', 1.0, 0.10000000000000001, -2.0, 5.0], ['upgrades/Weapons/Mount_Enhancements', 1.0, 0.10000000000000001, -12.0, 15.0], ['upgrades/Weapons/Turrets', 1.0, 0.10000000000000001, 1.0, 1.0], ['upgrades/Miscellaneous/SubUnits', 1.0, 0.10000000000000001, 1.0, 1.0], ['upgrades/Reactors/Light', 1.0, 0.10000000000000001, 12.0, 5.0], ['upgrades/Reactors/Medium', 1.0, 0.10000000000000001, 6.0, 3.0], ['upgrades/Engines/Engine_Enhancements_Light', 1.0, 0.10000000000000001, 5.0, 2.0], ['upgrades/Engines/Engine_Enhancements_Medium', 1.0, 0.10000000000000001, -2.0, 7.0], ['upgrades/Shield_Systems/Light', 1.0, 0.10000000000000001, 12.0, 5.0], ['upgrades/Capacitors/Reactors', 1.0, 0.10000000000000001, 12.0, 5.0], ['upgrades/Capacitors/Shields', 1.0, 0.10000000000000001, 12.0, 5.0], ['upgrades/Shield_Systems/Medium', 1.0, 0.10000000000000001, 6.0, 3.0], ['upgrades/Armor_Modification', 1.0, 0.10000000000000001, 12.0, 6.0], ['upgrades/Hull_Upgrades', 1.0, 0.10000000000000001, 12.0, 6.0], ['upgrades/ECM_Systems', 1.0, 0.10000000000000001, 6.0, 3.0], ['upgrades/Repair_Systems', 1.0, 0.10000000000000001, 2.0, 1.0], ['upgrades/Radar/Basic', 1.0, 0.10000000000000001, 6.0, 3.0], ['upgrades/Miscellaneous', 1.0, 0.10000000000000001, 3.0, 2.0], ['upgrades/Ammunition', 1.0, 0.10000000000000001, 21.0, 5.0]]
whole list: []
whole list: []
whole list: [['Natural_Products/Food', 1.2, 0.10000000000000001, 5.0, 3.0], ['Natural_Products/Liquor', 0.80000000000000004, 0.10000000000000001, 0.0, 0.0], ['Natural_Products/Plants', 0.69999999999999996, 0.10000000000000001, 0.0, 0.0], ['Natural_Products/Natural_Resources', 0.69999999999999996, 0.10000000000000001, 0.0, 0.0], ['Raw_Materials/Metals/Crude', 0.65000000000000002, 0.20000000000000001, 0.0, 0.0], ['Raw_Materials/Metals/Precious', 0.65000000000000002, 0.20000000000000001, 0.0, 0.0], ['Raw_Materials/Metals/Alloys', 0.80000000000000004, 0.20000000000000001, 0.0, 0.0], ['Raw_Materials/Metals/Radioactive', 0.65000000000000002, 0.20000000000000001, 0.0, 0.0], ['Raw_Materials/Gems/Jewelry', 1.05, 0.10000000000000001, 10.0, 0.0], ['Raw_Materials/Gems/Industrial', 0.69999999999999996, 0.20000000000000001, 0.0, 0.0], ['Raw_Materials/Stone', 0.69999999999999996, 0.10000000000000001, 0.0, 0.0], ['Fuels/Crude', 0.69999999999999996, 0.20000000000000001, 0.0, 0.0], ['Fuels/Refined', 1.1000000000000001, 0.20000000000000001, 3.0, 2.0], ['Compressed_Gasses', 1.2, 0.10000000000000001, 5.0, 5.0], ['Recycled_Products', 1.1000000000000001, 0.10000000000000001, 0.0, 0.0], ['Machinery_Goods', 1.2, 0.20000000000000001, 0.0, 0.0], ['Supplies/Aerospace_Supplies', 0.80000000000000004, 0.10000000000000001, 0.0, 0.0], ['Supplies/Agriculteral_Supplies', 0.69999999999999996, 0.10000000000000001, 0.0, 0.0], ['Supplies/Mining_Supplies', 1.3, 0.10000000000000001, 1.0, 1.0], ['Supplies/Construction_Supplies', 1.2, 0.10000000000000001, 1.0, 1.0], ['Supplies/Medical_Supplies', 1.1000000000000001, 0.10000000000000001, 5.0, 3.0], ['Electronics', 0.90000000000000002, 0.10000000000000001, 0.0, 0.0], ['Electronics/Robotics', 1.2, 0.10000000000000001, 1.0, 1.0], ['Manufactured_Goods', 0.69999999999999996, 0.20000000000000001, 0.0, 0.0], ['Entertainment', 1.2, 0.10000000000000001, 1.0, 1.0], ['Contraband', 0.0, 0.0, 0.0, 0.0], ['starships/Confed/Light', 1.0, 0.0, 0.0, 6.0], ['starships/Confed/Medium', 1.0, 0.0, 0.0, 6.0], ['starships/Confed/Heavy', 1.0, 0.0, 0.0, 6.0], ['starships/Confed/Milspec', 1.0, 0.0, 0.0, 6.0], ['upgrades/Weapons/Mounted_Guns_Confed_Milspec', 1.0, 0.10000000000000001, 2.0, 5.0], ['upgrades/Weapons/Beam_Arrays_Confed_Milspec', 1.0, 0.10000000000000001, 4.0, 4.0], ['upgrades/Weapons/Turrets', 1.0, 0.10000000000000001, 1.0, 1.0], ['upgrades/Miscellaneous/SubUnits', 1.0, 0.10000000000000001, 1.0, 1.0], ['upgrades/Engines/Confed_Milspec', 1.0, 0.10000000000000001, 0.0, 5.0], ['upgrades/Shield_Systems/Confed_Milspec', 1.0, 0.10000000000000001, 12.0, 5.0], ['upgrades/Armor_Modification/Confed_Milspec', 1.0, 0.10000000000000001, 12.0, 5.0], ['upgrades/Hull_Upgrades/Confed_Milspec', 1.0, 0.10000000000000001, 12.0, 5.0], ['upgrades/ECM_Systems/Confed_Milspec', 1.0, 0.10000000000000001, 12.0, 5.0], ['upgrades/Radar/Intermediate', 1.0, 0.10000000000000001, 12.0, 5.0], ['upgrades/Miscellaneous/Confed_Milspec', 1.0, 0.10000000000000001, 12.0, 5.0], ['upgrades/Ammunition', 1.0, 0.10000000000000001, 37.0, 7.0]]
Segmentation fault (core dumped)
chris@Hal:~$ 



I'd really like to play this game, but can't. Please help.

---

### Post by silvercatjewelry on 2007-09-19
Hi, did you down load from the repositories?  When I downloaded from the repository, installed and ran the game I was having sound problems.  I went to [http://vegastrike.sourceforge.net/wiki/Vegastrike](http://vegastrike.sourceforge.net/wiki/Vegastrike) for help.  It turned out I found out that there may be a problem with the version from the repository.  Anyway I downloaded and compiled the check out svn and I am enjoying the game.  Great Game!

I am running ubuntu feisty 64 on my system.

---

### Post by Xavier Oddmon on 2007-09-28
Yes, I did install from the repositories. I'll try to download the version from the web page overnight tonight, then (hopefully) it'll work tomorrow.

---

### Post by borkabrak on 2007-10-04
I had the same problem:  The version of vegastrike I got from the synaptic repository crashed immediately after the loading screen.  

My solution didn't even involve compiling -- I just went to the download page on the official vegastrike page (mentioned above), and downloaded the precompiled binary for linux.

Worked like a charm.

I feel it worthwhile here to make an editorial addendum:  While I'm pleased that a solution exists and that these forums proved useful yet again in directing me to it, I'm still rather disturbed by the fact that the default repositories don't work in at least one case.

I understand that maintenance of the official repositories cannot be anything like an easy or trivial task, but I still fear that if ubuntu is to remain the relative linux powerhouse that it is, it will be necessary to tighten up in this regard.

---

### Post by Xavier Oddmon on 2007-10-04
Yeah, I downloaded it manually, and although I have to launch it from the folder it's installed in, that's no big deal. Now i've just got to figure out how exactly it works. It looks pretty cool, but also seems to have a really steep learning curve.

---

### Post by Achetar on 2007-11-11
Yes, it has a VERY steep learning curve, i got it same time as you (0.4.3 downloaded from the repos and works fine with me). I also tried Development 0.5.0, but crashes so often its no fun :( can't wait until they get it working, cuz it has laucher type thing (it has a game menu, whereas 0.4.3 don't)

---

### Post by zazuge on 2009-08-16
the thread is old but i warn people that v0.4.3 have lots of problems
like cargo tractoring that won't work and other missing sprits
don't wast  you time collecting money because the save game are not compatible with later versions ^^

---

