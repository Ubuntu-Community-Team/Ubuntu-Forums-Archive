---
title: "Input Signal out of range"
date: 2009-05-23
forum: General Help
---

### Post by Will Murray on 2009-05-23
Hello,

I am quite new to ubuntu and I like it but when I launch the game Warsow I get the error "Input Signal out of range, Please change settings to 1440x900 60Hz", this message is displayed by my monitor and not by the computer/ubuntu. I already have these settings set in Display options.

My Screen: HP w1907

Thanks in advance for any help.

---

### Post by Aped on 2009-05-23
The game is probably changing your resolution for you when it starts up, many do. Is there a .cfg file you can find the resolution in, or some other way for you to change the video options without having to actually open the game itself?

Good luck, I guess ;)

PS Sometimes that monitor error is actually **refresh rate** related, not necessarily your resolution that the app is borking, though some monitors will report these things as the same problem (I had one that did it a long time ago, really frustrating;) just something to keep in mind, probably not an issue here tho.

---

### Post by Will Murray on 2009-05-23
I managed to find this config file, though I am unable to change anything. I get a permissions error if I try.


```
// Key bindings



unbindall



bind 1          "use Gunblade"

bind 2          "use Riotgun"

bind 3          "use Grenade Launcher"

bind 4          "use Rocket Launcher"

bind 5          "use Plasmagun"

bind 6          "use Lasergun"

bind 7          "use Electrobolt"



bind MWHEELUP   "weapnext"

bind MWHEELDOWN "weapprev"



bind BACKSPACE  "drop weapon"



bind CTRL       "+attack"

bind MOUSE1     "+attack"

bind MOUSE2     "+special"

bind MOUSE3     "+special"

bind SPACE      "+moveup"

bind c          "+movedown"

bind z          "+zoom"



bind END        "centerview"

bind ALT        "+strafe"

bind SHIFT      "+speed"



bind UPARROW    "+forward"

bind DOWNARROW  "+back"

bind LEFTARROW  "+left"

bind RIGHTARROW "+right"



bind w          "+forward"

bind s          "+back"

bind a          "+moveleft"

bind d          "+moveright"



bind TAB        "+scores"



bind t          "messagemode"

bind y          "messagemode2"



bind F1         "vote yes"

bind F2         "vote no"

bind F3         "join"

bind F4         "ready"

bind F5         "chase"

bind F6		"score"

bind F10        "menu_quit"

bind F12        "screenshot"



bind -		"sizedown"

bind =		"sizeup"



// Default cvar values for archived cvars

// (so that they are set before loading a map)



set cg_autoaction_demo "0"

set cg_autoaction_screenshot "0"

set cg_autoaction_spectator "0"

set cg_bloodTrail "10"

set cg_bloodTrailAlpha "1.0"

set cg_clientHUD "default"

set cg_crosshair "1"

set cg_crosshair_color "255 255 255"

set cg_crosshair_size "32"

set cg_crosshair_strong "2"

set cg_crosshair_strong_color "255 255 255"

set cg_crosshair_strong_size "32"

set cg_damage_blend "1"

set cg_damage_kick "0"

set cg_decals "1"

set cg_explosionsRing "1"

set cg_cartoonRockets "0"

set cg_forceMyTeamAlpha "0"

set cg_forceTeamPlayersTeamBeta "0"

set cg_gibs "1"

set cg_grenadeTrail "20"

set cg_grenadeTrailAlpha "0.5"

set cg_gun "1"

set cg_gun_fov "90"

set cg_gunbob "1"

set cg_gunx "0"

set cg_guny "0"

set cg_gunz "0"

set cg_handOffset "5"

set cg_laserBeamSubdivisions "10"

set cg_outlineItemsBlack "1"

set cg_outlineModels "1"

set cg_outlineWorld "0"

set cg_outlinePlayersBlack "0"

set cg_particles "1"

set cg_pickup_flash "1"

set cg_playerTrailsColor "0.0 1.0 0.0"

set cg_predictLaserBeam "1"

set cg_raceGhosts "0"

set cg_raceGhostsAlpha "0.25"

set cg_rocketFireTrail "90"

set cg_rocketTrail "40"

set cg_rocketTrailAlpha "0.35"

set cg_scoreboardFont "virtue_10"

set cg_scoreboardStats "1"

set cg_scoreboardWidthScale "1.0"

set cg_shadows "1"

set cg_showAwards "2"

set cg_showBloodTrail "1"

set cg_showFPS "0"

set cg_showhelp "1"

set cg_showHUD "1"

set cg_showObituaries "3"

set cg_showPickup "1"

set cg_showPlayerNames "1"

set cg_showPlayerNames_alpha "0.4"

set cg_showPlayerNames_xoffset "0"

set cg_showPlayerNames_yoffset "16"

set cg_showPlayerNames_zfar "824"

set cg_showPlayerTrails "0"

set cg_showPointedPlayer "1"

set cg_showPressedKeys "0"

set cg_showSpeed "0"

set cg_showTeamLocations "1"

set cg_showTimer "2"

set cg_showViewBlends "0"

set cg_showMiniMap "0"

set cg_simpleItems "0"

set cg_simpleItemsSize "12"

set cg_teamALPHAcolor "255 65 35"

set cg_teamALPHAmodel ""

set cg_teamALPHAskin "default"

set cg_teamBETAcolor "150 62 255"

set cg_teamBETAmodel ""

set cg_teamBETAskin "default"

set cg_teamDELTAcolor "255 220 0"

set cg_teamDELTAmodel ""

set cg_teamDELTAskin "default"

set cg_teamGAMMAcolor "0 255 0"

set cg_teamGAMMAmodel ""

set cg_teamGAMMAskin "default"

set cg_teamPLAYERScolor ""

set cg_teamPLAYERSmodel ""

set cg_teamPLAYERSskin "default"

set cg_viewSize "100"

set cg_voiceChats "1"

set cg_volume_announcer "1.0"

set cg_volume_effects "1.0"

set cg_volume_hitsound "1.0"

set cg_volume_players "1.0"

set cg_volume_voicechats "1.0"

set cg_weaponAutoswitch "2"

set cg_weaponFlashes "2"

set cg_weaponlist "1"

set cl_compresspackets "1"

set cl_demoavi_fps "25"

set cl_demoavi_scissor "0"

set cl_downloads "1"

set cl_downloads_from_web "1"

set cl_freelook "1"

set cl_maxfps "90"

set cl_pps "35"

set cl_run "1"

set cl_stereo "0"

set cl_stereo_separation "0.4"

set cl_synchusercmd "1"

set cl_ucmdFPS "62"

set cl_ucmdMaxResend "3"

set color ""

set con_drawNotify "1"

set con_fontSystemBig "virtue_16"

set con_fontSystemMedium "bitstream_12"

set con_fontSystemSmall "bitstream_10"

set con_notifytime "3"

set con_printText "1"

set fov "100"

set g_allow_falldamage "1"

set g_antilag "1"

set g_antilag_maxtimedelta "250"

set g_antilag_timenudge "0"

set g_autorecord "0"

set g_autorecord_maxdemos "0"

set g_ca_allow_selfdamage "0"

set g_ca_allow_teamdamage "0"

set g_ca_armor "150"

set g_ca_competitionmode "0"

set g_ca_health "100"

set g_ca_roundlimit "0"

set g_ca_strong_ammo "10 15 20 25 75 100 10"

set g_ca_weak_ammo "0 15 15 50 75 120 10"

set g_ca_weapons "16383 1535 8959 6399"

set g_challengers_queue "1"

set g_countdown_time "5"

set g_disable_vote_allow_falldamage "0"

set g_disable_vote_allow_teamdamage "0"

set g_disable_vote_allow_uneven "0"

set g_disable_vote_allready "0"

set g_disable_vote_ca_allow_selfdamage "0"

set g_disable_vote_ca_allow_teamdamage "0"

set g_disable_vote_ca_competitionmode "0"

set g_disable_vote_ca_roundlimit "0"

set g_disable_vote_challengers_queue "0"

set g_disable_vote_deadbody_filter "0"

set g_disable_vote_extended_time "0"

set g_disable_vote_gametype "0"

set g_disable_vote_kick "0"

set g_disable_vote_lock "0"

set g_disable_vote_map "0"

set g_disable_vote_maxteamplayers "0"

set g_disable_vote_maxteams "0"

set g_disable_vote_maxtimeouts "0"

set g_disable_vote_mute "0"

set g_disable_vote_nextmap "0"

set g_disable_vote_numbots "0"

set g_disable_vote_remove "0"

set g_disable_vote_restart "0"

set g_disable_vote_scorelimit "0"

set g_disable_vote_timein "0"

set g_disable_vote_timelimit "0"

set g_disable_vote_timeout "0"

set g_disable_vote_unlock "0"

set g_disable_vote_unmute "0"

set g_disable_vote_vmute "0"

set g_disable_vote_vunmute "0"

set g_disable_vote_warmup "0"

set g_disable_vote_warmup_timelimit "0"

set g_gametype "dm"

set g_instagib "0"

set g_maplist ""

set g_maprotation "1"

set g_match_extendedtime "2"

set g_maxteams "2"

set g_maxtimeouts "2"

set g_numbots "0"

set g_scorelimit "0"

set g_ctf_timer "0"

set g_teams_allow_uneven "1"

set g_teams_maxplayers "0"

set g_teams_teamdamage "1"

set g_timelimit "10"

set g_uploads_demos "1"

set g_votable_gametypes ""

set g_vote_allowed "1"

set g_vote_electtime "40"

set g_vote_percent "55"

set g_warmup_enabled "1"

set g_warmup_timelimit "5"

set g_itdm_capture_time "5"

set gl_delayfinish "1"

set gl_ext_bgra "1"

set gl_ext_compiled_vertex_array "1"

set gl_ext_generate_mipmap "1"

set gl_ext_draw_range_elements "1"

set gl_ext_depth_texture "1"

set gl_ext_fragment_shader "1"

set gl_ext_gamma_control "1"

set gl_ext_GLSL "1"

set gl_ext_GLSL_branching "1"

set gl_ext_GLSL_no_half_types "0"

set gl_ext_multitexture "1"

set gl_ext_occlusion_query "1"

set gl_ext_shader_objects "1"

set gl_ext_shading_language_100 "1"

set gl_ext_shadow "1"

set gl_ext_swap_control "1"

set gl_ext_texture3D "1"

set gl_ext_texture_compression "0"

set gl_ext_texture_cube_map "1"

set gl_ext_texture_edge_clamp "1"

set gl_ext_texture_env_add "1"

set gl_ext_texture_env_combine "1"

set gl_ext_texture_env_dot3 "1"

set gl_ext_texture_filter_anisotropic "0"

set gl_ext_texture_non_power_of_two "1"

set gl_ext_vertex_buffer_object "0"

set gl_ext_vertex_shader "1"

set gl_extensions "1"

set gl_finish "0"

set hand "0"

set in_grabinconsole "0"

set in_minmsecs "2"

set irc_nick "WarsowPlayer"

set irc_password ""

set irc_port "6667"

set irc_server "irc.quakenet.org"

set irc_user "WswPlayer"

set logconsole ""

set logconsole_append "1"

set logconsole_flush "0"

set logconsole_timestamp "0"

set lookspring "0"

set lookstrafe "0"

set m_accel "0"

set m_filter "1"

set m_filterStrength "0.5"

set m_forward "1"

set m_pitch "0.022"

set m_side "1"

set m_yaw "0.022"

set model "viciious"

set name "player"

set r_3dlabs_broken "1"

set r_bloom "0"

set r_bloom_alpha "0.2"

set r_bloom_darken "4"

set r_bloom_diamond_size "8"

set r_bloom_fast_sample "0"

set r_bloom_intensity "1.3"

set r_bloom_sample_size "320"

set r_bumpscale "1"

set r_clear "0"

set r_colorbits "0"

set r_detailtextures "1"

set r_dynamiclight "1"

set r_environment_color "0 0 0"

set r_faceplanecull "1"

set r_fastsky "0"

set r_flarefade "3"

set r_flares "0"

set r_flaresize "40"

set r_gamma "1.0"

set r_ignorehwgamma "0"

set r_lodbias "0"

set r_lodscale "5.0"

set r_mapoverbrightbits "2"

set r_maxLMBlockSize "1024"

set r_mode "4"

set r_overbrightbits "0"

set r_packlightmaps "1"

set r_picmip "0"

set r_screenshot_jpeg "1"

set r_screenshot_jpeg_quality "85"

set r_shadows_alpha "0.4"

set r_shadows_nudge "1"

set r_shadows_projection_distance "32"

set r_shadows_maxtexsize "512"

set r_shadows_pcf "0"

set r_shadows_self_shadow "0"

set r_skymip "0"

set r_stencilbits "8"

set r_subdivisions "4"

set r_swapinterval "0"

set r_texturebits "0"

set r_texturemode "GL_LINEAR_MIPMAP_LINEAR"

set r_portalmaps "1"

set r_portalmaps_maxtexsize "256"

set r_occlusion_queries "2"

set r_occlusion_queries_finish "1"

set r_outlines_world "1.8"

set r_outlines_scale "1"

set r_outlines_cutoff "712"

set r_lighting_bumpscale "8"

set r_lighting_deluxemapping "1"

set r_lighting_diffuse2heightmap "0"

set r_lighting_specular "1"

set r_lighting_glossintensity "2"

set r_lighting_glossexponent "48"

set r_lighting_models_followdeluxe "1"

set r_lighting_ambientscale "0.6"

set r_lighting_directedscale "1"

set r_lighting_packlightmaps "1"

set r_lighting_maxlmblocksize "1024"

set r_coronascale "0.2"

set s_module "1"

set s_musicvolume "0.8"

set s_volume "0.8"

set scr_consize "0.5"

set scr_conspeed "3"

set sensitivity "3"

set skin "default"

set sv_compresspackets "1"

set sv_hostname "warsow server"

set sv_ip ""

set sv_port "44400"

set sv_public "0"

set sv_pure "0"

set sv_reconnectlimit "3"

set sv_skilllevel "1"

set sv_uploads "1"

set sv_uploads_baseurl ""

set sv_uploads_from_server "1"

set vid_customheight "768"

set vid_customwidth "1024"

set vid_displayfrequency "0"

set vid_fullscreen "1"

set vid_xpos "3"

set vid_ypos "22"

set zoomfov "30"

set zoomsens "0"

```

