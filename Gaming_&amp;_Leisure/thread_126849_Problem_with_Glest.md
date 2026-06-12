---
title: "Problem with Glest"
date: 2006-02-07
forum: Gaming &amp; Leisure
---

### Post by geo926 on 2006-02-07
I am using a Toshiba Sattelite M35X-S309 and I get this message when starting Glest.
> george@ubuntu:~$ glest
open /dev/[sound/]dsp: Device or resource busy
OpenAL Vendor: J. Valenzuela
OpenAL Version: 0.0.7
OpenAL Renderer: Software
OpenAl Extensions: Software
Exception: Couldn't open audio device.


Any ideas, sound works with everything else...

---

### Post by Lord Illidan on 2006-02-07
Maybe you have to do ```
killall esd
``` before you start the game.

---

### Post by geo926 on 2006-02-07
That worked thankyou very much!

---

