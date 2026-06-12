---
title: "mouse isnt working"
date: 2005-04-10
forum: Desktop Environments
---

### Post by trike on 2005-04-10
I have installed hedgehog onto a spare pc so i could take a look and see what its like the problem is that the mouse wont work. Its a serial type mouse as the pc is fairly old.
i think the keybord is working as i clicked ctrl+alt+del and it went back to logon
i have disabled usb in the hope that it might make it work with no luck.
Any ideas?
TIA

---

### Post by localzuk on 2005-04-10
[QUOTE=trike]I have installed hedgehog onto a spare pc so i could take a look and see what its like the problem is that the mouse wont work. Its a serial type mouse as the pc is fairly old.
i think the keybord is working as i clicked ctrl+alt+del and it went back to logon
i have disabled usb in the hope that it might make it work with no luck.
Any ideas?
TIA[/QUOTE]
 Have a look at altering your /etc/X11/xorg.conf with information from these pages:

[http://www.x.org/X11R6.8.2/doc/xorg.conf.5.html#sect6](http://www.x.org/X11R6.8.2/doc/xorg.conf.5.html#sect6)
[http://www.x.org/X11R6.8.2/doc/mouse.html](http://www.x.org/X11R6.8.2/doc/mouse.html)

---

### Post by heimo on 2005-04-10
This is guesswork... But you should have something like this in /etc/X11/xorg.conf

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/ttyS0"
        Option          "Protocol"              "Logitech"
        Option          "Emulate3Buttons"       "true"
EndSection
```

This was not taken from working system (I'm using PS2-mouse). You can also try "Microsoft" instead of Logitech and you can try /dev/ttyS1 instead of /dev/ttyS0. One way to find out which serial port your mouse is attached is to cat the port - like this:
```
sudo cat /dev/ttyS0

```
And then move your mouse a little bit. You should see garbage on screen. Then press ctrl + C to exit. If you didn't see anything, it's wrong port. Note that the S character is uppercase S and **not** lowercase s.

---

