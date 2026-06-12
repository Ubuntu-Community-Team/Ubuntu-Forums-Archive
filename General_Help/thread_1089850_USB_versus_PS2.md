---
title: "USB versus PS2"
date: 2009-03-07
forum: General Help
---

### Post by hatrack on 2009-03-07
Hi All !

I have an odd problem, not directly connected to Ubuntu, except that it applies to a system running "Hardy".

I have two computers, networked together. One (an old Pentium 3) is running Win2k and is used because it is compatible with my now-old graphics processing s/w and scanners. The other (a newer machine) is running Hardy.

To save space on my desk, I have purchased a switch which allows two computers to share one monitor and use the same keyboard and mouse, switching between the two running computers via a hot-key combination. This switch unit, however, is designed to work with PS2 devices. This is OK in the case of the old machine (running Win2k) but my newer computer (running Hardy) has USB ports for keyboard and mouse. I have tried the simple option of fitting PS2-to-USB changers to the cables for keyboard and mouse and then simply plugging the cables into the USB ports but (not surprisingly) this doesn't work.I think that it is probably necessary to modify xorg.conf but I am not sure of the changes that I should make. Naturally, I am concerned that I can lock myself out of the computer if I configure things wrongly, so I thought it best to seek advice from others.

The relevant section of my xorg.conf file is --

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

I will be most grateful for any advice that anyone can offer and apologise for posting a message that is slightly "off-topic" for this forum.

Best regards to all ...

---

### Post by cariboo on 2009-03-07
The only thing I can suggest, is to exchange the device for one that uses usb connections, and use the usb ports on you computer running W2K.

Jim

---

### Post by hatrack on 2009-03-07
Hi Jim !

Thank you for your quick reply. 

I had a feeling that it might be the case that the switch unit is only "half-compatible". It comes with PS2 connectors on both sets of cables for mice and keyboards and specifically says in the literature that it is designed for "PS2 machines". That I understood when I bought it.

Unfortunately, there is only one form of this switch unit available (the one that I have) and ... even if I could swap this particular example, I would then have the opposite problem ... my old computer only has PS2 connectors !

Whilst it is irritating, this problem certainly isn't "the end of the world" so far as usage is concerned. I have my old Pentium 3 computer plugged in correctly, using the PS2 connectors plus its sVGA output. For my newer computer, only the sVGA connection is made and a keyboard and mouse are plugged into the appropriate USB sockets. The old computer thus becomes the "Master" in this set up and must always be running. I can hot switch graphics displays from the two computers, via the keyboard which has PS2 connectors but, when entering data, etc. from the newer machine, this goes in via the seperate keyboard/mouse. So, I must have two sets of input devices on my desktop but need only one display monitor.

A big advantage to me but ... not as elegant as I would have liked and hoped that I could achieve when I started all this !

Many thanks again and best regards ...
Eric

---

