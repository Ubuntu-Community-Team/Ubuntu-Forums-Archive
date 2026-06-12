---
title: "control mouse with joystick"
date: 2008-11-17
forum: Gaming &amp; Leisure
---

### Post by oddish2211 on 2008-11-17
i've just succesfully installed World of Warcraft with wine, great but i want to use my Saitek pro Gamer Command Unit with it.
in windows i used an tool to map a few keyboard keys to some keys on my joystick and use the analog stick as a mouse. (i mapped the analog stick to a set of commands like "analog stick right  =hold mouse button and move right")

is there an tool to map joystick buttons/movements in ubuntu? or maybe an windows tool that works within wine?

---

### Post by oddish2211 on 2008-11-18
is there such a tool?

---

### Post by crazyfuturamanoob on 2008-11-18
Joy2Key can convert joystick/gamepad events to key presses, but not mouse movement.

For mouse movement, check box System->Settings->Keyboard->Mouse buttons->Enable mouse movement by keyboard.

Then, set your analog stick as numpad arrows with joy2key.


This should work. I have done it before with my self-soldered xbox-controller.

Also, look for js2mouse. They are surely better than my solution, although it's hard to install.

---

### Post by oddish2211 on 2008-11-18
if i install joy2key, and then start the program from the terminal, i get the message;
```
Error opening /dev/js0!
Are you sure you have joystick support in your kernel?
```

i'm using ubuntu 8.10

---

### Post by grossaffe on 2008-11-19
qjoypad is a program that can do it, although It didn't do very well when I tested it in a gaming environment (Wolfenstein: ET).  Its also not updated anymore and has a few bugs

---

### Post by crazyfuturamanoob on 2008-11-19
> **oddish2211 said:**
> if i install joy2key, and then start the program from the terminal, i get the message;
```
Error opening /dev/js0!
Are you sure you have joystick support in your kernel?
```

i'm using ubuntu 8.10

Try to re-plug your joystick/gamepad.

---

### Post by oddish2211 on 2008-11-19
i re-connected my joystick, same problem.

and for qjoypad, if i download de *.deb file and install it, i get the following message;
Error: Dependency is not satifiable: libqt3c102-mt

i've tried installing it with apt-get in the terminal and then i get the message that the package is missing/obsolete or is only available through an other source.
but there is an package to replace it;
libqt3-mt

but when i install this package and then install qjoypad from the *.deb file
i get the same error.

---

### Post by grossaffe on 2008-11-19
> **oddish2211 said:**
> i re-connected my joystick, same problem.

and for qjoypad, if i download de *.deb file and install it, i get the following message;
Error: Dependency is not satifiable: libqt3c102-mt

i've tried installing it with apt-get in the terminal and then i get the message that the package is missing/obsolete or is only available through an other source.
but there is an package to replace it;
libqt3-mt

but when i install this package and then install qjoypad from the *.deb file
i get the same error.

I think I had problems installing it at first too.  Don't remember what I did to fix it, but you should search around to see if you can find a solution.

---

### Post by crazyfuturamanoob on 2008-11-19
> **grossaffe said:**
> I think I had problems installing it at first too.  Don't remember what I did to fix it, but you should search around to see if you can find a solution.

I think the solution for that was to use an older version.. not really sure about this.

---

### Post by oddish2211 on 2008-11-21
it works! , i installed qjoypad from the *.rpm file and i converted it with alien.

thanks!

---

