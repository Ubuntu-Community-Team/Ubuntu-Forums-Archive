---
title: "Help with COD"
date: 2005-03-23
forum: Gaming &amp; Leisure
---

### Post by george29 on 2005-03-23
Hello All,

....edit..........

I've sorted some of it, but now i get the message below telling me my version of windows doesn't support COD? anybody got any ideas on how to fix it? 

cheers
George

CODUO MP 1.51 build win-x86 Dec  6 2004
----- FS_Startup -----
Current language: english
Current search path:
Z:\usr\local\games\cod\uo\pakuo07.pk3 (157 files)
Z:\usr\local\games\cod\uo\pakuo06_lowres.pk3 (1918 files)
Z:\usr\local\games\cod\uo\pakuo06.pk3 (12 files)
Z:\usr\local\games\cod\uo\pakuo05.pk3 (3 files)
Z:\usr\local\games\cod\uo\pakuo04.pk3 (7646 files)
Z:\usr\local\games\cod\uo\pakuo03.pk3 (2275 files)
Z:\usr\local\games\cod\uo\pakuo02.pk3 (790 files)
Z:\usr\local\games\cod\uo\pakuo01.pk3 (1657 files)
Z:\usr\local\games\cod\uo\pakuo00.pk3 (6233 files)
Z:\usr\local\games\cod/uo
Z:\usr\local\games\cod\main\pakb.pk3 (60 files)
Z:\usr\local\games\cod\main\paka.pk3 (41 files)
Z:\usr\local\games\cod\main\pak9.pk3 (149 files)
Z:\usr\local\games\cod\main\pak8.pk3 (235 files)
Z:\usr\local\games\cod\main\pak6.pk3 (3 files)
Z:\usr\local\games\cod\main\pak5.pk3 (4858 files)
Z:\usr\local\games\cod\main\pak4.pk3 (1668 files)
Z:\usr\local\games\cod\main\pak3.pk3 (1992 files)
Z:\usr\local\games\cod\main\pak2.pk3 (694 files)
Z:\usr\local\games\cod\main\pak1.pk3 (2642 files)
Z:\usr\local\games\cod\main\pak0.pk3 (12816 files)
Z:\usr\local\games\cod/main
Z:\usr\local\games\cod\uo\localized_english_pakuo00.pk3 (2578 files)
    localized assets pak file for english
Z:\usr\local\games\cod\main\localized_english_pak5.pk3 (46 files)
    localized assets pak file for english
Z:\usr\local\games\cod\main\localized_english_pak3.pk3 (7 files)
    localized assets pak file for english
Z:\usr\local\games\cod\main\localized_english_pak2.pk3 (9 files)
    localized assets pak file for english
Z:\usr\local\games\cod\main\localized_english_pak1.pk3 (3736 files)
    localized assets pak file for english
Z:\usr\local\games\cod\main\localized_english_pak0.pk3 (1204 files)
    localized assets pak file for english

File Handles:
----------------------
53429 files in pk3 files
execing default_mp.cfg
couldn't exec language.cfg
couldn't exec uoconfig_mp.cfg
couldn't exec autoexec_mp.cfg
========= autoconfigure
configure_mp.csv: using configuration 2200 cpu MHz 512 sys MB 64 vid MB
execing configure_mp.cfg
fs_basegame is write protected.
fs_basepath is write protected.
fs_homepath is write protected.
Hunk_Clear: reset the hunk ok
...detecting CPU, found Intel Pentium III
Measured CPU speed is 2.52 GHz
System memory is 758 MB (capped at 1 GB)
Video card memory is 64 MB
Streaming SIMD Extensions (SSE) supported

Winsock Initialized
Opening IP socket: localhost:28960
Hostname: localhost.localdomain
Alias: localhost
Alias: ubuntu
IP: 127.0.0.1
WARNING: IPX_Socket: bind: WSAEINVAL
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
Initializing OpenGL subsystem
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Hunk_Clear: reset the hunk ok
Your version of Microsoft Windows(TM) does not support Call of Duty.

...................edit end.........................

I'm new to linux, so not entirely sure what i'm doing but i used the Loki installer to install my copies of COD and COD:UO (which i normally play using winXP) and that has installed all the files to 

/usr/local/games/cod

I've also followed the instructions to install WineCVS from here [http://winecvs.linux-gamers.net/index.php/Main_Page](http://winecvs.linux-gamers.net/index.php/Main_Page)

and that seems to have worked. 

home/george/.WineCVS/installs/cvscedega/bin/wine (etc,etc)

I'm now a bit stumped as to how i'm supposed to actually play COD, i've tried some commands in a terminal and keep getting command unknown (or something similar).

Could someone point me in the right direction?
..............edit ....................

sorted that out with $ sudo chmod 777 /usr/local/games/cod
then sudo -s  to link the exe files to the virtual C drive.
......................................................................................

Thank you

George

---

### Post by crane on 2005-03-27
The quickest fix I have found is to simply change the wine config file to run as win98.

---

### Post by rockstar2008 on 2008-02-29
i took my laptop to the person who works on it and i got it back and my screen has lines going through it and i tryed to play call of duty united offensive multiplayer and my other games and it said ...registered window class
...created window@0,0 (640x480)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 32, 24, 8 )
...35 PFDs found
...GLW_ChoosePFD failed
...GLW_ChoosePFD( 32, 24, 0 )
...35 PFDs found
...GLW_ChoosePFD failed
...failed to find an appropriate PIXELFORMAT
...restoring display settings
...WARNING: could not set the given mode (3)
...shutting down QGL
...unloading OpenGL DLL
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Hunk_Clear: reset the hunk ok
Could not load OpenGL.  Make sure that you have the latest drivers for your video card from the manufacturer's web site. 




HOW DO I FIX THIS :confused: you can email me at [email]reece_lambert@yahoo.com[/email]

---

