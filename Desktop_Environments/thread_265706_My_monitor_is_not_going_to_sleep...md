---
title: "My monitor is not going to sleep.."
date: 2006-09-26
forum: Desktop Environments
---

### Post by zurih on 2006-09-26
Hi

I have Samsung 960BF LCD monitor.
I set up the power management prefs that puts the display to sleep after 1 minute of in-activity.
For some reason its not working.

My video card is NVIDIA 6600GT, nForce2 motherboard.

What could be the problem?

Thanks in advance

---

### Post by Warbo on 2006-09-26
The only thing I can think of is making sure "Option      "DPMS"" is in the monitor section of the file /etc/X11/xorg.conf. If it is, then I'm stumped.

---

### Post by zurih on 2006-09-26
yep. there is one already.

Section "Monitor"
        Identifier      "Samsung 960BF"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
EndSection

anything else I can check??

thanks

---

### Post by orb9220 on 2006-09-26
Do a xset -q in a term and post results.

---

### Post by zurih on 2006-09-27
> **orb9220 said:**
> Do a xset -q in a term and post results.


```

Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  auto repeat delay:  191    repeat rate:  37
  auto repeating keys:  00ffffffdffffbbf
                        fadfffdfffdfe5ef
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
Bug Mode: compatibility mode is disabled
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On
File paths:
  Config file:  /etc/X11/xorg.conf
  Modules path: /usr/lib/xorg/modules
  Log file:     /var/log/Xorg.0.log

```

---

### Post by orb9220 on 2006-09-27
xset -dpms
will turn off DPMS

---

### Post by KhaaL on 2006-09-27
while we're on the subject, is there a command in the terminal to turn off/send the monitor to sleep?

---

### Post by zurih on 2006-09-27
> **orb9220 said:**
> xset -dpms
will turn off DPMS

"The -dpms option disables DPMS (Energy Star) features."

As I know my monitor supports that.
Does it effent on other things?

> 
Do a xset -q in a term and post results.


interesting...

---

### Post by orb9220 on 2006-09-27
No what it is doing is telling xserver to disregard dpms all togerther. It does not affect anything but how x handles the monitor. You could still use screensavers,etc...

But I still havn't fiqured out how the whole x versus gnome-power works. Looks like x can overide what gnome says to do.

---

### Post by zurih on 2006-09-28
> **KhaaL said:**
> while we're on the subject, is there a command in the terminal to turn off/send the monitor to sleep?

just figured it out:

```
xset dpms force standby
``` will send the monitor to sleep :)

but still the auto sleep after x minutes is not working with\without dpms.

---

