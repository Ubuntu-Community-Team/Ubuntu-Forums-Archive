---
title: "Beryl Manager giving white screen"
date: 2007-05-28
forum: Desktop Effects &amp; Customization
---

### Post by rightNow on 2007-05-28
Newly installed Feisty on Dell GX110 with Intel(r) 82810E Graphics Controller integrated with motherboard.  Installed Beryl with: "sudo aptitude install beryl beryl-manager emerald-themes"

"glxinfo | grep rendering"
gives: "direct rendering: No"

"glxinfo | egrep "glx (vendor|version)""
gives: "server glx vendor string: SGI
            server glx version string: 1.2
            client glx vendor string: SGI
            client glx version string: 1.4"

My understanding is that direct rendering should be enabled but I'm not sure how to do this or if it is possible.  Thanks for the help.

---

### Post by smylie on 2007-05-29
Add the line
```
        Load    "dri"
```

to the module section of your /etc/X11/xorg.conf file.

If it's already there, (and it probably is), check /var/log/Xorg.0.log  for errors regarding dri.

```
grep -i dri /var/log/Xorg.0.log
```

That should hopefully give you a better idea of why it's not being enabled.

---

### Post by rightNow on 2007-05-30
"Load      "dri"" 
Does exist in the module section of /ect/X11/xorg.conf

"grep -i dri /var/log/Xorg.0.log"
gives
  X.Org Video Driver: 1.1
        X.Org XInput driver : 0.7
        ABI class: X.Org Video Driver, version 1.1
        ABI class: X.Org Video Driver, version 1.1
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
(II) Loading extension XFree86-DRI
        ABI class: X.Org Video Driver, version 1.1
        ABI class: X.Org Video Driver, version 1.1
(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
        ABI class: X.Org Video Driver, version 1.1
        ABI class: X.Org Video Driver, version 1.1
(**) I810(0): DRI is disabled because it runs only at 16-bit depth.
        ABI class: X.Org Video Driver, version 1.1
(II) I810(0): Not using driver mode "1280x1024" (width too large for virtual size)
(**) I810(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) I810(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) I810(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(**) I810(0): *Driver mode "640x480": 35.0 MHz, 42.9 kHz, 84.6 Hz
(**) I810(0):  Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 84.9 Hz
(**) I810(0):  Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) I810(0):  Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) I810(0):  Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) I810(0):  Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) I810(0):  Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
        ABI class: X.Org Video Driver, version 1.1
(EE) AIGLX: Screen 0 is not DRI capable

Thanks

---

### Post by rightNow on 2007-05-30
Fixed using: Incorrect DefaultDepth section from [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Thanks for the help!

---

### Post by rightNow on 2007-05-30
The Beryl Manager is no longer giving a white screen and is functional but it is very choppy and laggy, any ideas?

Thanks.

---

