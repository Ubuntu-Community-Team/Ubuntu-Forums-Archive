---
title: "Who is running Quake Wars succesfully?"
date: 2008-01-13
forum: Gaming &amp; Leisure
---

### Post by phxtravis on 2008-01-13
I am looking for someone who has similar specs to me and has ran ETQW successfully. Since I can't get the thing to start and I can't find a very good ATI Driver.

Ubuntu 7.10
ATI 2600HD mobility
AMD TurionX2

After doing a fresh install of ubuntu I tried to start ETQW before installing any graphics drivers to see if it'd work. Well it didn't and I got this:
[HTML]This system qualifies for Low quality.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1152x864
execing 'specs/minspec.dat'
execing 'specs/minspec_cpu.dat'
execing 'specs/minspec_gamedetail.dat'
execing 'specs/minspec_gpu.dat'
execing 'specs/minspec_gpudetail.dat'
execing 'specs/minspec_lighting.dat'
execing 'specs/minspec_foliage.dat'
Vendor: Device:
execing 'specs/minspec_foliage.dat'
Opening IP socket: localhost:-1
Failed to open server license code file for reading.
SDL_ListModes:
1152x864 1024x768 800x600 720x400 640x480 640x400 640x350 512x384 320x240 320x200 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual
------- Initializing renderSystem --------
----- R_InitOpenGL -----
signal caught: 'Segmentation fault', si_code 1
thread priority set to 1
callstack:
0x0
[0x082d1151]
[0x082ce638]
[0xffffe600]
Trying to exit gracefully..
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()
travis@travis-laptop:~$ 
[/HTML]

Previous to the fresh 7.10 install I tried ATI's 7.11 and 7.12(2 different 7.12's), none of them worked. Also after I installed each of those I couldn't open the Catalyst via "Applications". And of coarse none of them helped with ETQW. I am also unable to change my resolution past 1152*864. I have tried to select "restricted drivers manager" but when i do I get:
"Your hardware does not need any restricted drivers"

Anyone have any Ideas?

---

### Post by almostlinux on 2008-01-14
Please post the output of:

glxinfo | grep direct

If that says 'No', it means the OS is not using your graphic card properly.

See: [http://community.enemyterritory.com/forums/showthread.php?p=269527](http://community.enemyterritory.com/forums/showthread.php?p=269527)

---

### Post by mikedep333 on 2008-01-14
> **phxtravis said:**
> 

Ubuntu 7.10
ATI 2600HD mobility
AMD TurionX2

...

I have tried to select "restricted drivers manager" but when i do I get:
"Your hardware does not need any restricted drivers"

Your graphics card is too new for the restricted drivers manager's ati/amd driver to work. You need to install the latest driver manually/using its installer/using DKMS. Sell the link below.

> **phxtravis said:**
> After doing a fresh install of ubuntu I tried to start ETQW before installing any graphics drivers to see if it'd work. Well it didn't ...

That's right. You need to have ATI/AMD's driver installed to run quake wars.

> **phxtravis said:**
> 

Previous to the fresh 7.10 install I tried ATI's 7.11 and 7.12(2 different 7.12's), none of them worked.

Anyone have any Ideas?

Install the latest ati drivers according to this guide.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0)

Fedback here:
[http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)

---

### Post by Sockerdrickan on 2008-01-14
You should have gotten a nVidia card. I run it very nice.

---

### Post by KhaaL on 2008-01-14
I think it's possible for phxtravis to just download envy and let it do all the hassle of installing the latest driver for him, no?

---

### Post by SidewinderPro2 on 2008-01-15
I'm running it successfully on the 8800GTS. I'm going to say go with Khaal with this one. Get Envy from Synaptic and install the right drivers. Its the easiest way to get the right drivers going. The default drivers that are installed by Ubuntu aren't going to carry you far. 

The game runs just as well on Linux as it does in Vista for me. Still don't know how to get my 360 controller working...

---

### Post by ragexiii on 2008-03-04
I'm also experiencing the same problem. I'm on Ubuntu 7.10 and It seems like OpenGL is not installed or my drivers aren't installed properly although I've tried using Envy to install my drivers. 

I tried typing glxinfo | grep direct
and it  says that it couldn't find RGB GLX visual.

Anyone has any other suggestions?

Here are my pc specs:
Mobo: Asus Striker Extreme
Processor: Intel QX6800 Quad Core Extreme
RAM: Gskill DDR-2 2GB x 2
GPU: Asus 8800GTX 768MB DDR3 PCIex x 2
Sound Card: Auzentech Meridian X
DVD Drive: Pioneer SATA DVD-RW
Storage:
Western Digital Raptor 150GB 16MB 10000rpm SATA x2 Raid 0
Western Digital 500GB SATA
External WD 500GB SATA (via eSATA cable)
Display: Dell 2407WFP
Input Devices:
Razer Tarantula
Razer Deathadder
Razer Lachesis

---

### Post by eragon100 on 2008-03-04
Get a nvidia card. I dindd't have to do ANYRTHING else than double-clicking the install to get it to run perfectly. Nvidia works a lot better than ATI on linux anyway :popcorn:

---

