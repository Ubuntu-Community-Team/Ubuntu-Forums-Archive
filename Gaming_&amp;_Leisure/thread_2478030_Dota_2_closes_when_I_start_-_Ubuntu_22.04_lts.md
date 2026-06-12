---
title: "Dota 2 closes when I start - Ubuntu 22.04 lts"
date: 2022-08-14
forum: Gaming &amp; Leisure
---

### Post by rafaelsangali on 2022-08-14
I'm new to ubuntu, I'm on version 22.04 lts, &#8203;&#8203;I have a Geforce gt 730 video card with drivers installed on version 390.154 (which is recommended by ubuntu itself).
 The problem is that when I start dota 2 that has native support for Linux it simply crashes, this is the log that appears.


```

Could not connect to X session manager: None of the authentication protocols specified are supported
Could not connect to X session manager: None of the authentication protocols specified are supported
Could not connect to X session manager: None of the authentication protocols specified are supported
Could not connect to X session manager: None of the authentication protocols specified are supported
Could not connect to X session manager: None of the authentication protocols specified are supported
GameAction [AppID 570, ActionID 1] : LaunchApp changed task to UpdatingAppInfo with ""
GameAction [AppID 570, ActionID 1] : LaunchApp changed task to ProcessingInstallScript with ""
GameAction [AppID 570, ActionID 1] : LaunchApp changed task to SynchronizingCloud with ""
GameAction [AppID 570, ActionID 1] : LaunchApp changed task to SiteLicenseSeatCheckout with ""
GameAction [AppID 570, ActionID 1] : LaunchApp changed task to CreatingProcess with ""
GameAction [AppID 570, ActionID 1] : LaunchApp waiting for user response to CreatingProcess ""
GameAction [AppID 570, ActionID 1] : LaunchApp continues with user response "CreatingProcess"
/bin/sh\0-c\0/home/rafael/.local/share/Steam/ubuntu12_32/reaper SteamLaunch AppId=570 -- '/home/rafael/.local/share/Steam/steamapps/common/SteamLinuxRuntime_soldier'/_v2-entry-point --verb=waitforexitandrun -- '/home/rafael/.local/share/Steam/steamapps/common/SteamLinuxRuntime'/scout-on-soldier-entry-point-v2 --  '/home/rafael/.local/share/Steam/steamapps/common/dota 2 beta/game/dota.sh' +engine_experimental_drop_frame_ticks 1 +@panorama_min_comp_layer_dimension 0 -prewarm_panorama -high \0
Game process added : AppID 570 "/home/rafael/.local/share/Steam/ubuntu12_32/reaper SteamLaunch AppId=570 -- '/home/rafael/.local/share/Steam/steamapps/common/SteamLinuxRuntime_soldier'/_v2-entry-point --verb=waitforexitandrun -- '/home/rafael/.local/share/Steam/steamapps/common/SteamLinuxRuntime'/scout-on-soldier-entry-point-v2 --  '/home/rafael/.local/share/Steam/steamapps/common/dota 2 beta/game/dota.sh' +engine_experimental_drop_frame_ticks 1 +@panorama_min_comp_layer_dimension 0 -prewarm_panorama -high ", ProcID 3060, IP 0.0.0.0:0
chdir /home/rafael/.local/share/Steam/steamapps/common/dota 2 beta
ERROR: ld.so: object '/home/rafael/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/rafael/.local/share/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS64): ignored.
ERROR: ld.so: object '/home/rafael/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/rafael/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
GameAction [AppID 570, ActionID 1] : LaunchApp changed task to WaitingGameWindow with ""
ERROR: ld.so: object '/home/rafael/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
pid 3067 != 3064, skipping destruction (fork without exec?)
GameAction [AppID 570, ActionID 1] : LaunchApp changed task to Completed with ""
Installing breakpad exception handler for appid(steam)/version(1658944613)
pid 3174 != 3170, skipping destruction (fork without exec?)
pid 3179 != 3170, skipping destruction (fork without exec?)
pid 3221 != 3170, skipping destruction (fork without exec?)
Using breakpad crash handler
[S_API] SteamAPI_Init(): Loaded '/home/rafael/.local/share/Steam/linux64/steamclient.so' OK.
Game process updated : AppID 570 "/home/rafael/.local/share/Steam/ubuntu12_32/reaper SteamLaunch AppId=570 -- '/home/rafael/.local/share/Steam/steamapps/common/SteamLinuxRuntime_soldier'/_v2-entry-point --verb=waitforexitandrun -- '/home/rafael/.local/share/Steam/steamapps/common/SteamLinuxRuntime'/scout-on-soldier-entry-point-v2 --  '/home/rafael/.local/share/Steam/steamapps/common/dota 2 beta/game/dota.sh' +engine_experimental_drop_frame_ticks 1 +@panorama_min_comp_layer_dimension 0 -prewarm_panorama -high ", ProcID 3226, IP 0.0.0.0:0
Setting breakpad minidump AppID = 570
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
SteamInternal_SetMinidumpSteamID:  Caching Steam ID:  76561198342508678 [API loaded yes]
SteamInternal_SetMinidumpSteamID:  Setting Steam ID:  76561198342508678
Setting breakpad minidump AppID = 373300
*** stack smashing detected ***: terminated
crash_20220814235252_2.dmp[3246]: Uploading dump (out-of-process)
/tmp/dumps/crash_20220814235252_2.dmp
/home/rafael/.local/share/Steam/steamapps/common/dota 2 beta/game/dota.sh: line 109:  3226 Aborted                 (core dumped) ${STEAM_RUNTIME_PREFIX} ${GAME_DEBUGGER} "${GAMEROOT}"/${GAMEEXE} "$@"
crash_20220814235252_2.dmp[3246]: Finished uploading minidump (out-of-process): success = yes
crash_20220814235252_2.dmp[3246]: response: CrashID=bp-dba13de6-5ca0-4cb8-8551-8908c2220814
crash_20220814235252_2.dmp[3246]: file ''/tmp/dumps/crash_20220814235252_2.dmp'', upload yes: ''CrashID=bp-dba13de6-5ca0-4cb8-8551-8908c2220814''
pid 3246 != 3245, skipping destruction (fork without exec?)
Game process removed: AppID 570 "/home/rafael/.local/share/Steam/ubuntu12_32/reaper SteamLaunch AppId=570 -- '/home/rafael/.local/share/Steam/steamapps/common/SteamLinuxRuntime_soldier'/_v2-entry-point --verb=waitforexitandrun -- '/home/rafael/.local/share/Steam/steamapps/common/SteamLinuxRuntime'/scout-on-soldier-entry-point-v2 --  '/home/rafael/.local/share/Steam/steamapps/common/dota 2 beta/game/dota.sh' +engine_experimental_drop_frame_ticks 1 +@panorama_min_comp_layer_dimension 0 -prewarm_panorama -high ", ProcID 3226 
ThreadGetProcessExitCode: no such process 3245
ThreadGetProcessExitCode: no such process 3237
ThreadGetProcessExitCode: no such process 3236
ThreadGetProcessExitCode: no such process 3226
ThreadGetProcessExitCode: no such process 3222
ThreadGetProcessExitCode: no such process 3170
ThreadGetProcessExitCode: no such process 3065
ThreadGetProcessExitCode: no such process 3064
ThreadGetProcessExitCode: no such process 3063
Game 570 created interface STEAMAPPLIST_INTERFACE_VERSION001 / 
Game 570 created interface STEAMAPPS_INTERFACE_VERSION008 / 
Game 570 created interface STEAMHTMLSURFACE_INTERFACE_VERSION_005 / 
Game 570 created interface STEAMHTTP_INTERFACE_VERSION003 / 
Game 570 created interface STEAMINVENTORY_INTERFACE_V003 / 
Game 570 created interface STEAMMUSICREMOTE_INTERFACE_VERSION001 / 
Game 570 created interface STEAMMUSIC_INTERFACE_VERSION001 / 
Game 570 created interface STEAMPARENTALSETTINGS_INTERFACE_VERSION001 / 
Game 570 created interface STEAMREMOTESTORAGE_INTERFACE_VERSION016 / 
Game 570 created interface STEAMSCREENSHOTS_INTERFACE_VERSION003 / 
Game 570 created interface STEAMUGC_INTERFACE_VERSION016 / 
Game 570 created interface STEAMUSERSTATS_INTERFACE_VERSION012 / 
Game 570 created interface STEAMVIDEO_INTERFACE_V002 / 
Game 570 created interface SteamController008 / 
Game 570 created interface SteamFriends017 / 
Game 570 created interface SteamMatchGameSearch001 / 
Game 570 created interface SteamMatchMaking009 / 
Game 570 created interface SteamMatchMakingServers002 / 
Game 570 created interface SteamNetworking006 / 
Game 570 created interface SteamUser021 / 
Game 570 created interface SteamUser021 / User
Game 570 created interface SteamUtils010 / 
Game 570 method call count for IClientAppManager::GetCurrentLanguage : 1
Game 570 method call count for IClientAppManager::GetAppStateInfo : 1
Game 570 method call count for IClientUtils::RecordSteamInterfaceCreation : 23
Game 570 method call count for IClientUtils::IsSteamChina : 1
Game 570 method call count for IClientUtils::GetLauncherType : 1
Game 570 method call count for IClientUtils::GetSteamUILanguage : 1
Game 570 method call count for IClientUtils::GetAppID : 26
Game 570 method call count for IClientUser::GetSteamID : 4
Uploaded AppInterfaceStats to Steam
```

---

