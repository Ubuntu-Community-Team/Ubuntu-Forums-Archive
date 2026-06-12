---
title: "Logitech Wingman - analog not working"
date: 2008-03-07
forum: Gaming &amp; Leisure
---

### Post by forrestcupp on 2008-03-07
I hope this is in the right section.

I have a Logitech Wingman Action USB gamepad that has a 4 direction pad and an analog stick.  The gamepad works perfectly except that the analog stick only gives the 4 digital readouts, which means no smooth movement.  The X and Y axes can only read -1, 0, or 1.

Does anyone have any ideas on how I can get smooth movement with this?

---

### Post by forrestcupp on 2008-03-08
No one knows anything about gamepads?

---

### Post by themacmeister on 2008-03-18
You need to install the joystick package - it is called 'joystick2005_xxxxxx' or something stupid in Synaptic, but once installed, you should have a module called analog.

type in jstest /dev/input/js0, and move your analog sticks around... if it doesn't register, control-c or control-z out, type sudo /usr/sbin/modprobe joydev

sudo /usr/sbin/modprobe analog

try jstest again, you should now have it working!!!

to make it automatic, you need to create startup scripts in /etc/rc3.d

I made mine called S97joystick, and it also recreated the symlink from /dev/input/js0 to /dev/js0 (to support older games).

good luck!

---

