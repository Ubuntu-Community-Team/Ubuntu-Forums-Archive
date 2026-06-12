---
title: "Wine Errors"
date: 2007-06-03
forum: Gaming &amp; Leisure
---

### Post by Nerdyboy42a on 2007-06-03
Hello.  I'm trying to run a game called Ever17 using wine.  I installed it to wine's virtual C: drive and then tried to run it using the terminal, and wine spits out this code:

```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
wine: Unhandled page fault on read access to 0x72756f43 at address 0x4137a1 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x72756f43 in 32-bit code (0x004137a1).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:004137a1 ESP:0033fc18 EBP:00000000 EFLAGS:00010206(   - 00      - RIP1)
 EAX:72756f43 EBX:0043ca6c ECX:72756f4d EDX:0038f08e
 ESI:007ca9dc EDI:72756f43
Stack dump:
0x0033fc18:  007ca9dc 00000000 0043ca6c 00413359
0x0033fc28:  007ca9dc 72756f43 7b882156 7b881fe4
0x0033fc38:  00000000 0040e1ec 00178f18 7b881fe4
0x0033fc48:  7b882156 72617473 2e707574 00726373
0x0033fc58:  5f435037 625c7375 642e6d67 74007461
0x0033fc68:  00330000 0033fc70 00000000 00000000
Backtrace:
=>1 0x004137a1 in ever17pc_us (+0x137a1) (0x00000000)
0x004137a1: movb        0x0(%edi),%bl
Modules:
Module  Address                 Debug info      Name (87 modules)
PE        400000-  80c000       Export          ever17pc_us
ELF     7b800000-7b921000       Deferred        kernel32<elf>
  \-PE  7b820000-7b921000       \               kernel32
ELF     7bc00000-7bc94000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc94000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cc07000-7cc1b000       Deferred        winejoystick<elf>
  \-PE  7cc10000-7cc1b000       \               winejoystick
ELF     7d217000-7d2ae000       Deferred        oleaut32<elf>
  \-PE  7d230000-7d2ae000       \               oleaut32
ELF     7d2ae000-7d2c2000       Deferred        lz32<elf>
  \-PE  7d2b0000-7d2c2000       \               lz32
ELF     7d2c2000-7d2db000       Deferred        version<elf>
  \-PE  7d2d0000-7d2db000       \               version
ELF     7d2db000-7d302000       Deferred        msvfw32<elf>
  \-PE  7d2e0000-7d302000       \               msvfw32
ELF     7d302000-7d35c000       Deferred        quartz<elf>
  \-PE  7d310000-7d35c000       \               quartz
ELF     7d380000-7d3b2000       Deferred        uxtheme<elf>
  \-PE  7d390000-7d3b2000       \               uxtheme
ELF     7d3b2000-7d3c7000       Deferred        midimap<elf>
  \-PE  7d3c0000-7d3c7000       \               midimap
ELF     7d3c7000-7d3df000       Deferred        msacm32<elf>
  \-PE  7d3d0000-7d3df000       \               msacm32
ELF     7d3df000-7d497000       Deferred        libasound.so.2
ELF     7d497000-7d4c9000       Deferred        winealsa<elf>
  \-PE  7d4a0000-7d4c9000       \               winealsa
ELF     7d773000-7d778000       Deferred        libxfixes.so.3
ELF     7d778000-7d781000       Deferred        libxcursor.so.1
ELF     7d781000-7d79d000       Deferred        imm32<elf>
  \-PE  7d790000-7d79d000       \               imm32
ELF     7d79d000-7d7bb000       Deferred        ximcp.so.2
ELF     7d7bb000-7d7bd000       Deferred        xlcutf8load.so.2
ELF     7d7bd000-7d7c0000       Deferred        libxrandr.so.2
ELF     7d7c0000-7d7c8000       Deferred        libxrender.so.1
ELF     7daf4000-7e465000       Deferred        libglcore.so.1
ELF     7e465000-7e4f9000       Deferred        libgl.so.1
ELF     7e4f9000-7e4fe000       Deferred        libxdmcp.so.6
ELF     7e4fe000-7e501000       Deferred        libxau.so.6
ELF     7e501000-7e5ca000       Deferred        libx11.so.6
ELF     7e5ca000-7e5d7000       Deferred        libxext.so.6
ELF     7e5d7000-7e5dc000       Deferred        libxxf86vm.so.1
ELF     7e5dc000-7e5f4000       Deferred        libice.so.6
ELF     7e5f4000-7e682000       Deferred        winex11<elf>
  \-PE  7e600000-7e682000       \               winex11
ELF     7e682000-7e6a0000       Deferred        libexpat.so.1
ELF     7e6a0000-7e6cf000       Deferred        libfontconfig.so.1
ELF     7e6cf000-7e6e3000       Deferred        libz.so.1
ELF     7e6e3000-7e74d000       Deferred        libfreetype.so.6
ELF     7e74d000-7e80b000       Deferred        comctl32<elf>
  \-PE  7e760000-7e80b000       \               comctl32
ELF     7e80b000-7e862000       Deferred        shlwapi<elf>
  \-PE  7e820000-7e862000       \               shlwapi
ELF     7e862000-7e959000       Deferred        shell32<elf>
  \-PE  7e870000-7e959000       \               shell32
ELF     7e959000-7e96c000       Deferred        libresolv.so.2
ELF     7e96c000-7e98b000       Deferred        iphlpapi<elf>
  \-PE  7e970000-7e98b000       \               iphlpapi
ELF     7e98b000-7e9df000       Deferred        rpcrt4<elf>
  \-PE  7e9a0000-7e9df000       \               rpcrt4
ELF     7e9df000-7ea78000       Deferred        ole32<elf>
  \-PE  7e9f0000-7ea78000       \               ole32
ELF     7ea78000-7eac0000       Deferred        dsound<elf>
  \-PE  7ea80000-7eac0000       \               dsound
ELF     7eac0000-7eb04000       Deferred        advapi32<elf>
  \-PE  7ead0000-7eb04000       \               advapi32
ELF     7eb04000-7eb0f000       Deferred        libgcc_s.so.1
ELF     7eb0f000-7eb11000       Deferred        libnvidia-tls.so.1
ELF     7eb11000-7eb1a000       Deferred        libsm.so.6
ELF     7ebf9000-7ecb1000       Deferred        gdi32<elf>
  \-PE  7ec10000-7ecb1000       \               gdi32
ELF     7ecb1000-7ede7000       Deferred        user32<elf>
  \-PE  7ecd0000-7ede7000       \               user32
ELF     7ede7000-7ee74000       Deferred        winmm<elf>
  \-PE  7edf0000-7ee74000       \               winmm
ELF     7ee74000-7ee9a000       Deferred        msacm32<elf>
  \-PE  7ee80000-7ee9a000       \               msacm32
ELF     7efa4000-7efaf000       Deferred        libnss_files.so.2
ELF     7efaf000-7efb9000       Deferred        libnss_nis.so.2
ELF     7efb9000-7efcf000       Deferred        libnsl.so.1
ELF     7efcf000-7eff5000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7ca6000-b7caa000       Deferred        libdl.so.2
ELF     b7caa000-b7dde000       Deferred        libc.so.6
ELF     b7ddf000-b7df2000       Deferred        libpthread.so.0
ELF     b7dfd000-b7f11000       Deferred        libwine.so.1
ELF     b7f13000-b7f2e000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\KID\ever17PC_us\ever17PC_us.exe
        0000000e    0
        0000000d   15
        00000009    0 <==

```

