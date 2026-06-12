---
title: "How to set paronamic 1200x800 resolution on laptop?"
date: 2009-06-15
forum: General Help
---

### Post by arkadiuszmakarenko on 2009-06-15
I`ve installed Ubuntu some time ago, and during installation my resolution was set properly. Unfortunately yesterday I connected tv ,and i tried set mirror monitors, so after that I can`t set proper resolution on my laptop monitor. It`s 1024x768, In display there is no 1200x800 option. Laptop has Intel graphic card. 

It`s my xorg.config:
Section "Monitor"
Identifier "Configured Monitor"

EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection "Display"
Virtual 2048 768

EndSubSection
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

---

### Post by Bachstelze on 2009-06-15
Just delete everything in your xorg.conf (do not delete the file itself, though), and everything should be autodetected normally next time you start X.

---

### Post by arkadiuszmakarenko on 2009-06-15
> **HymnToLife said:**
> Just delete everything in your xorg.conf (do not delete the file itself, though), and everything should be autodetected normally next time you start X.

It worked! 1200x800 was aviliable in display! Thanx!

Simple solutions are allways the best! :)

---

