---
title: "Ubuntu display setting keep reverting to Mirrored on dual screens"
date: 2022-01-10
forum: Desktop Environments
---

### Post by makem2 on 2022-01-10
I am using Ubuntu 21.10 with an XFCE desktop on two monitors.

I select the Display Manager from the Applications Manager, choose the Primary Display, with the Secondary Display on the right. I uncheck the Mirrored Display box.

When I reboot or return from shutdown the screens are Mirrored. The Mirrored selection is highlighted in Advanced and in the choices I have to select the Secondary screen to the right option.

How can I get the settings such that once I make the choices they remain so until I use the Display Manager manually to change the settings?

Dual screen setup:

Primary screen, Display Port connection

Secondary screen, HDMI connection

Both are connected to an ASUS TUF Gaming Z590-Plus Wifi GFX. I am using NVIDIA driver metapackage from nvidia-driver-470 (propriety, tested)  which is selected in the Software  & Updates.

I notice the Secondary monitor lights up first with a no video message and after I login on the Primary monitor both then come on showing the Mirrored screens.

Edit: I have just realised that the Refresh rate is reverting to 60Hz having been set at 143.9 Hz.

---

### Post by &amp;KyT$0P# on 2022-01-10
With Nvidia graphics you need to set display configuration in **both** nvidia-settings **and** xfce4 display settings.  Use nvidia-settings as the primary tool for configuration, then make sure xfce4 display settings are synced to that configuration.

---

### Post by makem2 on 2022-01-11
nvidia-settings says Screen 1. I don't see anywhere to choose default screen and no mirrored

Think i've found how ty

But unable to save  /etc/X11xorg.conf for writing :(

I find this in terminal:

```

makem@makems-TUF:~$ nvidia-settings

(nvidia-settings:3833): GLib-GObject-CRITICAL **: 15:44:22.268: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 15:44:22.428: PRIME: No offloading required. Abort
** Message: 15:44:22.428: PRIME: is it supported? no

WARNING:  Unable to parse X.Org version string.

Package xorg-server was not found in the pkg-config search path.
Perhaps you should add the directory containing `xorg-server.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-server' found
Error executing /usr/share/screen-resolution-extra/nvidia-polkit: Permission denied

ERROR: Unable to open X config file '/etc/X11/xorg.conf' for writing.

```

Edit: Solved thanks to this post:

[URL="https://ubuntuforums.org/showthread.php?t=1482283"]https://ubuntuforums.org/showthread.php?t=1482283

But, I would still like to know why we must use a work around
[/URL]

---

