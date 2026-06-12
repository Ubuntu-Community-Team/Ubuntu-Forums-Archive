---
title: "CSS with Wine 0.9.40"
date: 2007-07-01
forum: Gaming &amp; Leisure
---

### Post by ubu-for on 2007-07-01
Does anybody else notice dropouts for CSS since Wine 0.9.40 (Vista)?

---

### Post by ubu-for on 2007-07-02
CSS crashes regularly in Vista and XP mode since Wine 0.9.40 and now even with 0.9.39.

```
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
wine: Unhandled page fault on read access to 0x00000024 at address 0xd34b423 (thread 0034), starting debugger...
Unhandled exception: page fault on read access to 0x00000024 in 32-bit code (0x0d34b423).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0d34b423 ESP:0034e5e8 EBP:00000002 EFLAGS:00210212(   - 00      - RIA1)
 EAX:00000020 EBX:00000000 ECX:1d843fc8 EDX:07255c00
 ESI:0d35ea18 EDI:00000090
Stack dump:
0x0034e5e8:  0d35ea18 005537b4 0d34b452 1d840002
0x0034e5f8:  0d35ea18 005537b4 0d35ea18 1d840006
0x0034e608:  0d34b7d5 1d840006 0d35ea18 1d840006
0x0034e618:  0d35ea3c 00000020 0d35ea18 0d3498da
0x0034e628:  1d840001 ffffffff 00000000 00000009
0x0034e638:  0034ff08 0034e67c 1000753b 00000003
Backtrace:
=>1 0x0d34b423 in datacache (+0xb423) (0x00000002)
  2 0x00000000 (0x00000000)
0x0d34b423: movl        0x24(%ebx),%eax
Modules:
Module  Address                 Debug info      Name (154 modules)
PE        350000-  386000       Deferred        tier0
PE        390000-  3ae000       Deferred        vstdlib
PE        3b0000-  3c4000       Deferred        inputsystem
PE        3e0000-  3f6000       Deferred        valve_avi
PE        400000-  41c000       Deferred        hl2
PE       ce40000- ce94000       Deferred        filesystem_steam
PE       d0f0000- d1ee000       Deferred        datamodel
PE       d300000- d33d000       Deferred        dmserializers
PE       d340000- d365000       Export          datacache
PE       d480000- d534000       Deferred        materialsystem
PE       d540000- d610000       Deferred        vguimatsurface
PE       d610000- d685000       Deferred        vgui2
PE       d690000- dc7d000       Deferred        engine
PE       dc80000- dc94000       Deferred        steam_api
PE       dec0000- dee9000       Deferred        stdshader_dbg
PE       def0000- df25000       Deferred        stdshader_dx6
PE       df30000- df58000       Deferred        stdshader_dx7
PE       df60000- dfa3000       Deferred        stdshader_dx8
PE       dfb0000- dfbf000       Deferred        unicode
PE       e230000- e266000       Deferred        soundemittersystem
PE       e270000- e28b000       Deferred        scenefilecache
PE       e290000- e40c000       Deferred        steamclient
PE       e410000- e450000       Deferred        tier0_s
PE       e450000- e4c9000       Deferred        vstdlib_s
PE       e5f0000- e7d3000       Deferred        gameui
PE       f650000- f660000       Deferred        vaudio_miles
PE       f660000- f724000       Deferred        friendsui
PE       ff30000- fffb000       Deferred        serverbrowser
PE      10000000-10030000       Deferred        launcher
PE      1cf40000-1cf67000       Deferred        vaudio_speex
PE      20000000-2031e000       Deferred        steam
PE      21100000-21164000       Deferred        mss32
PE      22000000-22642000       Deferred        server
PE      24000000-24476000       Deferred        client
PE      26000000-26138000       Deferred        vphysics
PE      26400000-26439000       Deferred        mssvoice.asi
PE      26f00000-26f2e000       Deferred        mssmp3.asi
PE      2a000000-2a0a8000       Deferred        shaderapidx9
PE      2c000000-2c3e3000       Deferred        studiorender
PE      60000000-60021000       Deferred        cserhelper
PE      628c0000-628d9000       Deferred        parsifal
ELF     71e00000-71e4a000       Deferred        dbghelp<elf>
  \-PE  71e10000-71e4a000       \               dbghelp
ELF     79db1000-79dfa000       Deferred        dsound<elf>
  \-PE  79dc0000-79dfa000       \               dsound
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7b943000-7b949000       Deferred        libnss_dns.so.2
ELF     7b949000-7b94c000       Deferred        libnss_mdns4_minimal.so.2
ELF     7baa0000-7bada000       Deferred        shdocvw<elf>
  \-PE  7bab0000-7bada000       \               shdocvw
ELF     7bc00000-7bc98000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc98000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c379000-7c3ca000       Deferred        crypt32<elf>
  \-PE  7c380000-7c3ca000       \               crypt32
ELF     7c3ca000-7c3ff000       Deferred        rsaenh<elf>
  \-PE  7c3d0000-7c3ff000       \               rsaenh
ELF     7c3ff000-7c414000       Deferred        psapi<elf>
  \-PE  7c410000-7c414000       \               psapi
ELF     7ca8b000-7caa2000       Deferred        mcicda<elf>
  \-PE  7ca90000-7caa2000       \               mcicda
ELF     7cbb3000-7cbc7000       Deferred        winejoystick<elf>
  \-PE  7cbc0000-7cbc7000       \               winejoystick
ELF     7cde9000-7ce69000       Deferred        libglu.so.1
ELF     7ce69000-7cf31000       Deferred        wined3d<elf>
  \-PE  7ce80000-7cf31000       \               wined3d
ELF     7cf31000-7cf5d000       Deferred        d3d9<elf>
  \-PE  7cf40000-7cf5d000       \               d3d9
ELF     7cf5d000-7cf7d000       Deferred        mpr<elf>
  \-PE  7cf60000-7cf7d000       \               mpr
ELF     7cf7d000-7cfc6000       Deferred        wininet<elf>
  \-PE  7cf90000-7cfc6000       \               wininet
ELF     7cfc6000-7d063000       Deferred        oleaut32<elf>
  \-PE  7cfe0000-7d063000       \               oleaut32
ELF     7d063000-7d08a000       Deferred        msvfw32<elf>
  \-PE  7d070000-7d08a000       \               msvfw32
ELF     7d08a000-7d0c4000       Deferred        avifil32<elf>
  \-PE  7d090000-7d0c4000       \               avifil32
ELF     7d0c4000-7d0d9000       Deferred        midimap<elf>
  \-PE  7d0d0000-7d0d9000       \               midimap
ELF     7d0d9000-7d0ff000       Deferred        msacm32<elf>
  \-PE  7d0e0000-7d0ff000       \               msacm32
ELF     7d0ff000-7d117000       Deferred        msacm32<elf>
  \-PE  7d110000-7d117000       \               msacm32
ELF     7d117000-7d153000       Deferred        wineoss<elf>
  \-PE  7d120000-7d153000       \               wineoss
ELF     7d153000-7d1e2000       Deferred        winmm<elf>
  \-PE  7d160000-7d1e2000       \               winmm
ELF     7d348000-7d37a000       Deferred        uxtheme<elf>
  \-PE  7d350000-7d37a000       \               uxtheme
ELF     7d37a000-7d38e000       Deferred        mswsock<elf>
  \-PE  7d380000-7d38e000       \               mswsock
ELF     7d38e000-7d3a2000       Deferred        lz32<elf>
  \-PE  7d390000-7d3a2000       \               lz32
ELF     7d3a2000-7d3bc000       Deferred        version<elf>
  \-PE  7d3b0000-7d3bc000       \               version
ELF     7d3bc000-7d479000       Deferred        comctl32<elf>
  \-PE  7d3d0000-7d479000       \               comctl32
ELF     7d479000-7d4d2000       Deferred        shlwapi<elf>
  \-PE  7d490000-7d4d2000       \               shlwapi
ELF     7d4d2000-7d5d0000       Deferred        shell32<elf>
  \-PE  7d4e0000-7d5d0000       \               shell32
ELF     7d5d0000-7d625000       Deferred        rpcrt4<elf>
  \-PE  7d5e0000-7d625000       \               rpcrt4
ELF     7d625000-7d6c4000       Deferred        ole32<elf>
  \-PE  7d630000-7d6c4000       \               ole32
ELF     7d6c4000-7d6d7000       Deferred        libresolv.so.2
ELF     7d6e7000-7d705000       Deferred        iphlpapi<elf>
  \-PE  7d6f0000-7d705000       \               iphlpapi
ELF     7d705000-7d732000       Deferred        ws2_32<elf>
  \-PE  7d710000-7d732000       \               ws2_32
ELF     7d98b000-7d9a5000       Deferred        wsock32<elf>
  \-PE  7d990000-7d9a5000       \               wsock32
ELF     7d9a7000-7d9ac000       Deferred        libxfixes.so.3
ELF     7d9ac000-7d9b5000       Deferred        libxcursor.so.1
ELF     7d9b5000-7d9d2000       Deferred        imm32<elf>
  \-PE  7d9c0000-7d9d2000       \               imm32
ELF     7d9d2000-7d9d8000       Deferred        libxrandr.so.2
ELF     7d9d8000-7d9e0000       Deferred        libxrender.so.1
ELF     7d9e0000-7d9e3000       Deferred        libxinerama.so
ELF     7df0c000-7df0e000       Deferred        libnvidia-tls.so.1
ELF     7df0e000-7e794000       Deferred        libglcore.so.1
ELF     7e794000-7e820000       Deferred        libgl.so.1
ELF     7e820000-7e825000       Deferred        libxdmcp.so.6
ELF     7e825000-7e828000       Deferred        libxau.so.6
ELF     7e828000-7e919000       Deferred        libx11.so.6
ELF     7e919000-7e927000       Deferred        libxext.so.6
ELF     7e927000-7e92c000       Deferred        libxxf86vm.so.1
ELF     7e92c000-7e944000       Deferred        libice.so.6
ELF     7e944000-7e94d000       Deferred        libsm.so.6
ELF     7e94d000-7e9dc000       Deferred        winex11<elf>
  \-PE  7e960000-7e9dc000       \               winex11
ELF     7ea4e000-7ea6e000       Deferred        libexpat.so.1
ELF     7ea6e000-7ea99000       Deferred        libfontconfig.so.1
ELF     7ea99000-7eaad000       Deferred        libz.so.1
ELF     7eaad000-7eb18000       Deferred        libfreetype.so.6
ELF     7eb18000-7eb60000       Deferred        advapi32<elf>
  \-PE  7eb20000-7eb60000       \               advapi32
ELF     7eb60000-7eb6c000       Deferred        libgcc_s.so.1
ELF     7ec56000-7ed16000       Deferred        gdi32<elf>
  \-PE  7ec70000-7ed16000       \               gdi32
ELF     7ed16000-7ee53000       Deferred        user32<elf>
  \-PE  7ed30000-7ee53000       \               user32
ELF     7ee72000-7ee7d000       Deferred        libnss_files.so.2
ELF     7ee7d000-7ee87000       Deferred        libnss_nis.so.2
ELF     7ee87000-7ee9e000       Deferred        libnsl.so.1
ELF     7ee9e000-7eea7000       Deferred        libnss_compat.so.2
ELF     7efc9000-7eff0000       Deferred        libm.so.6
ELF     b7c73000-b7c77000       Deferred        libdl.so.2
ELF     b7c77000-b7db8000       Deferred        libc.so.6
ELF     b7db9000-b7dd0000       Deferred        libpthread.so.0
ELF     b7de0000-b7ef4000       Deferred        libwine.so.1
ELF     b7ef6000-b7f11000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000039 (D) C:\Programs\Steam\SteamApps\halflife493\counter-strike source\hl2.exe
        0000002c   15
        00000026    0
        00000014    0
        00000057   15
        00000024    2
        00000015    0
        00000040    0
        00000042    0
        00000035    2
        00000034    0 <==
0000005f 
        00000061    0
        00000060    0
0000005d 
        0000000e    0
        00000053    0
        0000002d    0
        0000001e    1
        00000043    1
        00000038    0
        0000003b    0
        0000003d    0
        0000003c    0
        0000003f    1
        0000003e    0
        00000037    1
        00000036    0
        00000045    1
        00000044    0
        00000022    1
        00000021    0
        00000025    1
        00000009    0
        00000018    1
        00000017    0
        0000001f    1
        0000001a    0
        00000019    1
        0000001b    0
        0000004c    1
        0000001d    0
        00000056    0
        00000051    0
        0000004d    0
        00000048    0
        0000000c    0
        00000023    0
        00000020    0
        0000004f    0
        00000033    1
        00000052    0
        00000047    0
        0000002f    0
        0000004e    0
        0000004a    1
        0000004b    0
        00000049    0
        00000067    0
        00000066    0
        00000065    0
        00000064    0
        00000063    0
        00000062    0
        0000005e    0
```

