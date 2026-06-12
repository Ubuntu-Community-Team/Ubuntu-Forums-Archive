---
title: "Suddenly started to loose keyboard input"
date: 2012-09-10
forum: Desktop Environments
---

### Post by azurehoney on 2012-09-10
How could I find out what kills my keyboard in LXDE?

It has happened now twice and I presume it will happen again.

---

### Post by Rex Bouwense on 2012-09-10
Hi, 
What kind of hardware are you using?  For instance I had that problem with a laptop and discovered that a connecting cable was not fully installed.  Are you using a wireless keyboard?  Without additional information, we would be guessing at a solution.  Not sure that using LXDE really has anything to do with it.  Are you using Lubuntu or a downloaded LXDE on top of Ubuntu?  Not sure that has anything to do with anything either but at least you could log on to Ubuntu to see if LXDE was the cause.

---

### Post by azurehoney on 2012-09-10
LXDE on top of Ubuntu 12.04 64bit

Using Asus X53B laptop, no external keyboards



edit: Why I am sure that this is only LXDE bug?

1. Nothing like this has ever happened in other desktop environments yet

2. When I log out after this bug occurs I can still use keyboard in login screen (GDM)

3. Keyboard input is back after quick log out/in

---

### Post by azurehoney on 2012-09-18
.xsession-errors the moment it happened:

```
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[0x7fa8b00035c8] access_mms access error: cannot read data 2
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[0x7fa8b000b2b8] access_mms access error: cannot read data 2

(rhythmbox:3495): Rhythmbox-WARNING **: Unable to grab media player keys: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `org.gnome.SettingsDaemon.MediaKeys' on object at path /org/gnome/SettingsDaemon/MediaKeys
How are you gentlemen? All your base are belong to us. (Openbox received signal 11)

(rhythmbox:3495): GLib-GObject-CRITICAL **: g_value_get_uint: assertion `G_VALUE_HOLDS_UINT (value)' failed
Openbox-Message: Requested key "XF86Terminal" does not exist on the display
ObRender-Message: Cannot load image "/usr/share/icons/hicolor/48x48/apps/chromium-browser.png" from file "/usr/share/icons/hicolor/48x48/apps/chromium-browser.png"

(rhythmbox:3495): GLib-GObject-CRITICAL **: g_value_get_uint: assertion `G_VALUE_HOLDS_UINT (value)' failed
Openbox-Message: Requested key "XF86Terminal" does not exist on the display
```

dmesg

```
[ 8705.524301] ACPI Error: Needed [Integer/String/Buffer], found [Reference] ffff88007101c870 (20110623/exresop-422)
[ 8705.524317] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20110623/dswexec-460)
[ 8705.524326] ACPI Error: Method parse/execution failed [\_SB_.PCI0.VGA_.AF03] (Node ffff88014873afc8), AE_AML_OPERAND_TYPE (20110623/psparse-536)
[ 8705.524343] ACPI Error: Method parse/execution failed [\_SB_.PCI0.VGA_.ATIF] (Node ffff88014873ad48), AE_AML_OPERAND_TYPE (20110623/psparse-536)
[ 8724.076133] accounts-daemon[3720]: segfault at 2993 ip 00007f2d98068af0 sp 00007fffaa6987e8 error 4 in libdbus-1.so.3.5.8[7f2d98046000+42000]

```

---

