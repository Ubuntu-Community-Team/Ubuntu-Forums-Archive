---
title: "xchat-gnome fails to start due to an X server error"
date: 2006-08-24
forum: Desktop Environments
---

### Post by marvin88 on 2006-08-24
I get the following when trying to start xchat-gnome:
```
The program 'xchat-gnome' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadImplementation (server does not implement operation)'.
  (Details: serial 291 error_code 17 request_code 129 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```
My current X server version as listed in synaptic is **xserver-xorg-core 1:1.0.2-0ubuntu10.4**, and yes I do use Xgl, which is **xserver-xgl 7.0.0+cvs20060625**.

Does anybody have the same problem? Is it Xgl or something else?

Thanks,
marvin.

---

