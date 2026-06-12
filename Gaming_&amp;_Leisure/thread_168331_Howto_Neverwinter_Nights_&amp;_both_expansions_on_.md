---
title: "Howto: Neverwinter Nights &amp; both expansions on Dapper"
date: 2006-04-30
forum: Gaming &amp; Leisure
---

### Post by Nikusan on 2006-04-30
This guide is for the plain old version of nwn and sou & hotu. For the platinum version look [here]("http://ubuntuforums.org/showthread.php?t=113259").  This guide is written with the assumption that you have both expansion packs. However it will not be too hard to follow if you don't. Just leave out the installer scripts you don't need and be sure to get the appropriate patch.

**1 Download the [graphical installer scripts]("http://icculus.org/~ravage/nwn/").**

```
wget http://icculus.org/~ravage/nwn/donotlinktomyfiles/nwn_129_final.run
wget http://icculus.org/~ravage/nwn/donotlinktomyfiles/shadows_of_undrentide.run
wget http://icculus.org/~ravage/nwn/donotlinktomyfiles/hordes_of_the_underdark.run
```

**2 Install their dependencies:**
```
sudo apt-get install libgtk1.2
```

**3 Install the game:**
Make the scripts executable and run them in turn, providing the discs when asked. Be sure to have your CD Keys handy!

**4 Apply the 1.67 patch**
The patches are available [here]("http://nwn.bioware.com/support/patch.html"). I'm using the english hotu version, be sure to use sou or original if that is all you have.
```
cd ~/nwn
wget http://files.bioware.com/neverwinternights/updates/linux/167/English_linuxclient167_xp2.tar.gz
tar -xzf English_linuxclient167_xp2.tar.gz
```

**5 Apply the bug fix**
As of writing this there is a bug in the 1.67 patch, the fix is explained [here]("http://nwn.bioware.com/forums/viewtopic.html?topic=478668&forum=72&sp=30").
Note: This will probably be a moot point in the near future. If you can see NPCs in the game then the patch you downloaded has probably been fixed and you can disregard this step.
```
cd ~/nwn
wget http://files.bioware.com/neverwinternights/updates/linux/167/linuxclient167fix.tar.gz
rm -f dialogf.tlk
tar -xzf linuxclient167fix.tar.gz
```

**6 Optionally Install Community Expansion Pack**
You can download it [here]("http://nwvault.ign.com/cep/downloads/").
If you get the .rar version (much smaller download) be sure to have unrar installed:
```
sudo apt-get install unrar
```

You will have to manually extract the .mod, .hak, .tlk, etc files. The instructions are all included with the download.

**7 Play the game!**
```

~/nwn/nwn

```

**8 Optionally place a launcher in the menu**
Navigate to Applications > Accessories > Alacarte Menu Editor
Click on the games category.
Click on File > New Entry.
Name: "Neverwinter Nights"
Command: "~/nwn/nwn"
For an icon you can use the file ~/nwn/nwn.ico or you can use the kickass one [here]("http://www.gentoo.org/dyn/icons/GAM.xml").

**9 Be wary of the case sensitive nature of linux when installing modules**
If you have trouble getting a downloaded module to play, try changing the names of the files from that module to all lower case. For example, try changing ToM_2.tlk to tom_2.tlk.

---

### Post by hollywoodb on 2006-04-30
Nice guide... 

Also there is a guide to install NWN + expansions from the Diamond DVD version [here.]("http://nwn.bioware.com/forums/viewtopic.html?topic=469853&forum=72")

The official NWN Linux forum also has other howtos, forum is [here]("http://nwn.bioware.com/forums/viewforum.html?forum=72")

---

### Post by leech on 2006-04-30
This is great, though I find it quite amusing that for this one game, there are so many methods of installing it.  Though a lot of that is due to how many different releases there are;

Original Neverwinter Nights
Shadows Of Undertide Expansion
Hordes of the Underdark Expansion
Gold Edition
Platinum Edition
Diamond Edition
Kingmaker Expansion

I don't think I missed any.

The creator of the Platinum script, has told me that he's working on a universal installer for the game.  This should cover everything from the original campaign version to the Diamond Edition.

His homepage is [http://dsweb.acn.net/deathfirst/](http://dsweb.acn.net/deathfirst/) 

This is great news in my opinion.  The real beauty of Neverwinter Nights is that so far in my experience, it's not dependent at all on what distribution you're running.  Some of the older Loki games won't work without some tweaking on a modern distribution, but as long as this game has been out for Linux, it's worked quite well.

Leech

---

### Post by hollywoodb on 2006-04-30
Its unfortunate that NWN2 most likely will not have a linux client, and may not even have a linux server.

---

### Post by leech on 2006-05-03
There is small hope, but I don't think there is much of it.  Reading through a Faq I managed to find at one point, they said that just because they were adding DirectX to the rendering engine, they weren't going to take out OpenGL.  I think one of the major reasons why Neverwinter Nights was so successful, is that it had ports for all major platforms, Linux, Mac and Windows.  If NWN2 would follow suit, then I'm sure there would be a ton more sales than if there was no port.

Especially since a whole lot of NWN servers run on Linux machines.

Leech

---

### Post by dislexic_one on 2006-05-07
I finally got it installed, but I'm having an issue I hope someone can figure out.  I'm not a *nix noob, but this one's got me stumped.

I can start nwn, pick the prelude but when I select either "Create a new Character" or "Select  premade character" the game unpacks the module, but then on the load of the module it just exits.  No errors, nothing, nadda zip...

I hope someone can help me on this, I'm at a total loss.

---

### Post by leech on 2006-05-07
Did you run it from the terminal and it gave you no output?  

Check in ~/nwn/logs.  There are two different log files in there, check to see what error it is giving you.  If you can't fix it, post the logs here and I'll give a crack at it.

Leech

---

### Post by Echo35 on 2006-05-07
I tried this and could not get it to work at all. In fact, it wouldn't even install. It couldn't detect the second install CD, and gave me a few errors on the first one.

Unable to find file 'chitin.key'
Unable to find file 'data'
Unable to find file 'dmvault'
Unable to find file 'docs'
Unable to find file 'localvault'
Unable to find file 'modules'
Unable to find file 'servervault'
Unable to find file 'texturepacks'

I believe I actually have an older version of Neverwinter Nights (pre 1.29). Is there any way to install the older CD's? I tried Wine, and got the first one running, but the expansions wouldn't install through Wine. If anyone knows how to make those work in Wine, that would be helpful too.

---

### Post by dislexic_one on 2006-05-07
leech:  Yes I ran it from the terminal.  And like before nada.  Here's the log output I could find:

nwclientLog1.txt -
Sun May  7 00:35:30]Server Starting Up: 10 Second Heartbeat logging has been disabled
[Sun May  7 00:35:30]---- Server Options ----
Max Players: 6
Char Levels: (1-40)
Player Password: NO
DM Login Enabled: YES
Server Admin Login Enabled: YES
Post Game To Internet: YES
Game Type: Action
Difficulty: 2
PVP Setting: NONE
Vault: LOCAL
Only One Party: NO
Enforce Legal Characters: NO
Item Level Restrictions: NO
Player pausing: ENABLED
Auto Save: Enabled
Saving Characters in Saved Game
---- End Server Options ----
[Sun May  7 00:35:30] Player  [] () Joined as Server Admin 1
[Sun May  7 00:35:30] Player  () Joined as Player 1
[Sun May  7 00:35:30] Loading Module: Prelude


