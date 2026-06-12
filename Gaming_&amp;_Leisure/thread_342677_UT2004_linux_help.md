---
title: "UT2004 linux help"
date: 2007-01-20
forum: Gaming &amp; Leisure
---

### Post by Ace (SWE) on 2007-01-20
EDIT: i got it halfworking using this guide: [http://utforums.epicgames.com/showthread.php?t=558146](http://utforums.epicgames.com/showthread.php?t=558146)

but i get this when trying to run it
```
ace@ace-ubuntu:~/.ut2004/System$ ./ut2004-bin
Exporting MOV-TheEditorHasYou.....Successful!
Exporting MOV-WrongGameMatinee.....Successful!
Exporting JB-SubZero.....Successful!
Exporting JB-Solamander-Gold.....Successful!
Exporting JB-SavoIsland-Gold.....Successful!
Exporting JB-Poseidon-Gold.....Successful!
Exporting JB-Oasis.....Successful!
Exporting JB-NoSense-Gold.....Successful!
Exporting JB-MoonCraters-Gold.....Successful!
Exporting JB-IndusRage2-Gold.....Successful!
Exporting JB-DoomedHeaven-Gold.....Successful!
Exporting JB-Divergence.....Successful!
Exporting JB-Conduit-Gold.....Successful!
Exporting JB-Cosmos.....Successful!
Exporting JB-Cavern.....Successful!
Exporting JB-CastleBreak-Gold.....Successful!
Exporting JB-BabylonTemple-Gold.....Successful!
Exporting JB-Aswan.....Successful!
Exporting JB-Arlon-Gold.....Successful!
Exporting ONS-Exion-WarfareClassic.....Successful!
Exporting ONS-Exion-Warfare.....Successful!
Exporting ONS-Exion-Labyrinth.....Successful!
Exporting ONS-Exion-Gangways.....Successful!
Exporting ONS-Exion-FrostBite.....Successful!
Exporting ONS-Exion-FrontLine.....Successful!
Exporting ONS-Exion-ArcticStronghold.....Successful!
Exporting ONS-E-Torlan.....Successful!
Exporting ONS-E-TDB-Aztec.....Successful!
Exporting JB-Addien-Dwy-Gold.....Successful!
Exporting FC-SunShine.....Successful!
Exporting DM-BP2-GoopGod.....Successful!
Exporting DM-BP2-Calandras.....Successful!
Exporting JB-Heights-Gold-v2.....Successful!
Exporting CTF-BP2-Concentrate.....Successful!
Exporting CTF-BP2-Pistola.....Successful!
Exporting AS-BP2-Thrust.....Successful!
Exporting AS-BP2-SubRosa.....Successful!
Exporting AS-BP2-Outback.....Successful!
Signal: SIGSEGV [segmentation fault]
Aborting.


Crash information will be saved to your logfile.
Segmentation fault (core dumped)
ace@ace-ubuntu:~/.ut2004/System$ ./ut2004-bin
Exporting MOV-TheEditorHasYou.....Successful!
Exporting MOV-WrongGameMatinee.....Successful!
Exporting JB-SubZero.....Successful!
Exporting JB-Solamander-Gold.....Successful!
Exporting JB-SavoIsland-Gold.....Successful!
Exporting JB-Poseidon-Gold.....Successful!
Exporting JB-Oasis.....Successful!
Exporting JB-NoSense-Gold.....Successful!
Exporting JB-MoonCraters-Gold.....Successful!
Exporting JB-IndusRage2-Gold.....Successful!
Exporting JB-DoomedHeaven-Gold.....Successful!
Exporting JB-Divergence.....Successful!
Exporting JB-Conduit-Gold.....Successful!
Exporting JB-Cosmos.....Successful!
Exporting JB-Cavern.....Successful!
Exporting JB-CastleBreak-Gold.....Successful!
Exporting JB-BabylonTemple-Gold.....Successful!
Exporting JB-Aswan.....Successful!
Exporting JB-Arlon-Gold.....Successful!
Exporting ONS-Exion-WarfareClassic.....Successful!
Exporting ONS-Exion-Warfare.....Successful!
Exporting ONS-Exion-Labyrinth.....Successful!
Exporting ONS-Exion-Gangways.....Successful!
Exporting ONS-Exion-FrostBite.....Successful!
Exporting ONS-Exion-FrontLine.....Successful!
Exporting ONS-Exion-ArcticStronghold.....Successful!
Exporting ONS-E-Torlan.....Successful!
Exporting ONS-E-TDB-Aztec.....Successful!
Exporting JB-Addien-Dwy-Gold.....Successful!
Exporting FC-SunShine.....Successful!
Exporting DM-BP2-GoopGod.....Successful!
Exporting DM-BP2-Calandras.....Successful!
Exporting JB-Heights-Gold-v2.....Successful!
Exporting CTF-BP2-Concentrate.....Successful!
Exporting CTF-BP2-Pistola.....Successful!
Exporting AS-BP2-Thrust.....Successful!
Exporting AS-BP2-SubRosa.....Successful!
Assertion failed: Ptr [File:../../Core/Inc/FMallocAnsi.h] [Line: 32]

History: 

Exiting due to error

```

logs:
1```
Log: Log file open, Sat Jan 20 19:29:34 2007
Init: Name subsystem initialized
Init: Version: 3369 (128.29)
Init: Compiled: Dec  2 2005 19:36:10
Init: Command line: 
Init: (This is Linux patch version 3369.0)
Init: Character set: Unicode
Init: Base directory: /home/ace/Desktop/ut2004/System/
Init: Ini:UT2004.ini   UserIni:User.ini
Init: Build label: UT2004 Build UT2004_Build_[2005-11-23_16.22]
Init: Object subsystem initialized
Log: Initializing OpenGLDrv...
Log: binding libGL.so.1
Log: Game class is 'GameInfo'
Log: Bringing Level Entry.myLevel up for play (0) appSeconds: 1.476596...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Browse: NvidiaLogo.ut2?Name=Ace?Class=Engine.Pawn?Character=Remus?team=0?Sex=M
Log: Collecting garbage
Log: Purging garbage
Log: Garbage: objects: 33836->33833; refs: 350043
Log: Game class is 'CinematicGame'
Log: Bringing Level NvidiaLogo.myLevel up for play (0) appSeconds: 1.916744...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Created and initialized a new SDL viewport.
Log: Exporting MOV-TheEditorHasYou.....Successful!
Log: Exporting MOV-WrongGameMatinee.....Successful!
Log: Exporting JB-SubZero.....Successful!
Log: Exporting JB-Solamander-Gold.....Successful!
Warning: Missing Cubemap Cubemap AW-Cubes.Cubes.MesaEnv2
Warning: Missing Cubemap Cubemap AW-Cubes.Cubes.MesaEnv1
Log: Exporting JB-SavoIsland-Gold.....Successful!
Log: Exporting JB-Poseidon-Gold.....Successful!
Warning: Missing Cubemap Cubemap AW-Cubes.Cubes.PS_Cube
Warning: Missing TexEnvMap TexEnvMap AW-Cubes.Cubes.SunC
Log: Exporting JB-Oasis.....Successful!
Log: Exporting JB-NoSense-Gold.....Successful!
Log: Exporting JB-MoonCraters-Gold.....Successful!
Log: Exporting JB-IndusRage2-Gold.....Successful!
Warning: Missing Class Class UnrealEd.Options2DShaperExtrudeToBevel
Warning: Missing Class Class UnrealEd.Options2DShaperExtrudeToPoint
Warning: Missing Class Class UnrealEd.Options2DShaperExtrude
Warning: Missing Class Class UnrealEd.Options2DShaperRevolve
Warning: Missing Class Class UnrealEd.OptionsBrushScale
Warning: Missing Class Class UnrealEd.Options2DShaperBezierDetail
Warning: Missing Class Class UnrealEd.OptionsSurfBevel
Warning: Missing Class Class UnrealEd.OptionsTexAlignPlanar
Warning: Missing Class Class UnrealEd.OptionsTexAlignCylinder
Warning: Missing Class Class UnrealEd.OptionsNewTerrain
Warning: Missing Class Class UnrealEd.OptionsNewTerrainLayer
Warning: Missing Class Class UnrealEd.OptionsMapScale
Warning: Missing Class Class UnrealEd.OptionsMatNewCameraPath
Warning: Missing Class Class UnrealEd.OptionsMatNewStaticMesh
Warning: Missing Class Class UnrealEd.OptionsDupTexture
Warning: Missing Class Class UnrealEd.OptionsRotateActors
Warning: Missing Class Class UnrealEd.OptionsNewClassFromSel
Warning: Missing Class Class UnrealEd.TexAlignerPlanar
Warning: Missing Class Class UnrealEd.TexAlignerDefault
Warning: Missing Class Class UnrealEd.TexAlignerBox
Warning: Missing Class Class UnrealEd.TexAlignerFace
Warning: Missing Class Class UnrealEd.Options2DShaperSheet
Log: Exporting JB-DoomedHeaven-Gold.....Successful!
Log: Exporting JB-Divergence.....Successful!
Log: Exporting JB-Conduit-Gold.....Successful!
Log: Exporting JB-Cosmos.....Successful!
Log: Exporting JB-Cavern.....Successful!
Log: Exporting JB-CastleBreak-Gold.....Successful!
Log: Exporting JB-BabylonTemple-Gold.....Successful!
Log: Exporting JB-Aswan.....Successful!
Log: Exporting JB-Arlon-Gold.....Successful!
Log: Exporting ONS-Exion-WarfareClassic.....Successful!
Log: Exporting ONS-Exion-Warfare.....Successful!
Log: Exporting ONS-Exion-Labyrinth.....Successful!
Log: Exporting ONS-Exion-Gangways.....Successful!
Log: Exporting ONS-Exion-FrostBite.....Successful!
Log: Exporting ONS-Exion-FrontLine.....Successful!
Log: Exporting ONS-Exion-ArcticStronghold.....Successful!
Log: Exporting ONS-E-Torlan.....Successful!
Log: Exporting ONS-E-TDB-Aztec.....Successful!
Log: Exporting JB-Addien-Dwy-Gold.....Successful!
Log: Exporting FC-SunShine.....Successful!
Log: Exporting DM-BP2-GoopGod.....Successful!
Log: Exporting DM-BP2-Calandras.....Successful!
Log: Exporting JB-Heights-Gold-v2.....Successful!
Log: Exporting CTF-BP2-Concentrate.....Successful!
Log: Exporting CTF-BP2-Pistola.....Successful!
Log: Exporting AS-BP2-Thrust.....Successful!
Log: Exporting AS-BP2-SubRosa.....Successful!
Log: Exporting AS-BP2-Outback.....Successful!
Log: Exporting AS-BP2-Jumpship.....Successful!
Log: Exporting AS-BP2-Acatana.....Successful!
Error: Audio initialization failed.
Log: 
Developer Backtrace:
Log: [ 1]  ./ut2004-bin [0x873df19]
Log: [ 2]  [0xffffe420]
Log: [ 3]  /lib/tls/i686/cmov/libc.so.6(memcpy+0x1a) [0xb7d2837a]
Log: [ 4]  ./ut2004-bin(_ZN18FArchiveFileReader9SerializeEPvi+0xad) [0x815ee6d]
Log: [ 5]  ./ut2004-bin(_ZN11ULinkerLoad9SerializeEPvi+0x49) [0x86f14e9]
Log: [ 6]  ./ut2004-bin(_ZlsR8FArchiveR6TArrayIhE+0x75) [0x8192765]
Log: [ 7]  ./ut2004-bin(_ZN10TLazyArrayIhE4LoadEv+0x68) [0x818dca8]
Log: [ 8]  ./ut2004-bin(_ZN10FSoundData4LoadEv+0x61) [0x825db31]
Log: [ 9]  ./ut2004-bin(_ZlsR8FArchiveR10TLazyArrayIhE+0x8b) [0x8263c5b]
Log: [10]  ./ut2004-bin(_ZN6USound9SerializeER8FArchive+0x6e) [0x825e75e]
Log: [11]  ./ut2004-bin(_ZN11ULinkerLoad7PreloadEP7UObject+0x175) [0x86f0675]
Log: [12]  ./ut2004-bin(_ZN7UObject7EndLoadEv+0x153) [0x8717873]
Log: [13]  ./ut2004-bin(_ZN7UObject16StaticLoadObjectEP6UClassPS_PKwS4_jP11UPackageMap+0x121) [0x8717161]
Log: [14]  ./ut2004-bin(_ZN7UObject21execDynamicLoadObjectER6FFramePv+0x162) [0x86e6912]
Log: [15]  ./ut2004-bin(_ZN7UObject12CallFunctionER6FFramePvP9UFunction+0xdb) [0x86e7a8b]
Log: [16]  ./ut2004-bin(_ZN7UObject17execFinalFunctionER6FFramePv+0x34) [0x86c4ea4]
Log: [17]  ./ut2004-bin(_ZN7UObject15execDynamicCastER6FFramePv+0x5d) [0x86c576d]
Log: [18]  ./ut2004-bin(_ZN7UObject7execLetER6FFramePv+0x25c) [0x86c4a3c]
Log: [19]  ./ut2004-bin(_ZN7UObject15ProcessInternalER6FFramePv+0x185) [0x86e8155]
Log: [20]  ./ut2004-bin(_ZN7UObject12CallFunctionER6FFramePvP9UFunction+0x47e) [0x86e7e2e]
Log: [21]  ./ut2004-bin(_ZN7UObject19execVirtualFunctionER6FFramePv+0x46) [0x86c4e66]
Log: [22]  ./ut2004-bin(_ZN7UObject15ProcessInternalER6FFramePv+0x185) [0x86e8155]
Log: [23]  ./ut2004-bin(_ZN7UObject12CallFunctionER6FFramePvP9UFunction+0x47e) [0x86e7e2e]
Log: [24]  ./ut2004-bin(_ZN7UObject19execVirtualFunctionER6FFramePv+0x46) [0x86c4e66]
Log: [25]  ./ut2004-bin(_ZN7UObject11execContextER6FFramePv+0x185) [0x86c4de5]
Log: [26]  ./ut2004-bin(_ZN7UObject15ProcessInternalER6FFramePv+0x185) [0x86e8155]
Log: [27]  ./ut2004-bin(_ZN7UObject12CallFunctionER6FFramePvP9UFunction+0x1ef) [0x86e7b9f]
Log: [28]  ./ut2004-bin(_ZN7UObject19execVirtualFunctionER6FFramePv+0x46) [0x86c4e66]
Log: [29]  ./ut2004-bin(_ZN7UObject15ProcessInternalER6FFramePv+0x185) [0x86e8155]
Log: [30]  ./ut2004-bin(_ZN7UObject12ProcessEventEP9UFunctionPvS2_+0x1f7) [0x86e8477]
Log: [31]  ./ut2004-bin(_ZN6ULevel10SpawnActorEP6UClass5FName7FVector8FRotatorP6AActoriiS6_P5APawni+0x60e) [0x82ecf8e]
Log: [32]  ./ut2004-bin(_ZN6AActor9execSpawnER6FFramePv+0x295) [0x845f065]
Log: [33]  ./ut2004-bin(_ZN7UObject15execHighNative1ER6FFramePv+0x5f) [0x86e2e4f]
Log: [34]  ./ut2004-bin(_ZN7UObject7execLetER6FFramePv+0x25c) [0x86c4a3c]
Log: [35]  ./ut2004-bin(_ZN7UObject15ProcessInternalER6FFramePv+0x185) [0x86e8155]
Log: [36]  ./ut2004-bin(_ZN7UObject12ProcessEventEP9UFunctionPvS2_+0x1f7) [0x86e8477]
Log: [37]  ./ut2004-bin(_ZN6ULevel14SpawnPlayActorEP7UPlayer8ENetRoleRK4FURLR7FString+0x2f8) [0x82ee6e8]
Log: [38]  ./ut2004-bin(_ZN11UGameEngine4InitEv+0x1163) [0x82ad5d3]
Log: [39]  ./ut2004-bin [0x8158609]
Log: [40]  ./ut2004-bin(main+0x33b4) [0x81531a4]
Log: [41]  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7ccf8cc]
Log: [42]  ./ut2004-bin(readdir+0x99) [0x814fba1]
Log: Unreal Call Stack: ULinkerLoad::Serialize <- TArray<< <- TLazyArray::Load <- 0 <- FSoundData::Load <- TLazyArray<< <- USound::Serialize <- LoadObject <- ULinkerLoad::Preload <- PreLoadObjects <- UObject::EndLoad <- UObject::StaticLoadObject <- UObject::ProcessEvent <- ULevel::SpawnActor <- UObject::ProcessEvent <- ULevel::SpawnPlayActor <- UGameEngine::Init <- InitEngine
Exit: Exiting.
Log: FileManager: Reading 0 GByte 6 MByte 5 KByte 385 Bytes from HD took 0.502810 seconds (0.502810 reading, 0.000000 seeking).
Log: FileManager: 0.000000 seconds spent with misc. duties
Uninitialized: Name subsystem shut down
Uninitialized: Allocation checking disabled
Uninitialized: Log file closed, Sat Jan 20 19:29:39 2007

```
2```
Log: Log file open, Sat Jan 20 19:46:26 2007
Init: Name subsystem initialized
Init: Version: 3369 (128.29)
Init: Compiled: Dec  2 2005 19:36:10
Init: Command line: 
Init: (This is Linux patch version 3369.0)
Init: Character set: Unicode
Init: Base directory: /home/ace/Desktop/ut2004/System/
Init: Ini:UT2004.ini   UserIni:User.ini
Init: Build label: UT2004 Build UT2004_Build_[2005-11-23_16.22]
Init: Object subsystem initialized
Log: Initializing OpenGLDrv...
Log: binding libGL.so.1
Log: Game class is 'GameInfo'
Log: Bringing Level Entry.myLevel up for play (0) appSeconds: 1.521382...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Browse: NvidiaLogo.ut2?Name=Ace?Class=Engine.Pawn?Character=Remus?team=0?Sex=M
Log: Collecting garbage
Log: Purging garbage
Log: Garbage: objects: 33836->33833; refs: 350043
Log: Game class is 'CinematicGame'
Log: Bringing Level NvidiaLogo.myLevel up for play (0) appSeconds: 1.956375...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Created and initialized a new SDL viewport.
Log: Exporting MOV-TheEditorHasYou.....Successful!
Log: Exporting MOV-WrongGameMatinee.....Successful!
Log: Exporting JB-SubZero.....Successful!
Log: Exporting JB-Solamander-Gold.....Successful!
Warning: Missing Cubemap Cubemap AW-Cubes.Cubes.MesaEnv2
Warning: Missing Cubemap Cubemap AW-Cubes.Cubes.MesaEnv1
Log: Exporting JB-SavoIsland-Gold.....Successful!
Log: Exporting JB-Poseidon-Gold.....Successful!
Warning: Missing Cubemap Cubemap AW-Cubes.Cubes.PS_Cube
Warning: Missing TexEnvMap TexEnvMap AW-Cubes.Cubes.SunC
Log: Exporting JB-Oasis.....Successful!
Log: Exporting JB-NoSense-Gold.....Successful!
Log: Exporting JB-MoonCraters-Gold.....Successful!
Log: Exporting JB-IndusRage2-Gold.....Successful!
Warning: Missing Class Class UnrealEd.Options2DShaperExtrudeToBevel
Warning: Missing Class Class UnrealEd.Options2DShaperExtrudeToPoint
Warning: Missing Class Class UnrealEd.Options2DShaperExtrude
Warning: Missing Class Class UnrealEd.Options2DShaperRevolve
Warning: Missing Class Class UnrealEd.OptionsBrushScale
Warning: Missing Class Class UnrealEd.Options2DShaperBezierDetail
Warning: Missing Class Class UnrealEd.OptionsSurfBevel
Warning: Missing Class Class UnrealEd.OptionsTexAlignPlanar
Warning: Missing Class Class UnrealEd.OptionsTexAlignCylinder
Warning: Missing Class Class UnrealEd.OptionsNewTerrain
Warning: Missing Class Class UnrealEd.OptionsNewTerrainLayer
Warning: Missing Class Class UnrealEd.OptionsMapScale
Warning: Missing Class Class UnrealEd.OptionsMatNewCameraPath
Warning: Missing Class Class UnrealEd.OptionsMatNewStaticMesh
Warning: Missing Class Class UnrealEd.OptionsDupTexture
Warning: Missing Class Class UnrealEd.OptionsRotateActors
Warning: Missing Class Class UnrealEd.OptionsNewClassFromSel
Warning: Missing Class Class UnrealEd.TexAlignerPlanar
Warning: Missing Class Class UnrealEd.TexAlignerDefault
Warning: Missing Class Class UnrealEd.TexAlignerBox
Warning: Missing Class Class UnrealEd.TexAlignerFace
Warning: Missing Class Class UnrealEd.Options2DShaperSheet
Log: Exporting JB-DoomedHeaven-Gold.....Successful!
Log: Exporting JB-Divergence.....Successful!
Log: Exporting JB-Conduit-Gold.....Successful!
Log: Exporting JB-Cosmos.....Successful!
Log: Exporting JB-Cavern.....Successful!
Log: Exporting JB-CastleBreak-Gold.....Successful!
Log: Exporting JB-BabylonTemple-Gold.....Successful!
Log: Exporting JB-Aswan.....Successful!
Log: Exporting JB-Arlon-Gold.....Successful!
Log: Exporting ONS-Exion-WarfareClassic.....Successful!
Log: Exporting ONS-Exion-Warfare.....Successful!
Log: Exporting ONS-Exion-Labyrinth.....Successful!
Log: Exporting ONS-Exion-Gangways.....Successful!
Log: Exporting ONS-Exion-FrostBite.....Successful!
Log: Exporting ONS-Exion-FrontLine.....Successful!
Log: Exporting ONS-Exion-ArcticStronghold.....Successful!
Log: Exporting ONS-E-Torlan.....Successful!
Log: Exporting ONS-E-TDB-Aztec.....Successful!
Log: Exporting JB-Addien-Dwy-Gold.....Successful!
Log: Exporting FC-SunShine.....Successful!
Log: Exporting DM-BP2-GoopGod.....Successful!
Log: Exporting DM-BP2-Calandras.....Successful!
Log: Exporting JB-Heights-Gold-v2.....Successful!
Log: Exporting CTF-BP2-Concentrate.....Successful!
Log: Exporting CTF-BP2-Pistola.....Successful!
Log: Exporting AS-BP2-Thrust.....Successful!
Log: Exporting AS-BP2-SubRosa.....Successful!
Critical: Assertion failed: Ptr [File:../../Core/Inc/FMallocAnsi.h] [Line: 32]
Exit: Executing UObject::StaticShutdownAfterError
Exit: Executing USDLClient::ShutdownAfterError
Exit: Exiting.
Log: FileManager: Reading 0 GByte 4 MByte 737 KByte 826 Bytes from HD took 0.017246 seconds (0.017246 reading, 0.000000 seeking).
Log: FileManager: 0.000000 seconds spent with misc. duties
Uninitialized: Name subsystem shut down
Uninitialized: Log file closed, Sat Jan 20 19:46:32 2007

```

---

