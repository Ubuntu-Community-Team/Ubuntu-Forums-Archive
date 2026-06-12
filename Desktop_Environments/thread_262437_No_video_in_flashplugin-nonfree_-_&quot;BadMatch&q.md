---
title: "No video in flashplugin-nonfree - &quot;BadMatch&quot; crash"
date: 2006-09-21
forum: Desktop Environments
---

### Post by javaJake on 2006-09-21
I've seen plenty of "no sound" threads, but no "no video" threads... until today! ;)

Anyway, to get down to business, Firefox crashes (both firefox and mozilla-firefox... don't ask why Ubuntu has two versions of firefox - I don't know) and Opera shows nothing but a blank grey square. Even stranger, Opera doesn't crash, but plays the sound and I can hit the pause button (if I know where it is).

Here's the error on the command line from Firefox:

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 144 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


Now, I am using radeon drivers... could it be my video driver, or is that too far fetched?

---

### Post by javaJake on 2006-09-21
Oh, and I am using the plugins straight from Adobe.

---

### Post by javaJake on 2006-09-23
*bump*

Everyone wavers at this one. AHA! I HAVE YOU! FINALLY! A problem you are all SCARED OF!

(Let's see if that gets you guys to help me out. :D )

---

### Post by javaJake on 2006-09-23
OK, figured it out. Just for the record, let me describe what I did.

I added "export XLIB_SKIP_ARGB_VISUALS=1" to the beginning of, say, /usr/bin/opera, or /usr/bin/firefox. (It turns out these files are SH files, not binary!)

This somehow disables "Composite" or something like that, I think. Anyway, there's a bug report about this here: [https://launchpad.net/products/firefox/+bug/59610](https://launchpad.net/products/firefox/+bug/59610)


Hope this helps anyone out there who had the same issue as I did.

---

