---
title: "Disable Mouse Acceleration"
date: 2015-04-08
forum: Gaming &amp; Leisure
---

### Post by Zukaro on 2015-04-08
EDIT: oops ;~; double posted by accident (my browser did something weird and then this got double posted :v)

I've been trying to disable mouse acceleration but it doesn't seem to be working.  The mouse I have is a Corsair Vengeance M65.


This is what my xinput looks like:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Corsair Corsair M65 Gaming Mouse            id=9    [slave  pointer  (2)]
&#9116;   &#8627; Corsair Corsair M65 Gaming Mouse            id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv5 307 Pen stylus                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv5 309 Finger touch                id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv5 307 Pen eraser                  id=17    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv5 307 Pen pad                     id=18    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Microsoft® LifeCam HD-5000                 id=8    [slave  keyboard (3)]
    &#8627; Corsair Corsair M65 Gaming Mouse            id=10    [slave  keyboard (3)]
    &#8627; USB Camera                                  id=14    [slave  keyboard (3)]
    &#8627; USB Keyboard                                id=15    [slave  keyboard (3)]
    &#8627; USB Keyboard                                id=16    [slave  keyboard (3)]

```

I've listed the properties of both listings of my mouse (I ignored the keyboard listing of my mouse as I assume that's not relevant to the pointer), the mouse acceleration property is 268 for both listings.

What I've been trying is:
```
xinput set-prop 11 268 -1
xinput set-prop 9 268 -1

```

But that doesn't seem to be working.  I'm not sure what else I can try.  Everything I've looked up only mentions the above method that I already tried.

---

### Post by lisati on 2015-04-09
> **Zukaro said:**
> EDIT: oops ;~; double posted by accident (my browser did something weird and then this got double posted :v)


It happens sometimes......

Duplicate of [http://ubuntuforums.org/showthread.php?t=2272842](http://ubuntuforums.org/showthread.php?t=2272842) closed so that the community's efforts aren't accidentally diluted.

---

