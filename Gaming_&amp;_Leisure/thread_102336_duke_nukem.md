---
title: "duke nukem"
date: 2005-12-11
forum: Gaming &amp; Leisure
---

### Post by Akya on 2005-12-11
i just found my old duke nukem cd and i wanted to install it but i cant install it i start it and it goes blank and says this in terminal

~/Desktop/Duke nukem$ wine inst.exe
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.
fixme:int: DOSVM_Int10Handler Get Font Information - Not Supported
fixme:int: DOSVM_Int10Handler Get Font Information - Not Supported
fixme:int: DOSVM_Int10Handler Select Active Display Page (0) - Not Supported
fixme:int: DOSVM_Int10Handler Toggle Intensity/Blinking Bit - Not Supported
fixme:int: DOSVM_Int10Handler Get Font Information - Not Supported
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe37b08 )-> (0x60024,00000011)fixme: xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme: xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme: x11drv:X11DRV_DDHAL_CreatePalette stub
fixme:int: DOSVM_Int10Handler Set ROM 8x8 Dbl Dot Chars (Graphics) - Not Supported
fixme:int: DOSVM_Int10Handler Get Font Information - Not Supported
fixme:int: DOSVM_Int10Handler Select vertical resolution - not supported
fixme:int: DOSVM_Int10Handler Get Font Information - Not Supported
fixme:int: DOSVM_Int10Handler Select Active Display Page (0) - Not Supported
fixme:int: DOSVM_Int10Handler Toggle Intensity/Blinking Bit - Not Supported

---

### Post by Dogmeat on 2005-12-11
You might want to check this out: [http://jonof.edgenetwork.org/index.php?p=jfduke3d](http://jonof.edgenetwork.org/index.php?p=jfduke3d)

It's a Duke Nukem 3D remake in OpenGL !! The good part is.. it runs natively on Linux! The bad part is.. you have to compile it from source (if you're not patient or determined to make it work)

I installed it myself it on hoary a while ago and it worked perfectly. Well, almost. I just had some major issues with music, as the game wouldn't play midi files for some odd reason. I missed the songs, (hey duke isnt the same without that kickass intro song) so i converted the midis to ogg vorbis and changed the code to play them instead and it worked.

---

### Post by wcoenen on 2008-11-12
Use dosbox instead of wine. Duke Nukem 3D and other DOS games will run fine in dosbox.

---

### Post by mister_k81 on 2008-11-15
> **Dogmeat said:**
> You might want to check this out: [http://jonof.edgenetwork.org/index.php?p=jfduke3d](http://jonof.edgenetwork.org/index.php?p=jfduke3d)

I installed it myself it on hoary a while ago and it worked perfectly. Well, almost. I just had some major issues with music, as the game wouldn't play midi files for some odd reason. I missed the songs, (hey duke isnt the same without that kickass intro song) so i converted the midis to ogg vorbis and changed the code to play them instead and it worked.

You need to download the timidity midi sequencer from the repositories to get sound to work. That also goes for playing it on DOSBox, I think? 

Also another OpenGL port you might want to try is EDuke32, which can be found here: 

[http://ny00123.sitesled.com/files_linpak_notes.html](http://ny00123.sitesled.com/files_linpak_notes.html)

---

### Post by wcoenen on 2008-11-17
In dosbox you don't need to install anything else to get sound and music working. Run the setup.exe that comes with duke3d and select soundblaster for both sound and music + default settings.

I'm sure the midi quality could be better, but that's part of the experience when playing old games for nostalgia's sake :)

BTW, kudos to whoever was involved in getting the duke3d source code released under the GPL =D>

---

### Post by danny_galaga on 2008-11-21
i have duke nukem 3d on my gp2x, which is linux based. i didnt have to compile anything (that i remember).

this the gp2x version

[http://archive.gp2x.de/cgi-bin/cfiles.cgi?0,0,0,0,20,956](http://archive.gp2x.de/cgi-bin/cfiles.cgi?0,0,0,0,20,956)

many links to duke nukem ports:

[http://en.wikipedia.org/wiki/Duke_Nukem_3D](http://en.wikipedia.org/wiki/Duke_Nukem_3D)

ive got to go to sleep so i dont which, if any are 'ready to go'...

edit: it does look eduke32 is the way to go...

---

