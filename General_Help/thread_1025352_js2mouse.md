---
title: "js2mouse"
date: 2008-12-30
forum: General Help
---

### Post by gcbzzzz on 2008-12-30
i'm trying to use my joypad as a mouse (or keyboard)

i've followed instructions on an archived thread here about setting up js2mouse on X.

I ended up writting this to my xorg.conf

```

Section "ServerLayout"
     [...]
     InputDevice "j2m" "SendCoreEvents"
EndSection
Section "InputDevice"
    Identifier     "j2m"
    Driver         "mouse"
    Option         "Protocol" "PS/2"
    Option "Device" "/dev/js2m_fifo"
    Option "ZAxisMapping" "4 5"
    Option "Buttons" "7"
    Option "ZAxisMapping" "6 7"protocol
EndSection

```

and then i run before starting X:

```

plucky$ sudo js2mouse
Number of  axes : 6
Number of  buttons : 13
Driver version : 131328
Joystick name : Honey Bee           AIRFLO

```

and my /var/log/Xorg.0.log has:
```

(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "Protocol" "PS/2"
(**) j2m: Device: "/dev/js2m_fifo"
(**) j2m: Protocol: "PS/2"
(**) Option "SendCoreEvents"
(**) j2m: always reports core events
(**) Option "Device" "/dev/js2m_fifo"
(EE) xf86OpenSerial: Cannot open device /dev/js2m_fifo
        No such file or directory.
(EE) j2m: cannot open input device
(EE) PreInit failed for input device "j2m"
(II) UnloadModule: "mouse"
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"

```

here's the info I have about the device that the js2mouse creates, i have no clue how to get more info here:
```
(0) ~
plucky$ l /dev/j2m_fifo 
prw-r--r-- 1 root root 0 Dec 30 04:00 /dev/j2m_fifo

(0) ~
plucky$ file /dev/j2m_fifo 
/dev/j2m_fifo: fifo (named pipe)
```

So, what did i screwed up?

---

