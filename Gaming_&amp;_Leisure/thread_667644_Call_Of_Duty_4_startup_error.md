---
title: "Call Of Duty 4 startup error"
date: 2008-01-14
forum: Gaming &amp; Leisure
---

### Post by frexell on 2008-01-14
Hi,
Has anyone found a good reliable site or thread how to get CoD 4 run on Ubuntu with Wine? I've been bouncing around the whole evening trying to figure what is need to run it and what's not. So examples / reviews indicate that DirectX would be need and some say not.  But basically I'm stuck in situation, that wine starts the game okay, but after few secs following error is printed:

----- Initializing Renderer ----
----- Client Initialization Complete -----
Attempting 44 kHz 16 bit [Windows default] sound
----- R_Init -----
Getting Direct3D 9 interface...
Pixel shader version is 3.0
Vertex shader version is 3.0
Video card or driver doesn't accelerate dynamic textures.
Video card or driver doesn't support separate alpha blend, glow will be disabled.

And terminal has following lines:

[email]rexell@frexell-ubuntu-desktop:~/.wine[/email]/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare$ wine iw3sp.exe 
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x33f93c,0x00000000), stub!

HW:
AMD Athlon 64 6800+
Club 3d Geforce 7600 GS
2GB of RAM
Ubuntu Gutsy 64-bit

---

