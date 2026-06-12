---
title: "Problems with PS2 Mouse (Inspiron 8100)"
date: 2005-10-02
forum: Desktop Environments
---

### Post by eantoranz on 2005-10-02
I'm having mouse problems since I installed Kubuntu.

This is a dell inspiron 8100 with a Genius Netscroll mouse.

The mouse buttons normally don't react to clicks... but I have noticed that I can "click" by dragging a little, releasing and moving.... quite weird, right? Something that happens sometimes is that the pointer dissapears... but I can make it come back by moving with the touchpad (buttons fail there too. The same trick applies).

This is the dmess error:
```

psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.

```

This is my pointer section form xorg.conf:
```

Section "InputDevice"

# Identifier and driver

    Identifier  "Mouse1"
    Driver      "mouse"
    Option "Protocol"    "NetScrollPS/2"
#    Option "Device"      "/dev/mouse"
        Option "Device" "/dev/psaux"

# Mouse-speed setting for PS/2 mouse.

#    Option "Resolution"        "256"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"  "Xqueue"
        Option "Protocol" "PS2"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"  "9600"
#    Option "SampleRate"        "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection

```

I added the Protocol option to give it a try.... but it didn't work. I still have the same problem.

Any ideas? :confused:

---

### Post by ngms27 on 2005-10-02
As I understand it the 2.6.x Kernels are bugged.

It will work with a 2.4.x kernel

I haven't found a fix myself yet.

---

### Post by mlomker on 2005-10-02
I spent a little time Googling and couldn't come up with anything.  I did run across the [Yahoo Group]("http://groups.yahoo.com/group/linux-dell-laptops").  Perhaps that'll be a good resource if you didn't know about it.

---

