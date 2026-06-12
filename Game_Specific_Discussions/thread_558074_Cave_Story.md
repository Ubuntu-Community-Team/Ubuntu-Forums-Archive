---
title: "Cave Story"
date: 2007-09-23
forum: Game Specific Discussions
---

### Post by Perfect Storm on 2007-09-23
**UGA's News Discussion of Cave Story.**

Discuss here. All discussions fall under the general rules of the UGA Code.
No swearing, profanity, nudity or other such subversive images or communications.
No Personal Attacks. Spamming of any kind will not be tolerated.

---

### Post by n2j3 on 2007-11-27
the [ livejournal](http://community.livejournal.com/doukutsu/101690.html) download url has been down for at least 3 days now (first time I checked). I got an rpm off [http://www.rpgameplace.de/rpms/](http://www.rpgameplace.de/rpms/) and then run alien on it. The resulting .deb can be found here:

[http://drop.io/cave_story_deb](http://drop.io/cave_story_deb)

To install , download the .deb file and then in your terminal
```

sudo dpkg -i doukutsu_20070919-1mdv2007.1_i386.deb
**and then as non-root user**
doukutsu

```

P.S. Even though the game runs natively on linux the configuration executable requires WINE. It's located at /etc/share/doukutsu/DoConfig.exe

---

### Post by GregLH on 2007-11-27
I'm getting an error doing as you said. Maybe you might know.
```
/usr/bin/doukutsu: 6: function: not found
mkdir: cannot create directory `/home/greg/.doukutsu': File exists
ln: creating symbolic link `/home/greg/.doukutsu/{doukutsu,DoConfig.exe,data,doc}' to `/usr/share/doukutsu/{doukutsu,DoConfig.exe,data,doc}': File exists
/usr/bin/doukutsu: 11: Syntax error: "}" unexpected

```

I mean I can wine it fine however it does have times of slowdowns on Ubuntu and I would like it to run at native speeds. :P

---

### Post by n2j3 on 2007-11-28
I'd love to say that I can replicate this error and help you but I'm afraid I'm at a loss.. I wonder if the .deb's worked for anyone else

---

### Post by yon2501 on 2007-12-02
im gettin an error message.

```
 sudo dpkg -i doukutsu_20070919-1mdv2007.1_i386.deb
dpkg: error processing doukutsu_20070919-1mdv2007.1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 doukutsu_20070919-1mdv2007.1_i386.deb
```

i opened with the package installer dose that matter or is terminal the only way to do it right?

---

### Post by yon2501 on 2007-12-02
ok scratch that last post i figured it out but now im getting the same error message as GregLH. i could get it on my psp but not on my favorite os :(

---

### Post by n2j3 on 2007-12-03
Still waiting for my new pc (the one destined for *ubuntu). It's due to arrive tomorrow, first thing will be sorting out this .deb mess. I run alien in Antix, another debian based distro so some dependencies could have been left out. Copying from the 'original' port site: 

> 
As I'm not allowed to release the source code there could be problems with certain distribution. Generally a standard Linux with libstdc++ 6.x and SDL 1.2 should be able to run it.


---

### Post by yon2501 on 2007-12-03
well until then ill just have to play it on my psp

---

### Post by osieorb18 on 2007-12-06
I have installed wine and nvidia-glx (non-legacy) and still cannot run Doukutsu.
Every time I try it I get the message:

> **err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !**

a lot of times and then:

> [B]err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
wine: Unhandled page fault on read access to 0x000006f8 at address 0x7e0efab6 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x000006f8 in 32-bit code (0x7e0efab6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e0efab6 ESP:0034fb1c EBP:0034fb44 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:7e19bb20 ECX:7ee52300 EDX:7e197580
 ESI:0015a408 EDI:00159e48
Stack dump:
0x0034fb1c:  00000000 00000000 00400000 00000000
0x0034fb2c:  00000000 00000054 00000000 0015a04c
0x0034fb3c:  7ea4e3d4 0015a04c 0034fbb4 7ea2caa6
0x0034fb4c:  0015a408 7ea43c95 00159e48 00000000
0x0034fb5c:  00000000 0034fba4 00159e48 7ed3daa0
0x0034fb6c:  7ed3daa0 0000c02d 0034fb84 7ee066d0
Backtrace:
=>1 0x7e0efab6 in wined3d (+0x1fab6) (0x0034fb44)
  2 0x7ea2caa6 in ddraw (+0x2caa6) (0x0034fbb4)
  3 0x7ea2ce92 DirectDrawCreate+0x102() in ddraw (0x0034fc04)
  4 0x0040b464 in doukutsu (+0xb464) (0x0034fc8c)
  5 0x00412a1c in doukutsu (+0x12a1c) (0x0034fde0)
  6 0x00481eab in doukutsu (+0x81eab) (0x0034ff0[/B]**8**[B])
  7 0x7b874f2e in kernel32 (+0x54f2e) (0x0034ffe[/B]**8**[B])
  8 0xb7ec49c7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7e0efab6: movl        0x6f8(%eax),%edx
Modules:
Module  Address                 Debug info      Name (81 modules)
PE        400000-  58e000       Export          doukutsu
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e0bd000-7e19e000       Export          wined3d<elf>
  \-PE  7e0d0000-7e19e000       \               wined3d
ELF     7e19e000-7e1b3000       Deferred        midimap<elf>
  \-PE  7e1a0000-7e1b3000       \               midimap
ELF     7e1b3000-7e1d9000       Deferred        msacm32<elf>
  \-PE  7e1c0000-7e1d9000       \               msacm32
ELF     7e1d9000-7e1f1000       Deferred        msacm32<elf>
  \-PE  7e1e0000-7e1f1000       \               msacm32
ELF     7e1f1000-7e22d000       Deferred        wineoss<elf>
  \-PE  7e200000-7e22d000       \               wineoss
ELF     7e22d000-7e2f2000       Deferred        libasound.so.2
ELF     7e301000-7e337000       Deferred        winealsa<elf>
  \-PE  7e310000-7e337000       \               winealsa
ELF     7e37b000-7e3ad000       Deferred        uxtheme<elf>
  \-PE  7e380000-7e3ad000       \               uxtheme
ELF     7e3ad000-7e3b2000       Deferred        libxfixes.so.3
ELF     7e3b2000-7e3bb000       Deferred        libxcursor.so.1
ELF     7e3bb000-7e3c1000       Deferred        libxrandr.so.2
ELF     7e3c1000-7e3c9000       Deferred        libxrender.so.1
ELF     7e3c9000-7e3ce000       Deferred        libxdmcp.so.6
ELF     7e3ce000-7e3d1000       Deferred        libxau.so.6
ELF     7e3d1000-7e4c2000       Deferred        libx11.so.6
ELF     7e4c2000-7e4d0000       Deferred        libxext.so.6
ELF     7e4d0000-7e4d5000       Deferred        libxxf86vm.so.1
ELF     7e4d5000-7e4ed000       Deferred        libice.so.6
ELF     7e4ed000-7e4f6000       Deferred        libsm.so.6
ELF     7e505000-7e590000       Deferred        winex11<elf>
  \-PE  7e510000-7e590000       \               winex11
ELF     7e69f000-7e6bf000       Deferred        libexpat.so.1
ELF     7e6bf000-7e6ea000       Deferred        libfontconfig.so.1
ELF     7e6ea000-7e6fe000       Deferred        libz.so.1
ELF     7e6fe000-7e769000       Deferred        libfreetype.so.6
ELF     7e769000-7e786000       Deferred        imm32<elf>
  \-PE  7e770000-7e786000       \               imm32
ELF     7e786000-7e79a000       Deferred        lz32<elf>
  \-PE  7e790000-7e79a000       \               lz32
ELF     7e79a000-7e7b4000       Deferred        version<elf>
  \-PE  7e7a0000-7e7b4000       \               version
ELF     7e7b4000-7e842000       Deferred        winmm<elf>
  \-PE  7e7c0000-7e842000       \               winmm
ELF     7e842000-7e88b000       Deferred        dsound<elf>
  \-PE  7e850000-7e88b000       \               dsound
ELF     7e88b000-7e8c1000       Deferred        dinput<elf>
  \-PE  7e890000-7e8c1000       \               dinput
ELF     7e8c1000-7e8d4000       Deferred        libresolv.so.2
ELF     7e8e3000-7e901000       Deferred        iphlpapi<elf>
  \-PE  7e8f0000-7e901000       \               iphlpapi
ELF     7e901000-7e95a000       Deferred        rpcrt4<elf>
  \-PE  7e910000-7e95a000       \               rpcrt4
ELF     7e95a000-7e9fb000       Deferred        ole32<elf>
  \-PE  7e970000-7e9fb000       \               ole32
ELF     7e9fb000-7ea50000       Export          ddraw<elf>
  \-PE  7ea00000-7ea50000       \               ddraw
ELF     7ea50000-7eb0e000       Deferred        comctl32<elf>
  \-PE  7ea60000-7eb0e000       \               comctl32
ELF     7eb0e000-7eb67000       Deferred        shlwapi<elf>
  \-PE  7eb20000-7eb67000       \               shlwapi
ELF     7eb67000-7ec6a000       Deferred        shell32<elf>
  \-PE  7eb80000-7ec6a000       \               shell32
ELF     7ec6a000-7ecb3000       Deferred        advapi32<elf>
  \-PE  7ec80000-7ecb3000       \               advapi32
ELF     7ecb3000-7ed4e000       Deferred        gdi32<elf>
  \-PE  7ecd0000-7ed4e000       \               gdi32
ELF     7ed4e000-7ee8c000       Deferred        user32<elf>
  \-PE  7ed70000-7ee8c000       \               user32
ELF     7ef9e000-7efa9000       Deferred        libnss_files.so.2
ELF     7efa9000-7efb3000       Deferred        libnss_nis.so.2
ELF     7efb3000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7eff1000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d51000-b7d55000       Deferred        libdl.so.2
ELF     b7d55000-b7e96000       Deferred        libc.so.6
ELF     b7e97000-b7eae000       Deferred        libpthread.so.0
ELF     b7ebd000-b7fd1000       Export          libwine.so.1
ELF     b7fd3000-b7fee000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\greg\nicholas\personal\Doukutsu\cavestory\Doukutsu.exe
        00000009    0 <==[/B]


what should i do?

---

### Post by osieorb18 on 2007-12-06
could someone help me out with this?

---

### Post by circlemaster on 2008-04-17
> **GregLH said:**
> I'm getting an error doing as you said. Maybe you might know.
```
/usr/bin/doukutsu: 6: function: not found
mkdir: cannot create directory `/home/greg/.doukutsu': File exists
ln: creating symbolic link `/home/greg/.doukutsu/{doukutsu,DoConfig.exe,data,doc}' to `/usr/share/doukutsu/{doukutsu,DoConfig.exe,data,doc}': File exists
/usr/bin/doukutsu: 11: Syntax error: "}" unexpected

```

I mean I can wine it fine however it does have times of slowdowns on Ubuntu and I would like it to run at native speeds. :P

To fix this open /usr/bin/doukutsu in a text editor and replace ```
#!/bin/sh
``` with ```
#!/bin/bash
``` (line 1)

Also a tip is to use "mkdir -p" so it doesn't spam that folders are already created :P

And please make a 64-bit build too!

---

### Post by www.rzr.online.fr on 2008-05-18
> **osieorb18 said:**
> could someone help me out with this?


Test the linux binary at 

[http://community.livejournal.com/doukutsu/102691.html?thread=1207331#t1207331](http://community.livejournal.com/doukutsu/102691.html?thread=1207331#t1207331)

[http://www.scibotic.com/uploads/2008/04/linuxdoukutsu-1.01.tar.bz2](http://www.scibotic.com/uploads/2008/04/linuxdoukutsu-1.01.tar.bz2)

Are there efforts done to opensource the game ?

  * [http://en.wikipedia.org/wiki/Cave_story](http://en.wikipedia.org/wiki/Cave_story)

---

### Post by Perfect Storm on 2008-05-18
Not what I know off.

But I made a 64-bit deb - [http://ubuntuforums.org/showthread.php?t=760712](http://ubuntuforums.org/showthread.php?t=760712) though

---

### Post by Kobayashi-kun on 2009-02-19
Drop.io is asking for a password to access the Cave Story Deb files.

D:

EDIT: Wait, ive found a alternate link.

---

### Post by LordOfMantas on 2009-08-08
Ok, so I've managed to get Cave Story running on my system.  There's just one teeny problem: I can't get the control configuration to stick.  I've tried copying the relevant files over to the virtual C drive in wine, opening them using wine, making my changes, and pasting the newly configured files back to the folder - but when I run Cave Story, it still acts as if I didn't change anything.  And something even stranger is that when I open the configuration program under wine, it shows my changes - but when I open it in Ubuntu, it shows the default configuration.  What am I doing wrong here?  Why didn't opening it in wine edit the data file so that everyone else could see it?  Shouldn't the changes stick regardless of how I made them?

---

### Post by Bradj47 on 2010-04-25
This thread hasn't been updated in a while. That drop.io link doesn't even work anymore. Anyone have a working link?

---

### Post by www.rzr.online.fr on 2011-04-25
> **Bradj47 said:**
> This thread hasn't been updated in a while. That drop.io link doesn't even work anymore. Anyone have a working link?

check:

[http://rzr.online.fr/q/close](http://rzr.online.fr/q/close)


does it playback sound in the intro ?

what is the license to distribute the software ?

---

