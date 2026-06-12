---
title: "Hangs on boot after adding new ATI video card"
date: 2009-11-25
forum: Desktop Environments
---

### Post by keepitsimpleengr on 2009-11-25
I running 9.10 on a four cpu 64bit hardware.

I have 2xGTX260 nvidia SLI,  I added a Radeon HD 4650 to drive 2nd monitor "AuxRight" (which wasn't very satisfactory when run off the nvida).

When booting, the system hangs with blank screens.  If the ServerLayout section line 'Screen 1 "AuxRight" RightOf "MainLeft"' is commented out, the system boots without the Radeon screen.

I've attached the xorg.conf & Xorg.0.log.

This system also boots WinXP-x64 & Vista-x64.

I could use a little help, I've never seen this type of hang.  Log stops at "RADEON(1): initializing int10".  I had to log in from another computer to save the log.

---

