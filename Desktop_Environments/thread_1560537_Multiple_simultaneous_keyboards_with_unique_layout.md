---
title: "Multiple simultaneous keyboards with unique layouts"
date: 2010-08-25
forum: Desktop Environments
---

### Post by Kisbey on 2010-08-25
As the title says, I'm interested in two (or more) simultaneous keyboards, each with a unique layout.

Everything I've researched indicates this should be possible, but I'm unable to get it to work.  Regardless of how I set things up, all keyboards consistently operate as if they share the CoreDevice setting in xorg.conf.  For example:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Keyboard1"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "evdev"
    Option         "CoreKeyboard"
    Option         "Device" "/dev/input/event3"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Keyboard1"
    Driver         "evdev"
    Option         "Device" "/dev/input/event4"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "ad"
EndSection

```In the above config, both keyboards behave as if they're set for the USA layout.  Changing the layout in gnome-keyboard-properties affects all of the connected keyboards equally, but has no provision for altering individual devices.

Any suggestions?

---

### Post by Kisbey on 2010-08-28
Solved.

Depending on what you're trying to do, this can be two or three steps.

1.)  Determine which layout will be assigned to each keyboard.

2.) [Optional] create a new keyboard layout if you're after a custom one (I recommend simply altered an existing layout).

3.) Use the setxkbmap command with the -device tag to apply your keyboard maps to the relevant devices.  If you don't know your device, start with 1 and work your way up.  Be prepared to undo your change by repeating it with your current layout.  For example, typing

```
 setxkbmap -device 3 af 
```sets both of my keyboards to Farsi, and typing

```
 setxkbmap -device 3 us 
```sets them both back to US.  It's probably best to have this line copied and ready to paste before every change to easily undo your changes.

In my case, I altered the Andorra keyboard layout with my custom, and applied it thusly:

```
 setxkbmap -device 7 ad 
```And that's it!  Each keyboard is operating simultaneously with a unique layout.  Typing on each results in the keys I want and there is no switching or hotkeys required to make this change.

---

### Post by Dr.Yak on 2012-12-11
> **Kisbey said:**
> If you don't know your device, start with 1 and work your way up.

Another (better) solution is to use xinput to give you a list of devices:
```
 ~# xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                           id=11   [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad          id=12   [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Laser Mouse                  id=14   [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                     id=15   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=10   [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                          id=13   [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                     id=16   [slave  keyboard (3)]

```

You can then use *grep* or *gawk* to get the *id* number. Here is an example:
```
setxkbmap -device `xinput list | gawk '/Logitech/&&/keyboard/{match($0,/id=([[:digit:]]+)/,f);print f[1]}'` bg
```
This looks for the keyboard having *Logitech* in its name and set its layout to bulgarian

---

