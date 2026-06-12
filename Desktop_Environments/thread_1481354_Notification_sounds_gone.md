---
title: "Notification sounds gone"
date: 2010-05-12
forum: Desktop Environments
---

### Post by x-shaney-x on 2010-05-12
After recent update (I can't remember exactly when but indicator-message was one of the updates) I no longer get any kind of notification sounds in evolution or empathy or anything.

Previously I would hear various beeps and squeaks.
Everything else sound wise is working normally.

---

### Post by squab on 2010-05-12
I think the options your looking for are under System->Prefernces->Sound in the Sound Effects tab.

---

### Post by x-shaney-x on 2010-05-12
Makes no difference.  I normally have window sounds disabled.  If I enable them I get window sounds but still no notification sounds.

---

### Post by x-shaney-x on 2010-05-16
Well they seem to be back again but not sure how or why or why they went.
All except Evolution anyway.

---

### Post by JavaPTGL on 2010-05-17
I Am Facing This Problem Too.
How To Solve This?

---

### Post by JavaPTGL on 2010-05-17
Oops!
My Mistake.I Had Completely Lowered The " Alert Volume " In Sound Preferences..
Now Everything Is Back To Normal. 
:guitar:

---

### Post by ccroy on 2011-07-17
Hi,

I recently upgraded from 9.10 to 10.04. I did this by backing up my data, changing my root partition size, and loading 10.04 from a CD I downloaded.

Now that I'm up and running I've lost any sounds that desktop programs generate. I use the Stopwatch program for my neck exercises as it can count down then "beep" when time is up. It works, but doesn't beep anymore. Another example is playing the Mahjong game, again no sounds.

I do get the start up sound, login sound, can play an audio CD, and can use online stopwatch programs with sound. 

The Stopwatch programmer suggested I look at xset. This is what my xset looks like:

 chris@chris:~$ xset q
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
  acceleration:  2/1    threshold:  4
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
chris@chris:~$ 

I can turn the bell on with xset b on, but I still have no program sounds and the change isn't permanent.

Any thoughts?

Thanks,

Chris Roy
Laguna Hills, CA

---

