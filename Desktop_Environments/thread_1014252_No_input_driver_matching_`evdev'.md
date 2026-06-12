---
title: "No input driver matching `evdev'"
date: 2008-12-17
forum: Desktop Environments
---

### Post by w14 on 2008-12-17
I'm trying to get the touchscreen working on my Flybook using PlOP's penmountlpc driver, with partial success. 

I have made some progress by adding an fdi file into /etc/hal/fdi/policy as follows:

<?xml version="1.0" encoding="utf-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
    <device>
      <match key="info.capabilities" contains="input.mouse">
        <match key="info.product" contains="TouchScreen">
            <merge key="input.x11_driver" type="string">plpevtch</merge>
            <merge key="input.X11_options.Device" type="string">/dev/input/event9</merge>
            <merge key="input.x11_options.Calibrate" type="string">True</merge>
            <merge key="input.x11_options.MinX" type="int">50</merge>
            <merge key="input.x11_options.MaxX" type="int">900</merge>
            <merge key="input.x11_options.MinY" type="int">50</merge>
            <merge key="input.x11_options.MaxY" type="int">900</merge>
        </match>
      </match>
     </device>
</deviceinfo>

This works - lshal shows the correct driver, and the touchscreen works. However, when the touchscreen driver is loaded, the normal mouse and keyboard do not work.

Here is my xorg logfile when the correct touchscreen driver is NOT loaded. In this case evdev tries and fails to run the touchscreen:

(II) config/hal: Adding input device PenmountLPC TouchScreen
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) PenmountLPC TouchScreen: always reports core events
(**) PenmountLPC TouchScreen: Device: "/dev/input/event9"
(II) PenmountLPC TouchScreen: Found x and y absolute axes
(II) PenmountLPC TouchScreen: Found absolute touchpad
(WW) PenmountLPC TouchScreen: Don't know how to use device
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "PenmountLPC TouchScreen"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device PS/2 Generic Mouse
(**) PS/2 Generic Mouse: always reports core events
(**) PS/2 Generic Mouse: Device: "/dev/input/event8"
(II) PS/2 Generic Mouse: Found x and y relative axes
(II) PS/2 Generic Mouse: Found 3 mouse buttons
(II) PS/2 Generic Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
(**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) AT Translated Set 2 keyboard: xkb_layout: "gb"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) AT Translated Set 2 keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) Video Bus: xkb_layout: "gb"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Video Bus: xkb_options: "lv3:ralt_switch"

And here is the log when the touchscreen driver is loaded correctly:

(II) config/hal: Adding input device PenmountLPC TouchScreen
(II) LoadModule: "plpevtch"

(II) Loading /usr/lib/xorg/modules/input//plpevtch_drv.so
(II) Module plpevtch: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) plpevtch brain: Rescanning devices (1).
(**) PenmountLPC TouchScreen-: always reports core events
(II) PenmountLPC TouchScreen-: Found 2 absolute axes.
(II) PenmountLPC TouchScreen-: Configuring as pointer.
(II) PenmountLPC TouchScreen-: plop touch
(II) PenmountLPC TouchScreen-: Found 75 mouse buttons
(**) PenmountLPC TouchScreen-: Configuring 2 absolute axes.
(**) Option "Calibrate" "True"
(**) PenmountLPC TouchScreen-: calibration mode active.
(**) PenmountLPC TouchScreen-: Configuring in Absolute mode.
(**) PenmountLPC TouchScreen-: AbsoluteScreen: 0.
(II) PenmountLPC TouchScreen-: Configured 75 mouse buttons
(II) XINPUT: Adding extended input device "PenmountLPC TouchScreen-" (type: MOUSE)
(**) PenmountLPC TouchScreen-: 2 valuators.
(**) evdev_btn.c (196): Registering 75 buttons.
(II) PenmountLPC TouchScreen-: Init
(II) PenmountLPC TouchScreen-: On
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(EE) No input driver matching `evdev'
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device PS/2 Generic Mouse
(II) LoadModule: "evdev"

(II) Reloading /usr/lib/xorg/modules/input//evdev_drv.so
(EE) No input driver matching `evdev'
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"

(II) Reloading /usr/lib/xorg/modules/input//evdev_drv.so
(EE) No input driver matching `evdev'
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Video Bus
(II) LoadModule: "evdev"

(II) Reloading /usr/lib/xorg/modules/input//evdev_drv.so
(EE) No input driver matching `evdev'
(EE) config/hal: NewInputDeviceRequest failed

Clearly the evdev module does exist.

Can anyone give me any clues where to go with this next?

Many thanks.

---

### Post by maddis on 2010-01-25
I seem to be having the same problem. Too bad no one has found any solution for it. I'll keep looking.

I've noticed that if I turn Calibrate to 'False' the touchscreen isn't working anymore, but the keyboard and mouse start working again!

---

