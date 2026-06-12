---
title: "NWN Gold install and permissions issue for Intrepid"
date: 2008-11-21
forum: Gaming &amp; Leisure
---

### Post by trooperchix on 2008-11-21
I followed the instructions to install Neverwinter Nights Gold using the install script at:

 [http://icculus.org/~ravage/nwn/](http://icculus.org/~ravage/nwn/)

I updated my repo for wine for intrepid.

I try and run the bugger, I get a quick flash of a black screen then it disappears and I'm back to looking at my desktop.  I believe it is a permissions issue, I seem to recall that from the last time I installed this bugger.  I'm pretty noob, so be as detailed as possible.  Grrr, love the game but can't get it running again.  Please help!!

Thanks
Trooperchix

PS.  I have gone through as many other postings in the forums I could find, non of the fixes proposed in them worked.

---

### Post by regor210 on 2008-11-21
Note. be careful not to change anything when  in Edit Menus.

What I do when I'm having this kind of problem is, right click on applications, Edit Menus then work my way to the launcher , right click on the launcher icon> Properties then copy the hole Command line and past it in Terminal, run it to see the errors. 

If you need more help post the errors.

---

### Post by trooperchix on 2008-11-21
> **regor210 said:**
> Note. be careful not to change anything when  in Edit Menus.

What I do when I'm having this kind of problem is, right click on applications, Edit Menus then work my way to the launcher , right click on the launcher icon> Properties then copy the hole Command line and past it in Terminal, run it to see the errors. 

If you need more help post the errors.

Here is what my terminal spit out for me...

eddie@kilimanjaro:~$ /home/eddie/nwn/nwn
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7ab5891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb7c23494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7e6553d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xb7e6078c]
#5 ./lib/libSDL-1.2.so.0 [0xb7e62457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e57f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e3a7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e3a8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7ab596e]
#2 /usr/lib/libX11.so.6 [0xb7c22619]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x40) [0xb7c18530]
#4 ./lib/libSDL-1.2.so.0 [0xb7e6051a]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x408) [0xb7e60a30]
#6 ./lib/libSDL-1.2.so.0 [0xb7e62457]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e57f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e3a7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e3a8dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7ab5891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb7c23494]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7e6bb1a]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x673) [0xb7e60c9b]
#5 ./lib/libSDL-1.2.so.0 [0xb7e62457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e57f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e3a7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e3a8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7ab596e]
#2 /usr/lib/libX11.so.6 [0xb7c22619]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb7bf71d6]
#4 ./lib/libSDL-1.2.so.0 [0xb7e62584]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e57f66]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e3a7de]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e3a8dc]
#8 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#10 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7ab5891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb7c23494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7e6580e]
#4 ./lib/libSDL-1.2.so.0 [0xb7e5ea89]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7e5eb3a]
#6 ./lib/libSDL-1.2.so.0 [0xb7e6260f]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e57f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e3a7de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e3a8dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7ab596e]
#2 /usr/lib/libX11.so.6 [0xb7c22619]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb7c18bc6]
#4 ./lib/libSDL-1.2.so.0 [0xb7e61ff3]
#5 ./lib/libSDL-1.2.so.0 [0xb7e62635]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7e57f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7e3a7de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7e3a8dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7ab5891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb7c23494]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7e6553d]
#4 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7e658e7]
#5 ./lib/libSDL-1.2.so.0 [0xb7e60368]
#6 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7e61092]
#7 ./lib/libSDL-1.2.so.0 [0xb7e63375]
#8 ./lib/libSDL-1.2.so.0 [0xb7e6352b]
#9 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7e587df]
#10 ./nwmain [0x84a0e31]
#11 ./nwmain(strftime+0x1de9) [0x80508a1]
#12 ./nwmain [0x805c9f2]
#13 ./nwmain [0x805a218]
#14 ./nwmain [0x8058ff1]
#15 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#16 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#17 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ab57c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7ab596e]
#2 /usr/lib/libX11.so.6 [0xb7c22619]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb7bf6435]
#4 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0xd4) [0xb7e610f4]
#5 ./lib/libSDL-1.2.so.0 [0xb7e63375]
#6 ./lib/libSDL-1.2.so.0 [0xb7e6352b]
#7 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7e587df]
#8 ./nwmain [0x84a0e31]
#9 ./nwmain(strftime+0x1de9) [0x80508a1]
#10 ./nwmain [0x805c9f2]
#11 ./nwmain [0x805a218]
#12 ./nwmain [0x8058ff1]
#13 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce7685]
#15 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted

---

### Post by trooperchix on 2008-11-21
bump

---

### Post by Perfect Storm on 2008-11-21
Try change

line 10 to 

export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH

in the nwn file.

---

### Post by trooperchix on 2008-11-22
> **Artificial Intelligence said:**
> Try change

line 10 to 

export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH

in the nwn file.

Um...  Which line 10?

---

### Post by Perfect Storm on 2008-11-22
You open the nwn file in nwn directory with a text editor application and edit line 10.


You can also see how to install NWN without wine here if everything goes wrong; [http://gaming.gwos.org/doku.php/guides:64bit:nwn](http://gaming.gwos.org/doku.php/guides:64bit:nwn)

---

### Post by trooperchix on 2008-11-22
Ok, here's a copy of the changed nwn file:

#!/bin/sh

# This script runs Neverwinter Nights from the current directory
cd /home/eddie/nwn
export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH

./nwmain $@

I updated as you stated, and it's getting closer.  It actually appears to launch and open a full page black window then it disappears again.  Do you see anything else that I should change?

Thanks ai

---

### Post by Perfect Storm on 2008-11-22
Which error pop up now?

---

### Post by trooperchix on 2008-11-22
To be honest, I don't know.  I tried it again, and it did the same as before except I saw a brief flash of the title page and couldn't get out of the game.  It's weird.  Is there a way to look for an error code?  a log file maybe?

---

### Post by Perfect Storm on 2008-11-22
You could check the error.log


EDIT:
See also: [http://ubuntuforums.org/showthread.php?t=666726](http://ubuntuforums.org/showthread.php?t=666726)
Do you run 64-bit?

---

### Post by trooperchix on 2008-11-22
No, I run 32 bit.  I'll go check that other link...

---

### Post by trooperchix on 2008-11-22
Where do I find the error log, and I think this might be a wierd video issue.  I also just tried to install AA and it launches, then everything kind of pixelates.  I also noticed on NWN that the screen comes up, I see a flash of the title screen, then a window opens asking for the registration key and then everything inside these windows goes black.  I've also noticed that I have a regular mouse pointer that sits in the middle of the window and then the pirate hand one the game has, and the pirate hand is the only one I have control of (in nwn, then the screen goes black just as stated above).

---

### Post by Perfect Storm on 2008-11-22
Which card do you have?

---

### Post by trooperchix on 2008-11-23
I'm having a bugger of a time figuring that out.  how do I do that?

---

### Post by Perfect Storm on 2008-11-23
> **trooperchix said:**
> I'm having a bugger of a time figuring that out.  how do I do that?

```
lspci
```

---

### Post by trooperchix on 2008-11-24
> **Artificial Intelligence said:**
> ```
lspci
```

Here's the output:

```

eddie@kilimanjaro:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
eddie@kilimanjaro:~$ 


```

I wonder if I am not running the right driver, as I am not running the restricted drivers I used to before this last upgrade to intrepid.  It's a thought..

---

### Post by Perfect Storm on 2008-11-24
AFAIK Mobile PM965/GM965/GL960 have Open Source driver. You'e not the first one with problems regarding intel card. You might search/making a new thread to solve your video card-problem. I can't help you there, I'm running only Nvidia cards.

---

### Post by trooperchix on 2008-11-27
Bummer.  Anyone out there having the same issues with whatever game, same video card, maybe we can start working on the issue here?

---

### Post by hitbyambulance on 2008-11-28
i'm trying to install this on a friend's PC with Intrepid Ibex, and i'm getting the EXACT same issues as trooperchix. the video card on this machine is an ATi Radeon 9550.

UPDATE: game works perfectly once "./lib" is removed from the nwn.ini script.

---