---

### Post by Will Murray on 2009-05-23
Ok I have pretty much figured out how to resolve the initial issue, but how to I change permissions so that I can change these files?

---

### Post by CatKiller on 2009-05-23
> **Will Murray said:**
> I managed to find this config file, though I am unable to change anything. I get a permissions error if I try.

The file is in your Home folder. It's ~/.warsow/basewsw/config.cfg. You don't need special permissions to edit it. The values you're looking for are seta vid_customheight, seta vid_customwidth and seta vid_displayfrequency. Change them to whatever resolution you're actually using.

If you want to edit a file outside of your Home folder, you don't need to change its permissions. You just need to use [sudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by Will Murray on 2009-05-23
> **CatKiller said:**
> The file is in your Home folder. It's ~/.warsow/basewsw/config.cfg. 

I looked but the only relevant files I can find to the game are located at:
```

/usr/share/games/warsow/basewsw
```

---

### Post by DeMus on 2009-05-23
> **Will Murray said:**
> I looked but the only relevant files I can find to the game are located at:
```

/usr/share/games/warsow/basewsw
```

Did you enable hidden files in your home folder? Use ctrl-h to switch on the hidden ones and look again.

---

### Post by unutbu on 2009-05-23
Try```


gksu gedit /usr/share/games/warsow/basewsw
```