nwclientError1.txt - 0 bytes / Empty

I've looked at just about every howto, faq and or install option and I keep getting the same result.  Which really sucks because Doom 3, and UT2K4 installed and worked like a champ.

I realy love NWN and I'm really looking forward to playing it under linux :razz:

---

### Post by leech on 2006-05-07
@Echo35

I think 1.29 was the first release for Linux.  If you have the very original copy of it, you may need to go to [http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html) and download the resources.

@dislexic_one

I'm stumped on that one.  Which edition of the game are you running?  If you're running the Platinum or the Diamond edition, following my HowTo should work.

Also make sure you have 3D working, etc.  My error log is empty too, but then my game is working.  I even tried it out with XGL enabled and it worked, though a little choppier than normal.

Leech

---

### Post by Echo35 on 2006-05-07
Well, I installed it in Windows, copied the whole directory over, and tried to "wine" it. It got to the Atari loading animation and then I got this error:

fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:wgl:wglChoosePixelFormatARB unused pfAttribFList
err:wgl:ConvertAttribWGLtoGLX buggy 40 GLX_BUFFER_SIZE default to 32
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fdbe5e0)->(0x4002a,00000008)wine: Unhandled page fault on read access to 0x00000000 at address 0xb7e03aa1 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7e03aa1).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:b7e03aa1 ESP:7faff914 EBP:7faffbbc EFLAGS:00210256(   - 00      RIZAP1)
 EAX:00000001 EBX:b7efcff4 ECX:b7efd380 EDX:7fb2e5e8
 ESI:00000000 EDI:00000000
Stack dump:
0x7faff914:  b7ef0ec9 7beadafe 7bead53a 7befcfc0
0x7faff924:  7bef3d84 7faff9d8 7bed4a5c 7befcfc0
0x7faff934:  7faff9e4 00000000 7befcfc0 7faff958
0x7faff944:  7befcfc0 00000020 00000000 7befcfc0
0x7faff954:  00000020 00000000 00000000 0000001d
0x7faff964:  00000000 00000000 00000000 00000000
0200: sel=1007 base=7fec2000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0xb7e03aa1 in libc.so.6 (+0x30aa1) (0xb7e03aa1)
  2 0xb7e010f8 __strtod_internal+0x38 in libc.so.6 (0xb7e010f8)
  3 0x7eb4452a in libglu.so.1 (+0x1552a) (0x7eb4452a)
  4 0x7eb4efb1 gluBuild2DMipmaps+0x6d in libglu.so.1 (0x7eb4efb1)
  5 0x7ea23814 wine_gluBuild2DMipmaps+0x34 in glu32 (0x7ea23814)
  6 0x0078502f in nwmain (+0x38502f) (0x0078502f)
  7 0x00000000 (0x00000000)
0xb7e03aa1: movzbl      0x0(%edi),%ecx
Modules:
Module  Address                 Debug info      Name (82 modules)
PE      0x00400000-0625f000     Export          nwmain
PE      0x21100000-2115f000     Deferred        mss32
PE      0x30000000-3006d000     Deferred        binkw32
ELF     0x7be86000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7cc45000-7ccc0000     Deferred        ddraw<elf>
  \-PE  0x7cc60000-7ccc0000     \               ddraw
ELF     0x7e67b000-7e690000     Deferred        midimap<elf>
  \-PE  0x7e680000-7e690000     \               midimap
ELF     0x7e7ad000-7e7d1000     Deferred        msacm32<elf>
  \-PE  0x7e7b0000-7e7d1000     \               msacm32
ELF     0x7e7d1000-7e7e8000     Deferred        msacm<elf>
  \-PE  0x7e7e0000-7e7e8000     \               msacm
ELF     0x7e7e8000-7e82c000     Deferred        wineoss<elf>
  \-PE  0x7e800000-7e82c000     \               wineoss
ELF     0x7e84a000-7e84e000     Deferred        libxfixes.so.3
ELF     0x7e84e000-7e857000     Deferred        libxcursor.so.1
ELF     0x7e857000-7e873000     Deferred        ximcp.so.2
ELF     0x7e873000-7e875000     Deferred        xlcutf8load.so.2
ELF     0x7e875000-7e87d000     Deferred        libxrender.so.1
ELF     0x7e87d000-7e8fc000     Deferred        winex11<elf>
  \-PE  0x7e890000-7e8fc000     \               winex11
ELF     0x7e8fc000-7e91b000     Deferred        libexpat.so.1
ELF     0x7e91b000-7e949000     Deferred        libfontconfig.so.1
ELF     0x7e949000-7e95d000     Deferred        libz.so.1
ELF     0x7e95d000-7e9c7000     Deferred        libfreetype.so.6
ELF     0x7e9c7000-7e9e3000     Deferred        imm32<elf>
  \-PE  0x7e9d0000-7e9e3000     \               imm32
ELF     0x7e9e3000-7e9f7000     Deferred        lz32<elf>
  \-PE  0x7e9f0000-7e9f7000     \               lz32
ELF     0x7e9f7000-7ea10000     Deferred        version<elf>
  \-PE  0x7ea00000-7ea10000     \               version
