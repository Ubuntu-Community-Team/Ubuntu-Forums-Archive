---
title: "Keys auto activating without keyboard."
date: 2009-02-14
forum: General Help
---

### Post by SniperZero on 2009-02-14
I am having a weird problem that the keys left and right alt activate every 30 seconds.

It starts with one of them then alternates to the other then back again every 30 seconds.

I never noticed it before due to gnome not really using the alt keys. However when running windows XP under virtualbox or a windows application under WINE is when it starts to get annoying. It still occurs even when virtualbox is not running.

I am running Ubuntu 8.10 - 2.6.27-11-generic

I have tried 
-Another keyboard
-Removing the keyboard
-Rebooting

output from xev
```
KeyPress event, serial 34, synthetic NO, window 0x4200001,
    root 0x13e, subw 0x0, time 17250536, (48,-15), root:(753,51),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x4200001,
    root 0x13e, subw 0x0, time 17250536, (48,-15), root:(753,51),
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x4200001,
    root 0x13e, subw 0x0, time 17280896, (48,-15), root:(753,51),
    state 0x10, keycode 108 (keysym 0xffea, Alt_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x4200001,
    root 0x13e, subw 0x0, time 17280896, (48,-15), root:(753,51),
    state 0x18, keycode 108 (keysym 0xffea, Alt_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x4200001,
    root 0x13e, subw 0x0, time 17310900, (48,-15), root:(753,51),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x4200001,
    root 0x13e, subw 0x0, time 17310900, (48,-15), root:(753,51),
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x4200001,
    root 0x13e, subw 0x0, time 17340904, (48,-15), root:(753,51),
    state 0x10, keycode 108 (keysym 0xffea, Alt_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x4200001,
    root 0x13e, subw 0x0, time 17340904, (48,-15), root:(753,51),
    state 0x18, keycode 108 (keysym 0xffea, Alt_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

Can anyone suggest something to figure out what is causing this or how to stop it.

Let me know if you need any other information.

Thanks
-Matt

---

### Post by khelben1979 on 2009-02-14
Have you looked in /etc/init.d/ to see if you have any "weird programs" that which causes your problem?

Does this problem arise when you use Windows XP without using Linux on it? It might be a hardware failure.

---

### Post by SniperZero on 2009-02-14
> **khelben1979 said:**
> Have you looked in /etc/init.d/ to see if you have any "weird programs" that which causes your problem?

Does this problem arise when you use Windows XP without using Linux on it? It might be a hardware failure.

I had a look there but doesn't seem to be anything suspicious. 

No the problem doesn't occur in Vista (dual boot setup).

---