This will give you root privileges in the gedit text editor so you can modify /usr/share/games/warsow/basewsw.

---

### Post by Will Murray on 2009-05-23
^ this worked, but now the game will not launch. I typed warsow in terminal and got this:


```
Added pk3 file /usr/share/games/warsow/basewsw/billboard.pk3 (14 files)
Added pk3 file /usr/share/games/warsow/basewsw/data0.pk3 (749 files)
Added pk3 file /usr/share/games/warsow/basewsw/data0_pure.pk3 (893 files)
Added pk3 file /usr/share/games/warsow/basewsw/data1.pk3 (121 files)
Added pk3 file /usr/share/games/warsow/basewsw/data1_pure.pk3 (28 files)
Added pk3 file /usr/share/games/warsow/basewsw/editortextures.pk3 (17 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wamphi.pk3 (26 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wca1.pk3 (14 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wca2.pk3 (6 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wca4.pk3 (6 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf1.pk3 (6 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf2.pk3 (13 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf3.pk3 (4 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf5.pk3 (6 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wda1.pk3 (23 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wda2.pk3 (8 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wda3.pk3 (31 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wda4.pk3 (13 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wda5.pk3 (22 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wda6.pk3 (21 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm1.pk3 (14 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm10.pk3 (6 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm10a.pk3 (6 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm11.pk3 (6 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm14.pk3 (6 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm15.pk3 (14 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm17.pk3 (9 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm19.pk3 (25 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm2.pk3 (6 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm3.pk3 (14 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm4.pk3 (14 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm5.pk3 (6 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm6.pk3 (6 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm7.pk3 (45 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm8.pk3 (70 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm9.pk3 (6 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wtest13.pk3 (66 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wtest18.pk3 (11 files)
Added pk3 file /usr/share/games/warsow/basewsw/modules_04.pk3 (15 files)
Added pk3 file /usr/share/games/warsow/basewsw/modules_041.pk3 (15 files)
Added pk3 file /usr/share/games/warsow/basewsw/modules_042.pk3 (15 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_blx_pure.pk3 (320 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_blxbis_pure.pk3 (80 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_chaoswsw_pure.pk3 (76 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_ecel_pure.pk3 (109 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_exwsw_pure.pk3 (139 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_factory_pure.pk3 (56 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_hazelh_pure.pk3 (89 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_hexagons_pure.pk3 (26 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_refly_pure.pk3 (8 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_russus_pure.pk3 (16 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_supersymmetry_ctf_pure.pk3 (8 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_supersymmetry_pure.pk3 (9 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_terrain_pure.pk3 (6 files)
Using /home/will/.warsow for writing
Executing: default.cfg
Couldn't execute: config.cfg
Couldn't execute: autoexec.cfg
fs_basepath is write protected.
fs_usehomedir is write protected.
Hostname: will-desktop
IP: 127.0.1.1
Game running at 62 fps. Server transmit at 20 pps
Console initialized.
------- sound initialization -------
Loading sound module: qf
SDL Audio driver initializing...
Calling SDL_Init(SDL_INIT_AUDIO)...
SDL_Init(SDL_INIT_AUDIO) passed.
SDL audio driver is "alsa"
Format we requested from SDL audio device:
Format: AUDIO_S16LSB
Freq: 44100
Samples: 1024
Channels: 2

Format we actually got:
Format: AUDIO_S16LSB
Freq: 44100
Samples: 1024
Channels: 2

Starting SDL audio callback...
SDL audio initialized.
Sound sampling rate: 44100
Initialization of qf succesful
------------------------------------

----- R_Init -----
Using libGL.so.1 for OpenGL...Display initialization
..XFree86-VidMode Extension Version 2.2
..XFree86-Xinerama Extension Version 1.1
Xlib:  extension "GLX" missing on display ":0.0".
..Failed to get colorbits 24, depthbits 24, stencilbits 8
Xlib:  extension "GLX" missing on display ":0.0".
..Failed to get colorbits 16, depthbits 16, stencilbits 8
Xlib:  extension "GLX" missing on display ":0.0".
..Failed to get colorbits 24, depthbits 24, stencilbits 0
Xlib:  extension "GLX" missing on display ":0.0".
..Failed to get colorbits 16, depthbits 16, stencilbits 0
..Error couldn't set GLX visual
********************
ERROR: Failed to load libGL.so.1
********************
Error: Failed to load libGL.so.1

```