ELF     0x7ea10000-7ea26000     Export          glu32<elf>
  \-PE  0x7ea20000-7ea26000     \               glu32
ELF     0x7ea26000-7ea4f000     Deferred        ws2_32<elf>
  \-PE  0x7ea30000-7ea4f000     \               ws2_32
ELF     0x7ea4f000-7ea68000     Deferred        wsock32<elf>
  \-PE  0x7ea60000-7ea68000     \               wsock32
ELF     0x7ea68000-7eaa9000     Deferred        dinput<elf>
  \-PE  0x7ea80000-7eaa9000     \               dinput
ELF     0x7eaa9000-7eb2f000     Deferred        winmm<elf>
  \-PE  0x7eab0000-7eb2f000     \               winmm
ELF     0x7eb2f000-7eba5000     Export          libglu.so.1
ELF     0x7eba5000-7ec44000     Deferred        libgl.so.1
ELF     0x7ec44000-7ed04000     Deferred        libx11.so.6
ELF     0x7ed04000-7ed1d000     Deferred        libice.so.6
ELF     0x7ed1d000-7edb3000     Deferred        opengl32<elf>
  \-PE  0x7ed50000-7edb3000     \               opengl32
ELF     0x7edb3000-7edd1000     Deferred        iphlpapi<elf>
  \-PE  0x7edc0000-7edd1000     \               iphlpapi
ELF     0x7edd1000-7ee1a000     Deferred        rpcrt4<elf>
  \-PE  0x7ede0000-7ee1a000     \               rpcrt4
ELF     0x7ee1a000-7eea6000     Deferred        ole32<elf>
  \-PE  0x7ee30000-7eea6000     \               ole32
ELF     0x7eea6000-7eee4000     Deferred        advapi32<elf>
  \-PE  0x7eeb0000-7eee4000     \               advapi32
ELF     0x7efca000-7f8ce000     Deferred        gdi32<elf>
  \-PE  0x7f010000-7f8ce000     \               gdi32
ELF     0x7f8ce000-7f9f0000     Deferred        user32<elf>
  \-PE  0x7f8f0000-7f9f0000     \               user32
ELF     0x7fb00000-7fb03000     Deferred        libxrandr.so.2
ELF     0x7fb03000-7fb10000     Deferred        libxext.so.6
ELF     0x7fb12000-7fb16000     Deferred        libxdmcp.so.6
ELF     0x7fb16000-7fb19000     Deferred        libxau.so.6
ELF     0x7fc61000-7fd60000     Deferred        kernel32<elf>
  \-PE  0x7fc80000-7fd60000     \               kernel32
ELF     0x7fe71000-7fe7c000     Deferred        libgcc_s.so.1
ELF     0x7fe7c000-7fe87000     Deferred        libnss_files.so.2
ELF     0x7fe87000-7fe91000     Deferred        libnss_nis.so.2
ELF     0x7fe91000-7fea7000     Deferred        libnsl.so.1
ELF     0x7fea7000-7feb1000     Deferred        libnss_compat.so.2
ELF     0x7feb1000-7feb6000     Deferred        libxxf86vm.so.1
ELF     0x7feb6000-7febb000     Deferred        libxxf86dga.so.1
ELF     0x7febb000-7fec2000     Deferred        libsm.so.6
ELF     0x7fec6000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7dcf000-b7dd3000     Deferred        libdl.so.2
ELF     0xb7dd3000-b7f01000     Export          libc.so.6
ELF     0xb7f01000-b7f14000     Deferred        libpthread.so.0
ELF     0xb7f26000-b7f40000     Deferred        libwine.so.1
ELF     0xb7f42000-b7f58000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000b    0
00000008 (D) Z:\home\echo35\nwn\NeverwinterNights\NWN\nwmain.exe
        00000010    0
        0000000f    0
        0000000c    0
        00000009    0 <==

From what I understand, the Linux client on the Bioware site also works with a Windows install, so I'm going to try that now.

---

### Post by Echo35 on 2006-05-07
Ok, I did that, and NWN runs great now, except it's laggy and I can't enable any special graphics options. Do I need a graphics card driver or something?

---

### Post by dislexic_one on 2006-05-07
[QUOTE=leech]@Echo35

I think 1.29 was the first release for Linux.  If you have the very original copy of it, you may need to go to [http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html) and download the resources.

@dislexic_one

I'm stumped on that one.  Which edition of the game are you running?  If you're running the Platinum or the Diamond edition, following my HowTo should work.

Also make sure you have 3D working, etc.  My error log is empty too, but then my game is working.  I even tried it out with XGL enabled and it worked, though a little choppier than normal.

Leech[/QUOTE]

Platinum Edition, and 3D works.  Like I said, UT2K4 and Doom 3 work great.

I'll try your howto and see if that works.  Thanks for the quick replies. :)

---

### Post by dislexic_one on 2006-05-07
LEECH:

Ok, tried it with your howto and I'm getting the same results.  It loads the main screen and I can pick new, then Original Campaign, Prelude, Create New Character it unpacks the module and just as it loads the module, it exits back to the terminal window. :( 

:?: :?: :?: :?: :?: :?: 

I wish I could narrow it down more, I can't tell if it's permissions, or graphics or what... it's wierd.

Any suggestions?

---

### Post by Nikusan on 2006-05-08
[QUOTE=Echo35]Ok, I did that, and NWN runs great now, except it's laggy and I can't enable any special graphics options. Do I need a graphics card driver or something?[/QUOTE]

You're probably right about needing a graphics driver. Try [reading this]("https://wiki.ubuntu.com/BinaryDriverHowto").

---

### Post by leech on 2006-05-08
[QUOTE=Echo35]Ok, I did that, and NWN runs great now, except it's laggy and I can't enable any special graphics options. Do I need a graphics card driver or something?[/QUOTE]

