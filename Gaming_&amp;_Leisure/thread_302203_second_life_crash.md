---
title: "second life crash"
date: 2006-11-18
forum: Gaming &amp; Leisure
---

### Post by suoko on 2006-11-18
Hi,

I was trying the beta client for linux of second life.

The game starts but as soon as I try to move my player, X crashes and I see as gdm tries to restart forever.
Then I have to press ALT+F1 and, although I cannot see the console, reboot the PC with Ctrl+Alt+Del.

I have edgy and an Intel 945 video card (I disabled beryl)

---

### Post by madmetal on 2006-11-18
second life client has a lot of bugs..
are you ok with 3D acceleration?

---

### Post by Perfect Storm on 2006-11-18
The 3D requirement is minimum: nVidia GeForce FX 5600, GeForce 6600 or better (according to their site.), so it might be the problem.

---

### Post by suoko on 2006-11-18
I have 3d and it works under windows

---

### Post by seanmiller on 2006-11-20
In the shell script "secondlife" (in the main directory) you need to uncomment the line "export LL_GL_NOEXT=x" and then you should be fine.

All the best,

Sean

---

### Post by madmetal on 2006-11-20
> **Artificial Intelligence said:**
> The 3D requirement is minimum: nVidia GeForce FX 5600, GeForce 6600 or better (according to their site.), so it might be the problem.

i have no problems with a FX5500 :D

---

### Post by madmetal on 2006-11-20
> **suoko said:**
> I have 3d and it works under windows

have you drivers installed on ubuntu?
run 
 glxinfo | grep direct 
at a terminal and if the anwser is yes then you are ok with 3d!

---

### Post by Mickeysofine1972 on 2006-11-20
Just thought i'd chip in

I run this on ubuntu 6.10 + 1.4Ghz AMD + 512Ram + GF4 MX 440

And it runs just fine!

sometimes i wonder who thinks up the specs for the software anyhoo

Mike

---

### Post by suoko on 2006-11-21
> **seanmiller said:**
> In the shell script "secondlife" (in the main directory) you need to uncomment the line "export LL_GL_NOEXT=x" and then you should be fine.

All the best,

Sean

Many thanks for the tip. Now it works although in window-mode only.

G.

---

### Post by Skerit on 2006-12-01
I get that crappy window creation failure thing... My xorg file is such a mess I don't even want to attempt anything, every 3D thing needed is activated but it still won't work. Ah well...

---

### Post by darkteckno on 2006-12-08
How do I go about installing it? I'm a complete noob!

---

### Post by gummibaerchen on 2007-01-18
> **darkteckno said:**
> How do I go about installing it? I'm a complete noob!

"I'm a complete noob!" helps no one.

Just download the package, untar it, and run with ./secondlife

---

### Post by NULL712 on 2007-06-16
How do I go about uninstalling second life. I got it from getdeb.net tried useing apt-get remove secondlife but that didn't work. any ideas?

Thanx.

---

### Post by kurotenshi on 2008-09-21
Hi, I've just recently decided to try Second Life.
After I log in, my character appears but before I do anything the client crashes. Nothing else complains, just the client.

I'm running Ubuntu Hardy and I've installed with the package from getdeb.