Anybody else?

---

### Post by Dritzen on 2007-07-02
I found that CSS runs a lot worse with 0.9.40 than it did with 0.9.39.  I had to turn the graphics settings down but since I've done that, I haven't lagged out of any games.

My main problem now is that when I try to play Half-Life 2, when it tries to load the initial movie before the first level, HL2 locks up.

I think I'm going to install 0.9.39 again

---

### Post by ubu-for on 2007-07-02
Before the Wine update, CSS worked great in Vista and Win98 mode.

---

### Post by Sammi on 2007-07-03
Just install an older package: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by ubu-for on 2007-07-03
> **Sammi said:**
> Just install an older package: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Thanks! But I already did.

---

### Post by joos13 on 2007-07-03
What's the most recent version of wine that runs Steam well?

---

### Post by ubu-for on 2007-07-03
> **joos13 said:**
> What's the most recent version of wine that runs Steam well?

Nearly every version! The most recent version is 0.9.40.

---

### Post by joos13 on 2007-07-03
> **ubu-for said:**
> Nearly every version! The most recent version is 0.9.40.

well from your post it appears that .9.40 has problems...

what version did you roll back to?

---

### Post by ubu-for on 2007-07-03
> **ubu-for said:**
> Before the Wine update, CSS worked great in Vista and Win98 mode.

