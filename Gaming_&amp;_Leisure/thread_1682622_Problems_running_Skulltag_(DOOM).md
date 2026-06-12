---
title: "Problems running Skulltag (DOOM)"
date: 2011-02-06
forum: Gaming &amp; Leisure
---

### Post by ubey on 2011-02-06
Hi

English is not my first language so I am sorry for the mistakes I might make.

I am playing FreeDoom on my netbook (Maverick Meerkat Desktop) and I find it very amusing.
Now I am a little desperate to try playing DOOM with other players using Skulltag. 

When i go to **Applications--> Games--> Skulltag **it asks me what WAD I want to use. No matter which one I choose Skulltag doesn't run. Then I ran it in Terminal and got the following output:

```
nicholas@nicholas-AOA110:~$ skulltag
Skulltag v0.98b - SVN revision 2692 - SDL version
Compiled on Mar  7 2010

M_LoadDefaults: Load system defaults.
W_Init: Init WADfiles.
 adding /usr/games/skulltag/skulltag.pk3 (453 files)
 adding /usr/games/skulltag/skulltag_data.pk3 (2540 files)
 adding /home/nicholas/.skulltag/DOOM2.WAD (2956 lumps)
I_Init: Setting up machine state.
CPU Vendor ID: GenuineIntel
  Name: Intel(R) Atom(TM) CPU N270 @ 1.60GHz
  Family 6, Model 28, Stepping 2
  Features: MMX SSE SSE2 SSE3 SSSE3
I_InitSound: Initializing FMOD
FMOD Sound System, copyright &#65533; Firelight Technologies Pty, Ltd., 1994-2009.
HOSS could not be initialized. Trying ALSA.
V_Init: allocate screen.
S_Init: Setting up sound.
ST_Init: Init startup screen.
P_Init: Checking cmd-line parameters...
G_ParseMapInfo: Load map definitions.
SC_GetFloat: Bad numeric constant "0.5".
Perhaps a problem with your LANG enviroment variable, try "export LANG=C".
Script skulltag.pk3:mapinfo/doomcommon.txt, Line 41

```What exactly is my computer trying to tell me? :neutral:

---

### Post by JLangford on 2011-02-06
I am still very new to ubuntu but from what I can see, the error is right at the end

> Perhaps a problem with your LANG enviroment variable, try "export LANG=C".
Script skulltag.pk3:mapinfo/doomcommon.txt, Line 41

Perhaps you know what to do with this?

Again, I am new to ubuntu so that could be nothing to do with it. :P

---

### Post by DoktorSeven on 2011-02-06
Try what it says, run from commandline:
```

export LANG=C
skulltag

```

---

### Post by JFekete9076 on 2011-08-04
Hello.

I has also tried Skulltag on Ubuntu Natty, but there is a problem using OpenGL rendering.
Check out this video: [http://www.mediafire.com/?xighe2oz5mm6kgj](http://www.mediafire.com/?xighe2oz5mm6kgj)

Update: I've also noticed that MIDI lags.

Another update: I'm using nVidia drivers 280.13 for Linux 64-bit.

Update on Aug 22nd, 2011: Although the link is broken, I have recently noticed that problem is gone.

---

