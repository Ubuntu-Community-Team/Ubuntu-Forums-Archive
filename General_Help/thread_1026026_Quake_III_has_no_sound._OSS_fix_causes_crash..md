---
title: "Quake III has no sound. OSS fix causes crash."
date: 2008-12-30
forum: General Help
---

### Post by sekander94 on 2008-12-30
When I try to run quake3 I get no sound with it. I tried typing

```

echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

```

to force quake to use oss sound. This makes sound work in the menus, but when I try to join a server (or play locally), the game hangs, and I am forced to hard reboot my computer.

The difference in Quake's output:

Without sound:
```

------- sound initialization -------
Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm.
VM file ui compiled to 594408 bytes of code
Can't find vm/ui.map
Couldn't load symbol file: vm/ui.map
ui loaded in 1963008 bytes on the hunk
78 arenas parsed
32 bots parsed
Can't find textures/sfx/logo512.tga
Can't find gfx/colors/black.tga
Cvar_Set2: ui_singlePlayerActive 0

```

With sound:
```

------- sound initialization -------
------------------------------------
Channel memory manager started
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
48000 speed
0xa9e0e000 dma buffer
No background file.
----------------------
Sound memory manager started
^3WARNING: sound/feedback/hit.wav is a 8 bit wav file
Loading vm file vm/ui.qvm.
VM file ui compiled to 594408 bytes of code
Can't find vm/ui.map
Couldn't load symbol file: vm/ui.map
ui loaded in 1963008 bytes on the hunk
78 arenas parsed
32 bots parsed
Can't find textures/sfx/logo512.tga
Can't find gfx/colors/black.tga
Cvar_Set2: ui_singlePlayerActive 0

```


My sound hardware (according to lshw):
```

  *-multimedia            
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

```

I am using Ubuntu 8.04.1 hardy (2.6.24-22-generic). 

Is there another fix to get the sound to work without crashing? Or a way to keep this method but stop the crashing?

---

