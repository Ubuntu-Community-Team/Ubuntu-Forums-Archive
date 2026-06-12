---
title: "ioquake3 based games not working"
date: 2014-08-17
forum: Gaming &amp; Leisure
---

### Post by 13l-jason on 2014-08-17
I play 2 games, both of which use the same game engine (ioquake3).  They are:
Open Arena & Urban Terror.

They both error out with the same message.  I was wondering if anyone could help with this.  

I have included the terminal output of each.  I'm running 64 bit Ubuntu 14.04 on a Dell GX620 with an Nvidia graphics card.  I don't think this is a graphics issue, but if you do, let me know, I'll provide additional information.


Open Arena
```
$ openarenaioq3 1.36+u20140116+gdde36d9-1/Ubuntu linux-x86_64 Jan 18 2014
Have SSE support
----- FS_Startup -----
Current search path:
/home/mythx/.openarena/baseoa
/usr/lib/openarena/baseoa
/usr/lib/openarena/baseoa/pak6-patch088.pk3 (711 files)
/usr/lib/openarena/baseoa/pak6-patch085.pk3 (559 files)
/usr/lib/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/lib/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/lib/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/lib/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/lib/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/lib/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/lib/openarena/baseoa/pak0.pk3 (1042 files)


----------------------
5433 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
OpenArena shaders not compatible with opengl2 renderer, going back to opengl1
Trying to load "renderer_opengl1_x86_64.so" from "/usr/lib/ioquake3"...
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
/usr/lib/ioquake3: symbol lookup error: /usr/local/lib/libSDL-1.2.so.0: undefined symbol: _XGetRequest
```

Urban Terror
```
$ urbanterror ioQ3 1.35 urt 4.2.018 linux-x86_64 Jan 16 2014
----- FS_Startup -----
Current search path:
/home/mythx/.q3a/q3ut4
/usr/share/games/urbanterror/q3ut4/zUrT42_qvm.pk3 (3 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0026.pk3 (16 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0025.pk3 (132 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0024.pk3 (253 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0023.pk3 (21 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0022.pk3 (88 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0021.pk3 (12 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0020.pk3 (348 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0019.pk3 (472 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0018.pk3 (144 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0017.pk3 (109 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0016.pk3 (12 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0015.pk3 (34 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0014.pk3 (25 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0013.pk3 (7 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0012.pk3 (173 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0011.pk3 (48 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0010.pk3 (26 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0009.pk3 (147 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0008.pk3 (377 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0007.pk3 (2097 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0006.pk3 (1136 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0005.pk3 (557 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0004.pk3 (1707 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0003.pk3 (1168 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0002.pk3 (1547 files)
/usr/share/games/urbanterror/q3ut4/zUrT42_0001.pk3 (2122 files)
/usr/share/games/urbanterror/q3ut4/ut4_jumpents.pk3 (8 files)
/usr/share/games/urbanterror/q3ut4/ut4_commune.pk3 (150 files)
/usr/share/games/urbanterror/q3ut4


----------------------
12939 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
/usr/lib/games/urbanterror/Quake3-UrT: symbol lookup error: /usr/local/lib/libSDL-1.2.so.0: undefined symbol: _XGetRequest
```

Thanks in advance

---

### Post by oldrocker99 on 2014-08-17
Please post the output of:
```
lspci | grep VGA
```

Your problem is related to OpenGL. To help, we need to find out what your graphics circuitry is, and which driver you're using.

---

### Post by 13l-jason on 2014-08-17
```

$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 430] (rev a1)

```

---

### Post by oldrocker99 on 2014-08-18
OK, the 430 is a pretty low-end graphics card. The latest nVidia drivers are 343.13, which are available from the xorg-edgers PPA:
```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

If the nvidia driver doesn't upgrade:
```
sudo apt-get install nvidia-graphics-drivers-343
```

The 500, 600 and 700 series nVidia cards are much faster than the 400 series, for what it's worth. This will insure that at least you have the latest drivers.

Good luck.

---

### Post by 13l-jason on 2014-08-18
Thanks for the info.  I added the repository and did the update/upgrade.  It upgraded a bunch of Nvidia stuff, but I still have the same problem.  There still is no package called nvidia-graphics-drivers-343, in fact there are no nvidia-graphics* packages available.  Is there another step I still need to do?

I know it's a poor video card, but it was free :)

Thanks again for the help

---

### Post by oldrocker99 on 2014-08-19
Oops, my bad. It's called **nvidia-343**. You can search the packages available with```
apt-cache search nvidia
``` Also, you can run the **NVIDIA X Server Settings** program to easily see which driver you're using.

Also, which desktop environment are you using? The Unity desktop is pretty resource-intensive, like KDE or GNOME. If you install a lighter-weight desktop like lubuntu-desktop or xubuntu-desktop, you **may** get better results

---

### Post by 13l-jason on 2014-08-19
Thanks for the help.  I thought that might be the case and already installed it.  Still having the same problem though.

Any other thoughts?  I usually do end up with the more difficult problems.

---

### Post by 13l-jason on 2014-08-19
BTW, in the meantime, I'm able to play it using Wine, but there's something wrong about emulating a windows env to run a program on Linux when there's a native Linux version available.

---

