---
title: "16-bit colors + Flash crashes Firefox"
date: 2005-12-25
forum: Desktop Environments
---

### Post by mikko.ohtamaa on 2005-12-25
I have Dell Inspiron 5000e with Ati Rage Mobility M3 display driver. I use DRI X extensions to get OpenGL acceleration. Pages containing Flash animations crash Firefox with the following error:

moo@moojr:~/freeorion/FreeOrion$ firefox
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 120 error_code 8 request_code 144 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

This happens with Firefox 1.0.3 and Firefox 1.5 

Solution:

Set XLIB_SKIP_ARGB_VISUALS environment variable and launch Firefox from a terminal. Obviously this changes the behavior of X rendering code and Flash works after this.

moo@moojr:~/freeorion/FreeOrion$ export XLIB_SKIP_ARGB_VISUALS=1
moo@moojr:~/freeorion/FreeOrion$ firefox

---