```
2008-09-22T01:05:30Z INFO: (anonymous namespace)::LogControlFile::loadFile: logging reconfigured from /home/carlos/Área de Trabalho/SecondLife_i686_1_20_15_92456/app_settings/logcontrol.xml
2008-09-22T01:05:30Z INFO: initConfiguration: Loading settings file list/home/carlos/Área de Trabalho/SecondLife_i686_1_20_15_92456/app_settings/settings_files.xml
2008-09-22T01:05:30Z INFO: loadSettingsFromDirectory: Loaded settings file /home/carlos/Área de Trabalho/SecondLife_i686_1_20_15_92456/app_settings/settings_crash_behavior.xml
2008-09-22T01:05:30Z INFO: loadSettingsFromDirectory: Loaded settings file /home/carlos/Área de Trabalho/SecondLife_i686_1_20_15_92456/app_settings/settings.xml
2008-09-22T01:05:30Z INFO: loadSettingsFromDirectory: Loaded settings file /home/carlos/Área de Trabalho/SecondLife_i686_1_20_15_92456/app_settings/settings_per_account.xml
2008-09-22T01:05:30Z INFO: loadSettingsFromDirectory: Loaded settings file /home/carlos/.secondlife/user_settings/settings_crash_behavior.xml
2008-09-22T01:05:30Z INFO: loadSettingsFromDirectory: Loaded settings file /home/carlos/.secondlife/user_settings/settings.xml
2008-09-22T01:05:30Z WARNING: loadFromFile: Cannot find file /home/carlos/.secondlife/user_settings/settings_per_account.xml to load.
2008-09-22T01:05:30Z WARNING: loadSettingsFromDirectory: Cannot load /home/carlos/.secondlife/user_settings/settings_per_account.xml - No settings found.
2008-09-22T01:05:30Z INFO: getFontListSans: Getting system font list from FontConfig...
2008-09-22T01:05:30Z INFO: getFontListSans: Preferring fonts of language: pt
2008-09-22T01:05:30Z INFO: getFontListSans: Using 47 system font(s).
2008-09-22T01:05:30Z WARNING: ll_apr_warn_status: ONCE: APR: No such file or directory
2008-09-22T01:05:30Z INFO: writeSystemInfo: Second Life version 1.20.15
2008-09-22T01:05:30Z INFO: writeSystemInfo: Local time: 2008-09-22T02:05:30 WEST
2008-09-22T01:05:30Z INFO: writeSystemInfo: CPU info:
processor	: 0 vendor_id	: GenuineIntel cpu family	: 6 model	: 15 model name	: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping	: 11 cpu MHz		: 2201.000 cache size	: 4096 KB physical id	: 0 siblings	: 2 core id		: 0 cpu cores	: 2 fdiv_bug	: no hlt_bug	: no f00f_bug	: no coma_bug	: no fpu		: yes fpu_exception	: yes cpuid level	: 10 wp		: yes flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida bogomips	: 4393.68 clflush size	: 64  processor	: 1 vendor_id	: GenuineIntel cpu family	: 6 model	: 15 model name	: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping	: 11 cpu MHz		: 2201.000 cache size	: 4096 KB physical id	: 0 siblings	: 2 core id		: 1 cpu cores	: 2 fdiv_bug	: no hlt_bug	: no f00f_bug	: no coma_bug	: no fpu		: yes fpu_exception	: yes cpuid level	: 10 wp		: yes flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida bogomips	: 4388.97 clflush size	: 64  
->mHasSSE:     1
->mHasSSE2:    1
->mHasAltivec: 0
->mCPUMhz:     2201
->mCPUString:  Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz

2008-09-22T01:05:30Z INFO: writeSystemInfo: Memory info:
MemTotal:      2074520 kB MemFree:        236808 kB Buffers:         36916 kB Cached:        1149364 kB SwapCached:          0 kB Active:         851152 kB Inactive:       668836 kB HighTotal:     1178432 kB HighFree:         1624 kB LowTotal:       896088 kB LowFree:        235184 kB SwapTotal:           0 kB SwapFree:            0 kB Dirty:            1908 kB Writeback:           0 kB AnonPages:      333704 kB Mapped:         124696 kB Slab:            36600 kB SReclaimable:    24068 kB SUnreclaim:      12532 kB PageTables:       2744 kB NFS_Unstable:        0 kB Bounce:              0 kB CommitLimit:   1037260 kB Committed_AS:   889740 kB VmallocTotal:   114680 kB VmallocUsed:     27568 kB VmallocChunk:    86624 kB 
2008-09-22T01:05:30Z INFO: writeSystemInfo: OS: Linux 2.6
2008-09-22T01:05:30Z INFO: writeSystemInfo: OS info: Linux 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686
2008-09-22T01:05:30Z INFO: writeDebugInfo: Opening debug file /home/carlos/.secondlife/logs/debug_info.log
2008-09-22T01:05:30Z INFO: updateVectorize: Vectorization         : DISABLED
2008-09-22T01:05:30Z INFO: updateVectorize: Vector Processor      : COMPILER DEFAULT
2008-09-22T01:05:30Z INFO: updateVectorize: Vectorized Skinning   : DISABLED
2008-09-22T01:05:30Z INFO: initCache: Headers: 139810 Textures size: 320 MB
2008-09-22T01:05:30Z INFO: purgeTextures: TEXTURE CACHE: PURGED: 0 ENTRIES: 43 CACHE SIZE: 794624 MB
2008-09-22T01:05:30Z INFO: initCache: VFS CACHE SIZE: 100 MB
2008-09-22T01:05:30Z WARNING: LLVFS: Using index file /home/carlos/.secondlife/cache/index.db2.x.81897508
2008-09-22T01:05:30Z WARNING: LLVFS: Using data file /home/carlos/.secondlife/cache/data.db2.x.81897508
2008-09-22T01:05:30Z WARNING: LLVFS: Using index file /home/carlos/Área de Trabalho/SecondLife_i686_1_20_15_92456/app_settings/static_index.db2
2008-09-22T01:05:30Z WARNING: LLVFS: Using data file /home/carlos/Área de Trabalho/SecondLife_i686_1_20_15_92456/app_settings/static_data.db2
2008-09-22T01:05:30Z INFO: initWindow: Initializing window...
2008-09-22T01:05:30Z INFO: ll_try_gtk_init: Starting GTK Initialization.
2008-09-22T01:05:30Z INFO: ll_try_gtk_init: GTK Initialized.
2008-09-22T01:05:30Z INFO: ll_try_gtk_init: - Compiled against GTK version 2.4.14
2008-09-22T01:05:30Z INFO: ll_try_gtk_init: - Running against GTK version 2.12.9
2008-09-22T01:05:30Z INFO: createContext, fullscreen=0 size=1000x700
2008-09-22T01:05:30Z INFO: createContext: Compiled against SDL 1.2.5
2008-09-22T01:05:30Z INFO: createContext:  Running against SDL 1.2.12
2008-09-22T01:05:30Z INFO: createContext: creating window 1000x700x32
2008-09-22T01:05:30Z INFO: x11_detect_VRAM_kb: Looking in /var/log/Xorg.0.log for VRAM info...
2008-09-22T01:05:30Z INFO: createContext: GL buffer:
2008-09-22T01:05:30Z INFO: createContext:   Red Bits 8
2008-09-22T01:05:30Z INFO: createContext:   Green Bits 8
2008-09-22T01:05:30Z INFO: createContext:   Blue Bits 8
2008-09-22T01:05:30Z INFO: createContext:   Alpha Bits 8
2008-09-22T01:05:30Z INFO: createContext:   Depth Bits 24
2008-09-22T01:05:30Z INFO: createContext:   Stencil Bits 8
2008-09-22T01:05:30Z WARNING: initExtensions: GL extension support DISABLED via LL_GL_NOEXT
2008-09-22T01:05:30Z INFO: initExtensions: Couldn't initialize mipmap generation
2008-09-22T01:05:30Z INFO: initExtensions: Couldn't initialize GL_ARB_texture_env_combine
2008-09-22T01:05:30Z INFO: initExtensions: Couldn't initialize GL_EXT_paletted_texture
2008-09-22T01:05:30Z INFO: initExtensions: Couldn't initialize separate specular color
2008-09-22T01:05:30Z INFO: initExtensions: Couldn't initialize anisotropic filtering
2008-09-22T01:05:30Z INFO: initExtensions: Couldn't initialize GL_ARB_texture_compression
2008-09-22T01:05:30Z INFO: initExtensions: Couldn't initialize GL_ARB_occlusion_query
2008-09-22T01:05:30Z INFO: initExtensions: Couldn't initialize GL_ARB_point_parameters
2008-09-22T01:05:30Z INFO: initExtensions: Couldn't initialize GL_ARB_shader_objects
2008-09-22T01:05:30Z INFO: initExtensions: Couldn't initialize GL_ARB_vertex_shader
2008-09-22T01:05:30Z INFO: initExtensions: Couldn't initialize GL_ARB_fragment_shader
2008-09-22T01:05:31Z INFO: loadGPUClass: GPU is ATI Mobility Radeon
2008-09-22T01:05:31Z INFO: applyBaseMasks: Setting GPU Class to Class0
2008-09-22T01:05:31Z WARNING: LLViewerImageList::getMaxVideoRamSetting: VRAM amount not detected, defaulting to 128 MB
2008-09-22T01:05:31Z WARNING: LLViewerImageList::getMaxVideoRamSetting: VRAM amount not detected, defaulting to 512 MB
2008-09-22T01:05:31Z INFO: LLViewerImageList::updateMaxResidentTexMem: Total Video Memory set to: 128 MB
2008-09-22T01:05:31Z INFO: LLViewerImageList::updateMaxResidentTexMem: Available Texture Memory set to: 96 MB
2008-09-22T01:05:31Z INFO: saveToFile: Saved to /home/carlos/.secondlife/user_settings/settings.xml
2008-09-22T01:05:31Z INFO: setShaders: 
~~~~~~~~~~~~~~~~~~
 Loading Shaders:
~~~~~~~~~~~~~~~~~~
2008-09-22T01:05:31Z INFO: saveToFile: Saved to /home/carlos/.secondlife/user_settings/settings.xml
2008-09-22T01:05:31Z INFO: printGLInfoString: GL_VENDOR:     ATI Technologies Inc.
2008-09-22T01:05:31Z INFO: printGLInfoString: GL_RENDERER:   ATI Mobility Radeon HD 2600
2008-09-22T01:05:31Z INFO: printGLInfoString: GL_VERSION:    2.1.7873 Release
2008-09-22T01:05:31Z INFO: LLTemplateParser: ### Message template version 2  ###
2008-09-22T01:05:31Z INFO: start_net: startNet - receive buffer size : 262142
2008-09-22T01:05:31Z INFO: start_net: startNet - send buffer size    : 262142
2008-09-22T01:05:31Z INFO: setStartupState: Startup state changing from 0 to 1
grab_gst_syms:81: Found DSO: libgstreamer-0.10.so.0
grab_gst_syms:94: Found DSO: libgstaudio-0.10.so.0
grab_gst_syms:108: Found DSO: libgstvideo-0.10.so.0
2008-09-22T01:05:32Z INFO: updateBrowserUserAgent: SecondLife/1.20.15.92456 (Second Life Release; default skin)
2008-09-22T01:05:32Z INFO: setStartupState: Startup state changing from 1 to 2
2008-09-22T01:05:32Z INFO: login_show: Initializing Login Screen
2008-09-22T01:05:32Z INFO: setStartupState: Startup state changing from 2 to 3
2008-09-22T01:05:32Z WARNING: getChild: Found child named Say but of wrong type
2008-09-22T01:05:32Z WARNING: createDummyWidget: Making dummy button named Say in chat_bar
2008-09-22T01:05:32Z WARNING: createDummyWidget: Making dummy button named end_call_btn in voice_remote
2008-09-22T01:05:32Z WARNING: createDummyWidget: Making dummy text named channel_label in voice_remote
2008-09-22T01:05:32Z WARNING: createDummyWidget: Making dummy button named voice_channel_bg in voice_remote
2008-09-22T01:05:32Z WARNING: createDummyWidget: Making dummy button named appearance_btn in toolbar
2008-09-22T01:05:32Z WARNING: createDummyWidget: Making dummy button named clothing_btn in toolbar
2008-09-22T01:05:32Z WARNING: createDummyWidget: Making dummy button named sit_btn in toolbar
2008-09-22T01:05:32Z WARNING: createDummyWidget: Making dummy button named History in chat_panel
2008-09-22T01:05:32Z WARNING: createDummyWidget: Making dummy combo_box named Gesture in chat_panel
2008-09-22T01:05:32Z WARNING: getChild: Found child named Say but of wrong type
2008-09-22T01:05:32Z WARNING: createDummyWidget: Making dummy button named Say in chat_panel
2008-09-22T01:05:32Z WARNING: createDummyWidget: Making dummy button named Chat in chat floater
2008-09-22T01:05:32Z INFO: startNextTransfer: Getting asset data for: c80260ba-41fd-8a46-768a-6bf236360e3a
2008-09-22T01:05:32Z WARNING: _queueDataRequest: Attempt to move asset data request upstream w/o valid upstream provider
2008-09-22T01:05:32Z INFO: assetCallback: Boom, error in audio file transfer: Circuit gone (-23017)
2008-09-22T01:05:32Z WARNING: createDummyWidget: Making dummy view named Menu Object Take in Menu Holder
2008-09-22T01:05:35Z WARNING: createDummyWidget: Making dummy view named bandwidth_tooltip in status
2008-09-22T01:05:35Z WARNING: createDummyWidget: Making dummy view named packet_loss_tooltip in status
2008-09-22T01:05:35Z WARNING: createDummyWidget: Making dummy view named friend_name_label in friends
2008-09-22T01:05:35Z WARNING: createDummyWidget: Making dummy view named friend_rights in friends
2008-09-22T01:05:35Z WARNING: createDummyWidget: Making dummy text named process_rights_label in friends
2008-09-22T01:05:35Z WARNING: createDummyWidget: Making dummy view named Shout in chat_bar
2008-09-22T01:05:36Z INFO: startNextTransfer: Getting asset data for: 4c8c3c77-de8d-bde2-b9b8-32635e0fd4a6
2008-09-22T01:05:36Z WARNING: _queueDataRequest: Attempt to move asset data request upstream w/o valid upstream provider
2008-09-22T01:05:36Z INFO: assetCallback: Boom, error in audio file transfer: Circuit gone (-23017)
2008-09-22T01:05:36Z INFO: setStartupState: Startup state changing from 3 to 4
2008-09-22T01:05:36Z INFO: idle_startup: Attempting login as: Kurotenshi Fhang
2008-09-22T01:05:36Z WARNING: loadFromFile: Cannot find file /home/carlos/.secondlife/kurotenshi_fhang/settings_crash_behavior.xml to load.
2008-09-22T01:05:36Z WARNING: loadSettingsFromDirectory: Cannot load /home/carlos/.secondlife/kurotenshi_fhang/settings_crash_behavior.xml - No settings found.
2008-09-22T01:05:36Z WARNING: loadFromFile: Cannot find file /home/carlos/.secondlife/kurotenshi_fhang/settings.xml to load.
2008-09-22T01:05:36Z WARNING: loadSettingsFromDirectory: Cannot load /home/carlos/.secondlife/kurotenshi_fhang/settings.xml - No settings found.
2008-09-22T01:05:36Z INFO: loadSettingsFromDirectory: Loaded settings file /home/carlos/.secondlife/kurotenshi_fhang/settings_per_account.xml
2008-09-22T01:05:36Z INFO: loadFile: Loading history.xml file at url_history.xml
2008-09-22T01:05:36Z INFO: loadFile: file missing, ill-formed, or simply undefined; not changing the file
2008-09-22T01:05:36Z WARNING: setLastError: Unable to open file for reading FILE:/home/carlos/.secondlife/kurotenshi_fhang/screen_home.bmp
2008-09-22T01:05:36Z WARNING: init_start_screen: Bitmap load failed
2008-09-22T01:05:36Z INFO: setStartupState: Startup state changing from 4 to 6
2008-09-22T01:05:37Z INFO: rewriteResult: [0] https://login.agni.lindenlab.com/cgi-bin/login.cgi
2008-09-22T01:05:37Z INFO: setStartupState: Startup state changing from 6 to 7
2008-09-22T01:05:37Z INFO: authenticate: Authenticating: Kurotenshi Fhang, 
2008-09-22T01:05:37Z INFO: authenticate: Options: inventory-root, inventory-skeleton, inventory-lib-root, inventory-lib-owner, inventory-skel-lib, initial-outfit, gestures, event_categories, event_notifications, classified_categories, buddy-list, ui-config, tutorial_setting, login-flags, global-textures, END
2008-09-22T01:05:37Z INFO: LLUserAuth::authenticate: uri=https://login.agni.lindenlab.com/cgi-bin/login.cgi
2008-09-22T01:05:37Z INFO: setStartupState: Startup state changing from 7 to 8
2008-09-22T01:05:41Z INFO: setStartupState: Startup state changing from 8 to 9
2008-09-22T01:05:41Z INFO: transferRate: Buffer size:   60294 B
2008-09-22T01:05:41Z INFO: transferRate: Transfer rate: 14.056 Kb/s
2008-09-22T01:05:41Z INFO: authResponse: Processed response: 0
2008-09-22T01:05:41Z INFO: setStartupState: Startup state changing from 9 to 10
2008-09-22T01:05:42Z INFO: LLCircuit::addCircuitData for 8.10.147.253:13001
2008-09-22T01:05:42Z INFO: setStartupState: Startup state changing from 10 to 11
2008-09-22T01:05:42Z INFO: LLVoiceClient::userAuthorized: name "Kurotenshi Fhang" , ID 91d20356-424e-4095-acb6-22af245cd80f
2008-09-22T01:05:42Z INFO: saveToFile: Saved to /home/carlos/.secondlife/user_settings/settings.xml
2008-09-22T01:05:42Z INFO: loadPresets: Loading WindLight settings from /home/carlos/Área de Trabalho/SecondLife_i686_1_20_15_92456/app_settings/windlight/skies/
2008-09-22T01:05:42Z INFO: loadDayCycle: Loading DayCycle settings from /home/carlos/Área de Trabalho/SecondLife_i686_1_20_15_92456/app_settings/windlight/days/Default.xml
2008-09-22T01:05:42Z INFO: loadAllPresets: Loading water settings from /home/carlos/Área de Trabalho/SecondLife_i686_1_20_15_92456/app_settings/windlight/water/
2008-09-22T01:05:42Z INFO: initVOClasses: Viewer Object size: 436
2008-09-22T01:05:42Z INFO: addRegion: Adding new region (1026:1051)
2008-09-22T01:05:42Z INFO: addRegion: Host: 8.10.147.253:13001
2008-09-22T01:05:42Z INFO: idle_startup: Adding initial simulator { 262656, 269056, 0 }
2008-09-22T01:05:42Z INFO: setStartupState: Startup state changing from 11 to 12
2008-09-22T01:05:42Z INFO: setSeedCapability: posting to seed https://sim7760.agni.lindenlab.com:12043/cap/4b4f9d96-41c8-d3be-0caf-17277ec67f83
2008-09-22T01:05:42Z INFO: LLAgent::setRegion: Moving agent into region:  located at 8.10.147.253:13001
2008-09-22T01:05:43Z INFO: LLEventPollResponder: LLEventPoll initialized with sender 8.10.147.253:13001
2008-09-22T01:05:43Z INFO: LLEventPollResponder::start <1> https://sim7760.agni.lindenlab.com:12043/cap/f8b33c53-dde3-7e21-3dba-276491cd71dc
2008-09-22T01:05:43Z INFO: LLHTTPSender::setSender 8.10.147.253:13001
2008-09-22T01:05:43Z INFO: setStartupState: Startup state changing from 12 to 13
2008-09-22T01:05:43Z INFO: idle_startup: Initializing communications...
2008-09-22T01:05:43Z WARNING: createDummyWidget: Making dummy icon named voice_channel_icon in voice_remote
2008-09-22T01:05:43Z INFO: LLDrawPoolWLSky: loading WindLight cloud noise from /home/carlos/Área de Trabalho/SecondLife_i686_1_20_15_92456/app_settings/windlight/clouds2.tga
2008-09-22T01:05:43Z WARNING: doRead: Unrecognized file extension es/ for local texture /home/carlos/Área de Trabalho/SecondLife_i686_1_20_15_92456/skins/default/textures/
2008-09-22T01:05:44Z WARNING: LLViewerImage::setIsMissingAsset: /home/carlos/Área de Trabalho/SecondLife_i686_1_20_15_92456/skins/default/textures/ 5c65e791-d18a-5ec5-d0cc-ad8f0d0f9cee: Marking image as missing
2008-09-22T01:05:44Z INFO: setStartupState: Startup state changing from 13 to 14
2008-09-22T01:05:44Z INFO: idle_startup: viewer: UserLoginLocationReply() Enabling 8.10.147.253:13001 with code 490783741
2008-09-22T01:05:44Z INFO: setStartupState: Startup state changing from 14 to 15
2008-09-22T01:05:44Z INFO: setStartupState: Startup state changing from 15 to 16
2008-09-22T01:05:45Z WARNING: process_agent_movement_complete: agent_movement_complete() with NULL avatarp.
2008-09-22T01:05:45Z INFO: process_agent_movement_complete: Changing home region to 262656:269056
2008-09-22T01:05:45Z INFO: sendToSim: Sending throttle settings, total BW 750
2008-09-22T01:05:45Z INFO: setStartupState: Startup state changing from 16 to 17
2008-09-22T01:05:45Z INFO: LLVoiceClient::parcelChanged: not logged in yet, deferring
2008-09-22T01:05:45Z INFO: LLInventoryModel::loadFromFile(/home/carlos/.secondlife/cache/ba2a564a-f0f1-4b82-9c61-b7520bfcd09f.inv)
2008-09-22T01:05:45Z INFO: loadFromFile: unable to load inventory from: /home/carlos/.secondlife/cache/ba2a564a-f0f1-4b82-9c61-b7520bfcd09f.inv
2008-09-22T01:05:45Z INFO: loadSkeleton: Successfully loaded 0 categories and 0 items from cache.
2008-09-22T01:05:45Z INFO: LLInventoryModel::loadFromFile(/home/carlos/.secondlife/cache/91d20356-424e-4095-acb6-22af245cd80f.inv)
2008-09-22T01:05:45Z INFO: loadFromFile: unable to load inventory from: /home/carlos/.secondlife/cache/91d20356-424e-4095-acb6-22af245cd80f.inv
2008-09-22T01:05:45Z INFO: loadSkeleton: Successfully loaded 0 categories and 0 items from cache.
2008-09-22T01:05:45Z INFO: LLInventoryModel::buildParentChildMap()
2008-09-22T01:05:45Z INFO: fetchDescendents: FetchInventoryDescendents capability not found.  Using deprecated UDP message.
2008-09-22T01:05:45Z INFO: LLInventoryView::init: reading from 0xbf8513d0
2008-09-22T01:05:45Z INFO: setStartupState: Startup state changing from 17 to 18
2008-09-22T01:05:45Z WARNING: createXml: Alert: [AvatarMoved] 
2008-09-22T01:05:45Z WARNING: createDialog: Alert: Sua home localização atual é inválida. You may want to set a new home location. Você será movido a uma região próxima.
2008-09-22T01:05:45Z INFO: setStartupState: Startup state changing from 18 to 19
2008-09-22T01:05:45Z INFO: idle: Transmitting sessions stats
2008-09-22T01:05:45Z INFO: addToMessage: STAT: Version: 0
2008-09-22T01:05:45Z INFO: addToMessage: STAT: Vertex Buffers Enabled: 0
2008-09-22T01:05:45Z INFO: process_money_balance_reply: L$, credit, committed: 0 0 0
2008-09-22T01:05:46Z INFO: LLAgent::sendAgentSetAppearance: TAT: Sent AgentSetAppearance: HEAD UPPER LOWER EYES
2008-09-22T01:05:46Z INFO: LLAgent::sendAgentSetAppearance: TAT: Sending cached texture data
2008-09-22T01:05:51Z INFO: setStartupState: Startup state changing from 19 to 20
2008-09-22T01:05:51Z INFO: setStartupState: Startup state changing from 20 to 21
2008-09-22T01:05:51Z INFO: setStartupState: Startup state changing from 21 to 22
2008-09-22T01:05:51Z INFO: idle_startup: Doing first audio_update_volume...
2008-09-22T01:05:51Z INFO: idle_startup: Done first audio_update_volume.
2008-09-22T01:05:51Z INFO: updateGeometry: WL Skydome strips in 3 batches.
2008-09-22T01:05:54Z INFO: startNextTransfer: Getting asset data for: 1294e5fa-7443-a73c-a3a5-e3a248fdeb9e
2008-09-22T01:05:54Z INFO: _queueDataRequest: Starting transfer for 1294e5fa-7443-a73c-a3a5-e3a248fdeb9e
2008-09-22T01:05:55Z INFO: processTransferInfo: Receiving 28acce82-67b9-8412-2e6b-0c11fc9bff09, size 12498 bytes
2008-09-22T01:05:55Z INFO: idle: Kills on unknown objects: 1
2008-09-22T01:05:57Z INFO: do_elfio_glibc_backtrace: Opening stack trace file /home/carlos/.secondlife/logs/stack_trace.log
2008-09-22T01:05:59Z INFO: do_elfio_glibc_backtrace: Finished generating stack trace.
2008-09-22T01:05:59Z INFO: handleViewerCrash: Handle viewer crash entry.
2008-09-22T01:05:59Z INFO: handleViewerCrash: Creating crash marker file /home/carlos/.secondlife/logs/SecondLife.error_marker
2008-09-22T01:05:59Z INFO: handleViewerCrash: Created crash marker file /home/carlos/.secondlife/logs/SecondLife.error_marker
2008-09-22T01:05:59Z INFO: handleViewerCrash: Handle viewer crash generating stats log.
2008-09-22T01:05:59Z INFO: writeDebugInfo: Opening debug file /home/carlos/.secondlife/logs/debug_info.log
2008-09-22T01:05:59Z INFO: fork: Forked child process 9269
*** Unclean shutdown. ***

*******************************************************
This is a BETA release of the Second Life linux client.
Thank you for testing!
Please see README-linux.txt before reporting problems.

carlos@carlos-laptop:~/Área de Trabalho/SecondLife_i686_1_20_15_92456$ 2008-09-22T01:05:59Z INFO: LLApp::setupErrorHandling - Starting error thread
2008-09-22T01:05:59Z INFO: run: thread_error - Waiting for an error
2008-09-22T01:05:59Z INFO: handleViewerCrash: Handle viewer crash entry.
2008-09-22T01:05:59Z INFO: LLThread::staticRun() Exiting: Error

```

