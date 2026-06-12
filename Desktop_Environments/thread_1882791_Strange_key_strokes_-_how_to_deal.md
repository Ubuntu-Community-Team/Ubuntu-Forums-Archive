---
title: "Strange key strokes - how to deal?"
date: 2011-11-17
forum: Desktop Environments
---

### Post by cnbiz850 on 2011-11-17
I have this strange thing happening since I installed Ubuntu on the new Dell laptop.  Initially I installed 10.04 64bits and now upgraded to 11.04 64bits, and it happens on both.

The following strange key stroke always occurs.  As outputs by xev:

```
KeyPress event, serial 35, synthetic NO, window 0x5800001,
    root 0x15d, subw 0x0, time 12097930, (142,124), root:(1013,586),
    state 0x0, keycode 235 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x5800001,
    root 0x15d, subw 0x0, time 12097930, (142,124), root:(1013,586),
    state 0x0, keycode 235 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Sometimes more frequently (like once per second), sometimes less (once maybe 10 minutes or longer).  It's always this keycode 235.  It was mapped to "F5" to turn up screen brightness.  It was also mapped to a touch sensitive button on the laptop that also adjusts the screen brightness.  I used xmodmap to remap it to NoSymbol.  But still X does not ignore it.  The remap doesn't seem even to affect "F5" key or the touch sensitive button, both of which still works adjusting the brightness and xev still reports as keycode 235.  

The problem for me is that it affects the screensaver, causing it never to turn on at times.  It also affects the auto repeat on a key I hold down, causing the repeat to stop.

I googled about it but can't find anything useful.  Anyone know what the problem might be?  How can I deal with it?  Is it possible to make X ignore it?

---

### Post by cnbiz850 on 2011-11-22
Any thoughts please?

---

