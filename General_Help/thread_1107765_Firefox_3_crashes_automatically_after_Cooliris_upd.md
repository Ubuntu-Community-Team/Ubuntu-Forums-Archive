---
title: "Firefox 3 crashes automatically after Cooliris update"
date: 2009-03-27
forum: General Help
---

### Post by whosee on 2009-03-27
Hello all, I'm running Hardy 8.04 with Firefox 3 and the other day I try to run Cooliris and it wanted me to update. So I did and ever since Firefox crashes immediately after opening. I tried completely removing via synaptic and reinstalling but get the same issue. I also tried running via terminal and get the following message:
[I]
The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 3932 error_code 8 request_code 128 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7fac767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7fac81e]
#2 /usr/lib/libX11.so.6 [0xb6aff518]
#3 /usr/lib/libX11.so.6(XESetCloseDisplay+0x31) [0xb6ae28d1]
#4 /usr/lib/libGL.so.1 [0xb4c517c9][/I]

Where do I go from here? I'm new to Ubuntu so the simpler the fix the better, thanks!

---

### Post by lovinglinux on 2009-03-27
Try deleting Cooliris extension directory. It's under your FF profile ~/.mozilla/firefox/*.default/extensions/  (back up the entire profile just in case).

---

### Post by whosee on 2009-03-28
That did the trick! Thank you very much lovinglinux!

---

### Post by dedmonds on 2009-03-28
For what it's worth, I had a very similar problem on my system with the forced update. The technical support at Cooliris was very helpful and provided me with two new builds to try to resolve the issue on my system within a few hours. I now have the Cooliris update running well on my system.

---

### Post by apitsch on 2009-04-25
im having the same problem with ubuntu 8.1, i dont know how to do what was recommened by lovinglinux

---

### Post by Knatchwa on 2009-04-30
Seems to happen with Jaunty as well, first time I tried installing it on firefox v3.10 It does seem to be an issue with Cooliris itself as Firefox works fine otherwise. To solve it I just used the Firefox -safe-mode and uninstalled Cooliris. And really that is the same thing that was offered earlier, the question still remains what is it's underlying cause, any guesses why Firefox and Cooliris with Jaunty don't seem to want to get along?

---

