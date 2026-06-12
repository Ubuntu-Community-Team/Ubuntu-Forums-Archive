---
title: "&quot;Sleep&quot; button is seen as &quot;Return&quot; in Lubuntu 16.04"
date: 2017-02-10
forum: Desktop Environments
---

### Post by Milan Knizek on 2017-02-10
Hi,

I recently installed Lubuntu 16.04 to update my Kodi & TVHeadEnd combo. Before, I used older LTS Xubuntu.

To define keyboard bindings in Openbox, I used obkey to assign a script to the Sleep button.

Obkey correctly recognises my keypress as XF86Sleep, however pressing the key later yields no action. Xev says that I press "Return" (Enter) key instead.

Here is the xev output on pressing the Sleep key:

```
= Pressing XF86Sleep key

KeyPress event, serial 48, synthetic NO, window 0x2200001,
    root 0x1eb, subw 0x0, time 31150322, (764,429), root:(766,458),
    state 0x0, keycode 36 (keysym 0xff0d, Return), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
"   XmbLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False

KeyRelease event, serial 48, synthetic NO, window 0x2200001,
    root 0x1eb, subw 0x0, time 31150450, (764,429), root:(766,458),
    state 0x0, keycode 36 (keysym 0xff0d, Return), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False

FocusOut event, serial 48, synthetic NO, window 0x2200001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 48, synthetic NO, window 0x2200001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 48, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0


```
And here the output on pressing the standard Enter key:
```

= Pressing Enter key

KeyPress event, serial 48, synthetic NO, window 0x2200001,
    root 0x1eb, subw 0x0, time 31234319, (764,429), root:(766,458),
    state 0x0, keycode 36 (keysym 0xff0d, Return), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
"   XmbLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False

KeyRelease event, serial 48, synthetic NO, window 0x2200001,
    root 0x1eb, subw 0x0, time 31234400, (764,429), root:(766,458),
    state 0x0, keycode 36 (keysym 0xff0d, Return), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False

```

Any idea what's wrong? Keycode and keysym are the same for both keys. (I do not have to say it used to work just fine in older Xubuntu.)

---

