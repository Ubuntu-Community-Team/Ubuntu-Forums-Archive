---
title: "xorg and evdev"
date: 2005-08-09
forum: Desktop Environments
---

### Post by Capsad on 2005-08-09
Hi,
I just bought a new mouse - Logitech MX510 and wanted to install it like here [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=46](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=46)
I read here [http://ubuntuforums.org/archive/index.php/t-31813.html](http://ubuntuforums.org/archive/index.php/t-31813.html) that
Driver      "evdev"
is wrong and that there has to be
Option       "Protocol"         "evdev" instead

now the mouse part of my xorg.conf looks like this:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "evdev"
EndSection

I also have the kernel module evdev loaded (self-made kernel, 2.6.12-4):
$ lsmod |grep evdev
evdev                   7296  0

But when I startx with this xorg.conf, it doesn't start and I get this error in /var/log/Xorg.0.log:

(**) Option "Protocol" "evdev"
(**) Configured Mouse: Protocol: evdev
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(==) Configured Mouse: Buttons: 3
(**) Configured Mouse: Protocol: evdev
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(==) Configured Mouse: Buttons: 3
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(EE) Configured Mouse: cannot register with evdev brain
(EE) Configured Mouse: cannot register with evdev brain
No core pointer

Fatal server error:
failed to initialize core devices


when I replace "evdev" with "ImPS/2" it starts, but I want to use evdev. I use ubuntu hoary with the newest updates, can anybody help me?
thanks in advance,
Capsad

---

