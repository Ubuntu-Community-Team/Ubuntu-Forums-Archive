---
title: "[Ubuntu Mate] screen rotation in Lenovo miix 320"
date: 2021-11-05
forum: Desktop Environments
---

### Post by guillaume-thomsen on 2021-11-05
Hi,
I'm putting Ubuntu Mate on a lenovo miix 320, after trying lubuntu (PcmanFM-Qt isn't for me) and classic Ubuntu (too slow on this small computer). A problem occurs with Mate and lubuntu, not with Ubuntu : the screen starts turned by 90 ° on the left. I fix this with ```
xrandr -o right
``` on startup, but :
- the desk doesn't like it with compiz (yes, I like to show off)
 as seen in this picture
[[IMG]https://i.postimg.cc/mtZDCnGX/Capture-du-2021-11-05-20-21-40.png[/IMG]]("https://postimg.cc/mtZDCnGX")
- the touchscreen doesn't rotate accordingly, so I can't use it

I'm sure there is a problem with the gyroscope detection, since this doesn't happen with Ubuntu. When I take the screen off ( it can become a tablet) on Ubuntu, the screen rotates accordingly to the way I hold and a virtual keyboard appears.

I'm not asking for so much under Ubuntu Mate. Just to tell the system that the screen's (and touchscreen's) normal position is landscape. Maybe I need to tweak xorg a ittle, but I have no clue as to how...

I don't know what more info you need to help me, but I can enter command line for you if asked.

Thanks in advance for your insights.

---

### Post by guillaume-thomsen on 2021-11-05
I do have this :
```
~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; HTX USB HID Device HTX HID Device Consumer Control    id=12    [slave  pointer  (2)]
&#9116;   &#8627; HTX USB HID Device HTX HID Device Mouse     id=13    [slave  pointer  (2)]
&#9116;   &#8627; HTX USB HID Device HTX HID Device Touchpad    id=14    [slave  pointer  (2)]
&#9116;   &#8627; FTSC1000:00 2808:1015                       id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; HTX USB HID Device HTX HID Device Wireless Radio Control    id=9    [slave  keyboard (3)]
    &#8627; HTX USB HID Device HTX HID Device Keyboard    id=10    [slave  keyboard (3)]
    &#8627; HTX USB HID Device HTX HID Device System Control    id=11    [slave  keyboard (3)]
    &#8627; FTSC1000:00 2808:1015 UNKNOWN               id=16    [slave  keyboard (3)]
    &#8627; gpio-keys                                   id=17    [slave  keyboard (3)]
    &#8627; gpio-keys                                   id=18    [slave  keyboard (3)]
    &#8627; HTX USB HID Device HTX HID Device Consumer Control    id=19    [slave  keyboard (3)]
```

based on this : [https://askubuntu.com/questions/1066142/calibrate-touchscreen-pad-ubuntu-18-04](https://askubuntu.com/questions/1066142/calibrate-touchscreen-pad-ubuntu-18-04)

Maybe it can help ?

---

### Post by guillaume-thomsen on 2021-11-05
I also found xinput_calibrator, wihch gives this after making me touch 4 points.:
```
~$ xinput_calibrator
Calibrating standard Xorg driver "FTSC1000:00 2808:1015"
    current calibration values: min_x=0, max_x=65535 and min_y=0, max_y=65535
    If these values are estimated wrong, either supply it manually with the --precalib option, or run the 'get_precalib.sh' script to automatically get it (through HAL).
    --> Making the calibration permanent <--
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf' (/usr/share/X11/xorg.conf.d/ in some distro's)
Section "InputClass"
    Identifier    "calibration"
    MatchProduct    "FTSC1000:00 2808:1015"
    Option    "MinX"    "20390"
    Option    "MaxX"    "20288"
    Option    "MinY"    "52326"
    Option    "MaxY"    "52162"
    Option    "SwapXY"    "1" # unless it was already set to 1
    Option    "InvertX"    "0"  # unless it was already set
    Option    "InvertY"    "0"  # unless it was already set
EndSection

```
I should paste this in evdev or Usbtouchscreen, according to
[http://manpages.ubuntu.com/manpages/disco/man1/xinput_calibrator.1.html](http://manpages.ubuntu.com/manpages/disco/man1/xinput_calibrator.1.html)

but I don't know how. Using a |pipe ? Never did before, so I won't try on my own. And how do I know witch one to use ?

---

### Post by guillaume-thomsen on 2021-11-05
I found this : [https://ubuntu-mate.community/t/ubuntu-mate-on-a-hybrid-lenovo-miix-320/22042](https://ubuntu-mate.community/t/ubuntu-mate-on-a-hybrid-lenovo-miix-320/22042), which is exactly what I needed. Leaving it here in case other look for it.

---

