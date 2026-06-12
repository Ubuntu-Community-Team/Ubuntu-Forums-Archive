---
title: "GDM Auto-Login Not Working?"
date: 2013-05-16
forum: Desktop Environments
---

### Post by victorhooi on 2013-05-16
Hi,

I've installed Ubuntu 13.04, along with the gnome-shell packages from the Gnome3 PPA.

Yes, non-stock, I know, but I'm hoping people here will be at least able to point me in the right direction, or give me advice on how to troubleshoot.

The desktop itself seems to be fine. GDM starts up, and I am able to login to Gnome Shell, and use that.

However, I'm trying to enable auto-login via GDM, and it's simply giving me a blank screen when the system starts up.
My /etc/gdm/custom.conf:

```

# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.

[daemon]
# Enabling automatic login
AutomaticLoginEnable = true
AutomaticLogin = myusername

# Enabling timed login
#  TimedLoginEnable = true
#  TimedLogin = user1
#  TimedLoginDelay = 10

# Reserving more VTs for test consoles (default is 7)
#  FirstVT = 9

[security]

[xdmcp]

[greeter]
# Only include selected logins in the greeter
IncludeAll = false
Include = myusername

[chooser]

[debug]
# More verbose logs
# Additionally lets the X server dump core if it crashes
#  Enable = true

```

When I startup, I simply get an empty background.

My /var/log/gdm/:0-greeter.log:

```

gnome-session[1402]: WARNING: Failed isActive call to ConsoleKit: Rejected send message, 2 matched rules; type="method_call", sender=":1.23" (uid=117 pid=1402 comm="/usr/bin/gnome-session --autostart /usr/share/gdm/") interface="org.freedesktop.ConsoleKit.Manager" member="IsActive" error name="(unset)" requested_reply="0" destination=":1.16" (uid=0 pid=1267 comm="/usr/sbin/console-kit-daemon --no-daemon ")
      JS LOG: IBus version is too old
      JS LOG: GNOME Shell started at Thu May 16 2013 22:54:28 GMT+1000 (EST)
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

(gnome-settings-daemon:1596): GLib-GIO-WARNING **: Error releasing name org.gnome.SettingsDaemon: The connection is closed

(gnome-settings-daemon:1596): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed

(gnome-settings-daemon:1596): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed

(gnome-settings-daemon:1596): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed

(gnome-settings-daemon:1596): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed

(gnome-settings-daemon:1596): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed

(gnome-settings-daemon:1596): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed

(gnome-settings-daemon:1596): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed

(gnome-settings-daemon:1596): wacom-plugin-CRITICAL **: gsd_wacom_device_get_device_type: assertion `GSD_IS_WACOM_DEVICE (device)' failed

(gnome-settings-daemon:1596): libappindicator-WARNING **: Unable to send signal for NewStatus: The connection is closed

(gnome-settings-daemon:1596): GLib-GIO-WARNING **: Error releasing name org.freedesktop.ScreenSaver: The connection is closed
[1368708863,000,xklavier.c:xkl_engine_start_listen/]    The backend does not require manual layout management - but it is provided by the applicatio

```

My /var/log/gdm/:0.log (excerpt):
```

X.Org X Server 1.13.3
Release Date: 2013-03-07
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
Current Operating System: Linux camperkiosk1 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/@/boot/vmlinuz-3.8.0-21-generic root=UUID=a1fda6ce-8d63-43aa-a2af-48437a4c646f ro rootflags=subvol=@ quiet splash vt.handoff=7
Build Date: 17 April 2013  10:43:13PM
xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.28.2
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 16 22:59:24 2013
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(==) Automatically adding GPU devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
        Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
(==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) config/udev: Adding drm device (/dev/dri/card0)
(--) PCI:*(0:0:2:0) 8086:0102:1043:844d rev 9, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
...
(**) evdev: Microsoft  Microsoft Basic Optical Mouse : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft  Microsoft Basic Optical Mouse " (type: MOUSE, id 9)
(II) evdev: Microsoft  Microsoft Basic Optical Mouse : initialized for relative axes.
(**) Microsoft  Microsoft Basic Optical Mouse : (accel) keeping acceleration scheme 1
(**) Microsoft  Microsoft Basic Optical Mouse : (accel) acceleration profile 0
(**) Microsoft  Microsoft Basic Optical Mouse : (accel) acceleration factor: 2.000
(**) Microsoft  Microsoft Basic Optical Mouse : (accel) acceleration threshold: 4
(II) config/udev: Adding input device Microsoft  Microsoft Basic Optical Mouse  (/dev/input/mouse0)
(II) No input driver specified, ignoring this device.
(II) This device may have been added with another device file.
(II) config/udev: Adding input device Microsoft Wired Keyboard 400 (/dev/input/event3)
(**) Microsoft Wired Keyboard 400: Applying InputClass "evdev keyboard catchall"
(II) Using input driver 'evdev' for 'Microsoft Wired Keyboard 400'
(**) Microsoft Wired Keyboard 400: always reports core events
(**) evdev: Microsoft Wired Keyboard 400: Device: "/dev/input/event3"
(--) evdev: Microsoft Wired Keyboard 400: Vendor 0x45e Product 0x752
(--) evdev: Microsoft Wired Keyboard 400: Found keys
(II) evdev: Microsoft Wired Keyboard 400: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 400" (type: KEYBOARD, id 10)
(II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event4)
(**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
(II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
(**) Eee PC WMI hotkeys: always reports core events
(**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event4"
(--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
(--) evdev: Eee PC WMI hotkeys: Found keys
(II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 11)

```

Any ideas on what's going on? Or what I can do to troubleshoot this?

Cheers,
Victor

---

### Post by dino99 on 2013-05-16
from the terminal, run:

gsettings set org.gnome.desktop.background show-desktop-icons true && gsettings set org.gnome.desktop.background show-desktop-icons false

---

### Post by markbl on 2013-05-16
Auto-login is a standard option in Ubuntu and it works in both Unity and GNOME Shell (with or without the GNOME 3 PPA). Get rid of any your custom changes and just set "automatic login" on in Settings/User Accounts. Works with both lightdm and gdm.

---

### Post by victorhooi on 2013-05-16
Hi,

@dino99 - Hmm, I haven't run that yet, but are you suggesting that it has logged in, but there's no background or desktop icons? Because there's no menu-bar at the top either, and pushing the mouse to the top left doesn't do anything, so I don't think it's logged in properly...?

@markbl - Hmm, the thing is, we're trying to use Salt Stack to manage configuration for these desktops - so whatever change I make has to be something scriptable, that I can duplicate and push out to boxes.

If I enable Settings/User Accounts/Automatic Login - what actually changes does that make to configuration files, Gconf etc.?

Cheers,
Victor

---