Wait, now I'm confused, re-reading your post, I realized that you said you were using Wine to run it?  There is  native client for it, no need for wine at all.  If you have the original, then just use the howto in the original post.  It'll install, and then make sure you also run the 1.66 update (or maybe even the 1.67 update if it's on liflg.org.)

Open a terminal and run ```
glxinfo | grep direct
``` and it should output > direct rendering: Yes

If it does not, then follow Nikusan's advice.

Leech

---

### Post by leech on 2006-05-08
[QUOTE=dislexic_one]LEECH:

Ok, tried it with your howto and I'm getting the same results.  It loads the main screen and I can pick new, then Original Campaign, Prelude, Create New Character it unpacks the module and just as it loads the module, it exits back to the terminal window. :( 

:?: :?: :?: :?: :?: :?: 

I wish I could narrow it down more, I can't tell if it's permissions, or graphics or what... it's wierd.

Any suggestions?[/QUOTE]

What video card do you have?  I'm running an nVidia 6800GT here just fine.  If it's a permissions issue, you could always just chmod 755 the directory.  I do know that if you have a problem with fonts not appearing, then it is due to permissions.  

Leech

---

### Post by Echo35 on 2006-05-08
I have a Raedon 9200 SE, so the ATI driver you gave me doesn't help. When I ran that command in shell, I got:

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

---

### Post by Echo35 on 2006-05-08
$ ./nwn
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Creating link /home/echo35/.kde/socket-ubuntu.
can't create mcop directory

Ok? It worked a little while ago, what's wrong now?

---

### Post by dislexic_one on 2006-05-08
[QUOTE=leech]What video card do you have?  I'm running an nVidia 6800GT here just fine.  If it's a permissions issue, you could always just chmod 755 the directory.  I do know that if you have a problem with fonts not appearing, then it is due to permissions.  

Leech[/QUOTE]

I'm running an nVidia GeForce FX 5200.

---

### Post by leech on 2006-05-09
[QUOTE=Echo35]I have a Raedon 9200 SE, so the ATI driver you gave me doesn't help. When I ran that command in shell, I got:

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect[/QUOTE]

That means you have no 3D acceleration.  ATI says their driver (the fglrx) supports the 8500 and higher.  Which means that is the driver you want.

Leech

---

### Post by Echo35 on 2006-05-09
I'll give the driver a try, but I'm still getting that wierd error:

$ ./nwn
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Link points to "/tmp/ksocket-echo35"
can't create mcop directory

---

### Post by Echo35 on 2006-05-09
I tried the driver, and I still get:

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

---

### Post by leech on 2006-05-10
Could you post the output of your /var/log/Xorg.0.log?

Leech

---

### Post by Simian on 2006-05-10
Thanks for the "How To" leech. :)

It worked well. But I am unable to read anything in the menus. The menus are the but there are no words. They are just blank.

Any ideas?


EDIT - it's ok I just needed to replace the dialog.tlk file

apparently it's a known bug [http://nwn.bioware.com/support/known.html#21]("http://nwn.bioware.com/support/known.html#21")

Thanks again though leech

---

### Post by Echo35 on 2006-05-10
[quote=leech]Could you post the output of your /var/log/Xorg.0.log?

Leech[/quote] 
The whole thing? Oh, by the way, that odd error also happens with winecfg when I hit the sound tab. What does that mean?

---

### Post by leech on 2006-05-10
Well, first off, Neverwinter Nights requires 3D acceleration to be working.  So let's worry about that first.

The mcop errors I think are KDE related, but I don't run KDE so I don't know.

Leech

---

### Post by Echo35 on 2006-05-11
Interesting. I don't even run KDE :confused:. Anyway, here's the (long) log.

EDIT: The file is too long to post and it won't let me attach it. Should I e-mail it to you?

---

### Post by leech on 2006-05-12
[QUOTE=Echo35]Interesting. I don't even run KDE :confused:. Anyway, here's the (long) log.

EDIT: The file is too long to post and it won't let me attach it. Should I e-mail it to you?[/QUOTE]

That's very strange indeed.  From what I could gather from Google, the mcop error is either KDE or probably in your case especially Arts.  See if you have the Arts Daemon.  

Run 'ps -A|grep art' from the terminal and see if it shows artsd as output.  

Not sure why Neverwinter Nights would give that error though, since I don't think it even uses the sound daemon, though I could be wrong.

Also you can gzip up the X.org log file and post it, that'll shrink it a lot.

I just copied it from /var/log to my home directory then run 'gzip Xorg.0.log' on it.

Leech

---

### Post by Echo35 on 2006-05-12
Nope, I use ASLA. I ran the command and arts didn't show up anyway. Ok, I gzipped it, and it seems to work, so here's the log.

---

### Post by brainkilla on 2006-05-12
[QUOTE=dislexic_one]LEECH:

Ok, tried it with your howto and I'm getting the same results.  It loads the main screen and I can pick new, then Original Campaign, Prelude, Create New Character it unpacks the module and just as it loads the module, it exits back to the terminal window. :( 

:?: :?: :?: :?: :?: :?: 

I wish I could narrow it down more, I can't tell if it's permissions, or graphics or what... it's wierd.

Any suggestions?[/QUOTE]

One of your guesses is right, it's 99% permission problem. I know, 'cause I had it with the game ;) . Just chmod everything in /usr/local/games/nwn, and you're good to go...

---

### Post by leech on 2006-05-12
[QUOTE=Echo35]Nope, I use ASLA. I ran the command and arts didn't show up anyway. Ok, I gzipped it, and it seems to work, so here's the log.[/QUOTE]

I'm completely stumped on the mcop error then.  As far as getting 3D going it looks like the Radeon driver doesn't recognize your particular model of the 9200SE (thank ATI for having different chip IDs for non-ATI manufactured cards).  What you'll need to do is make sure your /etc/X11/xorg.conf is configured to use fglrx instead of radeon.  Just use nano to edit it, like so.

