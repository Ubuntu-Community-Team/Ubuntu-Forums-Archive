---
title: "I can't make games work."
date: 2009-04-03
forum: Gaming &amp; Leisure
---

### Post by ariedry on 2009-04-03
everytime im runing a game thats happen ... even games for linux like Nexuiz ..


[IMG]http://i301.photobucket.com/albums/nn61/ariedry/screenshot2.png[/IMG]

---

### Post by kidux on 2009-04-03
Can you be more specific? Error codes spit out from terminal? What is happening, lock ups, crashes?

---

### Post by ariedry on 2009-04-03
nothing happen just that , im starting the game and that what happen ... the game is working but i cant see anythng just some colors >_>

---

### Post by RaiCoss on 2009-04-03
> **ariedry said:**
> nothing happen just that , im starting the game and that what happen ... the game is working but i cant see anythng just some colors >_>

Do you have an ATi card??

---

### Post by lisati on 2009-04-03
My two cents worth: my impressions is the picture looks like there's some kind of problem with the screen resolution, possibly due to needing a change in settings or installing of drivers.

As to a solution......

---

### Post by ariedry on 2009-04-03
ok ill try to change the resolution...

---

### Post by ariedry on 2009-04-03
Not working!!!!!!

---

### Post by ariedry on 2009-04-03
its kind of weird cuz its working for like 2 secs and then its going to that colors thing after im clicking on the screen..

---

### Post by hikaricore on 2009-04-03
You really need to give much more info about your system hardware and what version of which video driver you are using...

---

### Post by ariedry on 2009-04-03
> **hikaricore said:**
> You really need to give much more info about your system hardware and what version of which video driver you are using...

ok

---

### Post by ariedry on 2009-04-03
Laptop Acer Aspire 5730ZG
Intel Pentium DualCore T3200, Intel PM45 chipset, 2GB DDRII, HDD 250GB SATA, nVidia GeForce 9300M GS-256MB, HDMI, Dolby Home Theater 5.1 sound, S/PDIF, 5-in-1 card reader, 0.3MPix CrystalEye WebCam, WLAN 802.11 b/g/DraftN, GigaBit LAN, Modem,ExpressCard slot


well...

---

### Post by ariedry on 2009-04-03
Bump!!!!!

---

### Post by hikaricore on 2009-04-03
The next time you bump 6 minutes after posting I'll close your thread... it's not necessary.
Run:

> nvidia-settings

And see which driver release you're using.  Also please disable any desktop effects and test your games again if you're using them.

---

### Post by ariedry on 2009-04-03
ok 0.0 and ok >_>

:Edit: Thanks Man its worked :D :Edit:

---

### Post by Omecron on 2009-04-03
Did you enable the Nvidia drivers under System>Administration>Hardware Drivers?

---

### Post by hikaricore on 2009-04-03
Yea 0.0 is not a driver version...

---

### Post by wolfyking2 on 2009-04-03
ok, first of all, check the repos and what-not for Nvidia linux drivers.  Second, tell us the output of the games from a terminal.  If you don't know how to do that, drag the game launcher into a terminal, and whatever it says in the terminal, copy/paste it into your post so we can get an idea of what's wrong

---

