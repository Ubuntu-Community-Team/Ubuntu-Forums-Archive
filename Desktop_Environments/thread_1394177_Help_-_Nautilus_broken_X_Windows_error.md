---
title: "Help - Nautilus broken X Windows error"
date: 2010-01-30
forum: Desktop Environments
---

### Post by 3eyedsamurai on 2010-01-30
Background:
Ubuntu 64 9.10. The system has been running a little slow past few weeks but I thought is was all because of flash issues (some flash not playing and npviewer.bin eating up resources). Mouse sometimes wouldn't click on Nautilus (I would have to left click the desktop and then I could click 'once' on Nautilus). I rebooted this morning and now Nautilus is gone crazy. There are no desktop icons and the taskbar is full if icons saying "starting file manager". I tried rebooting, killing nautilus but nothing has fixed it.

I got the following error when I tried "nautilus &" from the terminal:

```
:~$ The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 597 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Happy to post any other code if you give me instructions. I have had this OS for 3 years and I would rather not have to reinstall if there is a better way. FYI; I have two monitors running separate X sessions - one is using Awn.

---

