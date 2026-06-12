---
title: "Backlight brightness reset to maximum after reboot (Inspiron 11z, Intel GM45)"
date: 2009-11-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Diether on 2009-11-24
On my Dell Inspiron 11z at each reboot the backlight brightness is reset from my user setting to maximum.

As far as I can track this from the boot messages the dimmed brightness setting is kept (even during power-off) until the kernel is initializing some parts of the graphics adapter.

At this time the system is still in text mode and later carries the brightness max. setting over to graphics mode (xfce) without readjustment.
I have copied out the lines of /var/log/messages in the time range where I believe the backlight reset happens:

kernel: [    2.293118] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/input/input5
kernel: [    2.293236] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
kernel: [    2.293341] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
kernel: [    2.464445] usb 3-1: configuration #1 chosen from 1 choice
kernel: [    2.467392] hub 3-1:1.0: USB hub found
kernel: [    2.469343] hub 3-1:1.0: 3 ports detected
kernel: [    2.702243] [drm] LVDS-8: set mode 1366x768 c
kernel: [    2.725039] usb 5-2: new low speed USB device using uhci_hcd and address 2
kernel: [    2.879930] usb 5-2: configuration #1 chosen from 1 choice
kernel: [    2.890593] usbcore: registered new interface driver hiddev
kernel: [    2.903135] input: HID 062a:0001 as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input6
kernel: [    2.903243] generic-usb 0003:062A:0001.0001: input,hidraw0: USB HID v1.10 Mouse [HID 062a:0001] on usb-0000:00:1d.0-2/input0
kernel: [    2.903262] usbcore: registered new interface driver usbhid
kernel: [    2.903265] usbhid: v2.6:USB HID core driver
kernel: [    2.962355] usb 3-1.1: new full speed USB device using uhci_hcd and address 3

I am running Xubuntu 9.10 with latest updates (Nov. 24, 2009)

Is somebody out there to give a hint?

Thanks,
Diether

---

### Post by mikewhatever on 2009-11-25
There is a bug report on the issue, but, apparently, no fix yet.

[https://bugs.launchpad.net/gnome-power/+bug/35223](https://bugs.launchpad.net/gnome-power/+bug/35223)

---

### Post by Diether on 2009-12-05
> **mikewhatever said:**
> There is a bug report on the issue, but, apparently, no fix yet.

[https://bugs.launchpad.net/gnome-power/+bug/35223](https://bugs.launchpad.net/gnome-power/+bug/35223)

I can't believe this has something to do with gnome power manager; I am running XUbuntu / XFCE Desktop and the brightness reset occurs significantly before any graphical components come up.

I have reconsidered / observed the issue again and came to the conclusion that the brightness reset is done in conjunction with one of the very first activities of the agpgart-intel (kernel?) module.
It must probably happen in  the following section of my /var/log/messages:

kernel: [    1.873282] Linux agpgart interface v0.103
kernel: [    1.878396] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
kernel: [    1.879587] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
kernel: [    1.917662] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
kernel: [    1.990400] usb 1-3: configuration #1 chosen from 1 choice
kernel: [    2.008168] [drm] Initialized drm 1.1.0 20060810
kernel: [    2.024426] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

As far as I can observe the issue it occurs right before the seconds counter switches to 2.xx.
I could not identify any kernel option being able to suppress the brightness reset.
Nevertheless, my Windows7 leaves the brightness untouched after reboot making me hope that a brightness reset is not mandatory when initializing the GM45 graphics hardware.

D.

---

