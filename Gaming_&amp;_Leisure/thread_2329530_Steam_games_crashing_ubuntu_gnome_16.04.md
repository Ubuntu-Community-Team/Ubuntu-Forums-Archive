---
title: "Steam games crashing ubuntu gnome 16.04"
date: 2016-07-02
forum: Gaming &amp; Leisure
---

### Post by module789 on 2016-07-02
I have steam installed with ubuntu gnome 16.04. When I play certain games my screen will glitch out, sound will often play back, and eventually everything will freeze up and I'll have to reboot. I've experienced this with stellaris, garry's mod, portal, tf2, and cs:go. But it happens by far the most with counterstrike global offensive. It doesn't happen every time I run the game, sometimes I'll go a few days and play it fine, but then it'll start crashing again for a few days and be ok after that. I suspect it might have something to do with the source engine.

I've removed the standalone steam runtime libraries with this script I have saved. I run this every once in a while to make sure steam isn't using outdated libraries, but it doesn't seem to help.
```

find $HOME/.steam/root/ubuntu12_32/steam-runtime/*/usr/lib/ -name "libstdc++.so.6" -exec mv "{}" "{}.bak" \; -print

```

I'm using a radeon r9 290 with the default drivers that ubuntu ships with. I experienced this with arch linux and couldn't figure out was wrong; I ended up moving to ubuntu for other reasons. Have other people with amd cards experienced this? Is this a hardware issue with my graphics card? Maybe not getting enough power? My power supply is 550 Watts so I think it should be fine.

Here is some information about my system to help with diagnosing the issue. If anyone could help I'd appreciate it.

$ lspci
```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
00:1c.2 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d0)
00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
00:1c.4 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 5 (rev d0)
00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family Z97 LPC Controller
00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii PRO [Radeon R9 290]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii HDMI Audio
03:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
06:00.0 USB controller: ASMedia Technology Inc. ASM1042A USB 3.0 Host Controller
```

