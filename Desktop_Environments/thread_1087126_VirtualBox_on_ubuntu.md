---
title: "VirtualBox on ubuntu"
date: 2009-03-04
forum: Desktop Environments
---

### Post by kokatsas on 2009-03-04
Hi guys,

I have installed VirtualBox on a server with Ubuntu 8.04.1.
Through my MacBook, I ssh to the server using the X forward in order to run VirtualBox through the command line.
I run 'VirtualBox' and the process runs successfully.
On the VirtualBox window, I select one of my three virtual machines (all Ubuntu) that are already running and click Show.
The window for the machine does not open and in my terminal i receive the following message:
admin@server:~$ VirtualBox
Qt WARNING: X Error: BadWindow (invalid Window parameter) 3
Major opcode: 7 (X_ReparentWindow)
Resource id: 0x44
Qt WARNING: X Error: BadWindow (invalid Window parameter) 3
Major opcode: 7 (X_ReparentWindow)
Resource id: 0x44
Qt WARNING: X Error: BadWindow (invalid Window parameter) 3
Major opcode: 20 (X_GetProperty)
Resource id: 0x36000e3
Qt WARNING: X Error: BadWindow (invalid Window parameter) 3
Major opcode: 12 (X_ReparentWindow)
Resource id: 0x36000e3

When i exit the VirtualBox window i get:
Locking assertion failure. Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6cf7767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6cf781e]
#2 /usr/lib/libX11.so.6 [0xb77dc518]
#3 /usr/lib/libX11.so.6(XFreePixmap+0x25) [0xb77b8aa5]
#4 /usr/lib/libQtGui.so.4 [0xb6ff501c]
#5 /usr/lib/libQtGui.so.4(_ZN7QPixmap5derefEv+0x61) [0xb6ff1fa1]
#6 /usr/lib/libQtGui.so.4(_ZN7QPixmapD0Ev+0x2d) [0xb6ff247d]
#7 /usr/lib/virtualbox/VirtualBox.so [0xb79882f1]
#8 /usr/lib/virtualbox/VirtualBox.so [0xb7964ab1]
#9 /lib/tls/i686/cmov/libc.so.6(exit+0xd4) [0xb7d87084]
#10 /usr/lib/libX11.so.6 [0xb77d563e]
#11 /usr/lib/libX11.so.6(_XError+0xfe) [0xb77d573e]
#12 /usr/lib/libX11.so.6 [0xb77dce5c]
#13 /usr/lib/libX11.so.6(_XReply+0x15a) [0xb77dd21a]
#14 /usr/lib/libX11.so.6(XSync+0x6a) [0xb77d124a]
#15 /usr/lib/libX11.so.6(XCloseDisplay+0x8e) [0xb77b1f5e]
#16 /usr/lib/libQtGui.so.4 [0xb6f9ff0a]
#17 /usr/lib/libQtGui.so.4(_ZN12QApplicationD1Ev+0x431) [0xb6f4ba01]
#18 /usr/lib/virtualbox/VirtualBox.so(TrustedMain+0xa3c) [0xb793f0dc]
#19 /usr/lib/virtualbox/VirtualBox [0x8049a11]

Need to mention that i can access my virtual machines directly through VNC, from my Mac.
It looks like an X window issue and i believe it's on the machine that the VirtualBox is installed.

Any ideas?
Cheers

---

