---
title: "Recent Xorg and mouse instablity"
date: 2008-07-15
forum: Desktop Environments
---

### Post by hob on 2008-07-15
Recently Xorg has become very unstable after several hours (update list below). Something in the latest update has caused Xorg to loose the mouse, but there is some other instability besides this.

The mouse just stops working several hours after boot, but the keyboard still works fine. To get the mouse working again, I just alt-tab to the window I was working in and the mouse works fine again for a while. When the mouse stops working the first time, the scroll "wheel" never functions again until reboot. When I reboot, everything is fine for a few hours, which says that it's not a configuration problem.

The mouse is an Alps GlidePoint trackpad, but it looks like Xorg is seeing a standard PS/2 mouse. That's fine.

I'm not sure what those ACPI interrupts are, but here's the output from dmesg:
```

[ 1546.810743] psmouse.c: Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 1550.004367] psmouse.c: Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 1552.687530] psmouse.c: Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 1554.648585] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 1554.648715] PM: Writing back config space on device 0000:0c:00.0 at offset 1 (was 100102, writing 100106)
[ 1554.648893] iwl3945: Radio disabled by HW RF Kill switch
[ 1554.648913] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
[ 1565.393143] psmouse.c: Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 1601.593413] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 1601.593574] PM: Writing back config space on device 0000:0c:00.0 at offset 1 (was 100102, writing 100106)
[ 1601.593793] iwl3945: Radio disabled by HW RF Kill switch
[ 1601.593817] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
[ 1610.805491] irq 217, desc: c0418b00, depth: 0, count: 0, unhandled: 0
[ 1610.805501] ->handle_irq():  c01687c0, handle_bad_irq+0x0/0x290
[ 1610.805514] ->chip(): c03f48e0, no_irq_chip+0x0/0x40
[ 1610.805524] ->action(): 00000000
[ 1610.805528]   IRQ_DISABLED set
[ 1610.805531]     IRQ_MASKED set
[ 1610.805535] unexpected IRQ trap at vector d9
[ 1635.783400] psmouse.c: Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 1636.276299] psmouse.c: resync failed, issuing reconnect request
[ 1636.576265] input: PS/2 Mouse as /devices/virtual/input/input20
[ 1637.175110] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input21
[ 1644.604926] psmouse.c: GlidePoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 1644.653201] psmouse.c: resync failed, issuing reconnect request
[ 1645.747053] input: PS/2 Mouse as /devices/virtual/input/input22
[ 1646.142708] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input23
[ 1649.648223] psmouse.c: GlidePoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 1649.662445] psmouse.c: resync failed, issuing reconnect request
[ 1653.586239] input: PS/2 Mouse as /devices/virtual/input/input24
[ 1653.625588] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input25
[ 1655.770072] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 1655.770227] PM: Writing back config space on device 0000:0c:00.0 at offset 1 (was 100102, writing 100106)
[ 1655.770441] iwl3945: Radio disabled by HW RF Kill switch
[ 1655.770465] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
[ 1702.671408] psmouse.c: GlidePoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 1702.840565] psmouse.c: resync failed, issuing reconnect request
[ 1703.014924] input: PS/2 Mouse as /devices/virtual/input/input26
[ 1704.119250] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input27
[ 1705.799935] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 1705.800096] PM: Writing back config space on device 0000:0c:00.0 at offset 1 (was 100102, writing 100106)
[ 1705.800317] iwl3945: Radio disabled by HW RF Kill switch
[ 1705.800342] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
[ 1717.335764] irq 217, desc: c0418b00, depth: 0, count: 0, unhandled: 0
[ 1717.335778] ->handle_irq():  c01687c0, handle_bad_irq+0x0/0x290
[ 1717.335791] ->chip(): c03f48e0, no_irq_chip+0x0/0x40
[ 1717.335801] ->action(): 00000000
[ 1717.335805]   IRQ_DISABLED set
[ 1717.335807]     IRQ_MASKED set
[ 1717.335811] unexpected IRQ trap at vector d9

```

(On a completely side note, what are the units of the timestamp on the left side of dmesg? This certainly didn't happen 26 minutes or 26 hours after boot, probably around the 8 hour mark.)

So this psmouse.c is causing the problem? Why did it suddenly stop working? How can I fix this? It's really frustrating trying to use a slow computer with no mouse.

After reading this thread here, [http://ubuntuforums.org/showthread.php?t=794670](http://ubuntuforums.org/showthread.php?t=794670), I added i8042.reset i8042.nomux to the kernel boot parameters in menu.lst. Nothing changed.

When the mouse starts behaving erratically, Xorg also stars having problems. Applications are really slow, and opening a terminal sometimes takes 10 seconds.

When looking at the System Monitor widget in Gnome, it sometimes shows a CPU usage of up to 80%. However, using top or htop in a terminal shows that no more than 5% of the CPU is in use at any time. I'm not sure what the difference is in measurement.

I've looked in /var/log/Xorg.0.log, but there doesn't seem to be any error messages there. When I grep for "mouse":
```

(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
(==) intel(0): Silken mouse enabled

```

Is there a Xorg error file somewhere?

Relevent sections of /etc/X11/xorg.conf:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

```


The software update that caused this problem, on 10 July 08, as taken from /var/log/dpkg.log:
```

gtk2-engines-murrine 0.53.1-1ubuntu2
gtk2-engines-ubuntulooks 0.9.12-12
libpoppler2 0.6.4-1ubuntu3
libpoppler-glib2 0.6.4-1ubuntu2
poppler-utils 0.6.4-1ubuntu3
linux-restricted-modules-common 2.6.24.13-19.45
linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45
libc6 2.7-10ubuntu3

```


I'm running Ubuntu 8.04 on a Dell Inspiron 1420n, Intel 1.8 GHz Core2 Duo with 2 gigs of ram. Thanks for all the help!

---

### Post by ToyKeeper on 2009-08-14
This (mouse scrolling breaks) just happened on my Dell d420, and I found an easier way to get it working again. Instead of rebooting, go through a suspend and resume cycle. On my system, this means... press Fn-Esc (Stand by), wait a few seconds, close the notebook lid, wait a few seconds, then open the lid.

Doing a suspend/resume cycle shouldn't be necessary, but at least it works. It can also reset the wired or wireless NICs if they get wedged such that reloading the driver doesn't help. However, this is the first time I've ever seen the touchpad spontaneously revert to PS/2 mode.

---

### Post by djurny on 2009-11-16
what usually helps is just simple rmmod'ing the driver 
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```
this takes the least amount of time :)
still looking for a better solution as well..

---

### Post by eris23 on 2009-11-18
I have the same problem.  Yes, I can rmmod and modprobe as a workaround, but is there a proper fix?

---

### Post by Zorael on 2009-11-18
I remember experiencing something similar during Karmic development, and I got around it by passing an option to psmouse.

In /etc/modprobe.d/options.conf;
```
options psmouse resetafter=10
```

---