---

### Post by Ethyrdude on 2008-09-21
This runs fine for me too, haven't seen anything except maybe a bit of lag when playing a particular place with lots of people in it and while my son is playing WOW, on his computer.  Installation was a breeze, just untar the tar.bz2 file, I never used the deb version, so I don't know how you would uninstall it because I don't know where it was installed to, perhaps under /usr/bin or /usr/games?  Mine is installed in my Downloads Directory and I just left it there and ran /home/<USER>/Downloads/SecondLife_i686_1_20_15_92456/secondlife, substituting <USER> with my user name. Now that same command is used in my custom launcher using their icon that they provided with the game.

If I wanted to uninstall it, I could just delete the SecondLife_i686_1_20_15_92456 directory, leaving .secondlife in my home folder to keep my settings if I wanted or delete it if there was a problem with my setup.  Installing from the deb file may have given you an outdated version and this has caused grief to others in the past, because there is no auto update for this.
(Just use the auto extractor that comes with Ubuntu to untar the files.  I still keep thinking I have to use tar -zxvf)

---

### Post by Sealbhach on 2008-09-22
I was using the Beta from the SL site and it just kept crashing. So I saw on the SL forums that someone has created a deb file so that you can apt-get install.

Details here:

[http://www.byteme.org.uk/secondlife/apt-get-a-secondlife.html](http://www.byteme.org.uk/secondlife/apt-get-a-secondlife.html)

I just added

```
 
deb http://apt.byteme.org.uk unstable main

```
to my Software Sources, then 

```
sudo apt-get update
sudo apt-get install slviewer
```

So far it's been stable, just used it for a few hours last night.


.

---

### Post by hp59dk on 2008-09-24
I was reading the Second Life txt file because i can not run it. It says:


Linux Operating System: A reasonably modern 32-bit Linux environment
          is required.  If you are running a 64-bit Linux distribution then
          you will need its 32-bit compatibility environment installed.

I am running a 64-bit distribution. Can You tell me what this means? How can i know what to install?

Thank You from Hans Pedersen



I know i should not post twise, but i found this tread and posted there too:

[http://ubuntuforums.org/showthread.php?p=5849492#post5849492](http://ubuntuforums.org/showthread.php?p=5849492#post5849492)

---

