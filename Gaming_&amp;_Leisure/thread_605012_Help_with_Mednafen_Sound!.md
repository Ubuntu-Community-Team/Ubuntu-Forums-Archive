---
title: "Help with Mednafen Sound!"
date: 2007-11-06
forum: Gaming &amp; Leisure
---

### Post by jondecker76 on 2007-11-06
I got Mednafen working pretty well except for sound....

I have an onboard sound card, and an MAudio Delta 1010. My speakers are hooked to the MAudio Delta 1010.

Looking through the documentation at [http://mednafen.sourceforge.net/documentation/#using-cli]("http://http://mednafen.sourceforge.net/documentation/#using-cli")
I can see that there is a -sounddevice option, but I have absolutely no clue how to use the option.. is it looking for "hw:1", "M Audio Delta 1010", etc etc.

Here are some things I have tried:

```

jondecker76@studio-desktop:~$ mednafen -sound 1 -sounddriver alsa -sounddevice "hw:0" -fs 1 -nes.xres 1400 -nes.yres 1050 -nes.stretch 1 "/home/jondecker76/ROMS/Nintendo/contra.nes"
Starting Mednafen 0.8.1
 Loading settings from "/home/jondecker76/.mednafen/mednafen.cfg"...
 Initializing joysticks...
  Joystick 0 - Jess Tech GGE909 PC Recoil Pad - Unique ID: ce96ea6b9d7ca56a
 Loading /home/jondecker76/ROMS/Nintendo/contra.nes...

  PRG ROM:    8 x 16KiB
  CHR ROM:    0 x  8KiB
  ROM CRC32:  0xf6035030
  ROM MD5:  0x5a5c2f4f1cafb1f55a8dc0d5ad4550e5
  Mapper:  2
  Mirroring: Vertical

  Loading cheats from /home/jondecker76/.mednafen/cheats/nes.cht...
   Error opening file: No such file or directory

 Initializing sound...
  Using "ALSA" audio driver with device "hw:0":ALSA Error: snd_pcm_hw_params_set_format(alsa_pcm, hw_params, sampformat) Invalid argument
Error opening a sound device.
Initializing video...
  Video Mode: 1400 x 1050 x 32 bpp
  OpenGL: Yes
   Pixel shader: none
  Fullscreen: Yes
  Special Scaler: None
  Scanlines: Off
  Destination Rectangle: X=0, Y=0, W=1400, H=1050
  OpenGL Implementation: NVIDIA Corporation GeForce 6200/AGP/SSE2 2.1.0 NVIDIA 96.39
  Checking maximum texture size...
   Apparently it is at least: 4096 x 4096
jondecker76@studio-desktop:~$ 



```

```

jondecker76@studio-desktop:~$ mednafen -sound 1 -sounddriver alsa -sounddevice "hw:1" -fs 1 -nes.xres 1400 -nes.yres 1050 -nes.stretch 1 "/home/jondecker76/ROMS/Nintendo/contra.nes"
Starting Mednafen 0.8.1
 Loading settings from "/home/jondecker76/.mednafen/mednafen.cfg"...
 Initializing joysticks...
  Joystick 0 - Jess Tech GGE909 PC Recoil Pad - Unique ID: ce96ea6b9d7ca56a
 Loading /home/jondecker76/ROMS/Nintendo/contra.nes...

  PRG ROM:    8 x 16KiB
  CHR ROM:    0 x  8KiB
  ROM CRC32:  0xf6035030
  ROM MD5:  0x5a5c2f4f1cafb1f55a8dc0d5ad4550e5
  Mapper:  2
  Mirroring: Vertical

  Loading cheats from /home/jondecker76/.mednafen/cheats/nes.cht...
   Error opening file: No such file or directory

 Initializing sound...
ALSA lib pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card
  Using "ALSA" audio driver with device "hw:1":ALSA Error: snd_pcm_open(&alsa_pcm, id ? id : "hw:0", SND_PCM_STREAM_PLAYBACK, 0) No such device
Error opening a sound device.
Initializing video...
  Video Mode: 1400 x 1050 x 32 bpp
  OpenGL: Yes
   Pixel shader: none
  Fullscreen: Yes
  Special Scaler: None
  Scanlines: Off
  Destination Rectangle: X=0, Y=0, W=1400, H=1050
  OpenGL Implementation: NVIDIA Corporation GeForce 6200/AGP/SSE2 2.1.0 NVIDIA 96.39
  Checking maximum texture size...
   Apparently it is at least: 4096 x 4096
jondecker76@studio-desktop:~$ 



```

```

jondecker76@studio-desktop:~$ mednafen -sound 1 -sounddriver alsa -sounddevice "M Audio Delta 1010" -fs 1 -nes.xres 1400 -nes.yres 1050 -nes.stretch 1 "/home/jondecker76/ROMS/Nintendo/contra.nes"
Starting Mednafen 0.8.1
 Loading settings from "/home/jondecker76/.mednafen/mednafen.cfg"...
 Initializing joysticks...
  Joystick 0 - Jess Tech GGE909 PC Recoil Pad - Unique ID: ce96ea6b9d7ca56a
 Loading /home/jondecker76/ROMS/Nintendo/contra.nes...

  PRG ROM:    8 x 16KiB
  CHR ROM:    0 x  8KiB
  ROM CRC32:  0xf6035030
  ROM MD5:  0x5a5c2f4f1cafb1f55a8dc0d5ad4550e5
  Mapper:  2
  Mirroring: Vertical

  Loading cheats from /home/jondecker76/.mednafen/cheats/nes.cht...
   Error opening file: No such file or directory

 Initializing sound...
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM M Audio Delta 1010
  Using "ALSA" audio driver with device "M Audio Delta 1010":ALSA Error: snd_pcm_open(&alsa_pcm, id ? id : "hw:0", SND_PCM_STREAM_PLAYBACK, 0) No such file or directory
Error opening a sound device.
Initializing video...
  Video Mode: 1400 x 1050 x 32 bpp
  OpenGL: Yes
   Pixel shader: none
  Fullscreen: Yes
  Special Scaler: None
  Scanlines: Off
  Destination Rectangle: X=0, Y=0, W=1400, H=1050
  OpenGL Implementation: NVIDIA Corporation GeForce 6200/AGP/SSE2 2.1.0 NVIDIA 96.39
  Checking maximum texture size...
   Apparently it is at least: 4096 x 4096
jondecker76@studio-desktop:~$ 



```



thanks,

Jon

---

### Post by flatulant on 2008-11-01
I am also having this problem, somebody help please.

---

### Post by jondecker76 on 2008-11-01
I did get this fixed - but I am at work right now, so working from memory...
Try this for the sound device parameter

-sounddevice "sexyal-literal-default"

it forces Alsa's default sound device

---

### Post by Mega_Mike on 2008-11-22
I have a sound problem too.  When playing Dracula X under mednafen, the music is extremely fast.  Anybody have a fix for this?

---

