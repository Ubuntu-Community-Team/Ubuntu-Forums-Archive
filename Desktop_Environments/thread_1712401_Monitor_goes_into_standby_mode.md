---
title: "Monitor goes into standby mode"
date: 2011-03-22
forum: Desktop Environments
---

### Post by cccc on 2011-03-22
hi

I have Xubuntu with XFCE Desktop installed.
I have disabled all screensaver and power save options, but Monitor still goes into black standby mode.
Howto prevent this?

---

### Post by matt_symes on 2011-03-22
Hi

Open a terminal and type

```
xset q
```

Post the results back here.

Kind regards

---

### Post by cccc on 2011-03-22
```
xset -q

Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  20
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  600    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Disabled
```

---

### Post by matt_symes on 2011-03-22
Hi

```
DPMS (Energy Star):
Standby: 0    Suspend: 0    Off: 0
DPMS is Disabled
```

Well that's odd. DMPS is off on your machine.

What do your log files say ?

I wonder if gnome-power-manager is causing the problem. I will need to do some research for you.

**EDIT: Just re-read your first post.**

> I have Xubuntu with XFCE Desktop installed.

So scrub gnome-power-manager as an idea.

*I assume you are using XFCE power manager ?*

Kind regards

---

### Post by matt_symes on 2011-03-22
Hi

Lets make doubly sure it's not a screen saver.  Open a terminal and type

```
xset s off
```

Wait to see if it sleeps.

Kind regards

---

### Post by cccc on 2011-03-22
Thx a lot, I'll try and let you know.

---

### Post by matt_symes on 2011-03-22
Hi

I have just downloaded a copy of xubuntu 10.10 and i am having a play. I hope you have 10.10.

Lets try to eliminate the power manager.

Open a terminal and type

```
xfce4-power-manager --quit
```

To confirm it is stopped type

```
pgrep xfce4-power-manager
```

If nothing is returned it has stopped.

Wait again to see if it goes into standby. If it does there is a setting there that's been missed.

Kind regards

---

### Post by cccc on 2011-03-23
Thx a lot:```

[B]xset s off
xset dpms 0 0 0
xset -dpms s off [/B]
```solved my problem.

BTW xfce4-power-manager is not installed on my system:```
# dpkg -l | grep xfce4-power-manager
#
```

---

### Post by matt_symes on 2011-03-23
Hi

Glad it's fixed. Must have been an old screen saver option kicking about. Is it persistent between boots ? If not you might have to add the command to a config file.

> BTW xfce4-power-manager is not installed on my system:

That's interesting. What version of xubuntu are you using ? I downloaded 10.10 yesterday and that was the default one installed.

Just for my curosity what power manager are you using. Any chance you could post ...

```
ps aux | grep -i power-manager
```

Kind regards

---

### Post by cccc on 2011-03-23
It's old, lucid, should upgrade, but it's 10 yeas old hardware. 
I've wrote a startup script to switch off DPMS and Screen Saver.

```
# ps aux | grep -i power-manager
root      4182  0.0  0.0   3316   808 pts/0    S+   17:30   0:00 grep -i power-manager
```

---

