---
title: "Cygwin problems"
date: 2007-10-15
forum: Desktop Environments
---

### Post by Jayasimha on 2007-10-15
Hi,

    I am a newbie to ubuntu. I am having problems using cygwin to remotely login to ubuntu thru my windows desktop.This is the output that i am getting....


$ xwin -query 10.225.76.155
Welcome to the XWin X Server
Vendor: The Cygwin/X Project
Release: 6.8.2.0-2

Contact: [email]cygwin-xfree@cygwin.com[/email]

XWin was started with the following command line:

xwin -query 10.225.76.155

_XSERVTransmkdir: Cannot create /tmp/.X11-unix with root ownership
winValidateArgs - g_iNumScreens: 1 iMaxConsecutiveScreen: 1
(II) XF86Config is not supported
(II) See [http://x.cygwin.com/docs/faq/cygwin-x-faq.html](http://x.cygwin.com/docs/faq/cygwin-x-faq.html) for more information
(==) FontPath set to "/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/TT
F/,/usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/CID/,/usr/X11R6/lib/
X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/"
winDetectSupportedEngines - Windows NT/2000/XP
winDetectSupportedEngines - DirectDraw installed
winDetectSupportedEngines - DirectDraw4 installed
winDetectSupportedEngines - Returning, supported engines 00000007
winSetEngine - Using Shadow DirectDraw NonLocking
winAdjustVideoModeShadowDDNL - Using Windows display depth of 32 bits per pixel
winFinishScreenInitFB - Masks: 00ff0000 0000ff00 000000ff
MIT-SHM extension disabled due to lack of kernel support
XFree86-Bigfont extension local-client optimization disabled due to lack of shar
ed memory support in the kernel
(--) Setting autorepeat to delay=500, rate=31
(--) winConfigKeyboard - Layout: "00000409" (00000409)
(--) Using preset keyboard for "English (USA)" (409), type "4"
Rules = "xorg" Model = "pc105" Layout = "us" Variant = "(null)" Options = "(null
)"
(--) 3 mouse buttons found
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from li
st!
winPointerWarpCursor - Discarding first warp: 837 494

it stops here and goes no further. is there a solution please help me out.
I have tried the same with a fc4 machine and it works perfectly fine.

---