```
sudo nano /etc/X11/xorg.conf
``` then use Control+W to do a search for radeon, then change that to fglrx, then use Control+X to save it, then it'll ask if you want to overwrite, just type Y.  Then you'll need to restart X.org.  Log out, then just hit Control+Alt+Backspace and it'll restart GDM, then log in and try the ```
glxinfo |grep direct
``` from a terminal again.  Hopefully this time it'll give you the answer of Yes.  It should auto load the fglrx module.  If not, you can try to reboot to see if it'll work.

Leech

---

### Post by Echo35 on 2006-05-13
](*,) .... *Smashes head against cpu* ](*,)

Nope, STILL not enabled. How hard can it be to make a graphics card work? Oh, I'd also like to point out that the mcop error happens when I click the "Sound" settings tab in winecfg, so I think it's a problem beyond Neverwinter Nights.

---

### Post by leech on 2006-05-13
Yeah, I pretty much thought the same thing about the mcop problem.  Honestly, I don't have an ATI card (for good reason, the support on linux pretty much sucks).  I would do a search on these forums for getting direct rendering working on your video card.

Leech

---

### Post by jefrey on 2006-05-20
Thanks for the guide!  Hopefully I'll be playing soon... :D 

Your guide is almost exactly what I had planned to do, with the exception of the bug fix and community expansion pack install.  Thanks for those!

---

### Post by leech on 2006-05-20
By the way, my guide works flawlessly on Dapper as well as Breezy and probably all other distributions.  I just updated the link on it to the proper install-nwn.sh script.  I have talked to the creator of that script, and he's updated it now to fix the patching and also to install the 1.67 patch as well.  It also supports the Diamond Edition (though I haven't personally tested that.)

Leech

---

### Post by Echo35 on 2006-05-21
I have been playing with it for a while now. The 3D rendering is still not enabled, however, NwN works flawlessly now. I don't know how, but the mcop error just went away and the game works smoothly. The only problem is that the mouse moves a little wierd, but I think that's just linked to the way I have the mouse settings set up in Breezy. I don't know why, but it all suddenly works now. Strange, but hey, I'm not complaining! Also note that the other programs I had that were not working previously are also now working, so something important seemed to fix itself.

---

### Post by leech on 2006-05-21
That's odd, but hey, I wouldn't complain if it magically fixed itself :D  Sounds to me like your 3D is working now, but I would think that glxinfo or fglrxinfo would tell you as such.

Leech

---

### Post by Echo35 on 2006-05-21
Hey, it is working! That's really odd. I didn't even do anything! Well, that's not the first time my computer seemingly "fixed itself". Oh well, that's cool.

---

### Post by RagerX on 2006-05-25
[QUOTE=Echo35]I tried this and could not get it to work at all. In fact, it wouldn't even install. It couldn't detect the second install CD, and gave me a few errors on the first one.

Unable to find file 'chitin.key'
Unable to find file 'data'
Unable to find file 'dmvault'
Unable to find file 'docs'
Unable to find file 'localvault'
Unable to find file 'modules'
Unable to find file 'servervault'
Unable to find file 'texturepacks'

I believe I actually have an older version of Neverwinter Nights (pre 1.29). Is there any way to install the older CD's? I tried Wine, and got the first one running, but the expansions wouldn't install through Wine. If anyone knows how to make those work in Wine, that would be helpful too.[/QUOTE]


This happened to me too. I fixed it by uninstalling Wine. :D

---

### Post by leech on 2006-05-26
No Wine required (unless you have the Diamond edition for the Kingmaker module).    If you have the original or gold edition, just use the installers from [http://icculus.org/~ravage/nwn](http://icculus.org/~ravage/nwn).

Leech

---

### Post by ZylGadis on 2006-05-26
[QUOTE=leech]No Wine required (unless you have the Diamond edition for the Kingmaker module).    If you have the original or gold edition, just use the installers from [http://icculus.org/~ravage/nwnhttp://icculus.org/~ravage/nwn](http://icculus.org/~ravage/nwnhttp://icculus.org/~ravage/nwn).

Leech[/QUOTE]

Leech, I believe you actually mean [http://icculus.org/~ravage/nwn]("http://icculus.org/~ravage/nwn"). Clicking what you have produces a rather awkward result :)

---

### Post by leech on 2006-05-26
Indeed you're right.  I got middle-mouse button happy there and pasted it too many times.  Well, that's what happens when you're trying to think off of 3 hours of sleep.

Leech

---

### Post by RagerX on 2006-05-28
[QUOTE=leech]No Wine required (unless you have the Diamond edition for the Kingmaker module).    If you have the original or gold edition, just use the installers from [http://icculus.org/~ravage/nwn](http://icculus.org/~ravage/nwn).

Leech[/QUOTE]

Yes..but not exactly true. The installer needs to use wine to extract the data from cd's 1 + 2, it comes bundled with it's own wine binaries. But it will only use them if you don't have wine already installed. It seems to fall over (well it did for me) if you have wine (version 0.9.13) installed.

---

### Post by hollywoodb on 2006-05-28
You don't need wine at all (except the kingmaker module), and you don't need the icculus.org installers.... all can be done natively in linux, howtos at the official forum:

[http://nwn.bioware.com/forums/viewforum.html?forum=72]("http://nwn.bioware.com/forums/viewforum.html?forum=72")

---

### Post by leech on 2006-05-29
Yeah, but the Icculus installers are much easier/nicer to use.  Wine is NOT required by the method I have written up, though.  It uses unshield to extract the files from the CD's for the Platinum and Diamond edition.

Leech

---

### Post by sir_cheats_a_lot on 2006-05-30
[QUOTE=hollywoodb]You don't need wine at all (except the kingmaker module), and you don't need the icculus.org installers.... all can be done natively in linux, howtos at the official forum:

[http://nwn.bioware.com/forums/viewforum.html?forum=72]("http://nwn.bioware.com/forums/viewforum.html?forum=72")[/QUOTE]

I wouldn't follow the directions on the official site...they tend to NOT work.  At least they never worked for me.  I used the Install script with unshield to get it working, but menu fonts ended up uncentered, and game play was sluggish.  so here i am playing NWN on windows, and the game randomly crashes out...bioware says it's the driver but i updated it and it still does it, so it's more likely a bad install(i'm just too lazy to reinstall it)  so i must quick save a lot, but not really a big deal.

 alternatively for installing Kingmaker just copy the kingmaker files from a windows install and put them in a archive.  I have a fat partition setup for sharing files between Linux and windows so all i had to do is move the files to that partition, then reboot.    This was mentioned somewhere in a forum.  So No Wine isn't needed at all.

---

### Post by hollywoodb on 2006-05-30
[QUOTE=sir_cheats_a_lot]I wouldn't follow the directions on the official site...they tend to NOT work.  At least they never worked for me.  I used the Install script with unshield to get it working, but menu fonts ended up uncentered, and game play was sluggish.  so here i am playing NWN on windows, and the game randomly crashes out...bioware says it's the driver but i updated it and it still does it, so it's more likely a bad install(i'm just too lazy to reinstall it)  so i must quick save a lot, but not really a big deal.
.........[/QUOTE]


I followed the howto for the Diamond edition (DVD with Shadows & Hordes + Kingmaker) and it worked out perfectly... I haven't bothered with the Kingmaker part yet though.

---

### Post by sir_cheats_a_lot on 2006-05-30
[QUOTE=hollywoodb]I followed the howto for the Diamond edition (DVD with Shadows & Hordes + Kingmaker) and it worked out perfectly... I haven't bothered with the Kingmaker part yet though.[/QUOTE]

Cool 8)   When i got the diamond edition DVD they didn't have a how to that worked. everytime it would get to ./fixinstall it would break, then i tried once without ./fixinstall and it worked but only the original campaign and SoU.  i wish i wasn't stuck on dialup; it would deifinatly make getting all the extra files easier.  I suppose i can go try it.
     Glad they got one right. :-D    Kingmaker wasn't exactly all that special.  kind of a waste of $20 really.  If shadowgaurd and witch's wake were a hour longer with a definate ending then it would have worth it.  hopefully i won't have a problem with the install this time.

---

### Post by seth0x2b on 2006-06-01
First of all:Nice thread and HowTo!
Games were the only thing I was missing now that I am 100% on Ubuntu. Since I only play RPG's(and, of course: Doom3 :) ) it's really nice to see Neverwinter Nights come back to life on my box. I installed it using the resources on Bioware's site, because for some reason my original cd's were not getting extracted using ravager's installer.
I then installed the 1.67 patch, and tried to run ./nwn, but for some reason, the screen was messed up. I fixed this by removing the ./lib reference in nwn, so that the game uses Dapper's SDL version. Voila! I works!
It runs the game really nice(considering I have a Radeon 9200SE).
My only problem is this: The mouse is very laggy, it moves really weird.
Did someone manage to get a solution for this?!
I have direct rendering enabled, but for some reason I get only 120 FPS(on Hoary with fglrx I was getting 700-800 FPS). Could this explain the mouse  behavior?!
Any hint/advice is welcomed!
Cheers

---

### Post by seth0x2b on 2006-06-02
Took me the whole morning but I finally got the mouse to work as smooth as possible!
It turns out the problem was that Neverwinter had no hardware mouse support, so the mouse movement was affected by the FPS.
I downloaded and compiled NWMouse from [http://home.woh.rr.com/nwmovies/](http://home.woh.rr.com/nwmovies/)
Instalation:
first open synaptic, do a search for libelf and install dev package(I installed everything, there were 4 libs).
After you install libelf:

```