---

### Post by CatKiller on 2009-05-23
> **Will Murray said:**
> ^ this worked, but now the game will not launch. I typed warsow in terminal and got this:

It looks like you've got a couple of problems.

```

Executing: default.cfg
Couldn't execute: config.cfg
Couldn't execute: autoexec.cfg
fs_basepath is write protected.
fs_usehomedir is write protected.

```

Have you changed the permissions on your Home folder at all? This might be why you haven't got a ~/.warsow folder.

```

Using libGL.so.1 for OpenGL...Display initialization
..XFree86-VidMode Extension Version 2.2
..XFree86-Xinerama Extension Version 1.1
Xlib:  extension "GLX" missing on display ":0.0".
..Failed to get colorbits 24, depthbits 24, stencilbits 8
Xlib:  extension "GLX" missing on display ":0.0".
..Failed to get colorbits 16, depthbits 16, stencilbits 8
Xlib:  extension "GLX" missing on display ":0.0".
..Failed to get colorbits 24, depthbits 24, stencilbits 0
Xlib:  extension "GLX" missing on display ":0.0".
..Failed to get colorbits 16, depthbits 16, stencilbits 0
..Error couldn't set GLX visual
********************
ERROR: Failed to load libGL.so.1
********************
Error: Failed to load libGL.so.1

```