### Post by ariedry on 2009-04-03
```
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x652ea8
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x652e80
fixme:ntoskrnl:KeInitializeEvent stub: 0x65256c 1 0
fixme:ntoskrnl:KeInitializeEvent stub: 0x652e6c 1 0
fixme:ntoskrnl:KeInitializeEvent stub: 0x652e90 1 0
fixme:ntoskrnl:KeInitializeEvent stub: 0x652ec0 1 0
fixme:ntoskrnl:KeInitializeEvent stub: 0x652e30 1 0
fixme:ntoskrnl:KeInitializeEvent stub: 0x652df0 1 0
fixme:ntoskrnl:KeInitializeEvent stub: 0x652e20 1 0
fixme:ntoskrnl:KeInitializeEvent stub: 0x652e10 1 0
fixme:ntoskrnl:KeInitializeEvent stub: 0x652530 1 0
wine: Call from 0x7b844350 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
wine: Unimplemented function ntoskrnl.exe.ExInitializeResourceLite called at address 0x7b844350 (thread 0014), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.ExInitializeResourceLite called in 32-bit code (0x7b8443c3).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b8443c3 ESP:0064e634 EBP:0064e698 EFLAGS:00000246(   - 00      - IZP1)
 EAX:7b82ec45 EBX:7b8b6ff4 ECX:00000000 EDX:0064e6bc
 ESI:0064e6bc EDI:00000001
Stack dump:
0x0064e634:  0064e6bc 00000008 0000003c 80000100
0x0064e644:  00000001 00000000 7b844350 00000002
0x0064e654:  7edf1dc0 7edf28a8 7edf072e 00110000
0x0064e664:  00000000 00117018 00000b00 0064e6a0
0x0064e674:  7edf0a7a 00110000 00000000 7edfbff4
0x0064e684:  00117018 0064e6a8 7b84435a 00000000
Backtrace:
=>0 0x7b8443c3 in kernel32 (+0x243c3) (0x0064e698)
  1 0x7edf1d58 in ntoskrnl (+0x11d58) (0x0064e6c8)
  2 0x7ede7448 in ntoskrnl (+0x7448) (0x0064e708)
  3 0x7ee72e67 in winedevice (+0x2e67) (0x0064e988)
  4 0x7ee73396 in winedevice (+0x3396) (0x0064e9d8)
  5 0x7ee47b7c in advapi32 (+0x27b7c) (0x0064ea28)
  6 0x7bc72c0e call_thread_entry_point+0xe() in ntdll (0x0064ea38)
  7 0x7bc74962 in ntdll (+0x64962) (0x0064ead8)
  8 0x7bc74b30 in ntdll (+0x64b30) (0x0064f3c8)
  9 0xb7e5750f start_thread+0xbf() in libpthread.so.0 (0x0064f4c8)
  10 0xb7dd3a0e __clone+0x5e() in libc.so.6 (0x00000000)
0x7b8443c3: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (28 modules)
PE	  650000-  654a80	Deferred        aavmker4.sys
ELF	7b800000-7b93e000	Export          kernel32<elf>
  \-PE	7b820000-7b93e000	\               kernel32
ELF	7bc00000-7bcb0000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb0000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ece0000-7ecf7000	Deferred        hal<elf>
  \-PE	7ecf0000-7ecf7000	\               hal
ELF	7ecf7000-7ed65000	Deferred        msvcrt<elf>
  \-PE	7ed10000-7ed65000	\               msvcrt
ELF	7ed65000-7edd1000	Deferred        rpcrt4<elf>
  \-PE	7ed70000-7edd1000	\               rpcrt4
ELF	7edd1000-7ee0b000	Export          ntoskrnl<elf>
  \-PE	7ede0000-7ee0b000	\               ntoskrnl
ELF	7ee0b000-7ee61000	Export          advapi32<elf>
  \-PE	7ee20000-7ee61000	\               advapi32
ELF	7ee61000-7ee76000	Export          winedevice<elf>
  \-PE	7ee70000-7ee76000	\               winedevice
ELF	7ee76000-7ee8f000	Deferred        libnsl.so.1
ELF	7ee8f000-7ee98000	Deferred        libnss_compat.so.2
ELF	7efc9000-7efef000	Deferred        libm.so.6
ELF	7eff4000-7f000000	Deferred        libnss_files.so.2
ELF	b7ce2000-b7ced000	Deferred        libnss_nis.so.2
ELF	b7cee000-b7cf2000	Deferred        libdl.so.2
ELF	b7cf2000-b7e50000	Export          libc.so.6
ELF	b7e51000-b7e6a000	Export          libpthread.so.0
ELF	b7e7b000-b7fb6000	Deferred        libwine.so.1
ELF	b7fb8000-b7fd5000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f (D) C:\windows\system32\winedevice.exe
	00000014    0 <==
	00000011    0
	00000010    0
Backtrace:
=>0 0x7b8443c3 in kernel32 (+0x243c3) (0x0064e698)
  1 0x7edf1d58 in ntoskrnl (+0x11d58) (0x0064e6c8)
  2 0x7ede7448 in ntoskrnl (+0x7448) (0x0064e708)
  3 0x7ee72e67 in winedevice (+0x2e67) (0x0064e988)
  4 0x7ee73396 in winedevice (+0x3396) (0x0064e9d8)
  5 0x7ee47b7c in advapi32 (+0x27b7c) (0x0064ea28)
  6 0x7bc72c0e call_thread_entry_point+0xe() in ntdll (0x0064ea38)
  7 0x7bc74962 in ntdll (+0x64962) (0x0064ead8)
  8 0x7bc74b30 in ntdll (+0x64b30) (0x0064f3c8)
  9 0xb7e5750f start_thread+0xbf() in libpthread.so.0 (0x0064f4c8)
  10 0xb7dd3a0e __clone+0x5e() in libc.so.6 (0x00000000)
wine: Call from 0x7b844350 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
wine: Call from 0x7b844350 to unimplemented function ntoskrnl.exe.ExInitializeResourceLite, aborting
err:module:import_dll Library NDIS.SYS (which is needed by L"C:\\windows\\system32\\drivers\\aswSP.sys") not found
err:winedevice:ServiceMain driver L"aswSP" failed to load
err:module:import_dll Library TDI.SYS (which is needed by L"C:\\windows\\system32\\drivers\\aswTdi.sys") not found
err:winedevice:ServiceMain driver L"aswTdi" failed to load
fixme:reg:GetNativeSystemInfo (0x33fba8) using GetSystemInfo()
fixme:advapi:RegisterEventSourceA ((null),"avast!"): stub
fixme:advapi:RegisterEventSourceW (L"",L"avast!"): stub
fixme:advapi:LsaOpenPolicy ((null),0x33f9bc,0x00000001,0x33f9d8) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -120, std (d/m/y): 27/09/2009, dlt (d/m/y): 27/03/2009
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0004,0x4200005a,(nil),0x0001,0x00000000,0x93b584,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0004,0x4200005a,(nil),0x0001,0x00000000,0x13d9d0,(nil)): stub
err:eventlog:ReportEventW L"AAVM - initialization error: AavmStart: Cannot load core driver!!!, 00000002.  "
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0004,0x4200005a,(nil),0x0001,0x00000000,0x93d664,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0004,0x4200005a,(nil),0x0001,0x00000000,0x13d9d0,(nil)): stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0004,0x4200005a,(nil),0x0001,0x00000000,0x93c914,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0004,0x4200005a,(nil),0x0001,0x00000000,0x13de80,(nil)): stub
err:eventlog:ReportEventW L"Internal error has occurred in module ChestS, function chestStart.  "
err:ole:RpcEpUnregister ept_insert failed with error 1753
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0x20db648 0x20db64c
WARNING: Trying to use ICMP (network ping) will fail unless running as root
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0x20db64c 0x20db650
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -120, std (d/m/y): 27/09/2009, dlt (d/m/y): 27/03/2009
Nexuiz Windows 08:04:14 Apr  2 2009 8846 release
Trying to load library... "shfolder.dll" - loaded.
Trying to load library... "zlib1.dll" - loaded.
WARNING: base gamedir data/ not found!
fixme:msvcrt:MSVCRT__sopen : pmode 0x01b6 ignored
Trying to load library... "libcurl-4.dll" - loaded.
Trying to load library... "libvorbis.dll" "vorbis.dll" - loaded.
Trying to load library... "libvorbisfile.dll" "vorbisfile.dll" - loaded.
Trying to load library... "libmodplug-0.dll" - loaded.
Trying to load library... "libogg.dll" "ogg.dll" - loaded.
Trying to load library... "libtheora.dll" - loaded.
Trying to load library... "libvorbis.dll" "vorbis.dll" - loaded.
Trying to load library... "libvorbisenc.dll" "vorbisenc.dll" - loaded.
Trying to load library... "OffscreenGecko.dll" - failed.
couldn't exec quake.rc
couldn't exec default.cfg
execing config.cfg
couldn't exec autoexec.cfg
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:0
Initializing Video Mode: fullscreen 640x480x32x60hz
Loading OpenGL driver opengl32.dll
GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Mobile IntelB. GM45 Express Chipset 20061102 x86/MMX/SSE2
GL_VERSION: 1.4 Mesa 7.2
DirectInput not initialized

joystick not found -- no valid joysticks (a5)

Trying to load library... "libjpeg.dll" - loaded.
Trying to load library... "libpng12.dll" - loaded.
Draw_CachePic: failed to load gfx/loading
Draw_CachePic: failed to load gfx/num_0
Draw_CachePic: failed to load gfx/num_1
Draw_CachePic: failed to load gfx/num_2
Draw_CachePic: failed to load gfx/num_3
Draw_CachePic: failed to load gfx/num_4
Draw_CachePic: failed to load gfx/num_5
Draw_CachePic: failed to load gfx/num_6
Draw_CachePic: failed to load gfx/num_7
Draw_CachePic: failed to load gfx/num_8
Draw_CachePic: failed to load gfx/num_9
Draw_CachePic: failed to load gfx/num_minus
Draw_CachePic: failed to load gfx/num_colon
Draw_CachePic: failed to load gfx/sb_shells
Draw_CachePic: failed to load gfx/sb_bullets
Draw_CachePic: failed to load gfx/sb_rocket
Draw_CachePic: failed to load gfx/sb_cells
Draw_CachePic: failed to load gfx/sb_armor
Draw_CachePic: failed to load gfx/sb_health
Draw_CachePic: failed to load gfx/sb_slowmo
Draw_CachePic: failed to load gfx/sb_invinc
Draw_CachePic: failed to load gfx/sb_energy
Draw_CachePic: failed to load gfx/sb_str
Draw_CachePic: failed to load gfx/sb_flag_red_taken
Draw_CachePic: failed to load gfx/sb_flag_red_lost
Draw_CachePic: failed to load gfx/sb_flag_red_carrying
Draw_CachePic: failed to load gfx/sb_key_carrying
Draw_CachePic: failed to load gfx/sb_flag_blue_taken
Draw_CachePic: failed to load gfx/sb_flag_blue_lost
Draw_CachePic: failed to load gfx/sb_flag_blue_carrying
Draw_CachePic: failed to load gfx/sbar
Draw_CachePic: failed to load gfx/sbar_minimal
Draw_CachePic: failed to load gfx/sbar_overlay
Draw_CachePic: failed to load gfx/inv_weapon0
Draw_CachePic: failed to load gfx/inv_weapon1
Draw_CachePic: failed to load gfx/inv_weapon2
Draw_CachePic: failed to load gfx/inv_weapon3
Draw_CachePic: failed to load gfx/inv_weapon4
Draw_CachePic: failed to load gfx/inv_weapon5
Draw_CachePic: failed to load gfx/inv_weapon6
Draw_CachePic: failed to load gfx/inv_weapon7
Draw_CachePic: failed to load gfx/inv_weapon8
Draw_CachePic: failed to load gfx/ranking
Draw_CachePic: failed to load gfx/complete
Draw_CachePic: failed to load gfx/inter
Draw_CachePic: failed to load gfx/finale
S_Startup: initializing sound output format: 48000Hz, 16 bit, 2 channels...
SndSys_Init: using the Win32 module
Set primary sound buffer format: yes
Using secondary sound buffer
   2 channel(s)
   16 bits/sample
   48000 samples/sec
DirectSound initialized
Sound format: 48000Hz, 2 channels, 16 bits per sample
CDAudio_SysGetAudioDiskInfo: drive not ready
CDAudio_Init: No CD in player.
Can't get initial CD volume
CD Audio Initialized
Draw_CachePic: failed to load gfx/mainmenu
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0xa4ea10 0xa4ea14
fixme:msvcrt:MSVCRT__sopen : pmode 0x01b6 ignored
fixme:wtsapi:WTSEnumerateSessionsA Stub (nil) 0x00000000 0x00000001 0xa4ea10 0xa4ea14
```

