---
title: "Can't get games to work"
date: 2010-12-29
forum: Gaming &amp; Leisure
---

### Post by savaan on 2010-12-29
I'm on 10.04 and trying to install games from the package manager such as Openarena. It installs and puts an icon in my menu, but does nothing when I click it. This also happens when I install other Linux native games from package manager. 
<snip>

---

### Post by rizzeh on 2010-12-30
you'll need to provide more info. What is the computer spec, what are error messages if any.
open the terminal and type in: openarena

Post the output here

---

### Post by VonSpyder on 2010-12-30
Ill bet its a permissions issue. it would be interesting to know where it installed.

---

### Post by savaan on 2010-12-31
I'm on a Dell, 3ghz Intel, 2gigs of RAM, using the onboard video which is Intel Graphics Media 950. I typed in openarena and got this:


```
ioq3+oa 1.35 linux-i386 Dec 18 2009
----- FS_Startup -----
Current search path:
/home/danyaeldemonic/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (1042 files)
/usr/share/games/openarena/baseoa

----------------------
4163 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
Your network rate is too slow for VoIP.
Set 'Data Rate' to 'LAN/Cable/xDSL' in 'Setup/System/Network' and restart.
Until then, VoIP is disabled.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "x11"
Initializing OpenGL display
Estimated display aspect: 1.600
...setting mode 3: 640 480
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  13
  Current serial number in output stream:  14
```

---

### Post by rizzeh on 2010-12-31
Intel Graphics Media 950 will be the problem here. You'd want nvidia or ati video with drivers installed to play 3D games.

---

### Post by disturbedite on 2010-12-31
> **rizzeh said:**
> Intel Graphics Media 950 will be the problem here. 

that is not necessarily true. onboard chips are capable of playing "3D games". i've been doing it for many years. although, results will vary in each specific situation for various reasons, such as how old the chip/mobo are.

---

### Post by tommcd on 2010-12-31
> **savaan said:**
> I'm on a Dell, 3ghz Intel, 2gigs of RAM, using the onboard video which is Intel Graphics Media 950. 
```
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)

```

Check and see if you have direct rendering enabled. Open a terminal and post the output of: 
```
glxinfo | grep -i render
```
It should report something like this for reference:
```

bash-4.1$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: GeForce 8400 GS/PCI/SSE2/3DNOW!
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 

```
The key info there is: "*direct rendering: Yes*". Also, your video card should be listed on the 
"*OpenGL renderer string:*" line.

---

