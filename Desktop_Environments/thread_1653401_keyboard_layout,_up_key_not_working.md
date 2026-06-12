---
title: "keyboard layout, up key not working"
date: 2010-12-26
forum: Desktop Environments
---

### Post by ryadav on 2010-12-26
i am using kubuntu and i would like to know how i can change my keyboard layout, i am using a ms media pro keyboard

just today i noticed randomly my up cursor key will stop working, the only way for me to fix this is to reboot, this is getting really annoying!

if i run xev and press the up key here is the output:

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   4294967168 0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 34, synthetic NO, window 0x4200001,
    root 0x15a, subw 0x0, time 8426048, (163,-16), root:(165,7),
    state 0x0, keycode 111 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


i have no idea what is eating up my cursor key, and if this is the only key affect???

---

### Post by inobe on 2010-12-26
system setting> input devices

or 

system settings> shortcuts and gestures

side note: i haven't experienced this and never seen any posts here regarding this.

---

### Post by koolmint on 2011-01-23
Have you found a solution for this symptom?
Because I suffered this too. Mine is Ubuntu 10.10 x64 and I use cherry keyboard(G80-11900).

---

### Post by droetker on 2011-02-06
Same here. Changing keyb layout does not help.

---

### Post by droetker on 2011-02-06
found it:
[https://bugs.kde.org/show_bug.cgi?id=256266](https://bugs.kde.org/show_bug.cgi?id=256266)

just disable khotkeys print screen, logout/login.

---

