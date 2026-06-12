---
title: "Some ubuntuforums pages crash firefox"
date: 2009-04-03
forum: General Help
---

### Post by KerryLB on 2009-04-03
Some pages I load on ubuntu forums crash firefox - no error message or 'crash report' request returned by ff.

This started happening a few days ago, and so far it only seems to be ubuntuforums pages that are doing this. I upgraded from ff v3.0.7 to 3.0.8 - didn't fix the problem.

Here's what comes up in Konsole:
> 
QPixmap: Invalid pixmap parameters
The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.            
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 38388 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.       
   To debug your program, run it with the --sync command line          
   option to change this behavior. You can then get a meaningful       
   backtrace from your debugger if you break on the gdk_x_error() function.)
Locking assertion failure.  Backtrace:                                      
#0 /usr/lib/libxcb-xlib.so.0 [0xb809b7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb809b96e]
#2 /usr/lib/libX11.so.6 [0xb6b8e619]
#3 /usr/lib/libXrender.so.1(XRenderFreePicture+0x41) [0xb6c3ff41]
#4 /usr/lib/libQtGui.so.4 [0xb42fa6bf]
#5 /usr/lib/libQtGui.so.4 [0xb42fb17d]
#6 /usr/lib/libQtGui.so.4(_ZN7QPixmap5derefEv+0x5d) [0xb42ef9ad]
#7 /usr/lib/libQtGui.so.4(_ZN7QPixmapD1Ev+0x30) [0xb42efdb0]
#8 /usr/lib/libQtGui.so.4 [0xb43e17d7]
#9 /usr/lib/libQtGui.so.4(_ZN12QPaintEngineD2Ev+0x2f) [0xb43294ff]
#10 /usr/lib/libQtGui.so.4 [0xb43d8e72]
#11 /usr/lib/libQtGui.so.4 [0xb42fa61c]
#12 /usr/lib/libQtGui.so.4 [0xb42fb17d]
#13 /usr/lib/libQtGui.so.4(_ZN7QPixmap5derefEv+0x5d) [0xb42ef9ad]
#14 /usr/lib/libQtGui.so.4(_ZN7QPixmapD2Ev+0x30) [0xb42efe10]
#15 /usr/lib/libQtGui.so.4 [0xb42f50ba]
#16 /usr/lib/libQtGui.so.4 [0xb42f572f]
#17 /usr/lib/libQtGui.so.4 [0xb42f4d5a]
#18 /lib/tls/i686/cmov/libc.so.6(exit+0x89) [0xb7e29d89]
#19 /usr/lib/libgdk-x11-2.0.so.0 [0xb67456b7]

Sometimes this happens as soon as the page is loaded, other times it happens while I'm scrolling down the page - and if I try it again on the same page it always crashes in the same position.

If I run 'sudo firefox' from Konsole, the problem goes away - but running ff with root permissions isn't something I want to be doing...

I've disabled all my firefox plugins/add-ons - problem doesn't go away.

Any suggestions? Or is this something I should be reporting on Mozilla's forums?


I'm running KDE 4.2 on Intrepid.

---

### Post by philinux on 2009-04-03
Could be the theme you're using for firefox and your desktop. Try the default or a different one.

---

### Post by KerryLB on 2009-04-03
Thanks Philinux!

Turns out it was my widget style. I changed it from Plastique to Oxygen - no more crashes. It also seems to be fine with the other widget styles there.... must be a bug in the Plastique style?

---

### Post by philinux on 2009-04-03
> **KerryLB said:**
> Thanks Philinux!

Turns out it was my widget style. I changed it from Plastique to Oxygen - no more crashes. It also seems to be fine with the other widget styles there.... must be a bug in the Plastique style?

Yep pain in the neck some themes.

---

