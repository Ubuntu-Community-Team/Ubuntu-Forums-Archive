---
title: "Notebook + LCD = problem with gnome shell"
date: 2012-03-21
forum: Desktop Environments
---

### Post by kacperfx on 2012-03-21
Hi,

I have a problem with gnome shell. When connected to a laptop LCD with HDMI - gnome shell does not start. There are only a clean desktop on both screens. I can start at the terminal (keyboard shortcut), but does not appear in the gnome panel, etc.

 In an Unity everything is working properly.

.xsession-errors :
```

Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/kacper/.profile
Loading resource: /etc/X11/Xresources/x11-common
Loading X session script /etc/X11/Xsession.d/00_handle_guest_session
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50_check_unity_support
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/55gnome-session_gnomerc
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/65compiz_profile-on-session
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/80appmenu
Loading X session script /etc/X11/Xsession.d/80appmenu-gtk3
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=pl_PL.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
gnome-session-is-accelerated: Zaphod mode not supported.
gnome-session-check-accelerated: Helper exited with code 256
gnome-session[1546]: WARNING: Session 'gnome' runnable check failed: Zako&#324;czono z kodem 1
GNOME_KEYRING_CONTROL=/tmp/keyring-IBWxfo
SSH_AUTH_SOCK=/tmp/keyring-IBWxfo/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-IBWxfo
SSH_AUTH_SOCK=/tmp/keyring-IBWxfo/ssh
GPG_AGENT_INFO=/tmp/keyring-IBWxfo/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-IBWxfo
SSH_AUTH_SOCK=/tmp/keyring-IBWxfo/ssh
GPG_AGENT_INFO=/tmp/keyring-IBWxfo/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-IBWxfo
SSH_AUTH_SOCK=/tmp/keyring-IBWxfo/ssh
GPG_AGENT_INFO=/tmp/keyring-IBWxfo/gpg:0:1

(gnome-settings-daemon:1608): color-plugin-WARNING **: failed to get edid: unable to get EDID for output

(gnome-panel:1627): Gtk-CRITICAL **: gtk_style_context_get: assertion `priv->widget_path != NULL' failed
gnome-session[1546]: WARNING: Application 'gnome-panel.desktop' killed by signal
** (gnome-fallback-mount-helper:1664): DEBUG: Starting automounting manager
(bluetooth-applet:1662): Bluetooth-DEBUG: adding killswitch idx 0 state KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:1662): Bluetooth-DEBUG: killswitch 0 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:1662): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:1662): Bluetooth-DEBUG: killswitch 0 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:1662): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:1662): Bluetooth-DEBUG: killswitch 0 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:1662): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:1662): Bluetooth-DEBUG: killswitch 0 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:1662): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:1662): Bluetooth-DEBUG: killswitch 0 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:1662): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:1662): Bluetooth-DEBUG: killswitch 0 is KILLSWITCH_STATE_UNBLOCKED
(bluetooth-applet:1662): Bluetooth-DEBUG: killswitches state KILLSWITCH_STATE_UNBLOCKED
Failed to play sound: File or data not found
Initializing nautilus-gdu extension
** (gnome-fallback-mount-helper:1664): DEBUG: Found ConsoleKit session at path /org/freedesktop/ConsoleKit/Session2
** (gnome-fallback-mount-helper:1664): DEBUG: ScreenSaver name appeared
** (gnome-fallback-mount-helper:1664): DEBUG: ScreenSaver proxy ready
** (gnome-fallback-mount-helper:1664): DEBUG: Screensaver GetActive() returned 0
** (gnome-fallback-mount-helper:1664): DEBUG: ConsoleKit session is active 1
** Message: applet now removed from the notification area
** (nm-applet:1682): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1682): DEBUG: old state indicates that this was not a disconnect 0
** Message: using fallback from indicator to GtkStatusIcon
** (nm-applet:1682): DEBUG: foo_client_state_changed_cb
** (nautilus:1683): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-open-terminal extension
Initializing nautilus-image-converter extension
** (nm-applet:1682): DEBUG: foo_client_state_changed_cb
/usr/lib/python2.7/dist-packages/gobject/constants.py:24:  Warning: g_boxed_type_register_static: assertion `g_type_from_name  (name) == 0' failed
  import gobject._gobject

** (gnome-screensaver:1737): WARNING **: wygaszacz ekranu jest ju&#380; uruchomiony w tej sesji
** (process:1731): DEBUG: Telepathy Indicator started

(nautilus:1683): Gdk-CRITICAL **: gdk_window_get_screen: assertion `GDK_IS_WINDOW (window)' failed

(nautilus:1683): Gdk-CRITICAL **: gdk_window_get_screen: assertion `GDK_IS_WINDOW (window)' failed

```My xorg.conf :
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 280.13  (buildd@allspice)  Thu Aug 11 20:54:45 UTC 2011

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 280.13  (buildmeister@swio-display-x86-rhel47-03.nvidia.com)  Wed Jul 27 17:15:58 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko/Epson"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "YMH RX-V663"
    HorizSync       15.0 - 68.0
    VertRefresh     49.0 - 61.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
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
    Option         "metamodes" "DFP-1: 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

