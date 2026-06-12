---
title: "PCSX2 Plugins Failing"
date: 2017-01-18
forum: Emulators
---

### Post by muddpup64 on 2017-01-18
Hi guys!

I'm working on trying to play Katamari Damacy on my linux machine but PCSX2 can not seem to be able to use openGL. Perhaps some one could help me.

Here's the console print:
```
PCSX2 1.4.0-0- compiled on Jan  6 2016
Savestate version: 0x9a0b0000

Host Machine Init:
    Operating System =  Linux 4.4.0-59-lowlatency x86_64
    Physical RAM     =  7779 MB
    CPU name         =  Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
    Vendor/Model     =  GenuineIntel (stepping 02)
    CPU speed        =  2.125 ghz (4 logical threads)
    x86PType         =  Standard OEM
    x86Flags         =  bfebfbff 0098e3bd
    x86EFlags        =  28100000

x86 Features Detected:
    SSE2.. SSE3.. SSSE3.. SSE4.1.. SSE4.2

Installing POSIX SIGSEGV handler...
Reserving memory for recompilers...

Loading plugins...
    Binding   GS: /usr/lib/i386-linux-gnu/pcsx2/libGSdx-1.0.0.so 
(p) (L) The configured GS plugin file was not found(LoadCorePlugins) 

/usr/lib/i386-linux-gnu/pcsx2/libGSdx-1.0.0.so
(GameDB) 9693 games on record (loaded in 324ms)

Loading plugins...
    Binding   GS: /usr/lib/games/PCSX2/libGSdx-1.0.0.so 
    Binding  PAD: /usr/lib/games/PCSX2/libonepad-1.1.0.so 
    Binding SPU2: /usr/lib/games/PCSX2/libspu2x-2.0.0.so 
    Binding CDVD: /usr/lib/games/PCSX2/libCDVDnull.so 
    Binding  USB: /usr/lib/games/PCSX2/libUSBnull-0.7.0.so 
    Binding   FW: /usr/lib/games/PCSX2/libFWnull-0.7.0.so 
    Binding DEV9: /usr/lib/games/PCSX2/libdev9null-0.5.0.so 
Plugins loaded successfully.


Initializing plugins...
    Init GS
    Init PAD
    Init SPU2
    Init CDVD
    Init USB
    Init FW
    Init DEV9
Plugins initialized successfully.

Bios Found: Japan   v01.00(17/01/2000)  Console
Bios Found: Europe  v02.00(14/06/2004)  Console
Bios Found: USA     v01.60(07/02/2002)  Console
Bios Found: Europe  v01.60(04/10/2001)  Console
HLE Notice: ELF does not have a path.

Opening plugins...
    Opening GS
Current Renderer: OpenGL (Hardware mode)
Failed to create the opengl context. Check your drivers support openGL 3.3. Hint: opensource drivers don't
Closing plugins...
    Closing GS
Plugins closed successfully.
Shutting down plugins...
Plugins shutdown successfully.
(p) GS plugin failed to open!(thread:MTGS)(thread:EE Core)
HLE Notice: ELF does not have a path.


Initializing plugins...
    Init GS
    Init PAD
    Init SPU2
    Init CDVD
    Init USB
    Init FW
    Init DEV9
Plugins initialized successfully.

Opening plugins...
    Opening GS
Current Renderer: OpenGL (Software mode)
Failed to create the opengl context. Check your drivers support openGL 3.3. Hint: opensource drivers don't
Closing plugins...
    Closing GS
Plugins closed successfully.
Shutting down plugins...
Plugins shutdown successfully.
(p) GS plugin failed to open!(thread:MTGS)(thread:EE Core)
```


Thanks guys!

---

### Post by deadflowr on 2017-01-18
*Thread moved to **Emulators**.* 

What's your GPU and does it support (or have support) for OpenGL 3.3
You can find out which by installing the package mesa-utils
```
sudo apt-get install mesa-utils
```
and then running
```
glxinfo | grep OpenGL
```

Also, it's less likely with intel gpus that you will be able to run OpenGL 3.3, but maybe more possible with either an AMD or Nvidia card.
(And more so with an Nvidia card. In my opinion)

---

### Post by muddpup64 on 2017-01-19
Print of glxinfo | grep OpenGL:
```
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 2.1 Mesa 11.2.0
OpenGL shading language version string: 1.20
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 2.0 Mesa 11.2.0
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extensions:

```

---

### Post by muddpup64 on 2017-01-19
From the research I've done, I am not running the most up to date version of OpenGL and my processor prevents me from getting an upgrade. Would upgrading my processor from an i3 to an i7 fix this?

---

### Post by deadflowr on 2017-01-20
Ironlake gpus tap out at OpenGL 2.1, so that's at its limit.

Two choices:

1) Try software mode (Not recommended since this will overly tax the cpu)
You can set it to software mode in the Config >> GS settings configure button >> Renderer.
You should have 3 option there, hardware, software and none.

2)Get a mid-range to high-quality dedicated graphics card. Preferably Nvidia.
(I would recommend this second option)

---

### Post by muddpup64 on 2017-01-20
The first option sounds deadly. And the second, impossible.... maybe.

On the T410 laptop models (which is the computer in question) there is no room for a dedicated graphics card. Intel gets around this by building the cpu to also handle the graphics. Which brings me to this question: would upgrading from the i3 to an i7 give me some more room? I know nothing about cpu's, so can you please explain this as though I am a toddler.

P.S. An external GPU is out of the question.

Thanks

---

### Post by deadflowr on 2017-01-21
> I know nothing about cpu's, so can you please explain this as though I am a toddler.
Basically, me neither.
But what I do know is that the cpu can only run within the specified framework of the motherboards chipset.
So there are a limited number of processors that can run on the motherboard you have.
I am not sure whether or not any that can will be able to increase the gpu-side capabilities.

However, you might be able to do some digging to find out the chipset and it's range of cpus
I'd run
```
sudo lshw
```
look for the motherboard name (probably marked as product), then run a web search for that board.
Intel has documentation on all it's hardware, so best bet is to look there (intel's website)
Their specs manuals they have usually contain information on which cpu's (and gpus) a particular board will support.

not helpful, but hopefully it points you in some direction.

---