---

### Post by ariedry on 2009-04-03
its found Broadcom STA wireless driver ,
when i active its disconnecting from the nextwork:mad:

---

### Post by FrozenFox on 2009-04-03
These lines you posted popped out at me..

* lines starting in 'wine' and 'fixme'
* Nexuiz Windows 08:04:14 Apr  2 2009 8846 release
* GL_VENDOR: Tungsten Graphics, Inc
* GL_RENDERER: Mesa DRI Mobile IntelB. GM45 Express Chipset 20061102 x86/MMX/SSE2
* GL_VERSION: 1.4 Mesa 7.2


First, this clearly suggests you're trying to run the Windows version of nexuiz through "Wine". If that's so, -why-? You should be running the native -linux- version of nexuiz. You can install it from Synaptic Package Manager.. you would be well advised to look into how to install packages on ubuntu properly before continuing further.

Next, the renderer stuff gives me the clear impression that you haven't installed your video drivers or they are not installed properly. I'm not sure how stuff could display for just a moment as you described earlier if no drivers at all installed, but from the output you gave, I figure it's possible. Please look into how to install your drivers, as mentioned before. There are countless tutorials on how to do so around online.

In the terminal, run "glxinfo | grep direct" and "glxgears". The first command should say yes, direct rendering is enabled. If it doesn't, your video drivers aren't installed or are not working. The second command should show you a short demo of '3d' gears turning, a demonstration of functioning or somewhat functioning 3d-capable video drivers.

