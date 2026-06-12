---
title: "HELP: S3 savage IX8 being detected as AGP 1x"
date: 2006-10-02
forum: Desktop Environments
---

### Post by malathia on 2006-10-02
Hi all. I'm sort of at a loss here. I've been experiencing issues with CPU utilization during graphics rendering. We're talking about for very simple 2D screensavers (100% CPU) and even just page downing in FireFox can jump my CPU to 60%+. Thinking this can't be right, I began to investigate. I've tried a few different routes for getting direct rendering to enable. As it stands right now, it won't enable, complaining of too little video ram to support DRI. While investigating /var/log/Xorg.0.log, I noticed that AGP is being detected and set to 1x. Is there any way to correct this? All documentation that I've seen for my laptop (it's a T22) suggest that this card should be AGP 2x. Maybe I'm going down the wrong avenue entirely to correct this CPU utilization issue? whatever it is, when graphics are the question, choppiness and sluggishness ensue. below I'll place some pertinent query outputs:

```
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 2.0
(II) SAVAGE(0): VESA VBE Total Mem: 8192 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Incorporated. M7 BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 1.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 2.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 1.1
(--) SAVAGE(0): Chip: id 8c12, "Savage/IX-MV"
(--) SAVAGE(0): Engine: "MobileSavage"
(--) SAVAGE(0): AGP card detected
(==) SAVAGE(0): Using AGP DMA
(II) SAVAGE(0): Savage3D/MX/IX does not support command DMA.
(==) SAVAGE(0): Will try only vertex DMA mode
(==) SAVAGE(0): Using AGP 1x mode
(==) SAVAGE(0): Using 16 MB AGP aperture
(II) SAVAGE(0): mapping MMIO @ 0xf1000000 with size 0x80000
(==) SAVAGE(0): Using gamma correction (1.0, 1.0, 1.0)
(--) SAVAGE(0): probed videoram:  8192k
```

```
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 2.0
(II) SAVAGE(0): VESA VBE Total Mem: 8192 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Incorporated. M7 BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 1.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 2.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 1.1
(--) SAVAGE(0): mapping framebuffer @ 0xf0000000 with size 0x800000
(II) SAVAGE(0): map aperture:0xb1fa5000
(II) SAVAGE(0): 8844 kB of Videoram needed for 3D; 8192 kB of Videoram available
(EE) SAVAGE(0): Insufficient Videoram available for 3D -- Try a lower color depth or smaller desktop.  For integrated savages try increasing the videoram in the BIOS.
(EE) SAVAGE(0): DRI isn't enabled
```

---

### Post by po0f on 2006-10-02
malathia,

I have a T22 also!  I don't have linux on it atm, but I was looking through my old notes, and I believe this is how your Device section should look:
```

Section "Device"
  Driver  "savage"
  Option "ShadowStatus"  "true"
  Option "AGPMode"       "2"
  Option "DMAMode"       "None"
EndSection
```

I hope this works for you, because I am about to put Linux back on it.  Let me know if it works!

[EDIT]

Set the color depth to 16.  At 24, DRI would eat up more than that phenomonal 8MB VRAM T22's have.  ;)

---

### Post by malathia on 2006-10-02
thanks for the reply poOf. I believe it is currently set at 16, since yeah, this card's so phenomenal that truecolor is just an insult to it :) but I'll check that as well, thanks for the tip. I'll try that now and let you know how it goes.

---

### Post by malathia on 2006-10-02
Okay, so I went in and added the Option "AGPMode" "2", and the Option "DMAMode" "false" This bumped the AGP slot to 2x. As for DRI, I was still getting that I didn't have enough video ram (8844 vs. 8192), even though I am operating in 16bit color. To fix this, I went into /etc/X11/xorg.conf and edited the default settings for 16bit depth to use 1280x1024 resolution. After a reboot, DRI and DRM enabled fine. I saw a 300% increase in my framerate while running glxgears -printfps, from choppy to smooth, CPU usage has been reduced and all around movement through gnome is far more tolerable.
I'm going to be experimenting over the rest of the night and tomorrow seeing if I can find a way around the resolution settings or at least just to get the screen to not have the black bars down the side, since it was built for 1400x1050 native :(.

I'll keep this updated with my findings.

---

### Post by po0f on 2006-10-03
malathia,

Can we trade Thinkpads?  My T22 is the one with the 1024x768 max resolution.  I forgot that there was a widescreen model.  Hope you get that issue resolved.  Guess I'll be installing Ubuntu on my lappy tomorrow.  ;)

---

