---
title: "Sixaxis controller not recognized by all emulators"
date: 2012-12-31
forum: Emulators
---

### Post by ntzrmtthihu777 on 2012-12-31
Hello all
Managed to bluetooth my Sixaxis PS3 controller to my ubuntu 12.04 install, having some difficulty getting it to work on some programs, emulators in particular.

jstest /dev/input/js1 shows the buttons and axis being pressed properly, but PCSX does not accept its input when using their respective configure joystick dialogues. (in fact it is configured, just horridly wrong, and refuses to be reconfigured)(Same problem for zsnes, but I switched over to bsnes and managed to manually set the controller up by editing the input configuration file manually)

Is there a similar option for PCSX? I checked the ~/.pcsx and did not see any such config files.

---

### Post by ntzrmtthihu777 on 2013-01-09
Managed to get it to work indirectly. Qjoypad was tricky as the amount of axis and buttons on the DS3 meant not all were on my screen. I eventually just randomly assigned keys buttons and "typed" with my pad to figure out what Qjoypad called each PS3 button, then manually edit the layout file (its in ~/.qjoypad3 )

The buttons equate to:
```

[FONT=Courier New]DS3    QJOY
up     5
down   7
left   8
right  6
start  4
select 1
tri    13
O      14
X      15
&#12525;     16
l1     11
l2     9
l3     2
r1     12
r2     10
r3     3
ps     17[/FONT]
```The format for the layout file is:
```
# QJoyPad 4.1 Layout File

Joystick 2 {
        Button 1: key 28
        Button 2: key 52
        Button 3: key 54
        Button 4: key 24
        Button 5: key 111
        Button 6: key 114
        Button 7: key 116
        Button 8: key 113
        Button 9: key 38
        Button 10: key 41
        Button 11: key 25
        Button 12: key 27
        Button 13: key 26
        Button 14: key 40
        Button 15: key 53
        Button 16: key 39
        Button 17: key 29
}

```This is my personal layout, I saved it as PCSX.lyt. This assumes the following layout:
[FONT=Courier New]___________________________________[/FONT]
[FONT=Courier New]|Tab| Q = | W = | E = | R = | T = |
[U]|__   | str | L-1 | Tri | R-1 | Sel |
[/U]|Caps   *| A = | S = | D[/FONT][FONT=Courier New] = | F[/FONT][FONT=Courier New] = |
_|Lock_  | L-2 | Sqr | Cir | R-2 |_
|LeftShift| Z = | X[/FONT][FONT=Courier New] = | C[/FONT][FONT=Courier New] = |
_|________          | L-3 |  _X_  | R-3 |_
[/FONT]

---

