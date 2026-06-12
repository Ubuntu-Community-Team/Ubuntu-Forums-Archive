---
title: "Urban Terror"
date: 2010-04-17
forum: Gaming &amp; Leisure
---

### Post by jakeeee on 2010-04-17
Soo.
A couple questions. :)

Can I hook up a game controller to play Urban terror?
I'm used to playing 360 so like the keyboard controls confuse me a bit xD

Is there voice chat?
If so how do I do it?

And is anyone else playing it on a netbook? lol
I'm playing it on my eeepc(:

---

### Post by jkxx on 2010-04-18
You could try plugging in your 360 controller to see if it gets picked up. All my wine games can see the two controllers I have plugged in - including my fav PS2 one for racing games.

I'm not sure about native games though, usually depends on what the devs used to make the game. If it's based on SDL it'll probably see the controller.

Good luck :)

---

### Post by SVEN1 on 2010-04-19
There was one player a while back that had a custom fitted hand controller set up, don't recall what it was but, it was expensive.
It made him too good.

---

### Post by robozman on 2010-06-18
I am playing on a netbook.  If you use the game controller to mouse+keyboard programs it will trap the mouse in the corner.  I haven't figured it out.  Using QJoyPad.  Using AAO (Acer Aspire One)

---

### Post by ~Aquatic on 2010-08-05
> **robozman said:**
> I am playing on a netbook.  If you use the game controller to mouse+keyboard programs it will trap the mouse in the corner.  I haven't figured it out.  Using QJoyPad.  Using AAO (Acer Aspire One)

It traps in the corner for me too! _[Here]("http://www.gentoo-wiki.info/HOWTO_Joystick_as_Mouse#Calibrate_Joystick")_ it says how to fix this problem but I don't really get it.

> **  [SIZE=3]Cursor hung to top-left corner [/SIZE]**

This  glitch causes the joystick/gamepad buttons to not work and the mouse  cursor to be moved to the top-left corner of the display.
Apart  from the non-functional gamepad, you can also verify that you are  affected by this bug because your Xorg.0.log file will contain lines  like these:
```
(II) evdev brain: Rescanning devices (1).
(**) Option "SendCoreEvents"
(**) usbmouse-usb-0000:00:1d.0-2/input0: always reports core events
(II) usbmouse-usb-0000:00:1d.0-2/input0: Found 6 absolute axes.
(II) usbmouse-usb-0000:00:1d.0-2/input0: Configuring as pointer.
(II) usbmouse-usb-0000:00:1d.0-2/input0: Found 0 relative axes.
(II) usbmouse-usb-0000:00:1d.0-2/input0: Configuring as pointer.
(II) usbmouse-usb-0000:00:1d.0-2/input0: Found 42 mouse buttons
(**) usbmouse-usb-0000:00:1d.0-2/input0: Configuring 6 absolute axes.
(II) usbmouse-usb-0000:00:1d.0-2/input0: Checking button DIGI_STYLUS (330)
(II) usbmouse-usb-0000:00:1d.0-2/input0: Checking bit 330
(EE) usbmouse-usb-0000:00:1d.0-2/input0: AbsoluteTouch: 'DIGI_Touch' does not exist.
(**) usbmouse-usb-0000:00:1d.0-2/input0: Configuring in Absolute mode.
(**) usbmouse-usb-0000:00:1d.0-2/input0: AbsoluteScreen: 0.
(**) usbmouse-usb-0000:00:1d.0-2/input0: Configuring 2 relative axes.
(II) usbmouse-usb-0000:00:1d.0-2/input0: Configured 42 mouse buttons

```42 buttons for my usb mouse?! I don't have any USB mouse plugged...the joystick has been (incorrectly) seen as a mouse.
To fix this problem, simply tighten your Device option in the InputDevice section for your USB mouse. For example, use a line like this:
  ```
Option "Device" "/dev/input/by-id/usb-Logitech_Optical_USB_Mouse-event-mouse"
```

---

### Post by ~Aquatic on 2010-08-06
"Bump"

---

### Post by def670 on 2011-01-11
im running on an AAO 752 - almost a laptop.  lol.

trying to get a logitech dual action controller going, but i dont see anywhere to enable it in the Urban Terror control setup.  is there a specific joystick enable radio button somewhere?
thanks
def

---

### Post by robozman on 2011-04-20
Sorry to bump and old thread but I got a game controller to work with Digital Paint, Paintball 2 and Tremulous because that game allows you to use buttons at look up and look down and left and right.  I don't know if Urban Terror has that because I don't play anymore (Minecraft Multiplayer/Tremulous) but you can try that.  If you bind let's say the arrow keys to look (thats how I play Trem on my NETBOOK) and then you bind the aiming stick to control the arrow keys then since It's not a mouse you won't have the game incorrectly registering the controller I think.  I think the mouse=joystick thing probably with never work, on the other hand the joystick=keyboard=aiming might just work.
Sorry if you can't see photo, my netbook screen is pretty low res and it took me a while before I saw the delay option on the take screenshot.

---

