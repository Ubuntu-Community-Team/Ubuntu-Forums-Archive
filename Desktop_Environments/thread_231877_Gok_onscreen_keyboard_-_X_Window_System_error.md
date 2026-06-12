---
title: "Gok onscreen keyboard - X Window System error"
date: 2006-08-07
forum: Desktop Environments
---

### Post by bgryderclock on 2006-08-07
I am trying to use the GOK onscreen keyboard in ubuntu 6.06

When I enter "gok" in the termal I get this message in the terminal and then nothing:```
user@user-desktop:~$ gok
/dev/js0: No such file or directory
The program 'gok' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDevice, invalid or uninitialized input device'.
  (Details: serial 148 error_code 168 request_code 145 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```I tried entering "gok --sync" and got the same message.

What should I try, where should I look?
Is there any other onscreen keyboard I can try?

---