tar -zxvf nwmouse-latest.tar.gz
cd nwmouse
./nwmouse_install
mkdir <nwn directory>/nwmouse
cp -a cursors <nwn directory>/nwmouse/
cp -a libdis <nwn directory>/nwmouse/
cp nwmouse.so <nwn directory>/

```
then open nwn with any text editor and add this 
```

export XCURSOR_PATH=`pwd`
export XCURSOR_THEME=nwmouse
export LD_PRELOAD=./nwmouse.so

```
under "export SDL_VIDEO_X11_DGAMOUSE=0"
That's it! Run ./nwn, and don't be scared...you'll see nwmouse doing it's thing with nwn.It will tell you if it all went ok...
You now have to start ./nwn again and voila!: Hardware mouse support.

If by some reason you can't compile nwmouse, i'll attach the .so, although I don't think there will be any problems.


[EDIT]: The game mouse cursor will be replaced by the system's default cursor.To fix this, download [http://home.woh.rr.com/nwmovies/cursors.tar.gz](http://home.woh.rr.com/nwmovies/cursors.tar.gz) and extract the contents in the "nwmouse/cursors" directory.
Cheers

---

### Post by digimars on 2006-06-08
I got the game working fine (using the Diamond release on Dapper).  I can run the game fine when I go to the game's directory and use "./nwn", but I would like to set up a menu entry for it.

I added a menu entry under games using the command "~/nwn/nwn", but it gives me this error:
Could not launch menu item

Details: Failed to execute child process "~/nwn/nwn" (No such file or directory)

The game is installed under my user directory "/home/me/nwn".  So I tried to use "/home/me/nwn/nwn" for a command and nothing happens.

Does anyone know how I can set this up?

---

### Post by seth0x2b on 2006-06-08
You could try this as the launcher's command:
```
sh -c "cd /home/<user>/nwn/ && ./nwn"
``` Replace <user> with your username of course :)

Cheers

---

### Post by digimars on 2006-06-08
Awesome!  That did the trick, thanks!

---

### Post by hellfire_bg on 2006-06-08
Is there any way to get the movies working in dapper. I tried with NWMovies but i get this error:
> ./nwmovies.pl AtariLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: AtariLogo: Tue Jun  6 08:47:09 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
1149572831.546112: BinkLib: SDL_PRELOAD Initialized
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
NOTICE: NWMovies.pl finished playing: AtariLogo: Tue Jun  6 08:47:13 2006
./nwmovies.pl BiowareLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: BiowareLogo: Tue Jun  6 08:47:14 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/BiowareLogo.bik
1149572834.579726: BinkLib: SDL_PRELOAD Initialized
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
NOTICE: NWMovies.pl finished playing: BiowareLogo: Tue Jun  6 08:47:14 2006
./nwmovies.pl WotcLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: WotcLogo: Tue Jun  6 08:47:14 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/WOTCLogo.bik
1149572835.037499: BinkLib: SDL_PRELOAD Initialized
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
NOTICE: NWMovies.pl finished playing: WotcLogo: Tue Jun  6 08:47:15 2006
./nwmovies.pl fge_logo_black >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: fge_logo_black: Tue Jun  6 08:47:15 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/fge_logo_black.bik
1149572835.614518: BinkLib: SDL_PRELOAD Initialized
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
NOTICE: NWMovies.pl finished playing: fge_logo_black: Tue Jun  6 08:47:15 2006
./nwmovies.pl NWNIntro >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: NWNIntro: Tue Jun  6 08:47:16 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/NWNintro.bik
1149572836.095388: BinkLib: SDL_PRELOAD Initialized
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
NOTICE: NWMovies.pl finished playing: NWNIntro: Tue Jun  6 08:47:16 2006
./nwmovies.pl Prelude >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: Prelude: Tue Jun  6 08:47:24 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/prelude.bik
1149572844.647864: BinkLib: SDL_PRELOAD Initialized
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
NOTICE: NWMovies.pl finished playing: Prelude: Tue Jun  6 08:47:24 2006
./nwmovies.pl AtariLogo >> nwmovies.log 2>&1


---

### Post by seth0x2b on 2006-06-08
I had the same problem with nwmovies, I managed to fix it but I don't know exactly how.
I must say that I have never got them to show up on screen, only audio and black screen while playing.But I play them separetly every time I finish a chapter :D.
Go here [http://nwn.bioware.com/forums/viewtopic.html?topic=473100&forum=72]("http://nwn.bioware.com/forums/viewtopic.html?topic=473100&forum=72") and see if it helps.

Cheers

---

### Post by hellfire_bg on 2006-06-09
I just want them to work... The worst thing is that several months ago i managed to get them working perfectly but i too don`t remember how i did this (i guess i followed a HOWTO). I`m not even sure on what distro it was. It was either on gentoo or on Ubuntu 5.10. BTW i saw this thread and tried to recompile libSDL as suggested. Now i can`t even start NWN with NWMovies enabled. I get this error:
./nwn
NOTICE: NWMovies: Version: 20060113.161108
NOTICE: SDL Library determined to be: /usr/lib/libSDL-1.2.so.0
WARNING: NWMovies: INI recalculation required: 7734576:0 1146250588:0 410148:0 1146250588:0
WARNING: NWMovies: SDL_WM_GrabInputRaw() not visible.  Looking for it the hard way.
WARNING: NWMovies: This may not work.
NOTICE: NWMovies: (crumb) Entry point determined: 0xc440
SERIOUS FATAL ERROR: NWMovies: (cookie) Magic cookie not found.
SERIOUS FATAL ERROR: NWMovies: (cookie)    Please contact David Holland (zzqzzq_zzq@hotmail.com)
./nwn: line 13:  2284 Aborted                 ./nwmain $@
And this is both times when i use Bioware`s lib and the one i compiled.

---

### Post by seth0x2b on 2006-06-09
>  SERIOUS FATAL ERROR: NWMovies: (cookie) Magic cookie not found.
I'm not sure, but I think there's something wrong with your game executable(nwmain). Try reinstalling the client files.

Cheers

---

### Post by Fallom on 2006-06-13
I have NWN Diamond, and the install guide on the Bioware forums worked great up until this step for installing Kingmaker: "wine KingmakerSetup.exe"

Doing that just gets me this error: "wine: could not load L"N:\\KingmakerSetup.exe": Module not found
"

I checked .wine/dosdevices/n and the exe is definitely both in there and in my NWN install directory.

---

### Post by jadugarr on 2006-06-15
[QUOTE=Fallom]I have NWN Diamond, and the install guide on the Bioware forums worked great up until this step for installing Kingmaker: "wine KingmakerSetup.exe"

Doing that just gets me this error: "wine: could not load L"N:\\KingmakerSetup.exe": Module not found
"

I checked .wine/dosdevices/n and the exe is definitely both in there and in my NWN install directory.[/QUOTE]

You should check out the native nwn installer like others have suggested.  It should work a lot better than using wine.

I have problem with running nwn after using the installer in Dapper.  When I try to run the game I get an error that it can't find the shared libraries libmss.so.6 .   I do have the nvidia drivers installed, so I spoze it's just a matter of creating a symbolic link to the proper library.  Any help is appreciated.

---

### Post by seth0x2b on 2006-06-15
[quote=jadugarr] I have problem with running nwn after using the installer in Dapper.  When I try to run the game I get an error that it can't find the shared libraries libmss.so.6 .   I do have the nvidia drivers installed, so I spoze it's just a matter of creating a symbolic link to the proper library.  Any help is appreciated.[/quote]
In your "nwn" directory there is a folder called "miles". Copy the contents of that folder to /usr/lib/ and it should work.

Cheers

---

### Post by jadugarr on 2006-06-15
[QUOTE=seth0x2b]In your "nwn" directory there is a folder called "miles". Copy the contents of that folder to /usr/lib/ and it should work.

Cheers[/QUOTE]

Thanks.  I did this and had to create a symbolic link libmss.so.6 to the file included in miles and also change the export path from /lib/ to /usr/lib.  I don't remember having to do this in Breezy, but it's now working great :).

---

### Post by Fallom on 2006-06-15
[QUOTE=jadugarr]You should check out the native nwn installer like others have suggested.  It should work a lot better than using wine.
[/QUOTE]

Well when I deleted everything and went through all the steps again everything seemed to work fine. The only thing I did differently was to just copy the kingmaker setup to the NWN folder instead of making a link.

---

### Post by herot on 2006-06-16
Amazing!! i installed Neverwinter Nights Gold last night using the Gold installer located [here.]("http://icculus.org/~ravage/nwn/") It works wonderfully... i did have a small issue getting the installer to "see" my cds when it asked to change from cd1 to cd2 etc... but i found that by listening to the drive i could let it "spin up" and "level out" fully before clicking to try again... 

additionally, i did not have to turn off supermount (same as turning off the automount feature for cd drives in Ubuntu?) to get NWN installled as it says you may need to do in the [FAQ]("http://icculus.org/~ravage/nwn/faq.html")

anyway, after installing it seems to play even better than it did in my old XP installation...!!!  I was able to install the patch from [here.]("http://nwn.bioware.com/support/patch.html") all i did was extract it and copy all the files from it into my ~/nwn/ folder... after doing this the savegames i had created in windows opened and ran fine!! (before i got a message saying the game was created using a newer version of NWN...when i tried to load them).

anyway, i have been using linux off and on for a while now but this is the first time i have seen such a break thru with gaming... alot of things can be made to RUN on linux but RUN FASTER??? my god man! look out microsoft!! i have backed up my old "c" and "d" drives and am formatting them to ext3 when i get home today!!

all hail Ubuntu!! and [WINE]("http://en.wikipedia.org/wiki/Wine_Is_Not_an_Emulator") of course!!

now how do i get this cool looking icon to actually start NWN instead of having to run it in a terminal everytime??? i tried ~/nwn/nwn with "run in terminal" option set and i can't seem to figure it out!

[COLOR="Red"]*UPDATE* nevermind Seth0x2b already posted the fix to this on page 6... thanx guys![/COLOR]

---

### Post by justin whitaker on 2006-06-16
Hey guys! Good to see so much success going on. Since I switched to Dapper for good, I've been working on getting all my games set up via Wine, Cedega, or via a native installer.

One question: can you point me to a how to for the DVD Platinum edition? It installs NWN and the expansions in one go, which seems someone antithetical to the .run strategy here. 

Will the Diamond how-to work?

---

### Post by herot on 2006-06-16
hollywoodb (page 1 of this topic) gave a link to [this site]("http://nwn.bioware.com/forums/viewtopic.html?topic=469853&forum=72") (bioware site) which talks about the DVD version... and also more NWN forum howtos are [here]("http://nwn.bioware.com/forums/viewforum.html?forum=72") 

hope this helps!!
and have fun!!

---

### Post by justin whitaker on 2006-06-16
[QUOTE=herot]hollywoodb (page 1 of this topic) gave a link to [this site]("http://nwn.bioware.com/forums/viewtopic.html?topic=469853&forum=72") (bioware site) which talks about the DVD version... and also more NWN forum howtos are [here]("http://nwn.bioware.com/forums/viewforum.html?forum=72") 

hope this helps!!
and have fun!![/QUOTE]

Thank you sir! I'l check those when I get home: corporate firewall and all. Forums=good, game sites=bad. ;)

---

### Post by mlind on 2006-06-17
This is probably known already, but you can run NWN in windowed mode too.
Just edit your **nwn/nwn.ini** file

On [Display Options] section, change FullScreen=1 to **FullScreen=0** and add
**AllowWindowedMode=1**

---

### Post by mlind on 2006-06-17
[QUOTE=jadugarr]Thanks.  I did this and had to create a symbolic link libmss.so.6 to the file included in miles and also change the export path from /lib/ to /usr/lib.  I don't remember having to do this in Breezy, but it's now working great :).[/QUOTE]

That error happens if you start NWN using nwmain istead of nwn script.

---

### Post by seth0x2b on 2006-06-18
I'll have to disagree. I always use the "nwn" script and had that problem the first time I installed the game. I copied the miles libs to /usr/lib, and everything worked ok


Cheers

P.S. And yes, I did have ```
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH
``` set up :)

---

### Post by mlind on 2006-06-18
[QUOTE=seth0x2b]I'll have to disagree. I always use the "nwn" script and had that problem the first time I installed the game. I copied the miles libs to /usr/lib, and everything worked ok


Cheers

P.S. And yes, I did have ```
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH
``` set up :)[/QUOTE]

Ok, well important part is that the game works ;)

my game is patched to v1.67 and nwn seems to contain miles exports already.
I didn't have to do any additional symlinking.

nwn script:
```

