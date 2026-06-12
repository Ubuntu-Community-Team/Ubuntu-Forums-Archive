---
title: "Doom 3 opengl"
date: 2012-10-19
forum: Gaming &amp; Leisure
---

### Post by Papas228 on 2012-10-19
ok so i'm having trouble launching doom 3 and quake 4. I'm using 12.10 x64 and i know i have my drivers setup up properly since i've played bastiona and amnesia. so not sure why it won't launch with the opengl issue. i've tried changing to 24bit display and nada. So just stumped as to why it won't start. by the way i'm running nvidia 304.60 drivers not sure if that's an issue with those drivers. also my ia32-libs are installed. any help would be helpful thanks in advance ^^.

---

### Post by Perfect Storm on 2012-10-19
Try launch the game via the terminal and post the output, it would be a great help for those who can help.

---

### Post by Papas228 on 2012-10-19
sorry lol

------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /usr/local/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/papo/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak008.pk4 (3 files)
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
dlopen(libGL.so.1)
idRenderSystem::Shutdown()
signal caught: Segmentation fault
si_code 1
Was in fatal error shutdown: Unable to initialize OpenGL
Trying to exit gracefully..

---

### Post by Papas228 on 2012-10-20
bump

---

### Post by Papas228 on 2012-10-20
well i switched from x64 to x86 and reinstalled everything and it works now.

---

### Post by raja.genupula on 2012-10-21
thats glad news , now please mark your thread as solved from thread tools .

---

### Post by maciimacii on 2013-08-01
> **Papas228 said:**
> sorry lol

------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /usr/local/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/papo/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak008.pk4 (3 files)
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
dlopen(libGL.so.1)
idRenderSystem::Shutdown()
signal caught: Segmentation fault
si_code 1
Was in fatal error shutdown: Unable to initialize OpenGL
Trying to exit gracefully..


That error might be because doom3 can't find the opengl driver in the ia32 /usr/lib32 directory.

Just set the library path to include /usr/lib32

export LD_LIBRARY_PATH="/usr/lib32:$LD_LIBRARY_PATH"


Here are some things I ran into trying to get doom3 running on 64 bits.

--------------------------------------------------------------------------------

Running 32bit Doom3 on 64bits with sound working (also for Quake4 sound) using the ia32 libraries.


Doom3/Quake4 have a alsa sound conflict with pulseaudio and the 32bit alsa-oss wrapper gets around it.


Download and install the 32bit ia32-libs and ia32-alsa-oss libraries.


[http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu26.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu26.1_amd64.deb)


[http://home.comcast.net/%7Edeletebox/ia32-alsa-oss_1.0.10-1_amd64.deb](http://home.comcast.net/%7Edeletebox/ia32-alsa-oss_1.0.10-1_amd64.deb)


Install the 64bit alsa-oss package as well and copy the 64bit aoss to aoss32 and edit aoss32 to point to the 32bit libraries.


sudo apt-get install alsa-oss


copy /usr/bin/aoss to /usr/bin/aoss32


sudo cp /usr/bin/aoss /usr/bin/aoss32


Edit aoss32 and replace the libdir= line with libdir=${prefix}/lib32


sudo gedit /usr/bin/aoss32


then make aoss32 executable


sudo chmod +x /usr/bin/aoss32


then set the library load path


export LD_LIBRARY_PATH="/usr/lib32:$LD_LIBRARY_PATH"


then start Doom3 and choose oss and stereo speakers in the Doom3 system settings.


then restart Doom3 using


aoss32 doom3


and sound should work with no problems.


No need to stop pulseaudio or to uninstall it.


A Doom3 startup script would be


export LD_LIBRARY_PATH="/usr/lib32:$LD_LIBRARY_PATH"
aoss32 doom3


The 64 bit Nvidia driver has an option to install Nvidia's 32bit opengl driver which is needed for Doom3.


I don't know about ATI.


If a 32bit system is being used then just installing alsa-oss and starting Doom3 with aoss doom3 is all that is needed.


------------------------------------------------------------


Another thing is the libstdc++.so.6 and libgcc_s.so.1 files in the doom3 directory.


These files are old versions and result in a segmentation fault when doom3 is quit and sometimes these files interfere with the opengl driver and can prevent doom3 from starting up.


If doom3 is running in fullscreen, then after doom3 exits, the Desktop might not return to it's original video mode from the doom3 video mode and the Desktop might get stuck in the doom3 video mode because of the old libstdc++.so.6 and libgcc_s.so files in the doom3 directory causing a segmentation fault when doom3 exits.


So, rename /usr/local/games/doom3/libstdc++.so.6 and /usr/local/games/doom3/libgcc_s.so.1 so that doom3 loads the newer versions of these files that are already on the system.


----------------------------------------------------------


I've been trying to work out a method of getting doom3 running on a multiarch system with working sound, without using the older ia32 libraries.


[https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch)


From what I understand (which might not be totally right), the ia32 32 bit libraries that used to be in /usr/lib32 have basically been moved to /usr/lib/i386-linux-gnu in the ia32-libs-multiarch package and the 64 bit libraries are in /usr/lib/x86_64-linux-gnu (There are also other libraries in /lib/i386-linux-gnu and /lib/x86_64-linux-gnu)


So, the Doom3 alsa/pulseaudio audio delay problems can be solved by using aoss and setting the doom3 driver to oss.


So,
Install the 64bit alsa-oss package and copy the 64bit aoss to aoss32 and edit aoss32 to point to the 32bit multiarch libraries.


sudo apt-get install alsa-oss


copy /usr/bin/aoss to /usr/bin/aoss32


sudo cp /usr/bin/aoss /usr/bin/aoss32


Edit aoss32 and replace the libdir= line with libdir=${prefix}/lib/i386-linux-gnu


sudo gedit /usr/bin/aoss32


then make aoss32 executable


sudo chmod +x /usr/bin/aoss32


then doom3 can be started by using aoss32 doom3.


Then there are the opengl 32 bit libraries ie Nvidia and ATI.


On my Ubuntu 12.04 system, the Nvidia 32 bit opengl libraries got installed into /usr/lib32, the same directory as the ia32 libraries.


If the Nvidia (or ATI) 32 bit libraries are getting installed into /usr/lib32, then the system doesn't really know where they are because they are not in the multiarch /usr/lib/i386-linux-gnu directory.


So, I think that the /usr/lib32 path would need to be added to the library loader path so that the system can find the opengl Nvidia (or ATI) opengl 32 bit libraries.


So, doom3 would need to be started with


export LD_LIBRARY_PATH="/usr/lib32:$LD_LIBRARY_PATH"
aoss32 doom3


I havn't tried this multiarch method, but it should work (maybe with a few tweaks).


I have tested the ia32 libraries doom3 method outlined in the first post and it works.


The issues with doom3, are that doom3 needs 32 bit libraries and doom3 has a alsa/pulseaudio sound delay problem.


There are some posts around the net suggesting how to get around the doom3 alsa/pulseaudio problem, but the only ones that seems to work consistently is to either suspend pulseaudio or use aoss and set the doom3 driver to oss.


The aoss method is more convenient than suspending pulseaudio.

---

