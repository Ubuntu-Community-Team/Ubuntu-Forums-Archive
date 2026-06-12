---
title: "Still no Unreal"
date: 2007-03-20
forum: Gaming &amp; Leisure
---

### Post by Pieboy337 on 2007-03-20
I am in dire need for help. I have tried looking through these forums for answers on my unreal tournament problems, but non of the tutorials seem to help. I keep trying to run my copy of unreal after using the loki installer, but after I type ./ut I just get this:

```
root@beepo-linux:/home/joel/ut# ./ut
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Signal: SIGIOT [iot trap]
Aborting.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Cannot open display ":0.0"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Cannot open display ":0.0"
```

I am really lost on this whole thing and have spent quite sometime trying to fix it with lots of different how to tutorials. Please could someone give me a simple step by step guide to get it working. I am using kubuntu edgy by the way.

---

### Post by DoktorSeven on 2007-03-20
Don't run UT as root, run it as your user.

If it spits out messages about not being able to initialize rendering or some crazy stuff like that, look into how to enable direct rendering for  your videocard (search forums).

$ glxinfo | grep direct
should give
direct rendering: Yes
if not, you do not have it set up correctly.

---

