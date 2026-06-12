---
title: "awn doesn't start"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by killkoy on 2007-10-25
when i run avant-window-navigator i get the following output in terminal

$ avant-window-navigator
Screen is composited.
APPLET : /usr/lib/awn/applets/taskman.desktop
The program 'avant-window-navigator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 815 error_code 8 request_code 72 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

when i run it with the --sync option i get the same message

awn-manager starts up without errors.

Thanks

---

### Post by killkoy on 2007-10-30
bump

---

### Post by killkoy on 2007-11-01
and again :)

---

### Post by boeing777 on 2007-11-01
Remove AWN & reinstall.  Sometimes that help.

---

### Post by aeonwings on 2007-11-01
This site is pretty useful. Might help. [http://phorolinux.com/how-to-install-avant-window-navigator-on-ubuntu-710-gutsy-gibbon.html]("http://phorolinux.com/how-to-install-avant-window-navigator-on-ubuntu-710-gutsy-gibbon.html")

---

### Post by Crafty Kisses on 2007-11-01
> **killkoy said:**
> when i run avant-window-navigator i get the following output in terminal

$ avant-window-navigator
Screen is composited.
APPLET : /usr/lib/awn/applets/taskman.desktop
The program 'avant-window-navigator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 815 error_code 8 request_code 72 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

when i run it with the --sync option i get the same message

awn-manager starts up without errors.

Thanks
Hmmm, do you have your GFX drivers installed?

---

