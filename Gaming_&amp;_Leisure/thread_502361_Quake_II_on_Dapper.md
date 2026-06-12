---
title: "Quake II on Dapper"
date: 2007-07-16
forum: Gaming &amp; Leisure
---

### Post by VoiceOvGod on 2007-07-16
Trying to get Quake 2 to run on Dapper.

Using WINE .99

Quake 2 acts like its going to load up, but ends up not loading at all.

Get following error:

```
~/.wine/dosdevices/c:/QuakeII$ wine: Unhandled page fault on read access to 0x7de70000 at address 0xb7e7d9dc (thread 0021), starting debugger...WineDbg starting on pid 0x20
Unhandled exception: page fault on read access to 0x7de70000 in 32-bit code (0xb7e7d9dc).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:b7e7d9dc ESP:7fb8fcdc EBP:7fb8fd18 EFLAGS:00010216(   - 00      -RIAP1)
 EAX:7de60088 EBX:7f897bc0 ECX:00003e09 EDX:7fd4b790
 ESI:7de70000 EDI:7fd5b71c
Stack dump:
0x7fb8fcdc:  7f85f82e 7fd4b7a4 7de60088 0001f79c
0x7fb8fcec:  7f89767c ffffffff 0040f0ca 0001f79c
0x7fb8fcfc:  00401045 7de61270 0041f019 00000348
0x7fb8fd0c:  0005003a 7fc381aa 0041f019 7fb8fd88
0x7fb8fd1c:  004031be 7de60088 0005003a 00000100
0x7fb8fd2c:  7fb8fd88 7f98f664 00000000 00000000
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0xb7e7d9dc memcpy+0x1c in libc.so.6 (0xb7e7d9dc)
  2 0x004031be in register (+0x31be) (0x004031be)
  3 0x7f96b842 in user32 (+0x9b842) (0x7f96b842)
  4 0x7f96f001 CallWindowProcA+0x79 in user32 (0x7f96f001)
  5 0x7f939e65 DispatchMessageA+0x169 in user32 (0x7f939e65)
  6 0x00404485 in register (+0x4485) (0x00404485)
0xb7e7d9dc memcpy+0x1c in libc.so.6: repe movsl (%esi),%es:(%edi)
Modules:
Module  Address                 Debug info      Name (84 modules)
PE      0x00400000-0042f000     Export          register
PE      0x10000000-1001a000     Deferred        getinfo
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e4ab000-7e4c0000     Deferred        midimap<elf>
  \-PE  0x7e4b0000-7e4c0000     \               midimap
ELF     0x7e5dd000-7e603000     Deferred        msacm32<elf>
  \-PE  0x7e5e0000-7e603000     \               msacm32
ELF     0x7e603000-7e647000     Deferred        wineoss<elf>
  \-PE  0x7e610000-7e647000     \               wineoss
ELF     0x7e647000-7e693000     Deferred        libgcrypt.so.11
ELF     0x7e693000-7e6a3000     Deferred        libtasn1.so.2
ELF     0x7e6a3000-7e6d0000     Deferred        libcrypt.so.1
ELF     0x7e6d1000-7e6e9000     Deferred        msacm<elf>
  \-PE  0x7e6e0000-7e6e9000     \               msacm
ELF     0x7e6e9000-7e752000     Deferred        libgnutls.so.12
ELF     0x7e752000-7e780000     Deferred        libcups.so.2
ELF     0x7e7c4000-7e7c8000     Deferred        libgpg-error.so.0
ELF     0x7e815000-7e846000     Deferred        uxtheme<elf>
  \-PE  0x7e820000-7e846000     \               uxtheme
ELF     0x7e864000-7e868000     Deferred        libxfixes.so.3
ELF     0x7e868000-7e884000     Deferred        imm32<elf>
  \-PE  0x7e870000-7e884000     \               imm32
ELF     0x7e884000-7f047000     Deferred        libglcore.so.1
ELF     0x7f047000-7f0cc000     Deferred        libgl.so.1
ELF     0x7f0cc000-7f1b2000     Deferred        libx11.so.6
ELF     0x7f1b2000-7f1ca000     Deferred        libice.so.6
ELF     0x7f1ca000-7f24d000     Deferred        winex11<elf>
  \-PE  0x7f1e0000-7f24d000     \               winex11
ELF     0x7f24d000-7f26c000     Deferred        libexpat.so.1
ELF     0x7f26c000-7f29a000     Deferred        libfontconfig.so.1
ELF     0x7f29a000-7f2ae000     Deferred        libz.so.1
ELF     0x7f2ae000-7f318000     Deferred        libfreetype.so.6
ELF     0x7f318000-7f3a0000     Deferred        winmm<elf>
  \-PE  0x7f320000-7f3a0000     \               winmm
ELF     0x7f3a0000-7f3cc000     Deferred        winspool<elf>
  \-PE  0x7f3b0000-7f3cc000     \               winspool
ELF     0x7f3cc000-7f48c000     Deferred        comctl32<elf>
  \-PE  0x7f3e0000-7f48c000     \               comctl32
ELF     0x7f48c000-7f4d5000     Deferred        rpcrt4<elf>
  \-PE  0x7f4a0000-7f4d5000     \               rpcrt4
ELF     0x7f4d5000-7f566000     Deferred        ole32<elf>
  \-PE  0x7f4f0000-7f566000     \               ole32
ELF     0x7f566000-7f5c1000     Deferred        shlwapi<elf>
  \-PE  0x7f580000-7f5c1000     \               shlwapi
ELF     0x7f5c1000-7f68d000     Deferred        shell32<elf>
  \-PE  0x7f5e0000-7f68d000     \               shell32
ELF     0x7f68d000-7f72a000     Deferred        comdlg32<elf>
  \-PE  0x7f6a0000-7f72a000     \               comdlg32
ELF     0x7f7ff000-7f8b0000     Deferred        gdi32<elf>
  \-PE  0x7f810000-7f8b0000     \               gdi32
ELF     0x7f8b0000-7f9dc000     Export          user32<elf>
  \-PE  0x7f8d0000-7f9dc000     \               user32
ELF     0x7f9dc000-7fa1c000     Deferred        advapi32<elf>
  \-PE  0x7f9f0000-7fa1c000     \               advapi32
ELF     0x7fa1c000-7fa3b000     Deferred        iphlpapi<elf>
  \-PE  0x7fa20000-7fa3b000     \               iphlpapi
ELF     0x7fa3b000-7fa66000     Deferred        ws2_32<elf>
  \-PE  0x7fa40000-7fa66000     \               ws2_32
ELF     0x7fa66000-7fa80000     Deferred        wsock32<elf>
  \-PE  0x7fa70000-7fa80000     \               wsock32
ELF     0x7fb92000-7fb9b000     Deferred        libxcursor.so.1
ELF     0x7fbce000-7fcd0000     Deferred        kernel32<elf>
  \-PE  0x7fbf0000-7fcd0000     \               kernel32
ELF     0x7fcd3000-7fce0000     Deferred        libxext.so.6
ELF     0x7fdf0000-7fdf8000     Deferred        libxrender.so.1
ELF     0x7fdf8000-7fdfb000     Deferred        libxau.so.6
ELF     0x7fdfb000-7fe00000     Deferred        libxxf86vm.so.1
ELF     0x7fe00000-7fe0a000     Deferred        libnss_files.so.2
ELF     0x7fe0a000-7fe13000     Deferred        libnss_nis.so.2
ELF     0x7fe13000-7fe28000     Deferred        libnsl.so.1
ELF     0x7fe28000-7fe31000     Deferred        libnss_compat.so.2
ELF     0x7fe31000-7fe36000     Deferred        libxxf86dga.so.1
ELF     0x7fe36000-7fe40000     Deferred        libgcc_s.so.1
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e00000-b7e02000     Deferred        libnvidia-tls.so.1
ELF     0xb7e0f000-b7e12000     Deferred        libdl.so.2
ELF     0xb7e12000-b7f41000     Export          libc.so.6
ELF     0xb7f41000-b7f53000     Deferred        libpthread.so.0
ELF     0xb7f6d000-b7f87000     Deferred        libwine.so.1
ELF     0xb7f8a000-b7fa0000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000020 (D) C:\QuakeII\Splash\Register.exe
        00000022    0
        00000021    0 <==
00000015
        0000001c    0
00000019
        0000001b    0
        0000001a    0
00000015
        00000018    0
        00000016    0
00000012
        00000014    0
        00000013    0
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Quake2\\q2.ico") failed, error 193
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Quake2\\q2.ico") failed, error 193
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Quake2\\q2.ico") failed, error 193
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\windows\\system32\\notepad.exe \"C:\\Quake2\\Docs\\Readme.txt\"") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\windows\\system32\\notepad.exe \"C:\\Quake2\\Docs\\Release.txt\"") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Quake2\\Docs\\Manual.html") failed, error 193
err:menubuilder:ExtractFromICO Invalid ico file format
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink



```