Since the last Wine update CSS works now without any problems only in Win98 mode with version 0.9.39 and 0.9.40.

---

### Post by joos13 on 2007-07-03
> **Dritzen said:**
> I found that CSS runs a lot worse with 0.9.40 than it did with 0.9.39.  I had to turn the graphics settings down but since I've done that, I haven't lagged out of any games.

My main problem now is that when I try to play Half-Life 2, when it tries to load the initial movie before the first level, HL2 locks up.

I think I'm going to install 0.9.39 again

so you didnt experience the lag problems with .9.40 as posted above, ubu-for?

---

### Post by ubu-for on 2007-07-03
> **joos13 said:**
> what version did you roll back to?

I currently use Wine 0.9.40.

> **joos13 said:**
> so you didnt experience the lag problems with .9.40 as posted above, ubu-for?

Wine 0.9.40 (Win98) works great! No lagging.

I'm lovin' it!

---

### Post by Jordan777 on 2007-07-03
Doesn't the amount of time it takes to start up bother you though?  I mean it's not like minutes or anything but it's quite longer than if you just ran CSS on Windows.

---

### Post by joos13 on 2007-07-03
did you have problems with the 26% error?  I can t seem to get around it.  Ive posted elsewhere about it but no one has responded for a few days.

---

### Post by ubu-for on 2007-07-03
> **Jordan777 said:**
> Doesn't the amount of time it takes to start up bother you though?  I mean it's not like minutes or anything but it's quite longer than if you just ran CSS on Windows.

