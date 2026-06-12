---
title: "Original Xbox controller help, ubuntu 10.10"
date: 2010-11-08
forum: Gaming &amp; Leisure
---

### Post by skeetlez on 2010-11-08
I made my old xbox controller (which worked fine) into a usb gaming pad and it works fine, but it seems the triggers are only reconized as analog and i need them to register as buttons or something. Im using mupen64plus on 10.10 64bit.

the problem is the triggers will activate, but never turn off

thanks in advance!:)

---

### Post by tahirih on 2011-01-14
I'm having the exact same problem! Somebody answer us cuz I'm stumped lol

---

### Post by JRBASTIEN on 2011-01-16
We don't get a lot of answers for these old XBox controllers.  Mine is still unanswered too ([http://ubuntuforums.org/showthread.php?t=1667997&highlight=xbox](http://ubuntuforums.org/showthread.php?t=1667997&highlight=xbox)).

So let's put our efforts together and may be we can solved our problems.

Have you try a remapping utility?  I'm not sure they will allow you to remap the triggers to the buttons on the same device but it is worth looking.

See those 2 links:

[http://ubuntuforums.org/showthread.php?t=761044](http://ubuntuforums.org/showthread.php?t=761044)
[http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/)

---

### Post by JRBASTIEN on 2011-01-17
I think I found what you are looking for.  This thread here shows you how to do it:

[http://ubuntuforums.org/showthread.php?t=825464&highlight=original+xbox+controllers](http://ubuntuforums.org/showthread.php?t=825464&highlight=original+xbox+controllers)

Supported Controllers
Original Xbox controllers through USB (with a cable modification)
Xbox 360 USB Controllers
Xbox 360 Wireless Controllers through the Wireless USB Adapter
Xbox 360 USB Guitar
Some third party controllers may work as well (MadCatz) and they are probably already available. To check support for a particular controller, review the file xboxdrv.cpp and look for the line XPadDevice xpad_devices. You may even be able to add in support for your particular controller by adding the hardware identifiers into xboxdrv.cpp and recompiling the driver (the README talks about this further in depth).

Features
Executes in user space on top of libusb. This means that you do not have to recompile the kernel
Provides a joystick device (/dev/input/js0)
Allows remapping of the buttons and axises
**[COLOR="Red"]Support of the analog triggers (LT, RT) along with reconfiguration into a digital mode (they function just as buttons)[/COLOR]**
Change the LED status of the ring of light on the 360 pads
Many other features! See the author's webpage listed in the links below

---

