---
title: "garbled/frozen display with Server 10.10 on PE2850"
date: 2010-10-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by feetloaf on 2010-10-13
Hi, All,

So I installed Ubuntu Server 10.10 on an old PowerEdge 2850 and am getting garbled and frozen display. dmesg refers to radeon, but doesn't show any errors. The display adapter is functional; video output seems fine during POST and with the Ubuntu installation program, but upon starting X, I get this wierd, blurry rectangular shape that slowly fades into view on the monitor. Using Ctrl+Alt+F1 doesn't give me a console, nothing I do with the keyboard changes the display. I would be fine with just getting a bash prompt after bootup, I don't need a desktop environment. Fortunately, I chose to install OpenSSH server during installation, so I can work with it that way. How can I get the local console working?

> root@s2g-web2:/var/log# dmesg | grep -i "drm"
[    9.281001] [drm] Initialized drm 1.1.0 20060810
[    9.367637] [drm] radeon defaulting to kernel modesetting.
[    9.367643] [drm] radeon kernel modesetting enabled.
[    9.372445] [drm] initializing kernel modesetting (RV100 0x1002:0x5159).
[    9.382840] [drm] register mmio base: 0xFE0F0000
[    9.382844] [drm] register mmio size: 65536
[    9.413091] [drm] radeon: irq initialized.
[    9.414534] [drm] Detected VRAM RAM=64M, BAR=128M
[    9.414541] [drm] RAM width 32bits DDR
[    9.414737] [drm] radeon: 16M of VRAM memory ready
[    9.414740] [drm] radeon: 512M of GTT memory ready.
[    9.414774] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    9.437919] [drm] Loading R100 Microcode
[    9.442908] [drm] radeon: ring at 0x00000000D0000000
[    9.442937] [drm] ring test succeeded in 1 usecs
[    9.443268] [drm] radeon: ib pool ready.
[    9.443529] [drm] ib test succeeded in 0 usecs
[    9.444781] [drm] DFP table revision: 3
[    9.444898] [drm] Radeon Display Connectors
[    9.444904] [drm] Connector 0:
[    9.444909] [drm]   VGA
[    9.444913] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[    9.444916] [drm]   Encoders:
[    9.444919] [drm]     CRT1: INTERNAL_DAC1
[    9.444922] [drm] Connector 1:
[    9.444925] [drm]   VGA
[    9.444929] [drm]   DDC: 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c
[    9.444932] [drm]   Encoders:
[    9.444935] [drm]     CRT2: INTERNAL_DAC2
[    9.444938] [drm] Connector 2:
[    9.444940] [drm]   DVI-I
[    9.444945] [drm]   HPD1
[    9.444950] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[    9.444953] [drm]   Encoders:
[    9.444956] [drm]     CRT2: INTERNAL_DAC2
[    9.444958] [drm]     DFP1: INTERNAL_TMDS1
[    9.622958] [drm] fb mappable at 0xF0040000
[    9.622964] [drm] vram apper at 0xF0000000
[    9.622967] [drm] size 786432
[    9.622970] [drm] fb depth is 8
[    9.622973] [drm]    pitch is 1024
[    9.789351] fb0: radeondrmfb frame buffer device
[    9.789354] drm: registered panic notifier
[    9.789481] [drm] Initialized radeon 2.5.0 20080528 for 0000:0b:0d.0 on minor 0


---

### Post by feetloaf on 2010-10-15
Bump

# lspci -nn | grep VGA
0b:0d.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] [1002:5159]

---

### Post by feetloaf on 2010-12-20
This turned out to be caused by icompatibility with both of my monitors (Polaroid and Samsung), borrowing a third monitor (Acer) let me finish setting it up so I could use SSH thereafter.

---

