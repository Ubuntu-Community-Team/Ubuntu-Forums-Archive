---
title: "World of Warcraft 2.0 update"
date: 2006-12-06
forum: Gaming &amp; Leisure
---

### Post by loldongs on 2006-12-06
I've been trying to update wow to version 2.0.1, but wine keeps crashing when i run the install program. I can download the files etc, but the patching process kills wine.

anyone having the same problem, or know a fix?

---

### Post by hikaricore on 2006-12-06
I was able to update just fine, are you running the updater.exe program in the patch directory?  And what version of wine are you running.

---

### Post by Poka64 on 2006-12-06
> **loldongs said:**
> I've been trying to update wow to version 2.0.1, but wine keeps crashing when i run the install program. I can download the files etc, but the patching process kills wine.

anyone having the same problem, or know a fix?


Same thing happens for me too, the updater.exe keeps crashing when I try to update.

Runnig wine 0.9.26 from the winehq reps.

---

### Post by Drezliok on 2006-12-06
My WoW install is runnable from linux and windows. I used windows to update it.

---

### Post by Poka64 on 2006-12-06
Drezliok: do you run WoW from your Windows partition?

---

### Post by Drezliok on 2006-12-06
It's installed on a fat32 drive, so it can be used by windows. So, yes. It's on my storage drive.

My Girl Friend doesn't want to mess with linux for games yet, so windows it still here for that. I had 2 copies but that was stupid so I canned the one in my /home. Why waste space.

Runs as good as ever [after I changed the settings for it to make it wine freindly]

When My Girl Friend gets her new PC in the very near future I won't have any windows partitians on my Xubuntu box. I'll be Windows free.:mrgreen:

---

### Post by Juhku on 2006-12-07
Has anyone else has problems with WoW not working after this patch? I had everything running fine on WoW version 1.12, but now the game freezes and sound gets stuck into a loop as soon as I enter the world. Actually it freezes so badly i have to cold boot the computer, no keymashing gets me anywhere.

I'm using Ubuntu 6.10 and wine 0.9.26. No patches or tweaks other that the regedit to fix the graphics bug and some sound settings in Config.ftw, not even any addons.

Of course this could be due to buggy patch code, from what I read in the forums everywhere, but if anyone here has had the same problem and found a solution I'd be extremely grateful for help. Just got the game installed after a long break and now this... I just want to get to try out the new talents :(

---

### Post by Crooksey on 2006-12-07
Reading this shows the benifits of cedega, works fine here :)

---

### Post by Juhku on 2006-12-07
Ok, a bit of update. I tried the game in d3d mode, and also with sound disabled. No go, still freezes the whole computer couple of seconds after loading the world.

---

