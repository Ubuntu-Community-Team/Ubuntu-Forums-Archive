---
title: "Prey Demo works with wine"
date: 2006-06-23
forum: Gaming &amp; Leisure
---

### Post by snooze on 2006-06-23
And it works pretty well too.

1024x728, video maxed, high quality settings. (AA turned off).
amd 2600+, nvidia 6600gt, 1.5 gigs ram.

It's not perfect. There is some slowdown and sound stutter,
but considering my system specs and video settings, and WINE ,
it's amazing.

Definately worth the huge d/l. (450+ megs).

---

### Post by bocmaxima on 2006-06-23
[QUOTE=snooze]And it works pretty well too.

1024x728, video maxed, high quality settings. (AA turned off).
amd 2600+, nvidia 6600gt, 1.5 gigs ram.

It's not perfect. There is some slowdown and sound stutter,
but considering my system specs and video settings, and WINE ,
it's amazing.

Definately worth the huge d/l. (450+ megs).[/QUOTE]


Kick ***

---

### Post by strattonbrazil on 2006-06-24
I can't get the demo to start.  It loads fine, but gives me a startup error in the program when it loads:

Prey 0.2.95 win-x86 May 30 2006 21:14:05
798 MHz Intel CPU with MMX & SSE & SSE2
1520 MB System Memory
64 MB Video Memory
Winsock Initialized
Found interface: eth0  - 192.168.1.9/1.0.0.0
Found interface: eth1  - 192.168.1.100/1.0.0.0
Found interface: sit0  - /
Sys_InitNetworking: adding loopback interface
prey using MMX & SSE & SSE2 for SIMD processing
enabled Flush-To-Zero mode
enabled Denormals-Are-Zero mode
------ Initializing File System ------
Loaded pk4 C:\Program Files\Prey Demo\base\demo00.pk4 with checksum 0x86294060
Current search path:
C:\Program Files\Prey Demo/base
C:\Program Files\Prey Demo\base\demo00.pk4 (11273 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------

Running in restricted demo mode.

----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
2647 strings read from strings/english001.lang
Couldn't open journal files
couldn't exec editor.cfg
execing default.cfg
couldn't exec preyconfig.cfg
couldn't exec autoexec.cfg
2647 strings read from strings/english001.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Initializing OpenGL subsystem
...registered window class
...registered fake window class
...initializing QGL
...calling LoadLibrary( 'opengl32' ): succeeded
...calling CDS: failed, bad mode
...trying next higher resolution:ok
...created window @ 0,0 (640x480)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD failed
Shutting down OpenGL subsystem
...wglMakeCurrent( NULL, NULL ): success
...releasing DC: failed
...resetting display
...shutting down QGL
...unloading OpenGL DLL
Initializing OpenGL subsystem
...initializing QGL
...calling LoadLibrary( 'opengl32' ): succeeded
...calling CDS: failed, bad mode
...trying next higher resolution:ok
...created window @ 0,0 (640x480)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD failed
Shutting down OpenGL subsystem
...wglMakeCurrent( NULL, NULL ): success
...releasing DC: failed
...resetting display
...shutting down QGL
...unloading OpenGL DLL
idRenderSystem::Shutdown()
Shutting down OpenGL subsystem
...shutting down QGL
Unable to initialize OpenGL

I don't know why this is happening.  All my other wine games run fine like Warcraft 3.  Any ideas?  I don't know what some of these systems are like QGL.  Anyways, has anyone else had these problems and fixed them?

---

### Post by FredB on 2006-06-24
[QUOTE=snooze]And it works pretty well too.

1024x728, video maxed, high quality settings. (AA turned off).
amd 2600+, nvidia 6600gt, 1.5 gigs ram.

It's not perfect. There is some slowdown and sound stutter,
but considering my system specs and video settings, and WINE ,
it's amazing.

Definately worth the huge d/l. (450+ megs).[/QUOTE]

Prey Demo is out ? Did you try with the ubuntu version of WINE ? Or a younger version ?

I remember having heard of Prey the first time in 1999 or so...

And Duke 4 Ever ? :-({|=

---

### Post by snooze on 2006-06-24
Hi strattonbrazil.

I don't really have an answer about QGL, but I did notice your system specs.
(798 MHz Intel CPU with MMX & SSE & SSE2)

These are the official Prey requirements:
 Minimum

    * CPU Speed: Intel Pentium 4 2.0Ghz / AMD Athlon XP 2000+ processor
    * RAM: 512MB system RAM
    * Video Card: 100% DirectX 9.0c compatible 64MB video card with latest manufacturer drivers (see supported chipsets below)
    * Drive: 8X CD-ROM (standard edition), DVD-ROM (Limited Collector's Edition)
    * Hard Drive: 2.2GB of uncompressed free hard drive space
    * Sound Card: 100% DirectX 9.0c compatible 16-bit sound card
    * Operating System: Microsoft Windows 2000 or XP with latest service pack installed
    * DirectX Version: DirectX 9.0c

Recommended

    * CPU Speed: Intel Pentium 4 2.5Ghz / AMD Athlon XP 2500+ processor
    * RAM: 1GB system RAM
    * Video Card: ATI Radeon X800 series or higher video card with latest manufacturer drivers
    * Sound Card: Creative Sound Blaster X-Fi series sound card
    * Internet: Broadband internet connection or LAN required for multiplayer

Supported Video Card Chipsets

    * ATI: ATI Radeon 9600 series, ATI Radeon 9700 series, ATI Radeon 9800 series, ATI Radeon X300 series, ATI Radeon X550 series, ATI Radeon X600 series, ATI Radeon X700 series, ATI Radeon X800 series, ATI Radeon X1300 series, ATI Radeon X1600 series, ATI Radeon X1800 series, ATI Radeon X1900 series, or better with latest manufacturer drivers
    * NVIDIA: NVIDIA GeForce3/Ti series, NVIDIA GeForce4/Ti, NVIDIA GeForce FX 5800 series, NVIDIA GeForce 5900 series, NVIDIA GeForce 6200 series, NVIDIA GeForce 6600 series, NVIDIA GeForce 6800 series, NVIDIA GeForce 7300 series, NVIDIA GeForce 7600 series, NVIDIA GeForce 7800 series, NVIDIA GeForce 7900 series, or better with latest manufacturer drivers.


Hope that helps.

---

### Post by snooze on 2006-06-24
I'm using ubuntu wine 0.9.16.
The newest, I think.

---

### Post by strattonbrazil on 2006-06-24
Hi Snooze,

I have CPU scaling turned on (it's a laptop), so the CPU kicks up when the game starts (up to 1.8 GHz).  Games like Doom 3, FEAR and Quake 4 all run great on my system.  Just don't know why FEAR doesn't work...

Thanks, though.

---

### Post by lotusleaf on 2006-06-24
Cool news, thanks for the thread.

FWIW:

[Prey](http://appdb.winehq.org/appview.php?appId=3465) is listed in the [Wine Application DB ](http://appdb.winehq.org/)([Prey demo listing here](http://appdb.winehq.org/appview.php?versionId=5118)) with positive ratings, this looks good!

I recommend to everyone who uses WINE (and has a few spare minutes) to always provide feedback to the WINE App DB for the program you're using.

I've also noticed a few older games which use DirectX to actually work with the latest WINE version. WINE is just getting better and better! :)

---

### Post by bocmaxima on 2006-06-25
Mine crashes after choosing english in the installer :(

---

### Post by snooze on 2006-06-25
I can't explain why some people have crashes.
It uses the DOOM3 engine.
Logic suggests that if doom3 works on your system, so should this.

---

### Post by snooze on 2006-06-25
I really hope that the full released version of Prey works natively.
I remember when only the demo of Sin would work.
Couldn't get the full version to work.

---

### Post by gaillard on 2006-06-25
can anyone do a speed comparison?

---

### Post by Bokonon on 2006-06-26
No love here.  Died on install, wine 0.9.16.

To be fair, I haven't messed with wine much other than trying to install things with winetools.  Not the best of luck so far installing anything other than Kingmaker (for NWN) via wine.

I have a windows partition for gaming :)

---

### Post by LinuxRocks on 2006-06-26
I can get it installed just fine using Cedega, but when I fire up the game, I get the spash screen, then it dies with this message:

mmtime pid=32181 tid=32192
wine: Unhandled exception, starting debugger...


Anyone care to share how they got it to run? Any config options need to be set.

For the record, HL2, Alice, FarCry, and others work great. Doom3 and Quake 4 run naively just fine as well.

I am using the latest Cedege and engine also.

Thanks!!!

Joe

---

### Post by MTZeon on 2006-06-28
[QUOTE=strattonbrazil]I can't get the demo to start.  It loads fine, but gives me a startup error in the program when it loads:

Prey 0.2.95 win-x86 May 30 2006 21:14:05
798 MHz Intel CPU with MMX & SSE & SSE2
1520 MB System Memory
64 MB Video Memory
Winsock Initialized
Found interface: eth0  - 192.168.1.9/1.0.0.0
Found interface: eth1  - 192.168.1.100/1.0.0.0
Found interface: sit0  - /
Sys_InitNetworking: adding loopback interface
prey using MMX & SSE & SSE2 for SIMD processing
enabled Flush-To-Zero mode
enabled Denormals-Are-Zero mode
------ Initializing File System ------
Loaded pk4 C:\Program Files\Prey Demo\base\demo00.pk4 with checksum 0x86294060
Current search path:
C:\Program Files\Prey Demo/base
C:\Program Files\Prey Demo\base\demo00.pk4 (11273 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------

Running in restricted demo mode.

----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
2647 strings read from strings/english001.lang
Couldn't open journal files
couldn't exec editor.cfg
execing default.cfg
couldn't exec preyconfig.cfg
couldn't exec autoexec.cfg
2647 strings read from strings/english001.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Initializing OpenGL subsystem
...registered window class
...registered fake window class
...initializing QGL
...calling LoadLibrary( 'opengl32' ): succeeded
...calling CDS: failed, bad mode
...trying next higher resolution:ok
...created window @ 0,0 (640x480)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD failed
Shutting down OpenGL subsystem
...wglMakeCurrent( NULL, NULL ): success
...releasing DC: failed
...resetting display
...shutting down QGL
...unloading OpenGL DLL
Initializing OpenGL subsystem
...initializing QGL
...calling LoadLibrary( 'opengl32' ): succeeded
...calling CDS: failed, bad mode
...trying next higher resolution:ok
...created window @ 0,0 (640x480)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD failed
Shutting down OpenGL subsystem
...wglMakeCurrent( NULL, NULL ): success
...releasing DC: failed
...resetting display
...shutting down QGL
...unloading OpenGL DLL
idRenderSystem::Shutdown()
Shutting down OpenGL subsystem
...shutting down QGL
Unable to initialize OpenGL

I don't know why this is happening.  All my other wine games run fine like Warcraft 3.  Any ideas?  I don't know what some of these systems are like QGL.  Anyways, has anyone else had these problems and fixed them?[/QUOTE]
you have to change the color depth in /etc/X11/xorg.conf from 16 to 24 :)

---

### Post by justjuice on 2006-10-14
I can't get it to install at all.  After I click the Next button on the installer, I get an error:

An error (-5009 : 0x80040707) has occurred while running the setup.
Please make sure you have finished any previous setup and closed other applications.
Details:
>Ctor\ObjectWrapper.cpp (163)
>Ctor\ObjectWrapper.cpp (391)
>Kernel\Component.cpp (1163)
>Kernel\CABFile.cpp (384)
>SetupDLL\SetupDLL.cpp (1526)
PAPP:Prey Point Release 1.2
PVendor....etc

I seem to be running version 0.9.12 according to Synaptic Package Manager.
And I'm running Ubuntu 5.04 Hoary Hedgehog.

Thanks.

Anyone got any ideas?

---

### Post by justjuice on 2006-10-17
So, I managed to get it installed, but there is no Prey.exe anywhere.  The installer says it installed successfully, but it seems not.  And I have tried with Wine in XP, 2000, and 98 mode, all with the same result. And it's definitely not anywhere as I try to locate anything called "Prey" using the locate command. All it finds is my installer and a couple of Prey icons.

The terminal has the following output.
Can someone help?

root@jj-ubuntu:/home/justin/Downloads # wine prey_demo
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:win:SetWindowTextA setting text "TITLE_CAPTIONBAR" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Prey Demo - InstallShield Wizard" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "TITLE_CAPTIONBAR" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Prey Demo - InstallShield Wizard" of other process window (nil) should not use SendMessage
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\nooverflow"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\faroman"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\rin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\lin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\itap0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfe1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\cgrid"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langnp2057"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfenp1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\nooverflow"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\faroman"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\rin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\lin851"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\itap0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfe1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\cgrid"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langnp2057"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfenp1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\nooverflow"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\faroman"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\rin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\lin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\itap0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfe1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\cgrid"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langnp2057"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfenp1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\nooverflow"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\faroman"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\rin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\lin4820"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\itap0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfe1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\cgrid"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langnp2057"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfenp1033"
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\nooverflow"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\faroman"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\rin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\lin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\itap0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfe1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\cgrid"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langnp2057"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfenp1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\nooverflow"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\faroman"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\rin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\lin851"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\itap0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfe1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\cgrid"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langnp2057"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfenp1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\nooverflow"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\faroman"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\rin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\lin851"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\itap0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfe1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\cgrid"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langnp2057"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfenp1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\sautoupd"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\nooverflow"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\faroman"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\rin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\lin1843"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\itap0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfe1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\cgrid"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langnp2057"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfenp1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\sautoupd"
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\widctlpar"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\nooverflow"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\faroman"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\rin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\lin720"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\itap0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfe1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\cgrid"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langnp2057"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfenp1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\nooverflow"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\faroman"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\rin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\lin0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\itap0"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfe1033"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\cgrid"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langnp2057"
err:richedit:ReadStyleSheet ReadStyleSheet: unknown token "\langfenp1033"
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
fixme:ole:VARIANT_UserFree handle unknown complex type
fixme:shell:IShellLinkA_fnGetPath (0x78535840): WIN32_FIND_DATA is not yet filled.
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Prey Demo\\prey.exe") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:IShellLinkA_fnGetPath (0x78535840): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x7852f280): WIN32_FIND_DATA is not yet filled.
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\Prey Demo\\prey.exe") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:IShellLinkA_fnGetPath (0x7852f280): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x76f5ff80): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x76f5ff80): WIN32_FIND_DATA is not yet filled.
fixme:advapi:GetFileSecurityW (L"C:\\Program Files\\InstallShield Installation Information\\{C6E70A7A-2A2F-4E3E-B99A-C4B488314306}\\") : returns fake SECURITY_DESCRIPTOR
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-0f00-00000a000000}
err:rpc:I_RpcReceive we got fault packet with status 6be
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-0f00-00000a000000}
err:rpc:I_RpcReceive we got fault packet with status 6be

---

### Post by mooter on 2007-02-09
I got Prey for xmas.  It runs better on Linux!
I got a Geforce 6800XT and can run it full with the exception of Anistropix at 8X and no antialiasing, (maybe I'll try Anistropic 4x and 2x Antialias)

Anyway,  I can't get it to recognise my surround sound.  It should be automatic, I'm only hooked up throught digital coax (spdif) and AC3 Passthrough works.

Anyone else getting surround to work?
My sound is hda-intel ICH7 STAC92xx

Peace

---

