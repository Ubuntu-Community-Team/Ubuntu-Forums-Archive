---
title: "Sunbird crashes"
date: 2008-10-01
forum: Desktop Environments
---

### Post by xu-thierry71 on 2008-10-01
Hi, and sorry for my frenchy english :)
I installed the sunbird package on my Xubuntu 8.04, but when I run sunbird, I get a nice window titled Sunbird but everything inside it is black...
Furthermore **ps axuw | grep sunbird ** gives something like:

thierry   6246  1.4  5.4 200504 56904 ?        Sl   16:57   1:15 /usr/lib/thunderbird/thunderbird-bin

200504 is huge no?

Sometimes "segfault" and :

[I]thierry@DELL:~$ *** Calendar schema version is: 7
Segmentation fault
sunbird
*** Calendar schema version is: 7
The program 'gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 3950 error_code 9 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)[/I]

Any idea?

Ta
Thierry

---

