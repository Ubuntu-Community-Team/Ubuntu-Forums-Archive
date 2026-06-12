---
title: "Steam in Wine Problems"
date: 2010-12-04
forum: Gaming &amp; Leisure
---

### Post by oman9978 on 2010-12-04
Hello,

I have recently installed ubuntu on my new gaming computer. Unfortunately, I can't get beyond the preparing to launch screen on source games. I have an Nvidia GTX 460 graphics card. For some reason the Nvidia X Server Settings thinks that my GPU is a 455 (I installed the proprietary drivers through the "additional drivers" tool in administration as I was having trouble disabling the X Window Server to install the drivers from Nvidia's website). I am not sure this has anything to do with the problem. I am using the on-board sound on my motherboard, not the HDMI audio on my graphics card.

Below is the message I get in terminal when trying to launch Half Life 2 Deathmatch. I have tried playing games that run natively in Linux such as Minecraft and Assault Cube and both of these games work fine.

I welcome any suggestions on how to fix this, thank you for your help in advance.

```
owen@owen-MCP61M-M3:~$ wine /home/owen/.wine/drive_c/Program\ Files/steam/steam.exe
CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
CellID: CSDS returned 171 servers.
CellID: Connecting to 203.77.185.188:27031. . .
CellID: Connect to 203.77.185.188:27031 took 138 MS
CellID: Nothing beat our old best time of 10 MS
fixme:mixer:ALSA_MixerInit No master control found on HDA NVidia, disabling mixer
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wbemprox:wbem_locator_ConnectServer 0x1d3008, L"ROOT\\CIMV2", (null), (null), (null), 0x00000080, (null), (nil), 0x435beb8)
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:win:EnumDisplayDevicesW ((null),0,0x32ce24,0x00000000), stub!
fixme:advapi:RegisterTraceGuidsW (0x3824f30, 0x3e7b720, {3dada31d-19ef-4dc1-b345-037927193422}, 1, 0x3e53b24, (null), (null), 0x3e7b738,)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd 0x10126
fixme:win:EnumDisplayDevicesW ((null),0,0x33dfec,0x00000000), stub!
Using breakpad crash handler
Setting breakpad minidump AppID = 320
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561197998238183 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561197998238183
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:d3d:debug_d3dformat Unrecognized 1129272385 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1129272385) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1094800211 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1094800211) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1129272385 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1129272385) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1094800211 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1094800211) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x149fb8, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x33e114)
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:avifile:AVIFileExit (): stub!
err:ntdll:RtlpWaitForCriticalSection section 0x14c7674 "?" wait timed out in thread 001e, blocked by 001f, retrying (60 sec)
CellID: Connecting to 209.197.6.229:27031. . .
CellID: timeout connecting to 209.197.6.229:27031
CellID: Connecting to 61.110.195.10:27031. . .
CellID: Connect to 61.110.195.10:27031 took 213 MS
CellID: Nothing beat our old best time of 10 MS


```

---

