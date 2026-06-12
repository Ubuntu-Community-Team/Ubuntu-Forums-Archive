---
title: "[B]Problems with drivers and running OpenGL code[/B]"
date: 2009-03-30
forum: General Help
---

### Post by Urema on 2009-03-30
Hi,

I posted yesterday about a message i kept getting when running an OpenGL program (no replies, understandable). Now after attempting to see if the desktop animation worked, i now get this message when running the opengl code:

"X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  159 (GLX)
  Minor opcode of failed request:  14 (X_GLXGetVisualConfigs)
  Serial number of failed request:  11
  Current serial number in output stream:  11
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6e7b7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6e7b96e]
#2 /usr/lib/libX11.so.6 [0xb6ec2619]
#3 /usr/lib/libX11.so.6(XESetCloseDisplay+0x44) [0xb6ea4294]
#4 /usr/lib/libGL.so.1 [0xb7d057c9]"

Plus the desktop animation wont enable keeps saying that the driver isnt activated even though it is.

Anybody know what is going on or any advice on what to do or where to[COLOR="Red"][/COLOR] go for help?

Thanks in advance,

N Dean G.

---