It looks like you haven't got a graphics driver that will do 3D properly installed. You'll need to sort that out to play this game. If you tell us what graphics card you've got, someone should hopefully be able to talk you through the process.

---

### Post by Will Murray on 2009-05-23
I do actually have the folder there, sorry for the confusion. It just doesn't have any cfg files in it.

I use a GeForce 8600GT, I have actually downloaded the driver for it (from the nvidia site) but I don't how to install it.

---

### Post by CatKiller on 2009-05-23
> **Will Murray said:**
> I use a GeForce 8600GT, I have actually downloaded the driver for it (from the nvidia site) but I don't how to install it.

You should be able to use the System -> Administration -> Hardware Drivers tool to install the driver for your card.

---

### Post by Will Murray on 2009-05-24
Ok I managed to install the drivers etc, but now I am back where I started. Input Signal out of Range.

The only improvement is, is that I can hear the in game music.

---

### Post by Will Murray on 2009-05-24
I have added a config.cfg with correct settings and an autoexec.cfg with correct settings in /home/will/.warsow/basewsw and still no luck.

I have also edited default.cfg in /usr/share/games/warsow/basewsw and nothing.

Only result is black screen (with game music playing in background) displaying:

Input Signal Out of Range, Change Settings to 1400x900 60Hz

And I need to restart to fix.

