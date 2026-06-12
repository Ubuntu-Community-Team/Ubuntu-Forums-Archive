---
title: "[SOLVED] America's Army problem, Xlib extensions."
date: 2006-02-02
forum: Gaming &amp; Leisure
---

### Post by RavenOfOdin on 2006-02-02
Hi
I downloaded America's Army Special Ops and installed it, but I can't seem to get past: 

> 
Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Xlib: extension XiG-SUNDRY-NONSTANDARD missing on display ':0.0'
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.


when running armyops.sh in terminal.

Is there a way I can fix this?

PS: I went to the America's Army site at [http://www.americasarmy.com/support/faq_linux.php?p=3&t=8#faq7](http://www.americasarmy.com/support/faq_linux.php?p=3&t=8#faq7) and I now know that my card - a 128 MB ATI Radeon 9200 - is supported. So this can't be an issue related to hardware.

---

### Post by RavenOfOdin on 2006-02-02
Just to update, I ran a whole battery of tests including fglrx-config, glxgears, and strace'ing the armyops.sh process to look for missing calls. I've narrowed the possibilities down, and (as is on many other threads here related to ATI cards) I've managed to make sure the drivers are installed as "fglrx" instead of "ati." But this issue is still continuing, albeit with a different error message:

> 
Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: Couldn't find matching GLX visual


---

