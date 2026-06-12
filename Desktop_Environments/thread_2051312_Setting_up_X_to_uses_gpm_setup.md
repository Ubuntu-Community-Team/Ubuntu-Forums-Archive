---
title: "Setting up X to uses gpm setup?"
date: 2012-09-01
forum: Desktop Environments
---

### Post by Pal Csanyi on 2012-09-01
Hi,

I have just installed Ubuntu 12.04.1 LTS and used Unity.

After a while I changed Desktop environment to Window Maker (my favorite
environment) and I must to setup manually keyboard layouts on console
(no graphical environment) and X Window.

I must purge unity and related packages so I now get X by running
startx. It's good for me.

But I haven't success so far in the mice setup.

On console I'm using the 'gpm' and it works fine.

When I used Debian system I have a setup there that works and I used gpm
settings for mice in X environment too.

The gpm settings are:
device=/dev/input/mice
responsiveness=
repeat_type=ms3
type=exps2
append='-B 32145'
sample_rate=

in the /etc/gpm.conf file.

As one can see my mice have setup for the left hand.

On Debian system this setup just works so I get the left hended mice in
X environment too, but on Ubuntu this isn't the case.

In Xorg.0.log I have following lines regarding of mice:

[   581.864] (II) config/udev: Adding input device ImPS/2 Generic Wheel
Mouse (/dev/input/event5) 
[   581.864] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev
pointer catchall" 
[   581.865] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel
Mouse' 
[   581.865] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so 
[   581.865] (**) ImPS/2 Generic Wheel Mouse: always reports core events 
[   581.865] (**) evdev: ImPS/2 Generic Wheel Mouse: Device:
"/dev/input/event5" 
[   581.865] (--) evdev: ImPS/2 Generic Wheel Mouse: Vendor 0x2 Product
0x5 
[   581.865] (--) evdev: ImPS/2 Generic Wheel Mouse: Found 3 mouse
buttons 
[   581.865] (--) evdev: ImPS/2 Generic Wheel Mouse: Found scroll
wheel(s) 
[   581.865] (--) evdev: ImPS/2 Generic Wheel Mouse: Found relative axes 
[   581.865] (--) evdev: ImPS/2 Generic Wheel Mouse: Found x and y
relative axes 
[   581.865] (II) evdev: ImPS/2 Generic Wheel Mouse: Configuring as
mouse 
[   581.865] (II) evdev: ImPS/2 Generic Wheel Mouse: Adding scrollwheel
support 
[   581.865] (**) evdev: ImPS/2 Generic Wheel Mouse: YAxisMapping:
buttons 4 and 5 
[   581.865] (**) evdev: ImPS/2 Generic Wheel Mouse: EmulateWheelButton:
4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   581.865] (**) Option "config_info"
"udev:/sys/devices/platform/i8042/serio1/input/input5/event5" 
[   581.865] (II) XINPUT: Adding extended input device "ImPS/2 Generic
Wheel Mouse" (type: MOUSE, id 10)
[   581.865] (II) evdev: ImPS/2 Generic Wheel Mouse: initialized for
relative axes. 
[   581.865] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping
acceleration scheme 1 
[   581.865] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration
profile 0 
[   581.865] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration
factor: 2.000 
[   581.865] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration
threshold: 4 
[   581.865] (II) config/udev: Adding input device ImPS/2 Generic Wheel
Mouse (/dev/input/mouse0) 
[   581.865] (II) No input driver specified, ignoring this device.
[   581.865] (II) This device may have been added with another device file.
[   581.866] (II) config/udev: Adding input device PC Speaker
(/dev/input/event3) 
[   581.866] (II) No input driver specified, ignoring this device.
[   581.866] (II) This device may have been added with another device
file. 


So I don't understand which setup has my mice in X?
Why can't I get in X environment the gpm setup of my mice?

-- 
Regards from Pal

---

### Post by Pal Csanyi on 2012-09-09
The question is wrong because no one can setup X to uses the gpm
configuration. 

I forgot that that on Debian I setup my mice to be lefthanded with the
following line in ~/.xinit file:
xmodmap -e "pointer = 3 2 1 4 5"

and after that line is the line
wmaker

that starts Window Maker window manager.

---

