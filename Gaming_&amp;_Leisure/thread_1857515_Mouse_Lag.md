---
title: "Mouse Lag"
date: 2011-09-13
forum: Gaming &amp; Leisure
---

### Post by cyb3rkn19ht on 2011-09-13
Same problem with a Razor Mamba.

---

### Post by lenzoid on 2011-09-15
> **cyb3rkn19ht said:**
> Same problem with a Razor Mamba.
Ouch. This probably ruins your gaming experience too. Which kernel version you using? Is it the same effect in every game? I used WinXP for gaming in the recent years and I didn't find a solution to that problem in Linux. Tried different xset m settings?

---

### Post by cyb3rkn19ht on 2011-10-10
Found the fix! here is the post:
[http://ubuntuforums.org/showpost.php?p=4310834&postcount=6](http://ubuntuforums.org/showpost.php?p=4310834&postcount=6)


Thanks I am running 2.6.39-0-generic. So far I have tested Minecraft, Lugaru and Onlive. I currently have xset m 10 4.

Here is all the info from xset q.
```
$ xset q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  0    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  10/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

```

---

