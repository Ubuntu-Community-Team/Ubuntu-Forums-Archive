---
title: "Serious Sam 2 Crashes to Taskbar"
date: 2014-05-03
forum: Gaming &amp; Leisure
---

### Post by devastater2 on 2014-05-03
Hi, maybe someone can help me here. I posted on the steam/game forum but last post there was a month ago, so I'm not sure if it's active right now. I bought and installed [SIZE=2]Serious sam 2 but when I go to open it, it shows a black screen for 2 seconds, the sound glitches in the backgorund, and then it minimizes [/SIZE]straight[SIZE=2] to the taskbar every time. If I click on the icon in task bar, smae deal, repeats this procedure. Any ideas?[/SIZE]


Run windows 7 and other games have been playing fine. I tried installing directx from within the steam folder as mentioned previously in older posts on the steam forum, but it was already properly installed.

Any help is appreciated or I guess it's refund time and this game looked great. I never even saw this before and have played 1st enc, 2nd enc and SS3. Even got the new early beta revolution that just came out too.




 -------- START OF LOG --------


LOG:   Core version: $Version: Serious Sam 2; 2.070.00:65824; 2006-PATCH-2-070-inc$
LOG:   Command:  $
LOG:   Initializing timer.
LOG:   Timestamp: 2014/05/03 00:48:25
LOG:   Binary name: Sam2.exe
LOG:   Binary soft path: Bin/
LOG:   Binary hard path: C:\Program Files (x86)\Steam\steamapps\common\Serious Sam 2\Bin\
LOG:   Application directory: C:\Program Files (x86)\Steam\steamapps\common\Serious Sam 2\
LOG:   Loading group files...
LOG:     All_PC_01.gro: 1194 files
LOG:     All_PC_02.gro: 5213 files
LOG:     All_PC_03.gro: 3274 files
LOG:     Movies_PC_01.gro: 56 files
LOG:     Movies_PC_02.gro: 44 files
LOG:     Patch_02_068.gro: 360 files
LOG:   --- Serious Engine Startup ---
LOG:   
LOG:   Examining underlying OS...
LOG:     Type: WinNT
LOG:     Version: 6.1, build 7601
LOG:     Misc: Service Pack 1
LOG:   
LOG:   Detecting CPU...
LOG:   Vendor: AuthenticAMD
LOG:     Type: 0, Family: 15, Model: 4, Stepping: 3
LOG:      MMX: Yes
LOG:      SSE: Yes
LOG:     CMOV: Yes
LOG:    Clock: 3415 MHz
LOG:   
LOG:   Error loading ImmWraper.dll: Dynamic module "C:\Program Files (x86)\Steam\steamapps\common\Serious Sam 2\Bin\ImmWrapper.dll" not found!.
LOG:     IFeel disabled
LOG:   Config file 'Content/SeriousSam2/Config/boot.cfg' doesn't exist.
LOG:   Processing config file 'Content/SeriousSam2/Config/autoexec.cfg'.
LOG:   Processing config file 'Content/SeriousSam2/Config/user.cfg'.
ERR:   <memory stream>(4) : error : invalid expression part.
ERR:   Syntax error in command.
LOG:   Loading cvars from "Content/SeriousSam2/Sam2.ini".
LOG:   
LOG:   Desktop settings:
LOG:     Color depth: 32-bit
LOG:     Desktop resolution: 1920 x 1080
LOG:     Virtual screen: 1920 x 1080
LOG:     Monitors attached: 1
LOG:   
LOG:   * Direct3D context created.
INF:   
INF:      Gfx API: Direct3D
INF:   Resolution: 1024 x 768
INF:       Vendor: MS DirectX
INF:     Renderer: NVIDIA GeForce GTX 660  
INF:      Version: 9.18.13.3523
TRC:   EAX is not supported.
INF:   
INF:      Sfx API: DirectSound
INF:       Device: Speakers (Realtek High Definition Audio)
INF:   Mixer freq: 44100 Hz
INF:    HW voices: 0
INF:   Max sounds: 25 (5 same)
INF:       Env FX: not supported
INF:   
LOG:   Winsock opened ok.
LOG:   Module 'Bin/CodecOGG.module' loaded in '0.00' seconds.
LOG:   Module 'Bin/Shaders.module' loaded in '0.20' seconds.
LOG:   Module 'Bin/Shaders.module' loaded in '0.00' seconds.
LOG:   Module 'Bin/ProcRender.module' loaded in '0.00' seconds.
LOG:   Module 'Bin/Sam2Game.module' loaded in '0.23' seconds.
TRC:   Boot stage completed.
TRC:   (Direct3D) Device lost - waiting for reset.
TRC:   (Direct3D) Device has been reset successfully.
LOG:   Timestamp: 2014/05/03 00:48:37
LOG:   Stopping simulation.
LOG:   Timestamp: 2014/05/03 00:48:37
LOG:   Stopping world ''.
LOG:   resFreeUnusedProxies() released '6' proxy object.
LOG:   '0' resources were reverted to resource proxy objects.
LOG:   resFreeUnusedStock() released 0 files in 0.01 seconds (0.000 freeing), after 1 passes
LOG:   World stopped in 0.01sec.
LOG:   resFreeUnusedProxies() released '1' proxy object.

---

### Post by devastater2 on 2014-05-04
This has been resolved by the developer. He suggested placing code:

+fullscreen 0


to the game launch params in Steam.

---

