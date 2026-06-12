---
title: "Quake 4 sound problem"
date: 2005-10-27
forum: Gaming &amp; Leisure
---

### Post by Kirzzy_Boy on 2005-10-27
I'm getting some serious sound problems when trying to run the game...

I tried:  ```
quake4 +set s_device oss
``` and got some nasty stuff screaming through my headset

I then got this: ```
found DLL in pak file: /usr/local/games/quake4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/kirzzy/.quake4/q4base/gamex86.so
enabled Flush-To-Zero mode
------------- Initializing Game -------------
gamename: baseQUAKE4-1
gamedate: Oct 19 2005
451ms to load 634k of entityDef
105ms to load 177k of articulatedFigure
Initializing event system
...527 event definitions
Initializing class hierarchy
...242 classes, 586024 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 2166.53 MHz
Compiled '/home/kirzzy/.quake4/q4base/scripts/main.script': 3830.3 ms
-------------- Compile stats ----------------

Memory usage:
     Strings: 54, 8464 bytes
  Statements: 84406, 1688120 bytes
   Functions: 3361, 380380 bytes
   Variables: 324172 bytes
    Mem used: 3531952 bytes
 Static data: 4948144 bytes
   Allocated: 6313652 bytes
 Thread size: 7072 bytes

...5 aas types
game initialized.
---------------------------------------------
Loading viseme file: annosoft
----------- Initializing Session ------------
----------------- BSE Init ------------------
--------- BSE Created Successfully ----------
WARNING: idChoiceWindow::InitVars: gui 'guis/mainmenu.gui' window 'pop_set_sndAdv_system_val' references undefined cvar 's_useOpenAL'
WARNING: idChoiceWindow::InitVars: gui 'guis/mainmenu.gui' window 'pop_set_sndAdv_device_val' references undefined cvar 's_deviceName'
WARNING: idChoiceWindow::InitVars: gui 'guis/mainmenu.gui' window 'pop_set_sndAdv_eax_val' references undefined cvar 's_useEAXReverb'
session initialized
---------------------------------------------
------ Common Initialization Complete -------
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 12235
detecting video ram ( set sys_videoRam to force ) ..
found XNVCtrl extension 1.6
2167 MHz CPU
1008 MB System Memory
128 MB Video Memory
Async thread started
snd_pcm_writei short write: 3760 out of 4096
snd_pcm_writei short write: 3760 out of 4096
snd_pcm_writei short write: 3760 out of 4096
snd_pcm_writei short write: 3760 out of 4096
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1880 out of 4096
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 1880 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 1880 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 1880 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 1880 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 1880 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 1880 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 1880 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
------------ Game Map Shutdown --------------
---------------------------------------------
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
Shutting down SDL subsystem
--------------- Game Shutdown ---------------
rvStatAllocator:  dump of usage stats
        0 total bytes handed out in 0 requests
        begin game:      0;  end game:        0
        player hit:      0;  player kill:     0
        player death:    0;
        damage dealt:    0;  damage taken:    0
        stat team:       0
        flag capture:    0;
        flag drop:       0;  flag return:     0
------------ Game Map Shutdown --------------
---------------------------------------------
Shutdown event system
---------------------------------------------
shutdown terminal support
```


Any ideas??

---

### Post by seethru on 2005-10-27
I was experiencing the same, my fix ended up being a simple restart. Also looks like it's still using ALSA and not OSS, despite that line.
There was another thread with this exact issue that had a few fixes posted.

---

### Post by DarkManX4lf on 2005-10-27
what kind of sound card do you have? brand/model ?

---

### Post by Kirzzy_Boy on 2005-10-28
Ok, my bad.....
Was tired and didn't do a proper search...

I found the sollution here if anyone read this: [http://ubuntuforums.org/showthread.php?t=80177&highlight=quake4+sound](http://ubuntuforums.org/showthread.php?t=80177&highlight=quake4+sound)

---

