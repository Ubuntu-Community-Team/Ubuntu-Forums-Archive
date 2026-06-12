---
title: "Prevent Screen From Blanking \ Power Saving"
date: 2012-12-26
forum: Desktop Environments
---

### Post by Kirk Schnable on 2012-12-26
Good afternoon,

I am working on resolving a slight glitch in my lab image before I deploy it to all computers... This seems to be a problem frequently seen, and Googling it produces no shortage of results.  Unfortunately, most of the results I've seen don't seem to actually work.

I am running the latest Ubuntu 12.04, and when the computer is left idle for a time, the screen goes blank.  We knew we didn't want this kind of behavior, and we made sure the power management preferences were all zero'ed, and also completely uninstalled xscreensaver from our Xubuntu image.

I believe this is an Xorg setting, not an XFCE related setting, because LightDM at the login screen also experiences the phenomenon.

We do not want this to happen, as we want our computer labs to always show the login screen.  Else, we are afraid people will walk in, and press the power button believing the computer to be off.

I plan to work with my responders to find a solution that actually works to prevent this from happening.  Hopefully, as future Googlers arrive at this thread, it will help them out too.

Thanks,
Kirk

---

### Post by Kirk Schnable on 2012-12-26
So far, I have tried these fixes, and they **do not work**.

*in /etc/rc.local*
```
/usr/bin/setterm -blank 0 -powersave off -powerdown 0
/usr/bin/xset s off
```

At this time, the output of "xset -q" is as follows:
[http://paste.ubuntu.com/1467902/](http://paste.ubuntu.com/1467902/)
> Keyboard Control:
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
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

I think this part is a problem, still.
[B]Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  600    cycle:  600[/B]

---

### Post by Kirk Schnable on 2012-12-26
I tried putting this in my /etc/rc.local file, and it didn't have any effect on my xset -q output.

```
/usr/bin/setterm -blank 0 -powersave off -powerdown 0
/usr/bin/xset s off
/usr/bin/xset s noblank
/usr/bin/xset s noexpose
/usr/bin/xset s 0 0
```

I put this code in to my LightDM login screen preparation script, and it ran, and made the Xorg setting changes.

So, it looks like putting xset commands in /etc/rc.local has no effect on the settings.

And now I will wait awhile, to see if this fixes the issue with the screen blanking.  

My xset -q output now is:
[http://paste.ubuntu.com/1467929/](http://paste.ubuntu.com/1467929/)
> Keyboard Control:
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
  prefer blanking:  no    allow exposures:  no
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

**Edit:** The modifications described above did have the desired effect on my Xorg settings, however the behavior still occurs.  I will continue researching... and if anyone has any ideas, please post them!

---

### Post by Kirk Schnable on 2012-12-26
I discovered this thread:
[http://ubuntuforums.org/showthread.php?t=2062608](http://ubuntuforums.org/showthread.php?t=2062608)

I created this /etc/X11/xorg.conf:
```
Section "ServerFlags"
Option "blanktime" "0"
Option "standbytime" "0"
Option "suspendtime" "0"
Option "offtime" "0"
EndSection
```

So far so good!

---