---

### Post by hikaricore on 2009-04-03
User obviously needs to search around the forum for info on installing nvidia graphics drivers.
This is not an issue with the games themselves but is infact the user not understanding the situation.

---

### Post by Bölvaður on 2009-04-03
1. Do not expect games to work in Wine, not without making sure it has high rating and with tweaking.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15484](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15484) I have never seen anything else than "garbage" rating on the wine website for a long time, so I was surprised to see scrambled image.. that is quite good compared to not being able to launch the window in the first place.

So I would judge this thread to be moved to the wine section?
or is the graphic card still a mastery? I thought that card is well supported and shouldn't be any trouble.


2. Installing games line nexuis is often easy to do from :
(move your pointer to the upper left corner of the screen); Applications &#8594; Add/Remove
You can find many fun games on there and the most amazing programs.


3. 6 minute bump is a cause for a celebration, this is a new record on the forum isn't it? Well... if we do not include the bump thread....

---

### Post by axelroo on 2009-04-04
By default Ubuntu/Kubuntu will use generic drivers for your display and rendering.  Even with the game and wine properly installed. Most 3d accelerated rendering will be slow and funky until you have the official nVidia or ATi drivers.  One way to make sure is consult the hardware drivers utility: jockey-gtk (Ubunutu) or jockey-kde (Kubuntu).  Often this program will point you in the right direction of installing the official drivers for your card.

You can also check the availability of rending using (in the terminal): glxinfo and glxgears.  If anything about Mesa turns up in glxinfo, that usually means the official drivers aren't installed. Hope that helps

---

### Post by Dejai on 2009-04-04
You would have to give us a whole range of specs starting with:
lspci | grep VGA

That error as in your above screen shot is a common problem many Linux gamers have and I believe there are many work arounds. I would suggest looking up your game on winehq and then following their instructions for execution. And hold on isn't this breaking the one and only rule of this forum?

---

