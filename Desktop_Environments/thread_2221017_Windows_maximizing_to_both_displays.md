---
title: "Windows maximizing to both displays"
date: 2014-04-30
forum: Desktop Environments
---

### Post by Zellus on 2014-04-30
Hi

    I've a problem with my Ubuntu 1404. I installed it some time ago, and used to use default graphic card driver. But it was working teribbly slow, even on desktop, so I decided to risk and install nvidia drivers. It worked :) I mean now it doesn't blink, moving windows don't have "tails". 
    The only problem that started now, is when I try to maximize a window, it does... to both screens. It is completly unusable, especially as far as both of them have different resolution. I have Dell l502x laptop with nvidia gt540m graphic card. I use built-in monitor+external 24 inch, hdmi connected. Another, related I think, problem is that when I restart, both screens are in the same place, means that the smaller one is a a repeated part of the bigger one and every time I have to change it in Displays.
    I tried to set it in compiz, but it doesn't work as I thought if will ( see Attachments).
    My /etc/X11/xorg.conf file:
```
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
EndSection


```

Hope you can help :) 
Thanks in advance.

---

### Post by Zellus on 2014-05-01
Today it fixed itself, no idea why. Anyway, not important now :)

---

