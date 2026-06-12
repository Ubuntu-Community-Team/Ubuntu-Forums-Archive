---
title: "Mouse sensitivity"
date: 2006-09-05
forum: Desktop Environments
---

### Post by zultan on 2006-09-05
I have a problem with configuring mouse sensitivity.
The gui tool in gnome doesnt change the sensitivity/acceleration, and i havent been able to find any xorg.conf variables that will work. 

The mouse is a Razor Diamondback (USB). 

Are there any tools/drivers i can install to fix this?

---

### Post by magomago on 2006-09-09
in the same positio nas you;.  i got a razer pro v1.6 and its incredibly sensitive....anyone know how to fix it?

---

### Post by wilsonisme on 2006-09-24
The buttons on the left side of the mouse adjust the internal firmware sensitivy a lot. Play with them

---

### Post by qrm on 2006-11-12
they dont do it for me :/ but sometimes after fresh istall i get the sensitivity right and sometimes the sensitivity option in setting doesnt change anything

---

### Post by JimboJoe on 2006-11-13
Same here. It seems that sensitivity can be configured, but is higher on "clickable" elements, like buttons, menus, etc.
Is that the same for you?

---

### Post by qrm on 2006-11-13
havent noticed, I remember that it has been with 2 installs on the same machine and I couldnt find a solution. Im afraid that the high dpi (1600) affects the sensitivity (higher dpi - feels quicker/faster), interferes somehow and you should try to configure it from xorg.conf. atm I have my sensitivity set from the GUI and resolution (dpi) set from xorg.conf. You might try lowering the resolution. This is how my mouse part of xorg.conf looks like:

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
Option "Resolution" "1600"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
Option "Emulate3Buttons" "true"
EndSection
```

btw I have all my buttons working with these settings :D

---

### Post by JimboJoe on 2006-11-13
don't you end up with the buttons on the right behaving like the mouse wheel? This is where I am now. And as I'm left-handed, I would like to have the Backward/Forward feature on those buttons...

---

### Post by qrm on 2006-11-13
yes they act as the mouse wheel and in nautilus too. If you want to change it you should try modifying ButtonMapping and ZAxismapping, but I dont know how, I just got this section from somewhere in this forum

---

### Post by JimboJoe on 2006-11-14
that seems to be more subtle, as when using xev, those buttons ARE the same as the wheel button. I will try evdev driver soon.

EDIT : Tried evdev. It autodetects 9 buttons (logical), but still, right buttons are the same as wheel buttons... ;-(
Any idea?

---