### Post by reiki on 2006-12-07
Ubuntu Edgy (6.10)
nVidia drivers 9629 (I'm pretty sure that's the number... I'm at work)
Wine 0.9.26 from the winehq repositories... no compiling, patching or otherwise messing with it.
Was running WoW 1.12 and I downloaded the patch to 2.0x as a zip file. Notice: I did NOT run the patcher from within WoW. I was basically following a Gentoo How-To-Update-Wow instructions.
Extracted the zip file into my WoW directory (it creates a FOLDER... don't just dump all the files into your WoW directory!)
Open a terminal, cd into that new patchdirectory I just made IN MY WOW directory.
wine updater.exe
Wine starts tells me it wants to install gecko engine (or something similar... at work now)
I said OK and it installed the gecko thing then updated.
Done deal
WoW plays fine.

And I apologize, but I won't be making teh patch file available as a download. It's like 492megs and I don't have that kind of bandwidth. :)  I just googled for it and found it no problem.

oh... and no slam to cedega users or to cedega, but I just don't want to pay to play a game that I already pay to play. :) I do see where it could have advantages for some folks though.

---

### Post by Juhku on 2006-12-07
Well, I had the patch downloaded to the WoW directory, and ran the updater.exe from there, but that couldn't be the problem, could it?

---

### Post by rejser on 2006-12-07
Hit the restart button in game, the downloader downloaded the patch, patched it, and the I played again.

---

### Post by Poka64 on 2006-12-07
This is what happens when I try to patch WoW.

```
fixme:powrprof:DllMain (0x7d490000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d490000, 0, (nil)) not fully implemented
fixme:ole:OleCreate 
        {8856f961-340a-11d0-a96b-00c04fd705a2}
        {00000112-0000-0000-c000-000000000046} semi-stub!
fixme:shdocvw:PersistStorage_InitNew (0x17f288)->(0x4e19f8)
fixme:shdocvw:WebBrowser_QueryInterface (0x17f288)->({0000011e-0000-0000-c000-000000000046} 0x34f22c) interface not supported
fixme:shdocvw:OleObject_SetHostNames (0x17f288)->(L"My Host Name", (null))
err:mshtml:load_gecko AutoRegister(NULL) failed: 80040154
err:mshtml:load_gecko AutoRegister(gre_dir) failed: 80040154
err:mshtml:init_nsio Could not get factory: 80040154
wine: Unhandled page fault on read access to 0x00000000 at address 0x7d2b3a6a (thread 000b), starting debugger...
peter@peter:~/.wine/drive_c/spel/World of Warcraft/WoW-1.12.x-to-2.0.1-enGB-patch$ Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7d2b3a6a).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7d2b3a6a ESP:0034ece0 EBP:0034ed18 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:7d2dbe94 ECX:7bc809c0 EDX:00000035
 ESI:0034f02c EDI:7d2d3a20
Stack dump:
0x0034ece0:  00000001 7d2e47b0 7d2d3a30 7d2d35da
0x0034ecf0:  80040154 001bae48 0017fd18 0034ed18
0x0034ed00:  60338322 001cfc38 00000000 7d2dbe94
0x0034ed10:  0034f02c 00000000 0034f068 7d2b2451
0x0034ed20:  0018dfa0 0018dfa8 7d2d3342 7d2d2878
0x0034ed30:  80040154 0034f048 0034ee18 7bc3aa4d
Backtrace:
=>1 0x7d2b3a6a init_nsio+0x14a in mshtml (0x0034ed18)
  2 0x7d2b2451 NSContainer_Create+0x151 in mshtml (0x0034f068)
  3 0x7d294680 HTMLDocument_Create+0x160 in mshtml (0x0034f0b8)
  4 0x7d2ac260 in mshtml (+0x2c260) (0x0034f0d8)
  5 0x7e9c7a64 CoCreateInstance+0x1c4 in ole32 (0x0034f138)
  6 0x7d33461c in shdocvw (+0x1461c) (0x0034f1d8)
  7 0x7d334fbb navigate_url+0x23b in shdocvw (0x0034f218)
  8 0x7d33d779 in shdocvw (+0x1d779) (0x0034f258)
  9 0x004a46f1 in installer (+0xa46f1) (0x00000007)
  10 0x00000000 (0x00000000)
0x7d2b3a6a init_nsio+0x14a in mshtml: movl      0x0(%eax),%edx
Modules:
Module  Address                 Debug info      Name (124 modules)
PE      400000-4f6000   Export          installer
PE      30000000-302c0000       Deferred        npswf32
PE      60000000-60007000       Deferred        accessiblemarshal
PE      60080000-600e9000       Deferred        js3250
PE      60140000-60167000       Deferred        nspr4
PE      60170000-601c9000       Deferred        nss3
PE      601d0000-6020a000       Deferred        nssckbi
PE      60210000-60217000       Deferred        plc4
PE      60220000-60226000       Deferred        plds4
PE      60230000-60238000       Deferred        npnul32
PE      60240000-6025a000       Deferred        smime3
PE      60260000-602ba000       Deferred        softokn3
PE      602c0000-602db000       Deferred        ssl3
PE      602e0000-602e6000       Deferred        xpcom
PE      602f0000-60304000       Deferred        xpcom_compat
PE      60310000-60375000       Deferred        xpcom_core
PE      60380000-60386000       Deferred        xpistub
PE      6c000000-6c00d000       Deferred        np32dsw
ELF     7b800000-7b91b000       Deferred        kernel32<elf>
  \-PE  7b820000-7b91b000       \               kernel32
ELF     7bc00000-7bc82000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc82000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cd49000-7cd4d000       Deferred        libgpg-error.so.0
ELF     7cd4d000-7cd9b000       Deferred        libgcrypt.so.11
ELF     7cd9b000-7cdae000       Deferred        libtasn1.so.3
ELF     7cdae000-7cddc000       Deferred        libcrypt.so.1
ELF     7cdec000-7ce5b000       Deferred        libgnutls.so.13
ELF     7ce5b000-7ce8a000       Deferred        libcups.so.2
ELF     7ce8a000-7cebb000       Deferred        winspool<elf>
  \-PE  7ce90000-7cebb000       \               winspool
ELF     7cebb000-7cf57000       Deferred        comdlg32<elf>
  \-PE  7cec0000-7cf57000       \               comdlg32
ELF     7cf57000-7cfa5000       Deferred        crypt32<elf>
  \-PE  7cf60000-7cfa5000       \               crypt32
ELF     7d0b6000-7d0cb000       Deferred        midimap<elf>
  \-PE  7d0c0000-7d0cb000       \               midimap
ELF     7d0f1000-7d109000       Deferred        msacm32<elf>
  \-PE  7d100000-7d109000       \               msacm32
ELF     7d109000-7d145000       Deferred        wineoss<elf>
  \-PE  7d110000-7d145000       \               wineoss
ELF     7d145000-7d1a9000       Deferred        msvcrt<elf>
  \-PE  7d150000-7d1a9000       \               msvcrt
ELF     7d1a9000-7d232000       Deferred        winmm<elf>
  \-PE  7d1b0000-7d232000       \               winmm
ELF     7d232000-7d25d000       Deferred        ws2_32<elf>
  \-PE  7d240000-7d25d000       \               ws2_32
ELF     7d25d000-7d277000       Deferred        wsock32<elf>
  \-PE  7d260000-7d277000       \               wsock32
ELF     7d277000-7d2e5000       Export          mshtml<elf>
  \-PE  7d280000-7d2e5000       \               mshtml
ELF     7d2e5000-7d318000       Deferred        urlmon<elf>
  \-PE  7d2f0000-7d318000       \               urlmon
ELF     7d318000-7d354000       Export          shdocvw<elf>
  \-PE  7d320000-7d354000       \               shdocvw
ELF     7d46a000-7d47e000       Deferred        lz32<elf>
  \-PE  7d470000-7d47e000       \               lz32
ELF     7d47e000-7d497000       Deferred        version<elf>
  \-PE  7d480000-7d497000       \               version
ELF     7d497000-7d4db000       Deferred        riched20<elf>
  \-PE  7d4a0000-7d4db000       \               riched20
ELF     7d508000-7d53a000       Deferred        uxtheme<elf>
  \-PE  7d510000-7d53a000       \               uxtheme
ELF     7d74f000-7d754000       Deferred        libxfixes.so.3
ELF     7d754000-7d75d000       Deferred        libxcursor.so.1
ELF     7d75d000-7d779000       Deferred        imm32<elf>
  \-PE  7d760000-7d779000       \               imm32
ELF     7d779000-7d797000       Deferred        ximcp.so.2
ELF     7d797000-7d799000       Deferred        xlcutf8load.so.2
ELF     7d799000-7d79c000       Deferred        libxrandr.so.2
ELF     7d79c000-7d7a4000       Deferred        libxrender.so.1
ELF     7d7a4000-7d7a7000       Deferred        libxinerama.so.1
ELF     7dcc1000-7e484000       Deferred        libglcore.so.1
ELF     7e484000-7e509000       Deferred        libgl.so.1
ELF     7e509000-7e5d2000       Deferred        libx11.so.6
ELF     7e5d2000-7e5df000       Deferred        libxext.so.6
ELF     7e5df000-7e5f7000       Deferred        libice.so.6
ELF     7e5f7000-7e685000       Deferred        winex11<elf>
  \-PE  7e610000-7e685000       \               winex11
ELF     7e685000-7e6a3000       Deferred        libexpat.so.1
ELF     7e6a3000-7e6d2000       Deferred        libfontconfig.so.1
ELF     7e6d2000-7e6e6000       Deferred        libz.so.1
ELF     7e6e6000-7e750000       Deferred        libfreetype.so.6
ELF     7e750000-7e7e7000       Deferred        oleaut32<elf>
  \-PE  7e760000-7e7e7000       \               oleaut32
ELF     7e7e7000-7e806000       Deferred        mpr<elf>
  \-PE  7e7f0000-7e806000       \               mpr
ELF     7e806000-7e84d000       Deferred        wininet<elf>
  \-PE  7e810000-7e84d000       \               wininet
ELF     7e84d000-7e90d000       Deferred        comctl32<elf>
  \-PE  7e860000-7e90d000       \               comctl32
ELF     7e90d000-7e920000       Deferred        libresolv.so.2
ELF     7e920000-7e93e000       Deferred        iphlpapi<elf>
  \-PE  7e930000-7e93e000       \               iphlpapi
ELF     7e93e000-7e992000       Deferred        rpcrt4<elf>
  \-PE  7e950000-7e992000       \               rpcrt4
ELF     7e992000-7ea26000       Export          ole32<elf>
  \-PE  7e9a0000-7ea26000       \               ole32
ELF     7ea26000-7ea7e000       Deferred        shlwapi<elf>
  \-PE  7ea30000-7ea7e000       \               shlwapi
ELF     7ea7e000-7eb6a000       Deferred        shell32<elf>
  \-PE  7ea90000-7eb6a000       \               shell32
ELF     7eb6a000-7eb75000       Deferred        libgcc_s.so.1
ELF     7ec54000-7ed0a000       Deferred        gdi32<elf>
  \-PE  7ec70000-7ed0a000       \               gdi32
ELF     7ed0a000-7ee40000       Deferred        user32<elf>
  \-PE  7ed20000-7ee40000       \               user32
ELF     7ee40000-7ee86000       Deferred        advapi32<elf>
  \-PE  7ee50000-7ee86000       \               advapi32
ELF     7ee86000-7ee91000       Deferred        libnss_files.so.2
ELF     7ee91000-7eea7000       Deferred        libnsl.so.1
ELF     7eea7000-7eeb0000       Deferred        libnss_compat.so.2
ELF     7eeb0000-7eeb2000       Deferred        libnvidia-tls.so.1
ELF     7eeb2000-7eeb7000       Deferred        libxdmcp.so.6
ELF     7eeb7000-7eec0000       Deferred        libsm.so.6
ELF     7efca000-7eff0000       Deferred        libm.so.6
ELF     7eff1000-7eff6000       Deferred        libxxf86vm.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cd0000-b7cd3000       Deferred        libxau.so.6
ELF     b7cd5000-b7cd9000       Deferred        libdl.so.2
ELF     b7cd9000-b7e0d000       Deferred        libc.so.6
ELF     b7e0e000-b7e21000       Deferred        libpthread.so.0
ELF     b7e31000-b7f42000       Deferred        libwine.so.1
ELF     b7f44000-b7f5f000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
        0000000e    0
        0000000d    0
0000000a (D) C:\windows\temp\Blizzard Installer Bootstrap - 0000035e\Installer.exe
        00000010    0
        0000000f    0
        0000000b    0 <==

```

---

### Post by Drezliok on 2006-12-07
Must be something with the updater. The onky trouble I have had is a small memory issue. But I had that before the patch.

I'll be asking about that error later on another thread.

I use a seperate Xserver to run my wine games.

---

### Post by chadk on 2006-12-08
Try downloading the patch from someplace else, then applying it manually using the updater.exe
You might just have a corrupt patch.

---

### Post by Juhku on 2006-12-11
> **chadk said:**
> Try downloading the patch from someplace else, then applying it manually using the updater.exe
You might just have a corrupt patch.

Actually i had downloaded the patch from an ftp mirror. Doing a reinstall from scratch for both WoW and wine to see if it helps.

---

### Post by willskills on 2006-12-11
> **Juhku said:**
> Actually i had downloaded the patch from an ftp mirror. Doing a reinstall from scratch for both WoW and wine to see if it helps.

I would imagine it will. I started with a Fresh Unbuntu Dapper install on Wednesday evening, and after about2 hours had CS:S and World of Warcraft running quite happily (with sound!).

I had my pre patch WoW client on an NTFS drive, so I just copied that over to my /home directory and ran just ran WoW, it patched (after the download of 700mb /snore) without any problems.

If anyone has any WoW related queries, I should be able to lend a hand,  you'll find me in #ubuntu on freenode as willskills.

Thanks

---

### Post by Juhku on 2006-12-12
Darn, I did a complete removal of wine from synaptic, then deleted the .wine folder and reinstalled everything, but no go. The game still freezes right after loading into the world. Any ideas?

---

### Post by JairunCaloth on 2006-12-13
I always just manualy patch by downloading the file from filefront, dropping it in the wow folder and running the patch with wine. Works every time.

---

### Post by Josh1 on 2006-12-13
Been working fine for me since it came out. WoW has run fine aswell :).

---

### Post by Juhku on 2006-12-13
Ah damnit. I might just give up and reinstall windows just to play. And get my next comp with an Nvidia graphics card :)

---

### Post by Ferrat on 2006-12-13
> **Crooksey said:**
> Reading this shows the benifits of cedega, works fine here :)

That's just naive, these are a few ppl that have a problem, I for one could update and can run WoW 2.01 without any problems what so ever, my guess is that some ppl using cedega has problems aswell, these problems ain't with wine, more likely SBW "S**t Behind the Wheel" (comical saying about ppl that ain't got all the skills needed yet, it's not the cars (wine) that's wrong but the driver (user)) ;P

---

### Post by khel on 2006-12-13
Everything works fine here with the latest wine 0.9.27 and ATI 9800Pro card, 
except minimap - it's all white :(  Any idea how to fix it?

---

### Post by hikaricore on 2006-12-13
> **khel said:**
> Everything works fine here with the latest wine 0.9.27 and ATI 9800Pro card, 
except minimap - it's all white :(  Any idea how to fix it?

This has been an issue for a long time for most, for me it only happens indoors or in dungeons.  You may want to check out the [Wine Application DataBase]("http://appdb.winehq.org/appview.php?iVersionId=5606") to see if there's any updated info on it there.

---

