---
title: "FCEU has choppy sound when in focus"
date: 2006-11-22
forum: Gaming &amp; Leisure
---

### Post by k1001001 on 2006-11-22
So I've gone through all the mess of installing FCEU, but now when I play games, the sound is choppy when the game is in focus on the screen. When FCEU is minimized, the sound is fine. I think this may be due to the high bitrate of the sound. I set up the startfceu method, and when it begins in terminal, here is what it outputs:

```
Starting FCE Ultra 0.98.12...
Loading /home/keith/ROMs/NES/mega2.zip_FILES/MEGAMAN2.NES...

 PRG ROM:   16 x 16KiB
 CHR ROM:    0 x  8KiB
 ROM CRC32:  0x0fcfc04d
 ROM MD5:  0x0527a0ee512f69e08b8db6dc97964632
 Mapper:  1
 Mirroring: Vertical

Initializing video... Video Mode: 800 x 600 x 8 bpp full screen

Initializing sound...
 Bits: 16
 Rate: 48000
 Channels: 1
 Byte order: CPU Native
 Buffer size: 1152 sample frames(24.000000 ms)
```

The 48khz bitrate seems a bit high to me, as I know CD quality sound is at 44.1khz. Is there any way to change this? Maybe 22050hz would be a better fit, or maybe 8 bit, since it is after all an 8 bit game.

Oh yeah, what the hell are the controls? WASZ is up, left, right, and down respectively, and Enter is start, but I can't figure out anything else.

---