---

### Post by Aped on 2009-05-25
Odd that you would have to create the cfg files, makes me think that it sort of invalidates the procedure of editing them ;)

Can you kindly paste the output of 
$ ls -la ~/.warsaw

and let me know which if any of those files you created yourself ;)

---

### Post by Will Murray on 2009-05-25
```
total 44
drwxr-xr-x 8 will will 4096 2009-05-24 18:23 .
drwxr-xr-x 3 will will 4096 2009-05-23 15:00 ..
-rw-r--r-- 1 will will   84 2009-05-23 16:21 autoexec.cfg
-rw-r--r-- 1 will will   84 2009-05-24 01:01 config.cfg
-rw-r--r-- 1 will will  636 2009-05-24 17:04 mapcache.txt
drwxr-xr-x 2 will will 4096 2009-05-24 17:09 tempmodules2251
drwxr-xr-x 2 will will 4096 2009-05-24 17:06 tempmodules4648
drwxr-xr-x 2 will will 4096 2009-05-23 15:00 tempmodules521
drwxr-xr-x 2 will will 4096 2009-05-23 15:02 tempmodules742
drwxr-xr-x 2 will will 4096 2009-05-24 18:23 tempmodules7751
drwxr-xr-x 2 will will 4096 2009-05-23 15:37 tempmodules8984
```

