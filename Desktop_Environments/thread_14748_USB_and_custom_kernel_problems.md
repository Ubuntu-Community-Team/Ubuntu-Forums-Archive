---
title: "USB and custom kernel problems"
date: 2005-02-09
forum: Desktop Environments
---

### Post by paul.hendrick on 2005-02-09
Hi all,
I have to compile a custom kernel on my ubuntu install, as I can't boot a stock kernel and have acpi enabled (i still dont know why).
I've recompiled the kernel and it boots fine, but whenever I insert a USB device, it isn't automatically mounted.
The gnome-volume-manager is running, and the hal-device-manager sees the device once it is inserted, but i can't use it. 
the old kernels work fine as long as I boot them with acpi=off, but with this being a laptop machine, i need acpi.

what should i check for in my kernel config to enable the usb auto mounting? 
cd mounting works fine, however.

thanks for any help.

---

### Post by Ironi on 2005-02-10
Does your kernel have hotplug support enabled? Check under "General setup" in menuconfig.

---

### Post by paul.hendrick on 2005-02-10
[QUOTE=Ironi]Does your kernel have hotplug support enabled? Check under "General setup" in menuconfig.[/QUOTE]

yeah, thats enabled in the kernel.
when I plug a device in, it IS detected, but it's not auto mounted.

---

### Post by paul.hendrick on 2005-02-13
still no ideas whats going wrong, anyone? I'm still stumped.

---

### Post by lukem on 2005-02-13
Are you able to mount them manually?

I've had problems with acpi also.  Unit wouldn't power down after shut down until I turned acpi on but then I lost sound.  In an older verison of linux I used to mount the usb devices (camera) maunally.  A little extra work, but it worked.

L

---

