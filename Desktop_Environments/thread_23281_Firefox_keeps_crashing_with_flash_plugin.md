---
title: "Firefox keeps crashing with flash plugin"
date: 2005-04-01
forum: Desktop Environments
---

### Post by sanitario on 2005-04-01
Everytime I try to load a page with flash content, Firefox crashes. 

If I run it in a terminal, I get this message: 
 mozilla-firefox
*** loading the extensions datasource
*** loading the extensions datasource
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 117 error_code 8 request_code 147 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Has anyone else had the same problem? 

TIA

---

### Post by vaskark on 2005-04-01
Yeah, I had the same problem. My only advice is to disable composite in xorg.conf. Just comment out the related lines and restart your X server. Hopefully this will be fixed soon ;)

---

### Post by mam28 on 2008-01-22
dont use adblock plus and the problem goes away.:guitar:

---