#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH

./nwmain $@

```

---

### Post by Zeterai on 2006-06-20
I'm having the same problem as one of the previous users; the solution was copying the /nwn/miles contents into usr/lib. The problem is, that and seemingly everything on my system is set under the group & user root, and I can't unlock anything at all. When I tried copying over it said I didn't have permission... I reinstalled dapper this morning since I had a few problems with Synaptic yesterday after playing with a few things.

Any clue as to how I can unlock that folder?


That's when I use ./nwmain. When I use just ./nwn it says it failed to intialize the graphics. I can't figure out how to put the NVIDIA drivers in... init 2 doesn't seem to turn off X, and init 1 is too low to let it install properly >.<

---

### Post by Zeterai on 2006-06-21
Fixed it. Turns out that when I enabled the nvidia drivers it somehow decided to change the profile for my gfx card in X to.. a radeon, using NVIDIA drivers. Weird.

I have no trouble using just nwn".exe" to run it, though I'm hitting a snag whilst trying to create a shortcut.

---

### Post by mlind on 2006-06-21
[QUOTE=Zeterai]Fixed it. Turns out that when I enabled the nvidia drivers it somehow decided to change the profile for my gfx card in X to.. a radeon, using NVIDIA drivers. Weird.

I have no trouble using just nwn".exe" to run it, though I'm hitting a snag whilst trying to create a shortcut.[/QUOTE]

yup, same here. I've created yet another launcher script, called **run-nwn**, which contains
```