here is a snippet of the system journal several minutes before a crash caused by counterstrike
```

Jul 02 13:17:01 saturn CRON[5774]: pam_unix(cron:session): session closed for user root
Jul 02 13:17:01 saturn CRON[5775]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 02 13:17:01 saturn CRON[5774]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 02 13:15:17 saturn gnome-session[1773]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Jul 02 13:13:53 saturn gnome-session[1773]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Jul 02 13:13:42 saturn gnome-session[1773]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Jul 02 13:13:40 saturn steam.desktop[26296]:  ##### swap interval = 0     swap limit = 1 #####
Jul 02 13:13:40 saturn steam.desktop[26296]: Failed to read the default inventory image file (materials/vgui/inventory_default.vtf)
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/knife_survival_bowie/knife_survival_bowie.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/knife_push/knife_push.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/knife_falchion_advanced/knife_falchion_advanced.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/pist_revolver/pist_revolver.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/snip_ssg08/snip_ssg08_scope.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/snip_ssg08/snip_ssg08.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/snip_scar20/snip_scar20.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/snip_g3sg1/snip_g3sg1.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/snip_awp/awp.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/smg_ump45/smg_ump45.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/smg_p90/smg_p90.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/smg_mp9/smg_mp9.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/smg_mp7/smg_mp7.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/smg_mac10/smg_mac10_1.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/smg_bizon/bizon.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/shot_xm1014/shot_xm1014.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/shot_sawedoff/shot_sawedoff_01.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/shot_nova/shot_nova.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/shot_mag7/shot_mag7.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/rif_sg556/rif_sg556.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/rif_m4a1_s/rif_m4a1_s.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/rif_m4a1/rif_m4a1.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/rif_galilar/rif_galilar.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/rif_famas/rif_famas.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/rif_aug/rif_aug.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/rif_ak47/ak47.vmt.
Jul 02 13:13:40 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/pist_tec9/pist_tec9.vmt.
Jul 02 13:13:36 saturn gnome-session[1773]: Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2000005 (Counter-St)
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/pist_p250/p250.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/pist_hkp2000/pist_hkp2000.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/pist_glock18/pist_glock18.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/pist_fiveseven/fiveseven.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/pist_elite/m9a1.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/pist_deagle/pist_deagle.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/pist_cz_75/pist_cz_75.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/pist_223/pist_223.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/mach_negev/mach_negev.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/mach_m249para/m249.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/knife_tactical/knife_tactical.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/knife_t/knife_t.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/knife_m9_bay/knife_m9_bay.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/knife_karam/karam.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/knife_gut/knife_gut.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/knife_flip/knife_flip.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/knife_ct/knife_ct.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/knife_bayonet/knife_bayonet.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: CustomMaterialManager: Cached KeyValues materials/models/weapons/v_models/knife_butterfly/knife_butterfly.vmt.
Jul 02 13:13:31 saturn steam.desktop[26296]: INTZ NOT SUPPORTED!
Jul 02 13:13:31 saturn steam.desktop[26296]: RESZ NOT SUPPORTED!
Jul 02 13:13:31 saturn steam.desktop[26296]: INTZ NOT SUPPORTED!
Jul 02 13:13:31 saturn steam.desktop[26296]: RESZ NOT SUPPORTED!
Jul 02 13:13:31 saturn steam.desktop[26296]: Did not detect any valid joysticks.
Jul 02 13:13:31 saturn steam.desktop[26296]: /home/nekro/.steam/steam/userdata/141964558/730/local
Jul 02 13:13:31 saturn steam.desktop[26296]: USRLOCAL path using Steam profile data folder:
Jul 02 13:13:31 saturn steam.desktop[26296]: Using breakpad minidump system 730/13540.345
Jul 02 13:13:31 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/localize_client.so error=/home/nekro/.steam/steam/steamapps/common/Cou
Jul 02 13:13:31 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/shaderapidx9_client.so error=/home/nekro/.steam/steam/steamapps/common
Jul 02 13:13:31 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/scaleformui_client.so error=/home/nekro/.steam/steam/steamapps/common/
Jul 02 13:13:31 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/vgui2_client.so error=/home/nekro/.steam/steam/steamapps/common/Counte
Jul 02 13:13:31 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/vguimatsurface_client.so error=/home/nekro/.steam/steam/steamapps/comm
Jul 02 13:13:31 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/vscript_client.so error=/home/nekro/.steam/steam/steamapps/common/Coun
Jul 02 13:13:31 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/soundemittersystem_client.so error=/home/nekro/.steam/steam/steamapps/
Jul 02 13:13:31 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/studiorender_client.so error=/home/nekro/.steam/steam/steamapps/common
Jul 02 13:13:25 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/datacache_client.so error=/home/nekro/.steam/steam/steamapps/common/Co
Jul 02 13:13:25 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/materialsystem_client.so error=/home/nekro/.steam/steam/steamapps/comm
Jul 02 13:13:25 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/vphysics_client.so error=/home/nekro/.steam/steam/steamapps/common/Cou
Jul 02 13:13:25 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/inputsystem_client.so error=/home/nekro/.steam/steam/steamapps/common/
Jul 02 13:13:25 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/filesystem_stdio_client.so error=/home/nekro/.steam/steam/steamapps/co
Jul 02 13:13:25 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/engine_client.so error=/home/nekro/.steam/steam/steamapps/common/Count
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GLX_EXT_swap_control_tear.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_buffer_storage.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ANGLE_texture_compression_dxt5.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ANGLE_texture_compression_dxt3.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_texture_compression_dxt1.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_texture_compression_s3tc.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ATI_meminfo.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_NVX_gpu_memory_info.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_texture_sRGB_decode.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_framebuffer_multisample_blit_scaled.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_AMD_pinned_memory.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_NV_bindless_texture.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_EXT_direct_state_access.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_debug_output.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_GREMEDY_string_marker.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_framebuffer_object.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_vertex_array_bgra.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_vertex_array_bgra.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_ARB_uniform_buffer.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_APPLE_client_storage.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_APPLE_texture_range.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_occlusion_query.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_vertex_buffer_object.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_map_buffer_range.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_APPLE_flush_buffer_range.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_EXT_bindable_uniform.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_draw_buffers2.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_sync.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_NV_fence.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_APPLE_fence.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_framebuffer_multisample.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_framebuffer_blit.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_framebuffer_object.
Jul 02 13:13:25 saturn steam.desktop[26296]: SDL failed to create GL compatibility profile (whichProfile=0!
Jul 02 13:13:25 saturn steam.desktop[26296]: SDL video target is 'x11'
Jul 02 13:12:17 saturn firefox.desktop[2583]: onWindowUnload@chrome://browser/content/downloads/indicator.js:484:5
Jul 02 13:12:17 saturn firefox.desktop[2583]: ensureTerminated@chrome://browser/content/downloads/indicator.js:234:5
Jul 02 13:12:17 saturn firefox.desktop[2583]: getIndicatorData@resource://app/modules/DownloadsCommon.jsm:253:9
Jul 02 13:12:17 saturn firefox.desktop[2583]: wrapper@chrome://privatetab/content/patcher.jsm:36:16
Jul 02 13:12:17 saturn firefox.desktop[2583]: before@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/nekro/.mozilla/firefox/odydn3k3.default/extensions/privateTab@infocatcher.xpi!/bootstrap.js:
Jul 02 13:12:17 saturn firefox.desktop[2583]: privateTab.isPrivateContent@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/nekro/.mozilla/firefox/odydn3k3.default/extensions/privateTab@infocatch
Jul 02 13:12:17 saturn firefox.desktop[2583]: privateTab.isPrivateWindow@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/nekro/.mozilla/firefox/odydn3k3.default/extensions/privateTab@infocatche
Jul 02 13:12:17 saturn firefox.desktop[2583]: pbu_isWindowPrivate@resource://gre/modules/PrivateBrowsingUtils.jsm:25:14
Jul 02 13:12:17 saturn firefox.desktop[2583]: WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).
Jul 02 13:12:14 saturn gnome-session[1773]: (gnome-shell:1966): Clutter-WARNING **: clutter_actor_raise Actor 'StWidget' is not in the same container as actor 'StWidget'
Jul 02 13:12:14 saturn gnome-session[1773]: (gnome-shell:1966): Clutter-WARNING **: clutter_actor_raise Actor 'StWidget' is not in the same container as actor 'StWidget'
Jul 02 13:12:14 saturn gnome-session[1773]: (gnome-shell:1966): Clutter-WARNING **: clutter_actor_raise Actor 'StWidget' is not in the same container as actor 'StWidget'
Jul 02 13:12:14 saturn gnome-session[1773]: (gnome-shell:1966): Clutter-WARNING **: clutter_actor_raise Actor 'StWidget' is not in the same container as actor 'StWidget'
Jul 02 13:12:14 saturn steam.desktop[26296]: STEAM_RUNTIME has been set by the user to: /home/nekro/.steam/ubuntu12_32/steam-runtime
Jul 02 13:12:14 saturn steam.desktop[26296]: Running Steam on ubuntu 16.04 64-bit
Jul 02 13:12:14 saturn gnome-session[1773]: (gnome-shell:1966): Clutter-WARNING **: clutter_actor_raise Actor 'StWidget' is not in the same container as actor 'StWidget'
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1110 +hsync -vsync (66.6 kHz e)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Printing DDC gathered Modelines:
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Using vrefresh ranges from config file
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): Using hsync ranges from config file
Jul 02 13:12:13 saturn /usr/lib/gdm3/gdm-x-session[1757]: (II) RADEON(0): EDID vendor "ACI", prod id 9364
Jul 02 13:12:02 saturn dleyna-server-service[31570]: dLeyna: Exit
Jul 02 13:11:57 saturn gnome-session[1773]: ** (gnome-shell:1966): CRITICAL **: cr_declaration_parse_list_from_buf: assertion 'parser' failed
Jul 02 13:11:57 saturn gnome-session[1773]: ** (gnome-shell:1966): CRITICAL **: cr_parser_new_from_buf: assertion 'a_buf && a_len' failed
Jul 02 13:11:53 saturn dleyna-renderer-service[31598]: dLeyna: Exit
Jul 02 13:11:52 saturn gnome-session[1773]: (gnome-software:2065): Gs-WARNING **: failed to call gs_plugin_refine on snappy: snapd returned status code 404: Not Found
Jul 02 13:11:52 saturn /usr/lib/snapd/snapd[866]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps/links 51.938µs 404
Jul 02 13:11:51 saturn /usr/lib/snapd/snapd[866]: daemon.go:181: DEBUG: uid=1000;@ GET /v2/snaps?q=kee 949.443809ms 200
Jul 02 13:11:51 saturn dleyna-renderer-service[31598]: Client :1.75 lost
Jul 02 13:11:51 saturn org.gnome.Photos[1770]: (gnome-photos:31371): GLib-GIO-CRITICAL **: g_file_icon_new: assertion 'G_IS_FILE (file)' failed
Jul 02 13:11:51 saturn org.gnome.Photos[1770]: (gnome-photos:31371): GLib-GIO-CRITICAL **: g_file_new_for_path: assertion 'path != NULL' failed
Jul 02 13:11:51 saturn org.gnome.Photos[1770]: (gnome-photos:31371): GLib-GIO-CRITICAL **: g_file_icon_new: assertion 'G_IS_FILE (file)' failed
Jul 02 13:11:51 saturn org.gnome.Photos[1770]: (gnome-photos:31371): GLib-GIO-CRITICAL **: g_file_new_for_path: assertion 'path != NULL' failed
Jul 02 13:11:51 saturn org.gnome.Photos[1770]: (gnome-photos:31371): GLib-GIO-CRITICAL **: g_file_icon_new: assertion 'G_IS_FILE (file)' failed
Jul 02 13:11:51 saturn org.gnome.Photos[1770]: (gnome-photos:31371): GLib-GIO-CRITICAL **: g_file_new_for_path: assertion 'path != NULL' failed
Jul 02 13:11:51 saturn /usr/lib/gdm3/gdm-x-session[1757]: Successfully activated service 'org.freedesktop.Tracker1.Miner.Extract'
Jul 02 13:11:51 saturn dleyna-renderer-service[31598]: Calling GetRenderers method
Jul 02 13:11:51 saturn /usr/lib/gdm3/gdm-x-session[1757]: Successfully activated service 'com.intel.dleyna-renderer'
Jul 02 13:13:31 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/shaderapidx9_client.so error=/home/nekro/.steam/steam/steamapps/common
Jul 02 13:13:31 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/scaleformui_client.so error=/home/nekro/.steam/steam/steamapps/common/
Jul 02 13:13:31 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/vgui2_client.so error=/home/nekro/.steam/steam/steamapps/common/Counte
Jul 02 13:13:31 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/vguimatsurface_client.so error=/home/nekro/.steam/steam/steamapps/comm
Jul 02 13:13:31 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/vscript_client.so error=/home/nekro/.steam/steam/steamapps/common/Coun
Jul 02 13:13:31 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/soundemittersystem_client.so error=/home/nekro/.steam/steam/steamapps/
Jul 02 13:13:31 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/studiorender_client.so error=/home/nekro/.steam/steam/steamapps/common
Jul 02 13:13:25 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/datacache_client.so error=/home/nekro/.steam/steam/steamapps/common/Co
Jul 02 13:13:25 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/materialsystem_client.so error=/home/nekro/.steam/steam/steamapps/comm
Jul 02 13:13:25 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/vphysics_client.so error=/home/nekro/.steam/steam/steamapps/common/Cou
Jul 02 13:13:25 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/inputsystem_client.so error=/home/nekro/.steam/steam/steamapps/common/
Jul 02 13:13:25 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/filesystem_stdio_client.so error=/home/nekro/.steam/steam/steamapps/co
Jul 02 13:13:25 saturn steam.desktop[26296]:  failed to dlopen /home/nekro/.steam/steam/steamapps/common/Counter-Strike Global Offensive/bin/engine_client.so error=/home/nekro/.steam/steam/steamapps/common/Count
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GLX_EXT_swap_control_tear.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_buffer_storage.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ANGLE_texture_compression_dxt5.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ANGLE_texture_compression_dxt3.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_texture_compression_dxt1.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_texture_compression_s3tc.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ATI_meminfo.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_NVX_gpu_memory_info.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_texture_sRGB_decode.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_framebuffer_multisample_blit_scaled.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_AMD_pinned_memory.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_NV_bindless_texture.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_EXT_direct_state_access.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_debug_output.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_GREMEDY_string_marker.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_framebuffer_object.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_vertex_array_bgra.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_vertex_array_bgra.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_ARB_uniform_buffer.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_APPLE_client_storage.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_APPLE_texture_range.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_occlusion_query.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_vertex_buffer_object.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_map_buffer_range.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_APPLE_flush_buffer_range.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_EXT_bindable_uniform.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_draw_buffers2.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_ARB_sync.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_NV_fence.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system DOES NOT support the OpenGL extension GL_APPLE_fence.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_framebuffer_multisample.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_framebuffer_blit.
Jul 02 13:13:25 saturn steam.desktop[26296]: This system supports the OpenGL extension GL_EXT_framebuffer_object.
Jul 02 13:13:25 saturn steam.desktop[26296]: SDL failed to create GL compatibility profile (whichProfile=0!
Jul 02 13:13:25 saturn steam.desktop[26296]: SDL video target is 'x11'

```