---

### Post by VoiceOvGod on 2007-07-16
Problem also occurred when trying to use Starcraft.

---

### Post by Steveway on 2007-07-16
Why are you trying to run Quake with Wine?
You only need Quake 2 and Quake 2 data from Synaptic and of course your CD's with the .wad files.

---

### Post by VoiceOvGod on 2007-07-16
Well, I'll be. I did not know that.

Thanks!

Where do I store the WAD files?

---

### Post by Steveway on 2007-07-16
I think quake2-data asks for the location, so you could leave them on the CD.
I can't say this for sure, cause I don't own Quake2.
And, by the way, have you taken a look into warsow? [www.warsow.net](www.warsow.net)
It uses the Quake2 engine with modifications from the Quake3 engine and is a pretty nice multiplayer shooter.

---

### Post by VoiceOvGod on 2007-07-16
Now I get this:

```
~$ quake2
***** WARNING *****

   The networking part of Quake II (especially the server part) contains
   several unfixed security issues. Therefore, Quake II should not be
   used over untrusted networks (like the internet). The version
   included in Debian is intended only for local play.

   See for an possibly non-exhaustive list of issues:
   http://archives.neohapsis.com/archives/bugtraq/2004-10/0299.html
   http://www.r1ch.net/stuff/r1q2/
   http://bugs.debian.org/280573

*******************

Do you understand the security implications of continuing?
y
QuakeIIForge 0.3
using /home/shiva/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
/dev/dsp: Input/output error
SNDDMA_Init: Could not mmap /dev/dsp.
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
recursive shutdown
Error: Couldn't load pics/colormap.pcx

```

---

### Post by VoiceOvGod on 2007-07-16
Ok, got it to actually run in WINE, but the sound isn't working... advice?

---

### Post by Steveway on 2007-07-16
> ------- sound initialization -------
loading oss sound output driver, ok
/dev/dsp: Input/output error
SNDDMA_Init: Could not mmap /dev/dsp.
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
recursive shutdown
Error: Couldn't load pics/colormap.pcx
There seems to be a problem with your soundsetup, do other soundapps work?

---

### Post by VoiceOvGod on 2007-07-16
My sound works fine except for in WINE.

---

### Post by VoiceOvGod on 2007-07-16
Also getting this:

```
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory


```

---

### Post by VoiceOvGod on 2007-07-16
Got it! had to install the ALSA-oss package.

Thanks!

---

### Post by VoiceOvGod on 2007-07-17
I just tried to start it up again, and now it wont acknowledge the CD drives.

WTF am I messing up?

---

