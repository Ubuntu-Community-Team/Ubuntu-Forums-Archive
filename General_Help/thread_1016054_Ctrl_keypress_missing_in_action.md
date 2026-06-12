---
title: "Ctrl keypress missing in action?"
date: 2008-12-19
forum: General Help
---

### Post by JelleB on 2008-12-19
Hi there,

Recently I got my hands on a Fujitsu-Siemens laptop, an Amilo m7400D to be exact, and I run Kubuntu 804 on it. As is customary for laptops, it has a keyboard with extra useless keys on the side that do not work out of the box. I tried to get them to work (so I could experiment with the wifi, it's off by default...). However I cannot remember/reproduce all steps I took to get it to work. Somewhere along the line I seem to have killed my Ctrl-key, both the left and right ones. I can still see some events with xev, but not the correct behavior I think. here is what xev tells me:
```
FocusOut event, serial 27, synthetic NO, window 0x3a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 27, synthetic NO, window 0x3a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 27, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
```
as you can see, no keypress is reported (but something is, so the key is not plain broken). To show this is not a fluke, here are the events from a regular keypress:
```
KeyPress event, serial 30, synthetic NO, window 0x3a00001,
    root 0x64, subw 0x0, time 1322675141, (138,522), root:(152,599),
    state 0x0, keycode 52 (keysym 0x7a, z), same_screen YES,
    XLookupString gives 1 bytes: (7a) "z"
    XmbLookupString gives 1 bytes: (7a) "z"
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x3a00001,
    root 0x64, subw 0x0, time 1322675303, (138,522), root:(152,599),
    state 0x0, keycode 52 (keysym 0x7a, z), same_screen YES,
    XLookupString gives 1 bytes: (7a) "z"
    XFilterEvent returns: False

```

I already tried to clear the ctrl with xmodmap -e "clear ctrl", but that did not solve anything. looking at /usr/share/apps/kxkb/ubuntu.xmodmap does not reveal any suspicious things either.
So there you have it: where does my keypress go, and how do I get it back?

---