It takes only a few seconds!

Why should it take longer, than shutting down Ubuntu, starting up Windows and starting CSS?

> **joos13 said:**
> Ive posted elsewhere about it but no one has responded for a few days.

Please use the [forum search](http://ubuntuforums.org/search.php?searchid=23126261) before posting a problem.

> **joos13 said:**
> did you have problems with the 26% error?  I can t seem to get around it.

Look at [this](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games#troubleshooting) HOWTO or [that](http://ubuntuforums.org/showpost.php?p=1429730&postcount=4) post.

Have fun!

---

### Post by joos13 on 2007-07-03
I've done extensive forum searching.  The SelfUpdate gets no further than 26%.  When I remove ClientRegistry.blob I get an error that prevents an attempt to update.  Several people have experienced the same problem and from what if seen, no solution has been posted.

---

### Post by ubu-for on 2007-07-04
> **joos13 said:**
> I've done extensive forum searching.  The SelfUpdate gets no further than 26%.  When I remove ClientRegistry.blob I get an error that prevents an attempt to update.  Several people have experienced the same problem and from what if seen, no solution has been posted.

You've already tried the following command, right?

```
wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```

If yes, try different Wine modes like "Win ME", "Win 2000", "Win Vista".

---

### Post by PaulieWalnuts on 2007-07-04
> **ubu-for said:**
> I currently use Wine 0.9.40.



Wine 0.9.40 (Win98) works great! No lagging.

I'm lovin' it!

How do I do this? if i set win98 in winecfg steam will complain about "Please turn off compatibility mode"  and not start

---

### Post by joos13 on 2007-07-04
When I try to change to Win98, wine complains that Steam is not compatable with Win95/98/ME.  When i try with Windows 2000 I get the same problem as before.

---

### Post by Insomn1a on 2007-07-04
anyone know how to get wine to work with a USB headset?

i get no sound using any of the drivers wine has listed, i know its DSP1 but i dont know how to adjust it.

any ideas?



#19
try starting steam from the terminal? maybe? lol

---

### Post by ubu-for on 2007-07-04
> **PaulieWalnuts said:**
> How do I do this? if i set win98 in winecfg steam will complain about "Please turn off compatibility mode"  and not start

Are you talking about installing Steam or starting Steam games?

Would you please disable smilies in your quote? Thank you very much in advance!

> **joos13 said:**
> When i try with Windows 2000 I get the same problem as before.

1. Use the Terminal to run Steam.
2. Try different Wine versions (last time: 0.9.12).
3. Try different Wine modes (last time: Win2000 or XP).
4. Try to install Steam at least 10 times in a row.
5. Use [this](http://www.von-thadden.de/Joachim/WineTools/index.html#download) tool to reboot "Windows".
6. Forget point 1 to 5, if you can copy and paste the already installed Steam (and games) from Windows to Ubuntu.

---

### Post by PaulieWalnuts on 2007-07-04
Okay, smilies shoulld be disabled .. 

I got it to work with the win98 mode, however that didnt fix my problem...
Whenever I run CSS it will play great, good fps but crashes at a random point within 5 minutes...  it just completely freezes. Can also be when downloading content such as maps or sounds before playing..  Cant even ctrl alt backspace out of it.
I have this problem both with CSS and CS.
I tried all sound drivers, even tried the game with the -nosound option but it will still freeze.

Im using ubuntu feisty on a c2d e4300, gigabyte ds3, ati x1950 pro (with fglrx drivers)

Any ideas on stuff i can try would be greatly appreciated

---

### Post by joos13 on 2007-07-04
how did you get it to work in win98 mode?  when i try to run steam through the terminal, it complains about compatability mode.  also, the 26% workaround doesnt work either.  please help, ive tried to many things already and nothing is working for me.

---

### Post by ubu-for on 2007-07-04
Maybe it's a problem with your ATI drivers?

BTW I've meant [this](http://ubuntuforums.org/showpost.php?p=2961222&postcount=18) post and not every quote in general. ;)

---

### Post by PaulieWalnuts on 2007-07-04
> **joos13 said:**
> how did you get it to work in win98 mode?  when i try to run steam through the terminal, it complains about compatability mode.  also, the 26% workaround doesnt work either.  please help, ive tried to many things already and nothing is working for me.

Are u making a new entry for steam.exe or changing the default one?
Making the entry for steam.exe didnt seem to work but changing the default one did.

---

### Post by PaulieWalnuts on 2007-07-04
> **ubu-for said:**
> Maybe it's a problem with your ATI drivers?

BTW I've meant [this](http://ubuntuforums.org/showpost.php?p=2961222&postcount=18) post and not every quote in general. ;)

Ah of course, well fixed anyway.. ;)
Could be my ATI drivers , however native linux games such as Quake4 and Warsow run just great. What drivers would you suggest i use?

---

### Post by ubu-for on 2007-07-04
> **joos13 said:**
> also, the 26% workaround doesnt work either.  please help, ive tried to many things already and nothing is working for me.

I'm not sure, but maybe you can get beyond 26% by deleting the "Steam Update File". It's more than one year ago, so please be flexible, if something doesn't make sense.

1. Try to update Steam.
2. You get the "26%" error message.
3. Don't close Steam and the error message (maybe incorrect).
4. Delete the "Steam Update File" in the Steam directory.
5. Click on retry update or start the Steam update again.

---

### Post by ubu-for on 2007-07-04
> **PaulieWalnuts said:**
> Ah of course, well fixed anyway.. ;)

Thank you!

> **PaulieWalnuts said:**
> Could be my ATI drivers , however native linux games such as Quake4 and Warsow run just great. What drivers would you suggest i use?

You are using the ATI drivers from Ubuntu and installed them with Synaptic, right?

You could try [Envy](http://www.albertomilone.com/nvidia_scripts1.html) instead or compile the most recent drivers from the ATI website. [Here](http://ubuntuforums.org/showthread.php?p=2950702#post2950702) is a similar thread to your problem.

BTW Don't use Beryl or Compiz parallel to Wine.

---

### Post by Insomn1a on 2007-07-04
> **Insomn1a said:**
> anyone know how to get wine to work with a USB headset?

i get no sound using any of the drivers wine has listed, i know its DSP1 but i dont know how to adjust ALSA or OSS to point to that file

any ideas?




somebody help me :( im total newb to this ](*,)

[http://ubuntuforums.org/showthread.php?t=491423](http://ubuntuforums.org/showthread.php?t=491423)

---

### Post by ubu-for on 2007-07-04
Nobody is ignoring your problem, but please be patient till someone knows the answer!

---

### Post by berserker on 2007-07-04
CSS crashes whenever I try to join a server with

```
failed to lock index buffer in CMeshDX8::LockIndexBuffer
```

Just installed Steam and CSS today.  Using wine 0.9.40.  Tried Vista, XP and 98 modes.

Any ideas?

EDIT:  Resolved by lowering settings in the Video options.

---

### Post by joos13 on 2007-07-04
Ok so I first tried to change to win98 mode.  I was not able to install steam with wine set to win98 mode, but after installing steam, I was able to try to run steam in win98 mode.  however still got the 26% error.  I tried deleting SteamTmp.exe and ClientRegistry.blob and running steam.exe from the terminal, but still got the 26% error.  I then did a SelfUpdate with SteamTmp intact and deleting ClientRegistry.blob and again got the 26% error.  Not really sure what you meant by Steam Update File, maybe I was deleting the wrong things.

---

### Post by Tyltyl on 2007-07-04
> **joos13 said:**
> Ok so I first tried to change to win98 mode.  I was not able to install steam with wine set to win98 mode, but after installing steam, I was able to try to run steam in win98 mode.  however still got the 26% error.  I tried deleting SteamTmp.exe and ClientRegistry.blob and running steam.exe from the terminal, but still got the 26% error.  I then did a SelfUpdate with SteamTmp intact and deleting ClientRegistry.blob and again got the 26% error.  Not really sure what you meant by Steam Update File, maybe I was deleting the wrong things.

I had the 26% bug and every work around didn't work.
I ended up installing an old steaminstall.exe instead of steaminstall.msi and it updated without problems.

---

### Post by joos13 on 2007-07-04
Well, I just tried installing steam from the CD and it worked.  guess I should have tried it long ago.  dont like not knowing what my original problem was, but oh well.  steam isnt able to display the store HTML page, complains about needing gecko.  I tried auto installing it, but that failed...of course.  Looked in synaptic and didnt see any gecko.  anyone have ideas.

btw thanks guys, esp ubu-for, for trying to help me.

---

### Post by Tyltyl on 2007-07-05
> **joos13 said:**
> Well, I just tried installing steam from the CD and it worked.  guess I should have tried it long ago.  dont like not knowing what my original problem was, but oh well.  steam isnt able to display the store HTML page, complains about needing gecko.  I tried auto installing it, but that failed...of course.  Looked in synaptic and didnt see any gecko.  anyone have ideas.

btw thanks guys, esp ubu-for, for trying to help me.

I don't know for sure, but the first time it asks me to install gecko it fails and the pages in the store don't show up. But if I close Steam and restart it installs without problems.

---

### Post by ubu-for on 2007-07-05
> **joos13 said:**
> Ok so I first tried to change to win98 mode.  I was not able to install steam with wine set to win98 mode, but after installing steam, I was able to try to run steam in win98 mode.  however still got the 26% error.  I tried deleting SteamTmp.exe and ClientRegistry.blob and running steam.exe from the terminal, but still got the 26% error.  I then did a SelfUpdate with SteamTmp intact and deleting ClientRegistry.blob and again got the 26% error.  Not really sure what you meant by Steam Update File, maybe I was deleting the wrong things.

I had the following in mind.

> Another workaround for 26% error
by Paul Anholt on Friday July 7th 2006, 15:52
After steam crashes at 26% open up wine file and browse to the steam directory under program files.
You should see steam.exe and steamnew.exe, rename steam.exe to steam.old and then rename steamnew.exe to steam.exe and launch it.

I know you've solved the problem, but [here](http://appdb.winehq.org/appview.php?versionId=1554&iTestingId=157) are some further infos about Steam with Wine.

---

### Post by joos13 on 2007-07-05
alright thanks.  steam complains right when i load cs that my gfx drivers are out of date.  i updated fglrx and am able to load other 3d games such as flightgear, so should i just ignore the warning?  do i need to get drivers off of ati's website?

edit:  when CSS loads, the screen goes black.  I alt tab out and restart css, get a "only one instance of program can be run at a time", click OK, then CSS menu appears.  I start a game, and everything loads fine, but as soon as i enter the game, it freezes.  the same thing happens when i try to load the stress test.

edit2:  when i install the proprietary drivers for my x300, do i need to uninstall the fglrx stuff?

edit3:  i havent messed with the proprietary driver yet.  heres teh status of my current driver

> josh@josh-laptop:~/Desktop$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300
OpenGL version string: 2.0.6334 (8.34.8 )          


It looks as if is is ok...

---

### Post by PaulieWalnuts on 2007-07-05
> **ubu-for said:**
> Thank you!



You are using the ATI drivers from Ubuntu and installed them with Synaptic, right?

You could try [Envy](http://www.albertomilone.com/nvidia_scripts1.html) instead or compile the most recent drivers from the ATI website. [Here](http://ubuntuforums.org/showthread.php?p=2950702#post2950702) is a similar thread to your problem.

BTW Don't use Beryl or Compiz parallel to Wine.

I was using the drivers from synaptic. After a day of getting the ati.com drivers to work, i can confirm this was not the problem. It still freezes :P

---

### Post by joos13 on 2007-07-05
OK, now CSS is screwing with my entire system.  I started up the stress test again, and it froze.  FYI resolution for CSS is 800x600.  So i hit the power on my computer and then turn it back on.  The login screen is in 800x600.  As soon as it loads gnome, it goes to 1400x1040, what i originally had, xcept it looks really crappy, aka nothing is redrawing, jagggedy pixelated blocs everywhere, pretty much unusable.  I manage to find the screen resolution options, and change to 1024x768, which works.  anything above this, 1152x768 and above, looks like crap.  i have restarted numerous times and nothing improves.  ahhhhhhhhhhh

---

### Post by ubu-for on 2007-07-05
I'm sorry guys, but I'm pretty sure that it's an ATI driver problem.

> **joos13 said:**
> I started up the stress test again, and it froze.

Forget the CSS stress test. Some weeks ago I got more than 120 FPS and now it looks like 0.5 FPS, but the game still works great.

---

### Post by joos13 on 2007-07-05
k, well ingame is a problem too, with the freezing up and all.  take a look at the fglrxinfo i posted, does that look ok?  if its installed in synaptic shouldnt it update when needed?  is there a way to force an update in synaptic, or do i have to dl the .run and turn it into a .deb?  if i do this, do i need to remove teh older fglrx stuff thats instlaled right now?

edit: fixed the resolution problem, not the css problem

---

### Post by joos13 on 2007-07-05
so im installing the newer driver.  im using the guide found here:

> [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Does anyone know what this means:

> sudo mkdir /lib/modules/$(uname -r)/volatile

particularly, what is the "$(uname -r)" part?  I tried substituting "josh" where uname is, but that didnt work

---

### Post by ubu-for on 2007-07-05
> **joos13 said:**
> take a look at the fglrxinfo i posted, does that look ok?

I'm sorry, but I'm only a user. A Nvidia user.

If you use Synaptic, you get the most recent and stable drivers for Ubuntu.

> **joos13 said:**
> if its installed in synaptic shouldnt it update when needed?

That's right!

> **joos13 said:**
> is there a way to force an update in synaptic

No.

> **joos13 said:**
> if i do this, do i need to remove teh older fglrx stuff thats instlaled right now?

Yes.

> **joos13 said:**
> particularly, what is the "$(uname -r)" part?

It's your current kernel version. Try the following.

```
uname -r
```

Good night!

---

### Post by Mike7171 on 2007-07-05
The only problem I'm having with CSS so far is that when I launch it, it gets to the initial loading screen, then the Steam window pops up over it. I can never play it because of it. No idea how to fix it either. I'm using Wine 0.0.40 I believe.

---

### Post by joos13 on 2007-07-05
does anybody playing css use an ati radeon gfx card?  If so, what driver do you have and by what process did you set it up?  ive tried several howto's and nothing is working for me..if my problem is the graphics card.  as i mention above, the game freezes when i enter a level.  is there a way to completely roll back my graphics to out-of-the box status?

---

### Post by Insomn1a on 2007-07-06
there is a tutorial out there somewhere that tells you how to turn the .run into a deb file and install the radeon drivers provided by [http://ati.amd.com](http://ati.amd.com)


i have one, x1600 pro PCI-E 512mb gddr2

---

### Post by joos13 on 2007-07-06
my gfx driver is the 8.34.8, which is the most recent one.  what drivers are yall using?  incase you dont know type $ fglrxinfo.

---

### Post by Arizon_Dread on 2007-07-23
> **joos13 said:**
> I've done extensive forum searching.  The SelfUpdate gets no further than 26%.  When I remove ClientRegistry.blob I get an error that prevents an attempt to update.  Several people have experienced the same problem and from what if seen, no solution has been posted.

I had the same problem (i think)

[http://ubuntuforums.org/showthread.php?t=482924](http://ubuntuforums.org/showthread.php?t=482924)

hope this helps

---