I created config.cfg and autoexec.cfg

---

### Post by Aped on 2009-05-25
> **Will Murray said:**
> ```
total 44
drwxr-xr-x 8 will will 4096 2009-05-24 18:23 .
drwxr-xr-x 3 will will 4096 2009-05-23 15:00 ..
-rw-r--r-- 1 will will   84 2009-05-23 16:21 autoexec.cfg
-rw-r--r-- 1 will will   84 2009-05-24 01:01 config.cfg
-rw-r--r-- 1 will will  636 2009-05-24 17:04 mapcache.txt
drwxr-xr-x 2 will will 4096 2009-05-24 17:09 tempmodules2251
drwxr-xr-x 2 will will 4096 2009-05-24 17:06 tempmodules4648
drwxr-xr-x 2 will will 4096 2009-05-23 15:00 tempmodules521
drwxr-xr-x 2 will will 4096 2009-05-23 15:02 tempmodules742
drwxr-xr-x 2 will will 4096 2009-05-24 18:23 tempmodules7751
drwxr-xr-x 2 will will 4096 2009-05-23 15:37 tempmodules8984
```

I created config.cfg and autoexec.cfg

Are you running 9.04? If so, I hear there are a lot of graphical awfulnesses with it. Might want to swap back to 8.10. 

What was it that made you feel config.cfg and autoexec.cfg were the way to go? Are you sure that they are in the right place/are properly formatted? Syntax can be a biter in these things... 

Other than that, I'm out of ideas. Maybe one of the gurubuntus can help you out, but I'm stumpied.

---

### Post by Will Murray on 2009-05-26
I was told on the warsow community website that these were the files that controlled the resolution/refresh rates.

Is there any easy way of changing to 8.10 other than formatting?

---

### Post by Will Murray on 2009-05-26
Ahhh problem solved, a person on the warsow forums gave me a command to add to my configs which seems to have solved the problem.

in case anyone is curious:

```
r_mode -1
```

---

### Post by shortsightedPenguin on 2010-01-09
I get the black screen : Input Signal Out of Range Change Settings to 1440 x 900 - 60Hz

I do not have any games installed. It is my package upgrade from Jaunty, and after it installed successfully I now get the black screen with the above message each time I log in.

How should I resolve this, anyone?, please? Thanks a million.
:(

---

### Post by shortsightedPenguin on 2010-01-09
> **shortsightedPenguin said:**
> I get the black screen : Input Signal Out of Range Change Settings to 1440 x 900 - 60Hz

I do not have any games installed. It is my package upgrade from Jaunty, and after it installed successfully I now get the black screen with the above message each time I log in.

How should I resolve this, anyone?, please? Thanks a million.
:(

Hi.. I just don't want this thread to slip by. . :) as I'm still needing solution to this. I do not have additional software/games installed prior or after the package upgrade from Jaunty to Karmic. It happened since my first boot after installation and I am able to log-in, it will turn into black screen with the message, after a few seconds.

> 
Input Signal Out of Range Change Settings to 1440 x 900 - 60Hz


Has anyone workaround for this? ?

---

### Post by PinUpGeek on 2011-05-20
I am having the exact same problem right from the get go. Nothingbto do with any games but immediately from when I boot the computer. Suggestions?

---