#!/bin/sh

cd /path/to/nwn
exec ./nwn

```

And create desktop launcher for this item instead. Looks ugly but works.

---

### Post by Zeterai on 2006-06-21
[[img]http://img139.imageshack.us/img139/4832/l33tgamnwnicon1yu.png[/img]](http://imageshack.us)

Icon for your launcher, looks awesome for me. I got it all working, though it took a couple hours. I have my NWN installed straight to the desktop and not root - I'm a module builder so I like having easy access to the haks/modules/erfs. 

My NEW problem is figuring out how to make the mouse work. It's choppy but I followed the directions for nwmouse - problem being...

"
zeterai@Frost:~/Desktop/nwmouse$ cp nwmouse.so ~/Desktop/nwn
cp: cannot stat `nwmouse.so': No such file or directory
"

---

### Post by Zeterai on 2006-06-21
Mayhaps my not having perl...or automake or libtool. libnw CVS... really, I seem to be missing a lot of things the ReadMe says I need.

---

### Post by seth0x2b on 2006-06-22
Could you post the result of 
```
ls
``` please?!
Did the compilation go ok?!
 
Cheers

---

### Post by bkress82 on 2006-07-12
Been reading this thread for helps using Ravage's graphical installers. I am using the one for the Gold edition, when i run it I see a window that shows the following:

```
Verifying archive integrity...All good.
Uncompressing Neverwinter Nights Gold Edition.............................
..............................
Press Return to close this window....
```

After I press return the window closes. It never asks me for any CD's or launches the installer shown in the screenshots. I haven't seen mention of this before so I figured I'd Post it, and see if anyone could help me out.

---

### Post by __lonewolf on 2007-09-19
hello all.
  I have nwn working on fiesty amd64, except for 1 issue.  I installed nwmouse, got it to compile with no errors.  When I try to run my script using nwmouse.so, I get the following error.

./nwmain: symbol lookup error: ./nwmouse.so: undefined symbol: XFixesSetCursorName
ERROR: ld.so: object './nwmouse.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object './nwmouse.so' from LD_PRELOAD cannot be preloaded: ignored.


any ideas?

Thanks in advance...

---

