---
title: "Latitude 2100 Karmic Upgrade Touchpad Problem"
date: 2010-02-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pdemchick on 2010-02-27
My Dell Latitude 2100 worked fine with the pre-installed Ubuntu 9.04.  I upgraded to 9.10 and the touchpad stopped working. Restored to factory condition and it again worked fine. I re-did the upgrade, this time asking it not to delete the obsolete items. Same problem. Any suggestions would be appreciated.

---

### Post by coffeeaddict22 on 2010-02-27
Hi,
Have a look in HAL.  Try ```
 lshal | grep touchpad -A20 -B20

``` and that might help to identify what we're trying to make work first of all.
Also, just check you haven't got a hardware switch you've turned off.

Post back the results of the above command, and we'll go from there.

---

### Post by pdemchick on 2010-03-04
Thank you very much. Sorry I was unavailable for a couple of days.  Here are the results.

*Paul*

paul@dell-desktop:~$ lshal | grep -A 20 -B 20 'touchpad'
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042'  (string)
  platform.id = 'i8042'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  info.linux.driver = 'psmouse'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'  (string)
  serio.description = 'i8042 AUX port'  (string)
  serio.id = 'serio1'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'SynPS/2 Synaptics TouchPad'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'  (string)
  input.device = '/dev/event7'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'SynPS/2 Synaptics TouchPad'  (string)
  input.x11_driver = 'synaptics'  (string)
  linux.device_file = '/dev/event7'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input7/event7'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  info.linux.driver = 'atkbd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 KBD port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)

---

### Post by coffeeaddict22 on 2010-03-04
OK.  To highlight: 

info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port' (string)
**info.product = 'SynPS/2 Synaptics TouchPad' (string)**
info.subsystem = 'input' (string)

Have a look [here;]("http://wiki.archlinux.org/index.php/Touchpad_Synaptics#No_scrolling.2Ftapping_with_Gnome_2.28") it's Arch, but I suspect the following quote may be your problem: 

Gnome 2.28 introduces a few additional features for managing touchpads. This change takes preference over previously configured options in the HAL policy file and thus may surprise some unsuspecting people. To change the Gnome 2.28 touchpad settings, go to System->Preferences->Mouse->Touchpad.

---

### Post by rijidij on 2010-03-09
Hi,
I don't mean to hijack your thread, but I'm having the same problem with my Sony Vaio VGN-T2XP.
It worked fine under Jaunty, but since doing an in-place upgrade to Karmic the touchpad is non-responsive.

Here is my lshal output:
```
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042'  (string)
  platform.id = 'i8042'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  info.linux.driver = 'psmouse'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'  (string)
  serio.description = 'i8042 AUX port'  (string)
  serio.id = 'serio1'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input_0'
  info.callouts.add = {'hal-probe-vmmouse'} (string list)
  info.capabilities = {'input', 'input.mouse', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'AlpsPS/2 ALPS GlidePoint'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input_0'  (string)
  input.device = '/dev/event8'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'AlpsPS/2 ALPS GlidePoint'  (string)
  input.x11_driver = 'synaptics'  (string)
  linux.device_file = '/dev/event8'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input8/event8'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.callouts.add = {'hal-probe-vmmouse'} (string list)
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'PS/2 Mouse'  (string)
```

There is also no "Touchpad" tab under System->Preferences->Mouse.

I hope somebody can help.

TIA,
Craig

---

### Post by rijidij on 2010-03-10
**Doh!** 
I was using the wrong version of the kernel... :-\" 

Solved by an upgrade to Grub2, and update.
I also had to remove my previous edit to xorg.conf

---

### Post by stednick on 2010-11-27
I am running into the same issue.  How were you able to solve this pdemchick?  Or did you install a new kernel?

---