uname -r
```

4.4.0-28-generic

```

$ cat ~/.steam/error.log
```

rm: cannot remove '/home/nekro/.steam/steam': Is a directory
rm: cannot remove '/home/nekro/.steam/bin': Is a directory
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"

(steam:2735): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",

(steam:2735): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
/usr/share/themes/Arc-Darker/gtk-2.0/main.rc:1090: error: unexpected identifier `direction', expected character `}'
Installing breakpad exception handler for appid(steam)/version(1465948400)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
Created shared memory when not owner SteamController_Shared_mem
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
[0702/133740:ERROR:main_delegate.cc(779)] Could not load cef_extensions.pak
[0702/133740:ERROR:browser_main_loop.cc(217)] Running without the SUID sandbox! See https://chromium.googlesource.com/chromium/src/+/master/docs/linux_suid_sandbox_development.md for more information on developing with the sandbox on.
Installing breakpad exception handler for appid(steamwebhelper)/version(20160614232302)
Installing breakpad exception handler for appid(steamwebhelper)/version(1465946582)
[0702/133740:ERROR:main_delegate.cc(779)] Could not load cef_extensions.pak
Installing breakpad exception handler for appid(steamwebhelper)/version(20160614232302)
Installing breakpad exception handler for appid(steamwebhelper)/version(1465948400)
Installing breakpad exception handler for appid(steamwebhelper)/version(1465948400)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 72: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 80: saw unknown, expected number
Generating new string page texture 12: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 13: 256x256, total string texture memory is 311.30 KB
Generating new string page texture 14: 128x256, total string texture memory is 442.37 KB
Generating new string page texture 18: 64x256, total string texture memory is 507.90 KB
Generating new string page texture 21: 16x256, total string texture memory is 524.29 KB
Generating new string page texture 22: 24x256, total string texture memory is 548.86 KB
Generating new string page texture 23: 32x256, total string texture memory is 581.63 KB
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
local (potentially out of sync) copy of roaming config loaded - 3503 bytes.

