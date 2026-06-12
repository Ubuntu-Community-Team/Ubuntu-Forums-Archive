---
title: "Notification Area icons missing! (also randr)"
date: 2009-12-28
forum: Desktop Environments
---

### Post by phantomcircuit on 2009-12-28
So I'm running a multi-head system.  Notification Area icons (pidgin/xchat tray icons for example) do not appear in either screens notification area when the programs are started in :0.1, but when started in :0.0 they appear in the notification area in :0.0

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
    Option         "RandR" "on"
    Option         "RandRRotation" "on"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LEN"
    HorizSync       40.8 - 49.0
    VertRefresh     40.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL E190S"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 140M"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 140M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Now possibly related is an issue I'm having with RandR.
```
$ sudo xrandr -o right
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  15
  Current serial number in output stream:  15

```

EDIT: Thought I should include the .xsession-errors file aswell
```
$ cat .xsession-errors
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

(gnome-settings-daemon:2009): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:2009): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
GNOME_KEYRING_SOCKET=/tmp/keyring-9wjX5J/socket
SSH_AUTH_SOCK=/tmp/keyring-9wjX5J/socket.ssh
Window manager warning: Failed to read saved session file /home/phantomcircuit/.config/metacity/sessions/10e24a474276422428126204079568137600000019440023.ms: Failed to open file '/home/phantomcircuit/.config/metacity/sessions/10e24a474276422428126204079568137600000019440023.ms': No such file or directory
** Message: adding killswitch idx 0 state 1
** Message: adding killswitch idx 1 state 1
** Message: Reading of RFKILL events failed
** Message: killswitch 0 is 1
** Message: killswitch 1 is 1
** Message: killswitches state 1
** Message: killswitch 0 is 1
** Message: killswitch 1 is 1
** Message: killswitches state 1
** (gnome-panel:2028): DEBUG: Adding applet 0.
** (gnome-panel:2028): DEBUG: Initialized Panel Applet Signaler.

(nautilus:2042): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** (gnome-panel:2028): DEBUG: Adding applet 1.

(polkit-gnome-authentication-agent-1:2079): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2079): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** (gnome-panel:2028): DEBUG: Adding applet 2.
** (gnome-panel:2028): DEBUG: Adding applet 3.
** (gnome-panel:2028): DEBUG: Adding applet 4.
** (gnome-panel:2028): DEBUG: Adding applet 5.
** (gnome-panel:2028): DEBUG: Adding applet 6.
** (gnome-panel:2028): DEBUG: Adding applet 7.
** (gnome-panel:2028): DEBUG: Adding applet 8.
Initializing nautilus-gdu extension
** (gnome-panel:2028): DEBUG: Adding applet 9.
** (gnome-panel:2028): DEBUG: Adding applet 10.
** (gnome-panel:2028): DEBUG: Adding applet 11.
** (gnome-panel:2028): DEBUG: Adding applet 12.
** (gnome-panel:2028): DEBUG: Adding applet 13.
** (gnome-panel:2028): DEBUG: Adding applet 14.
** (gnome-panel:2028): DEBUG: Adding applet 15.
** (gnome-panel:2028): DEBUG: Adding applet 16.
** (gnome-panel:2028): DEBUG: Adding applet 17.
** (gnome-panel:2028): DEBUG: Adding applet 18.
** (gnome-panel:2028): DEBUG: Adding applet 19.
** (gnome-panel:2028): DEBUG: Adding applet 20.
** (nm-applet:2075): DEBUG: foo_client_state_changed_cb
** (gnome-panel:2028): DEBUG: Adding applet 21.
** (gnome-panel:2028): DEBUG: Adding applet 22.
** (gnome-panel:2028): DEBUG: Adding applet 23.
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (nm-applet:2075): DEBUG: foo_client_state_changed_cb
evolution-alarm-notify-Message: Setting timeout for 3973 1262044800 1262040827
evolution-alarm-notify-Message:  Mon Dec 28 16:00:00 2009

evolution-alarm-notify-Message:  Mon Dec 28 14:53:47 2009

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x440006c (Buddy List)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

(firefox:2516): GLib-WARNING **: g_set_prgname() called multiple times
** (gnome-panel:2028): DEBUG: Removing applet 23.
** (gnome-panel:2028): DEBUG: Adding applet 23.

(thunderbird-bin:2929): GLib-WARNING **: g_set_prgname() called multiple times

(firefox:2961): GLib-WARNING **: g_set_prgname() called multiple times

```

---

