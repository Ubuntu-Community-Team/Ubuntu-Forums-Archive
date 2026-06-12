---
title: "Firefox crashing"
date: 2006-03-03
forum: Desktop Environments
---

### Post by drguitarum2005 on 2006-03-03
I'm running breezy with the latest 686 kernel and xfce 4.2.2. For some reason, when I go to certain webpages (I don't know if tis always the same ones or if it changes each time) such as performing a search on ebay, the page will begin to load and suddenly firefox will close. This happened with the 1.0.7 that came with ubuntu and with the latest firefox after I updated. What can I do to begin finding the root of this problem? System logs don't seem to tell me anything about it...

---

### Post by drguitarum2005 on 2006-03-04
anyone at all? this is very annoying...

---

### Post by aysiu on 2006-03-04
See if [this](http://www.ubuntuforums.org/showthread.php?t=103930) makes a difference.

---

### Post by drguitarum2005 on 2006-03-07
I tried that and i *think* it worked until I installed the flash plugin via firefox. any ideas?

---

### Post by drguitarum2005 on 2006-03-11
UPDATE:

after running firefox via console to see its output, the error I got was:

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 120 error_code 8 request_code 143 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


does anyone have any clue what this means? I got it with a fresh firefox, no extension, and going to a valid website, [www.weather.com](www.weather.com)

thanks!

---

