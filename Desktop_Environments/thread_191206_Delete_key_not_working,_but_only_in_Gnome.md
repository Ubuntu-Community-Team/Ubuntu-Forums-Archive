---
title: "Delete key not working, but only in Gnome"
date: 2006-06-07
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-06-07
The delete key on my laptop keyboard has stopped working in Gnome.
It works in xfce and standard terminal (not in x).

Now, I obviously am to blame for this as I was messing around with my keyboard to get my media keys working (e.g. fn+end = skip track).

However, I cannot remember where I would go about sorting this one out.

The output in xev from pressing delete is:

```
KeyPress event, serial 26, synthetic NO, window 0x3a00001,
    root 0x3e, subw 0x0, time 2925512307, (167,-13), root:(177,83),
    state 0x0, keycode 107 (keysym 0x1008ff31, XF86AudioPause), same_screen YES,    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3a00001,
    root 0x3e, subw 0x0, time 2925512370, (167,-13), root:(177,83),
    state 0x0, keycode 107 (keysym 0x1008ff31, XF86AudioPause), same_screen YES,    XLookupString gives 0 bytes:

```

Now, you can see why this is double-annoying.  Pressing delete pauses my music, but won't restart it as the key is only bound to pause.  So, not only does my delete key not delete, it pauses my music!  So how do I change the x-bindging from XF86AudioPause to Delete (or whatever it is supposed to be)?

I would really appreciate some help here as I feel an idiot for doing this in the first place, and it's most annoying!

---

