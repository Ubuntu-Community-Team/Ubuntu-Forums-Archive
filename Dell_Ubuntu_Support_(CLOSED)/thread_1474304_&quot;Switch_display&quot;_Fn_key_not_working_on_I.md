---
title: "&quot;Switch display&quot; Fn key not working on Inspiron 1545"
date: 2010-05-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lufte on 2010-05-05
Hi all. I've got an Inspiron 1545 running the 64 bits version of Xubuntu 10.04. Every Fn key (such as Toggle wireless, battery, next song, etc) works fine, except the "switch display" key (Fn+F1), wich is supposed to switch between different displays when available. The key is mapped as Super+p (yeah... pretty weird). This is the xev output:
```

KeyPress event, serial 31, synthetic NO, window 0x4a00001,
    root 0x111, subw 0x4a00002, time 11070098, (39,30), root:(45,88),
    state 0x0, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x4a00001,
    root 0x111, subw 0x4a00002, time 11070103, (39,30), root:(45,88),
    state 0x40, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XmbLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x4a00001,
    root 0x111, subw 0x4a00002, time 11070164, (39,30), root:(45,88),
    state 0x40, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x4a00001,
    root 0x111, subw 0x4a00002, time 11070174, (39,30), root:(45,88),
    state 0x40, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

I've tried the [[COLOR="Blue"]*Hotkeys*/*Troubleshooting - Ubuntu Wiki*[/COLOR]]("https://wiki.ubuntu.com/Hotkeys/Troubleshooting") guide, but since there are two different codes for the same key I don't know how to proceed. Any clue is appreciated.[]("https://wiki.ubuntu.com/Hotkeys/Troubleshooting")[]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAgQFjAA&url=https%3A%2F%2Fwiki.ubuntu.com%2FHotkeys%2FTroubleshooting&ei=ozPiS8-WNs6luAeL4aFd&usg=AFQjCNEGepRrRhg96LPK1jvFa_gTGMVO5Q&sig2=ZvTZ1XnjNul7x7mDWXn0pw")

---

### Post by estanton on 2010-05-05
I'm having the same problem with my studio 14z, just noticed it this evening.

---

### Post by Rackstar on 2010-05-21
I'm having the same issue.

Did you find a solution?

---

### Post by Rackstar on 2010-05-21
I wrote a workaround for this bug here:
[http://www.backports.ubuntuforums.org/showthread.php?p=9336932#post9336932](http://www.backports.ubuntuforums.org/showthread.php?p=9336932#post9336932)

---

### Post by lufte on 2010-06-15
> **Rackstar said:**
> I wrote a workaround for this bug here:
[http://www.backports.ubuntuforums.org/showthread.php?p=9336932#post9336932](http://www.backports.ubuntuforums.org/showthread.php?p=9336932#post9336932)

That seems to be a great workaround, but the key is still wrong. I tried the  [[COLOR=Blue]*Hotkeys*/*Troubleshooting -  Ubuntu Wiki*[/COLOR]]("https://wiki.ubuntu.com/Hotkeys/Troubleshooting") with an Ubuntu Karmic Koala live cd, and the key has the correct keycode if the gnome-settings-daemon is previously killed (like the guide says). But in Xubuntu there is no gnome-settings-daemon running, and I don't know wich xfce process could be the equivalent. Any clue?

By the way: thanks for the answer.

---

