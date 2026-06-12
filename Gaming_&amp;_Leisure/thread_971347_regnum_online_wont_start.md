---
title: "regnum online wont start ???"
date: 2008-11-04
forum: Gaming &amp; Leisure
---

### Post by markg48 on 2008-11-04
hi today after i install regnum online i tried to start the game the first error i got was my video card wasnt supported and that  i had to upgrade drivers so i installed the ati driver in the ubuntu package manager but now wen i start regnum online i put my user name and pass and enter but after i do that the client closes:confused::confused::confused:

---

### Post by markg48 on 2008-11-04
i ran this command from the terminal:

 cd '/home/mark/regnum

~/regnum$ G_SLICE=always-malloc ./rolauncher

and i get this error in the terminal:

The program 'rolauncher' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 10 error_code 1 request_code 143 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