I'm not really sure what any of this means, so if any of you do and could tell me, and possibly also tell me how to fix it, it would be greatly appreciated.

Thanks in advance!

---

### Post by Ferrat on 2007-06-04
> ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
wine: Unhandled page fault on read access to 0x72756f43 at address 0x4137a1 (thread 0009), starting debugger...


This is the reason you get a debug, your ALSA lib tries to open something that ain't there, try reinstalling ALSA and make sure you get it all

---

### Post by Nerdyboy42a on 2007-06-09
I tried this and reinstalled the following files (and purged them first to get rid of bum settings) (by using the following command):

sudo apt-get install linux-sound-base alsa-base alsa-utils

I can open the ALSA mixer from my terminal just fine, and double checked that the sound card is selected as the default card, but the game still throws up the same errors.

Sorry for all the trouble, and again the help is _most_ appreciated.

---

### Post by Peetke on 2007-06-10
What wine version are you using? What windows version do you have selected for the game in winecfg?

---

### Post by Nerdyboy42a on 2007-06-10
I have Wine 0.9.38 installed and have it configured to emulate windows XP.  Setting it just now to windows 98 didn't seem to change anything.

---

### Post by Nerdyboy42a on 2007-06-15
*bump*

---

### Post by cogadh on 2007-06-15
Do you have the English version of the game, or are you trying to run the Japanese import version?

---

### Post by Nerdyboy42a on 2007-06-16
I have the English version that came without corrupted voice files (unlike the first pressing).

---

