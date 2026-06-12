---
title: "Keyboard buttons v and 7 randomly stop working"
date: 2018-11-28
forum: Desktop Environments
---

### Post by mitap94 on 2018-11-28
I have had this problem for almost half a year. In the meantime I have reinstalled Ubuntu, changed to a new PC with identical hardware, but nothing helped.
The used Ubuntu version is 16.04.
In the text below I am basicaly copying my post from AskUbuntu where I couldn't find the solution.


I will try to explain the problem to the best of my abilities.
Some time after PC boot the v key and the 7 (not Num Pad) stop working. But they don't stop working completely, they work when using Shift+v and Shift+7 and I can type small v if I turn on CapsLock and press Shift+v.
When using the terminal (or text editor) the cursor blinks when these buttons are pressed, but nothing is written to the screen.
I would say that the problem is software related, like something is blocking v and 7 keys when pressed just by themselves.
To confirm this I tried using a virtual keyboard, then tried a different physical keyboard, changed USB ports and the behavior was always the same.
Does anyone have an idea what the problem could be or has had a similar problem?

I'm adding requested outputs:

```
$ xinput  
&#9121; Virtual core pointer                      id=2    [master pointer  (3)]  
&#9116;     &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]  
&#9116;     &#8627; Logitech USB Optical Mouse                  id=12   [slave  pointer  (2)]  
&#9123; Virtual core keyboard                     id=3    [master keyboard (2)]  
      &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]  
      &#8627; Power Button                                id=6    [slave  keyboard (3)]  
      &#8627; Video Bus                                   id=7    [slave  keyboard (3)]  
      &#8627; Power Button                                id=8    [slave  keyboard (3)]  
      &#8627; Sleep Button                                id=9    [slave  keyboard (3)]  
      &#8627; Eee PC WMI hotkeys                          id=13   [slave  keyboard (3)]  
      &#8627; Logitech USB Keyboard                       id=10   [slave  keyboard (3)]  
      &#8627; Logitech USB Keyboard                       id=11   [slave  keyboard (3)] 
``` 

```
$ setxkbmap -query  
rules:      evdev  
model:      pc105  
layout:     us
``` 

xev -event keyboard output when pressing v or 7

```
$ xev -event keyboard
KeymapNotify event, serial 28, synthetic NO, window 0x0,
    keys:  81  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
```

xev -event keyboard output when pressing other keys


```
$ xev -event keyboard output
KeyPress event, serial 28, synthetic NO, window 0x4e00001,
    root 0x151, subw 0x0, time 102625001, (555,-208), root:(615,384),
    state 0x10, keycode 40 (keysym 0x64, d), same_screen YES,
    XLookupString gives 1 bytes: (64) "d"
    XmbLookupString gives 1 bytes: (64) "d"
    XFilterEvent returns: False
```

```
$ sudo evtest /dev/input/by-id/usb-Logitech_USB_Keyboard-event-kbd
Event: time 1532686546.734457, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70019
Event: time 1532686546.734457, type 1 (EV_KEY), code 47 (KEY_V), value 1
Event: time 1532686546.734457, -------------- SYN_REPORT ------------
Event: time 1532686546.854412, type 4 (EV_MSC), code 4 (MSC_SCAN), value 70019
Event: time 1532686546.854412, type 1 (EV_KEY), code 47 (KEY_V), value 0
Event: time 1532686546.854412, -------------- SYN_REPORT ------------
```


I would gladly appreciate any help, as this is very frustrating and is hindering my work.

---

