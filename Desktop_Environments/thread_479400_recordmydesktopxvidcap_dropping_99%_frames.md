---
title: "recordmydesktop/xvidcap dropping 99% frames"
date: 2007-06-20
forum: Desktop Environments
---

### Post by grazzt on 2007-06-20
recordmydesktop --with-shared --no-sound --quick-subsampling --zero-compression -o test.ogg
Initial recording window is set to:
X:0   Y:0    Width:1680    Height:1050
Adjusted recording window is set to:
X:0   Y:4    Width:1680    Height:1040
Your window manager appears to be compiz


Detected 3d compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Capturing!
Shutting down.Saved 20 frames in a total of 420 requests
.....


Is there something Im doing wrong?

Ati video card, but Ive tried with both fglrx and open source radeon drive, and the result is the same.

(adding --no-wm-check doesnt fix it either)

Switching from beryl to metacity also doesnt fix it.

If I load gtk-recordmydesktop, X cpu usages goes up to 80%! (which also will dorp 99% of all frames it tries to record)

xvidcap is no better.

Its an amd 3200 cpu with 7.04 32 bit ubuntu installed.

I would like to record my desktop! :)

---