### Post by cogadh on 2007-06-16
Try installing the native Windows DCOM package, it can sometimes fix problems like this. 
Instructions: [http://wiki.winehq.org/NativeDcom](http://wiki.winehq.org/NativeDcom)

However, it should be noted that using this may make other Wine apps function incorrectly. If you only need Wine to run this app and installing DCOM works, that shouldn't be a problem. Just to be on the safe side, I would modify the step where you remove (delete) Wine's built-in "fake" DLLs. Instead of deleting them, move them to your home folder so you can restore them if you have to.

---

### Post by Nerdyboy42a on 2007-06-16
Sorry, same error.  I've reposted the code in case there is any changes I didn't notice:

```
wolf@wolf-desktop:~$ wine '/home/wolf/.wine/drive_c/KID/ever17PC_us/ever17PC_us.exe' 
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
wine: Unhandled page fault on read access to 0x72756f43 at address 0x4137a1 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x72756f43 in 32-bit code (0x004137a1).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:004137a1 ESP:0033fc18 EBP:00000000 EFLAGS:00010206(   - 00      - RIP1)
 EAX:72756f43 EBX:0043ca6c ECX:72756f4d EDX:0038f08e
 ESI:007ca9dc EDI:72756f43
Stack dump:
0x0033fc18:  007ca9dc 00000000 0043ca6c 00413359
0x0033fc28:  007ca9dc 72756f43 7b882156 7b881fe4
0x0033fc38:  00000000 0040e1ec 001794d8 7b881fe4
0x0033fc48:  7b882156 72617473 2e707574 00726373
0x0033fc58:  5f435037 625c7375 642e6d67 74007461
0x0033fc68:  00330000 0033fc70 00000000 00000000
Backtrace:
=>1 0x004137a1 in ever17pc_us (+0x137a1) (0x00000000)
0x004137a1: movb        0x0(%edi),%bl
Modules:
Module  Address                 Debug info      Name (80 modules)
PE        400000-  80c000       Export          ever17pc_us
PE      65340000-653d2000       Deferred        oleaut32
PE      65f00000-65fc2000       Deferred        ole32
ELF     7b800000-7b921000       Deferred        kernel32<elf>
  \-PE  7b820000-7b921000       \               kernel32
ELF     7bc00000-7bc94000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc94000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ccb2000-7ccc6000       Deferred        winejoystick<elf>
  \-PE  7ccc0000-7ccc6000       \               winejoystick
ELF     7d3d3000-7d3e7000       Deferred        lz32<elf>
  \-PE  7d3e0000-7d3e7000       \               lz32
ELF     7d3e7000-7d400000       Deferred        version<elf>
  \-PE  7d3f0000-7d400000       \               version
ELF     7d400000-7d427000       Deferred        msvfw32<elf>
  \-PE  7d410000-7d427000       \               msvfw32
ELF     7d427000-7d481000       Deferred        quartz<elf>
  \-PE  7d430000-7d481000       \               quartz
ELF     7d4a5000-7d4d7000       Deferred        uxtheme<elf>
  \-PE  7d4b0000-7d4d7000       \               uxtheme
ELF     7d4d7000-7d4ec000       Deferred        midimap<elf>
  \-PE  7d4e0000-7d4ec000       \               midimap
ELF     7d4ec000-7d504000       Deferred        msacm32<elf>
  \-PE  7d4f0000-7d504000       \               msacm32
ELF     7d504000-7d5bc000       Deferred        libasound.so.2
ELF     7d5bc000-7d5ee000       Deferred        winealsa<elf>
  \-PE  7d5d0000-7d5ee000       \               winealsa
ELF     7d894000-7d899000       Deferred        libxfixes.so.3
ELF     7d899000-7d8a2000       Deferred        libxcursor.so.1
ELF     7d8a2000-7d8be000       Deferred        imm32<elf>
  \-PE  7d8b0000-7d8be000       \               imm32
ELF     7d8be000-7d8dc000       Deferred        ximcp.so.2
ELF     7d8dc000-7d8de000       Deferred        xlcutf8load.so.2
ELF     7d8de000-7d8e1000       Deferred        libxrandr.so.2
ELF     7d8e1000-7d8e9000       Deferred        libxrender.so.1
ELF     7dc13000-7e584000       Deferred        libglcore.so.1
ELF     7e584000-7e618000       Deferred        libgl.so.1
ELF     7e618000-7e61d000       Deferred        libxdmcp.so.6
ELF     7e61d000-7e620000       Deferred        libxau.so.6
ELF     7e620000-7e6e9000       Deferred        libx11.so.6
ELF     7e6e9000-7e6f6000       Deferred        libxext.so.6
ELF     7e6f6000-7e6fb000       Deferred        libxxf86vm.so.1
ELF     7e6fb000-7e713000       Deferred        libice.so.6
ELF     7e713000-7e7a1000       Deferred        winex11<elf>
  \-PE  7e720000-7e7a1000       \               winex11
ELF     7e7a1000-7e7bf000       Deferred        libexpat.so.1
ELF     7e7bf000-7e7ee000       Deferred        libfontconfig.so.1
ELF     7e7ee000-7e802000       Deferred        libz.so.1
ELF     7e802000-7e86c000       Deferred        libfreetype.so.6
ELF     7e86c000-7e92a000       Deferred        comctl32<elf>
  \-PE  7e880000-7e92a000       \               comctl32
ELF     7e92a000-7e981000       Deferred        shlwapi<elf>
  \-PE  7e940000-7e981000       \               shlwapi
ELF     7e981000-7ea78000       Deferred        shell32<elf>
  \-PE  7e990000-7ea78000       \               shell32
ELF     7ea78000-7eac0000       Deferred        dsound<elf>
  \-PE  7ea80000-7eac0000       \               dsound
ELF     7eac0000-7eb04000       Deferred        advapi32<elf>
  \-PE  7ead0000-7eb04000       \               advapi32
ELF     7eb04000-7eb0f000       Deferred        libgcc_s.so.1
ELF     7eb11000-7eb1a000       Deferred        libsm.so.6
ELF     7ebf9000-7ecb1000       Deferred        gdi32<elf>
  \-PE  7ec10000-7ecb1000       \               gdi32
ELF     7ecb1000-7ede7000       Deferred        user32<elf>
  \-PE  7ecd0000-7ede7000       \               user32
ELF     7ede7000-7ee74000       Deferred        winmm<elf>
  \-PE  7edf0000-7ee74000       \               winmm
ELF     7ee74000-7ee9a000       Deferred        msacm32<elf>
  \-PE  7ee80000-7ee9a000       \               msacm32
ELF     7efa4000-7efaf000       Deferred        libnss_files.so.2
ELF     7efaf000-7efb9000       Deferred        libnss_nis.so.2
ELF     7efb9000-7efcf000       Deferred        libnsl.so.1
ELF     7efcf000-7eff5000       Deferred        libm.so.6
ELF     7eff5000-7eff7000       Deferred        libnvidia-tls.so.1
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7ca8000-b7cac000       Deferred        libdl.so.2
ELF     b7cac000-b7de0000       Deferred        libc.so.6
ELF     b7de1000-b7df4000       Deferred        libpthread.so.0
ELF     b7dff000-b7f13000       Deferred        libwine.so.1
ELF     b7f15000-b7f30000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\KID\ever17PC_us\ever17PC_us.exe
        00000010    0
        0000000f   15
        0000000e   15
        00000009    0 <==

```

---

### Post by cogadh on 2007-06-16
You may have me stumped. All I know for sure is you can ignore the ALSA errors at the start, I get those all the time and it is only due to the lack of a master volume control on multiple speaker setups. If you want surround sound in games, that will be a problem, but it doesn't prevent a game from launching or running.

The error, as I barely understand the Wine gibberish, is related to the game's launch executable, ever17PC_us.exe. It is causing a page fault on launch, which is the kind of thing that used to cause the old "Blue Screen of Death" on Win 98. I've never been able to figure out why those happen.

One thing you might want to try (and honestly, there's no real reason this should work), is navigate to the directory where the excutable is, then "wine" the executable:
```
cd /home/wolf/.wine/drive_c/KID/ever17PC_us
wine ever17PC_us.exe
```
This can sometime fix issues where the excutable is looking for something else in Wine's fake Windows install, but can't find it. After that, I'm out of ideas. It's entirely possible that you stumbled into one of those games that just won't run in Wine.

---

### Post by Nerdyboy42a on 2007-06-16
It's very odd.  It starts up and gives me the first window where you select configuration options, I click OK, then it looks like it's starting to make the main window/game area and then crashes.  I made sure to make MetaCity my window manager, so it shouldn't be a problem with Beryl.  If this gives you any hints, that'd be great, but thanks for all your help anyway.  I guess I just got unlucky : P.

Note:  It's been doing this the whole time.  I don't think changing to that directory caused anything to go different.

---

### Post by cogadh on 2007-06-16
Are you making any configuration changes before you click OK?

Also, do you have Wine set to emulate a virtual desktop?

---

### Post by Nerdyboy42a on 2007-06-17
I tried having it emulate a 1280*1024 desktop and nothing changed.  I made the game go into full screen instead of window mode and turned off CPU auto-detect, thinking that might have been causing issues.

---

