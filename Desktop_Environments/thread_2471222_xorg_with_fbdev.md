---
title: "xorg with fbdev"
date: 2022-01-24
forum: Desktop Environments
---

### Post by kyliny on 2022-01-24
I am a new bie.
I am trying to use x11 with fbdev display driver. And now startx was runinning without fatal errors. Also I traced fbdev.so and fbdevHW.so with sources, there are no errors at all. Here is what I did with steps:
```
1. startx xeyes ---- screen show black screen
2. ctrl - c  ---- screen show xeyes
3. startx xclock ----   screen show xeyes
4. ctrl - c ---- screen show xclock overlapped with xeyes background
```
I think xorg rendered backgournd on off-screen buffer but it didn't flip off-screen buffer to display memory.
What did I miss to setup xorg well? Please help me out, Thanks!!!
My xorg.conf
```
Section "Monitor"
    Identifier          "Monitor0"
EndSection
Section "Device"
        Option     "ShadowFB"              "false"
         #Option     "Rotate"                "CW"
         Option     "fbdev"                 "/dev/fb0"
         Option     "debug"                 "true"
         Identifier  "Card0"
         Driver      "fbdev"
EndSection
Section "Screen"
    Identifier          "Screen0"
    Device              "Card0"
    Monitor             "Monitor0"
    DefaultDepth        16
#    SubSection "Display"
#        Viewport 0 0
#       Depth 16
#       Modes "480x800"
#    EndSubSection
EndSection
```
```
my xorg log:
[ 14726.580] (==) Using config file: "/etc/X11/xorg.conf"
[ 14726.580] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 14726.582] (==) ServerLayout "Layout 0"
[ 14726.582] (**) |-->Screen "Screen0" (0)
[ 14726.582] (**) |   |-->Monitor "Monitor0"
[ 14726.583] (**) |   |-->Device "Card0"
[ 14726.584] (**) Option "BlankTime" "0"
[ 14726.584] (**) Option "StandbyTime" "0"
[ 14726.584] (**) Option "SuspendTime" "0"
[ 14726.584] (**) Option "OffTime" "0"
[ 14726.584] (==) Automatically adding devices
[ 14726.584] (==) Automatically enabling devices
[ 14726.584] (==) Automatically adding GPU devices
[ 14726.584] (==) Max clients allowed: 256, resource mask: 0x1fffff
[ 14726.584] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 14726.584]    Entry deleted from font path.
[ 14726.584] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 14726.584]    Entry deleted from font path.
[ 14726.584] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 14726.585]    Entry deleted from font path.
[ 14726.585] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 14726.585]    Entry deleted from font path.
[ 14726.585] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 14726.585] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[ 14726.585] (==) ModulePath set to "/usr/lib/arm-linux-gnueabihf/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 14726.585] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 14726.585] (II) Loader magic: 0xb6ffbf70
[ 14726.585] (II) Module ABI versions:
[ 14726.585]    X.Org ANSI C Emulation: 0.4
[ 14726.585]    X.Org Video Driver: 20.0
[ 14726.585]    X.Org XInput driver : 22.1
[ 14726.585]    X.Org Server Extension : 9.0
[ 14726.590] (--) using VT number 3
[ 14726.590] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[ 14726.591] (II) no primary bus or device found
[ 14726.591] (WW) "Shadow" will not be loaded unless you've specified it to be loaded elsewhere.
[ 14726.591] (WW) "ShadowFB" will not be loaded unless you've specified it to be loaded elsewhere.
[ 14726.591] (II) "glx" will be loaded by default.
[ 14726.591] (II) LoadModule: "glx"
[ 14726.592] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 14726.600] (II) Module glx: vendor="X.Org Foundation"
[ 14726.600]    compiled for 1.18.4, module version = 1.0.0
[ 14726.600]    ABI class: X.Org Server Extension, version 9.0
[ 14726.600] (==) AIGLX enabled
[ 14726.601] (II) LoadModule: "fbdev"
[ 14726.601] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 14726.602] (II) Module fbdev: vendor="X.Org Foundation"
[ 14726.602]    compiled for 1.18.1, module version = 0.4.4
[ 14726.602]    Module class: X.Org Video Driver
[ 14726.602]    ABI class: X.Org Video Driver, version 20.0
[ 14726.602] (II) FBDEV: driver for framebuffer: fbdev
[ 14726.604] (WW) Falling back to old probe method for fbdev
[ 14726.604] (II) Loading sub module "fbdevhw"
[ 14726.604] (II) LoadModule: "fbdevhw"
[ 14726.604] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 14726.605]    compiled for 1.18.4, module version = 0.0.2
[ 14726.605]    ABI class: X.Org Video Driver, version 20.0
[ 14726.605] [ fbdevHW: ] function: fbdevHWProbe line: 371
[ 14726.606] [ fbdevHW: ] namep: 0x0
[ 14726.606] (II) FBDEV(0): using /dev/fb0
[ 14726.606] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[ 14726.606] [ fbdevHW: ] namep: 0x0
[ 14726.606] (II) FBDEV(0): Creating default Display subsection in Screen section
        "Screen0" for depth/fbbpp 16/16
[ 14726.606] (**) FBDEV(0): Depth 16, (--) framebuffer bpp 16
[ 14726.606] (==) FBDEV(0): RGB weight 565
[ 14726.606] (==) FBDEV(0): Default visual is TrueColor
[ 14726.606] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[ 14726.607] [ fbdevHW: ] buf 0x0
[ 14726.607] (II) FBDEV(0): hardware:  (video memory: 1500kB)
[ 14726.607] (**) FBDEV(0): Option "fbdev" "/dev/fb0"
[ 14726.607] (**) FBDEV(0): Option "debug" "true"
[ 14726.607] (II) FBDEV(0): checking modes against framebuffer device...
[ 14726.607] (II) FBDEV(0): checking modes against monitor...
[ 14726.607] (--) FBDEV(0): Virtual size is 480x800 (pitch 480)
[ 14726.607] (**) FBDEV(0):  Built-in mode "current": 100.0 MHz, 208.3 kHz, 260.4 Hz
[ 14726.607] (II) FBDEV(0): Modeline "current"x0.0  100.00  480 480 480 480  800 800 800 800 -hsync -vsync -csync (208.3 kHz b)
[ 14726.607] (==) FBDEV(0): DPI set to (96, 96)
[ 14726.607] (II) Loading sub module "fb"
[ 14726.607] (II) LoadModule: "fb"
[ 14726.608] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 14726.609] (II) Module fb: vendor="X.Org Foundation"
[ 14726.609]    compiled for 1.18.4, module version = 1.0.0
[ 14726.609]    ABI class: X.Org ANSI C Emulation, version 0.4
[ 14726.609] (**) FBDEV(0): using shadow framebuffer
[ 14726.609] (II) Loading sub module "shadow"
[ 14726.609] (II) LoadModule: "shadow"
[ 14726.611] (II) Loading /usr/lib/xorg/modules/libshadow.so
[ 14726.612] (II) Module shadow: vendor="X.Org Foundation"
[ 14726.612]    compiled for 1.18.4, module version = 1.1.0
[ 14726.612]    ABI class: X.Org ANSI C Emulation, version 0.4
[ 14726.612] fbdev: PreInit done
[ 14726.612] fbdev: FBDevScreenInit 0
[ 14726.613] [ fbdevHW: ] function: fbdevHWModeInit line: 713
[ 14726.613] xfree init mode:   100000   480 480 480 480   800 800 800 800
[ 14726.613] fbdev init mode:   10000   480 0 0 0   800 0 0 0   16 5:6:5
[ 14726.672] (==) FBDEV(0): Backing store enabled
[ 14726.675] (==) FBDEV(0): DPMS enabled
[ 14726.675] fbdev: FBDevScreenInit done
[ 14726.676] (==) RandR enabled
[ 14726.735] (II) SELinux: Disabled on system
[ 14726.739] (II) AIGLX: Screen 0 is not DRI2 capable
[ 14726.739] (EE) AIGLX: reverting to software rendering
[ 14726.944] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[ 14726.948] (II) AIGLX: Loaded and initialized swrast
[ 14726.948] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[ 14727.161] (II) config/udev: Adding input device rda-keypad (/dev/input/event0)
[ 14727.162] (**) rda-keypad: Applying InputClass "evdev keyboard catchall"
[ 14727.162] (II) LoadModule: "evdev"
[ 14727.163] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 14727.165] (II) Module evdev: vendor="X.Org Foundation"
[ 14727.165]    compiled for 1.18.1, module version = 2.10.1
[ 14727.165]    Module class: X.Org XInput Driver
[ 14727.165]    ABI class: X.Org XInput driver, version 22.1
[ 14727.165] (II) Using input driver 'evdev' for 'rda-keypad'
[ 14727.165] (**) rda-keypad: always reports core events
[ 14727.165] (**) rda-keypad: always reports core events
[ 14727.165] (**) evdev: rda-keypad: Device: "/dev/input/event0"
[ 14727.166] (--) evdev: rda-keypad: Vendor 0 Product 0
[ 14727.166] (--) evdev: rda-keypad: Found keys
[ 14727.166] (II) evdev: rda-keypad: Configuring as keyboard
[ 14727.166] (**) Option "config_info" "udev:/sys/devices/platform/rda-keypad/input/input0/event0"
[ 14727.166] (II) XINPUT: Adding extended input device "rda-keypad" (type: KEYBOARD, id 6)
[ 14727.166] (**) Option "xkb_rules" "evdev"
[ 14727.166] (**) Option "xkb_model" "pc105"
[ 14727.166] (**) Option "xkb_layout" "us"
[ 14728.929] (II) evdev: rda-keypad: Close
[ 14728.938] (II) UnloadModule: "evdev"
[ 14728.965] (II) Server terminated successfully (0). Closing log file.
```

---

### Post by MAFoElffen on 2022-02-06
Both look good to me. I don't see any errors in the Xorg Log that stand out to me.

Is it working okay for you?

---

