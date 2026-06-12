---
title: "Xorg crashes on Exit"
date: 2009-08-24
forum: Desktop Environments
---

### Post by eath on 2009-08-24
Ok, I am running 9.04 64bit with nv180 drivers.  The Acer has a AMD Athalon 2 with a Nvidia GForce 8200 Integrated Graphics.  It is an ACER AX1300-U1801A.  I am using a CRT with VGA and a Flat Screen with HDMI.  All boots well.  The HDMI doesn't show anything until after the login sound w/ GDM.  Then it runs with out effort.  The problem is with the logout.  Normally when I logout, shut down, or press ALT CTRL F1, the VGA shuts off and the HDMI goes to my background color (not picture).  The computer is then dead in the water.  Only shutting of power and turning back on helps.  It doesn't always happen for the users, but the primary user (with SUDO privaleges) is always messing up.  I would give you an error script, but I don't know where to find it, if it is even writing one before it locks up.  I will include XORG, and .xsession errors.  If anyone has seen this problem or knows where to look, let me know.  I will search for whatever you think could help.

Xsession Errors
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-WlPW2w/socket
SSH_AUTH_SOCK=/tmp/keyring-WlPW2w/socket.ssh

(gnome-settings-daemon:3988): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:3988): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x1800) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
** (nm-applet:4073): DEBUG: applet_common_device_state_changed
** (gnome-panel:4065): DEBUG: Adding applet 0.
** (gnome-panel:4065): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:4065): DEBUG: Adding applet 1.
** (gnome-panel:4065): DEBUG: Adding applet 2.
** (gnome-panel:4065): DEBUG: Adding applet 3.
** (gnome-panel:4065): DEBUG: Adding applet 4.
** (gnome-panel:4065): DEBUG: Adding applet 5.
** (gnome-panel:4065): DEBUG: Adding applet 6.
** (gnome-panel:4065): DEBUG: Adding applet 7.
** (gnome-panel:4065): DEBUG: Adding applet 8.
** (gnome-panel:4065): DEBUG: Adding applet 9.
** (gnome-panel:4065): DEBUG: Adding applet 10.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
** (gnome-panel:4065): DEBUG: Adding applet 11.
I/O warning : failed to load external entity "/home/eath/.compiz/session/107d77d6962ebbdc28125115170737434100000037960019"

(gnome-panel:4065): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:4065): DEBUG: Adding applet 12.

** (nautilus:4066): WARNING **: Unable to add monitor: Not supported
** (gnome-panel:4065): DEBUG: Adding applet 13.
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
Starting gtk-window-decorator
evolution-alarm-notify-Message: Setting timeout for 6660 1251158400 1251151740
evolution-alarm-notify-Message:  Mon Aug 24 19:00:00 2009

evolution-alarm-notify-Message:  Mon Aug 24 17:09:00 2009

** (update-notifier:4071): DEBUG: crashreport_check

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
2009-08-24 17:16:21,290 CRITICAL 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```.nvidia-settings-rc
```
#
# /root/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Fri Aug 21 20:32:25 2009
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = Yes
ShowQuitDialog = Yes
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000

# Attributes:

Hortons:0.0/CursorShadow=0
Hortons:0.0/CursorShadowAlpha=64
Hortons:0.0/CursorShadowRed=0
Hortons:0.0/CursorShadowGreen=0
Hortons:0.0/CursorShadowBlue=0
Hortons:0.0/CursorShadowXOffset=4
Hortons:0.0/CursorShadowYOffset=2
Hortons:0.0/SyncToVBlank=1
Hortons:0.0/LogAniso=0
Hortons:0.0/FSAA=0
Hortons:0.0/TextureSharpen=0
Hortons:0.0/AllowFlipping=1
Hortons:0.0/FSAAAppControlled=1
Hortons:0.0/LogAnisoAppControlled=1
Hortons:0.0/OpenGLImageSettings=1
Hortons:0.0/FSAAAppEnhanced=0
Hortons:0.0/RedBrightness=0.000000
Hortons:0.0/GreenBrightness=0.000000
Hortons:0.0/BlueBrightness=0.000000
Hortons:0.0/RedContrast=0.000000
Hortons:0.0/GreenContrast=0.000000
Hortons:0.0/BlueContrast=0.000000
Hortons:0.0/RedGamma=1.000000
Hortons:0.0/GreenGamma=1.000000
Hortons:0.0/BlueGamma=1.000000
Hortons:0.0/DigitalVibrance[CRT-0]=0
Hortons:0.0/DigitalVibrance[DFP-0]=0
Hortons:0.0/XVideoTextureBrightness=0
Hortons:0.0/XVideoTextureContrast=4096
Hortons:0.0/XVideoTextureHue=0
Hortons:0.0/XVideoTextureSaturation=4096
Hortons:0.0/XVideoTextureSyncToVBlank=1
Hortons:0.0/XVideoSyncToDisplay=1
```xorg.conf
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Tue Mar 24 06:15:32 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    ModelName      "DELL E773c"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8200"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1440x900 +0+0, DFP: 1440x900 +0+900"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by eath on 2009-09-01
Ok, The nv180 that came with Jaunty 64 bit was crashing the X.  I deleted the driver that came with the "Use Proprietary Drivers" and installed Nvidia's nv195.   Hasn't crashed since in 30 logouts.:)

---