(steam:2735): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2735): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2735): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2735): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2735): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2735): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2735): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2735): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2735): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
roaming config store loaded successfully - 3503 bytes.
migrating temporary roaming config store
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
Failed to init SteamVR because it isn't installed
ExecCommandLine: ""/home/nekro/.steam/ubuntu12_32/steam" "
Installing breakpad exception handler for appid(steam)/version(1465948400)
System startup time: 54.03 seconds
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
rm: cannot remove '/home/nekro/.steam/bin': Is a directory
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
/usr/bin/ldd: line 119: printf: write error: Broken pipe
Generating new string page texture 92: 128x256, total string texture memory is 131.07 KB
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
ExecCommandLine: "/home/nekro/.steam/root/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
ExecSteamURL: "steam://open/downloads"
Generating new string page texture 111: 256x256, total string texture memory is 843.78 KB
Generating new string page texture 112: 128x256, total string texture memory is 974.85 KB
Installing breakpad exception handler for appid(steam)/version(1465948400)
Installing breakpad exception handler for appid(steam)/version(1465948400)
Generating new string page texture 113: 128x256, total string texture memory is 1.11 MB
Generating new string page texture 114: 256x256, total string texture memory is 393.22 KB
Installing breakpad exception handler for appid(steam)/version(1465948400)

```

---

### Post by MikeCyber on 2016-07-03
did you use root? never use root unless you need. Remove all, also in your home the hidden .steam directory and start again.

---

### Post by $yl9pAR%t on 2016-07-03
Ubuntu 16.04 and AMD GPU is not the best choice for gamers. Perhaps this is your problem.

[https://lists.ubuntu.com/archives/ubuntu-doc/2016-March/019771.html](https://lists.ubuntu.com/archives/ubuntu-doc/2016-March/019771.html)

---

### Post by module789 on 2016-07-03
> did you use root? never use root unless you need. Remove all, also  in your home the hidden .steam directory and start again.

Did I use root for what?

---

### Post by module789 on 2016-07-03
> **mefisto888 said:**
> Ubuntu 16.04 and AMD GPU is not the best choice for gamers. Perhaps this is your problem.

[https://lists.ubuntu.com/archives/ubuntu-doc/2016-March/019771.html](https://lists.ubuntu.com/archives/ubuntu-doc/2016-March/019771.html)

I know ubuntu 16.04 can't use catalyst drivers but from what I understand it's mostly a quality problem not a functional problem. I don't want to wipe my install and switch to 14.04 but if there's no other choice I guess I can try.

---

