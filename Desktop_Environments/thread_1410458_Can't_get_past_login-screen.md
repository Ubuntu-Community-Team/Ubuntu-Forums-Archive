---
title: "Can't get past login-screen"
date: 2010-02-18
forum: Desktop Environments
---

### Post by Spherical on 2010-02-18
I had no issues what-so-ever today to (auto) log on to my XBMC box. All was perfectly fine.
Until a disk-scan.

Now, I have to enter my password, but if I do, I just hit back to the login-screen.
This goes for all GUI's, KDE, Gnome, XBMC, XFCE, doesn't matter what I choose, I just get thrown back to the login after a short black screen.

The xorg error-log does not show anything worth mentioning (1 warning for the driver "void" not existing)

Anyone has any clue?

I'm running Kubuntu 8.10, because it works for my touchscreen, combined with XBMC.
Not much special to say...

---

### Post by Spherical on 2010-02-18
On another note... while on touchscreens.
Anyone have any experience with touchscreen (evdev/evtouch) under 9.10?
I'd like to upgrade, but can't be sure it works (although this current installation fails too huh)

If someone can assure me and tell me how to get my touchscreen working, I'm gonna reinstall, but I prefer not too

---

### Post by Zorael on 2010-02-19
It sounds like X is crashing.

Sometimes the gdm/kdm log will contain error messages that Xorg.0.log doesn't catch. So when using kdm, take a look at **/var/log/kdm.log**.

I think gdm has its own subdirectory in **/var/** with a bunch of files.

---

### Post by Spherical on 2010-02-19
This is all kdm.log reports:
```
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

```

Xorg.0.log reports:
```
(**) EVTouch TouchScreen: always reports core events
(**) Option "Device" "/dev/input/event8"
(EE) EVTouch TouchScreen: Unable to grab device (Device or resource busy).
(II) config/hal: Adding input device Logitech USB-PS/2 Optical Mouse
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(**) Option "xkb_variant" "euro"
(**) AT Translated Set 2 keyboard: xkb_variant: "euro"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) AT Translated Set 2 keyboard: xkb_options: "lv3:ralt_switch"

```

That Error is my touchscreen, it's been there forever, never caused any problems.

---

### Post by Zorael on 2010-02-19
Curious.

If you create a new user (from a recovery session or similar), does it happen for him as well?

---

### Post by Spherical on 2010-02-19
Yes, exactly the same happens.
It's really odd.

I'm thinking I'll just do a reinstall... I'm afraid there's not enough data to repair this issue.

---

### Post by kio_http on 2010-02-19
Try this

```
sudo dpkg --reconfigure xserver-xorg
```

If that fails then

```
sudo apt-get purge xserver-xorg
```
then
```
sudo apt-get install xserver-xorg
```

---

### Post by Spherical on 2010-02-19
Tried that already.

Sadly, it only screwed my touchscreen-configuration, but nothing else.

I've resorted to the last option:
Format
Install Kubuntu 9.10

It's working all now, I'm just hoping it stays that way ;)

---

### Post by Spherical on 2010-02-19
Ok, all is working the way I want it in Kubuntu 9.10

I've very "cleanly" installed my touchscreen and dualscreen setup the way I have had it working since Kubuntu 7.04, but who cares, it works.

This, sadly, makes the issue I started this thread with not yet solved. Although I hope nobody will encounter something like this

---

