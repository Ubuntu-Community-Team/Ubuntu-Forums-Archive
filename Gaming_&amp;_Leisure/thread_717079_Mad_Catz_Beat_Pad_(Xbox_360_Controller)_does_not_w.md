---
title: "Mad Catz Beat Pad (Xbox 360 Controller) does not work - no support in xpad driver"
date: 2008-03-06
forum: Gaming &amp; Leisure
---

### Post by roderick on 2008-03-06
_SOLVED_

I have solved this. Most people have posted about updating xpad.c to version 0.1.7 from the Xbox Linux project CVS source. I went this route and wasted 3 days trying to beat it into submission. I had kernel crashes all over the place.

So, after speaking with one of the maintainers for the xpad.c in kernel source, he suggested going back to the kernel version and modding from there. Sounded reasonable, and so I did. I had it first try. Boy, I wish I had tried this first, rather than attempting to use the 0.1.7 version.

Anyway, to get my controller working, I had to add two lines to xpad.c (version 0.0.6 from Ubuntu kernel source 2.6.24). These two lines defined the Beat Pad  as well as ensure that the DPAD is set to buttons, rather than AXES. Here's the patch:

```

--- xpad.c.orig 2008-03-09 23:58:32.000000000 -0230
+++ xpad.c      2008-03-10 00:39:56.000000000 -0230
@@ -121,6 +121,7 @@
        { 0x0738, 0x4540, "Mad Catz Beat Pad", MAP_DPAD_TO_BUTTONS, XTYPE_XBOX },
        { 0x0738, 0x4556, "Mad Catz Lynx Wireless Controller", MAP_DPAD_TO_AXES, XTYPE_XBOX },
        { 0x0738, 0x4716, "Mad Catz Wired Xbox 360 Controller", MAP_DPAD_TO_AXES, XTYPE_XBOX360 },
+       { 0x0738, 0x4740, "Mad Catz Beat Pad", MAP_DPAD_TO_BUTTONS, XTYPE_XBOX360 },
        { 0x0738, 0x6040, "Mad Catz Beat Pad Pro", MAP_DPAD_TO_BUTTONS, XTYPE_XBOX },
        { 0x0c12, 0x8802, "Zeroplus Xbox Controller", MAP_DPAD_TO_AXES, XTYPE_XBOX },
        { 0x0c12, 0x8810, "Zeroplus Xbox Controller", MAP_DPAD_TO_AXES, XTYPE_XBOX },
@@ -182,6 +183,7 @@
        { USB_INTERFACE_INFO('X', 'B', 0) },    /* X-Box USB-IF not approved class */
        { USB_DEVICE_INTERFACE_PROTOCOL(0x045e, 0x028e, 1) },   /* X-Box 360 controller */
        { USB_DEVICE_INTERFACE_PROTOCOL(0x1430, 0x4748, 1) },   /* RedOctane Guitar Hero X-plorer */
+       { USB_DEVICE_INTERFACE_PROTOCOL(0x0738, 0x4740, 1) },   /* Mad Catz Beat Pad */
        { }
 };

```

This process did not work for me when I attempted the same thing using version 0.1.7, so you probably want to try this first (unless you have a wireless controller, in which case you probably need a newer version - best of luck in that case).


_Original Post below_:

I've read through the forums and tried several avenues to make this work.

I am currently running Hardy Heron (dev release) with Kernel 2.6.24-11-generic.

I have downloaded the latest (v 0.1.7) xpad driver and successfully compiled it. After reviewing additional forums, I reviewed the source code and patched it for my specific model.

Here is the diff:

```
--- xpad.c.orig 2008-03-06 17:09:03.000000000 -0330
+++ xpad.c      2008-03-06 17:11:44.000000000 -0330
@@ -102,6 +102,7 @@
        { 0x0738, 0x4526, "Mad Catz Control Pad Pro", GAMEPAD_XBOX },
        { 0x0738, 0x4536, "Mad Catz MicroCON", GAMEPAD_XBOX },
        { 0x0738, 0x4540, "Mad Catz Beat Pad", GAMEPAD_XBOX_MAT },
+       { 0x0738, 0x4740, "Mad Catz Beat Pad", GAMEPAD_XBOX_MAT },
        { 0x0738, 0x4556, "Mad Catz Lynx Wireless Controller", GAMEPAD_XBOX },
        { 0x0738, 0x4716, "Mad Catz Xbox 360 Controller", GAMEPAD_XBOX360 },
        { 0x0738, 0x6040, "Mad Catz Beat Pad Pro", GAMEPAD_XBOX_MAT },
@@ -162,6 +163,7 @@
        { USB_DEVICE(0x045e, 0x0291) }, /* Xbox 360 Wireless Controller */
        { USB_DEVICE(0x045e, 0x0719) }, /* Xbox 360 Wireless PC Receiver */
        { USB_DEVICE(0x1430, 0x4748) }, /* RedOctane Guitar Hero X-plorer */
+       { USB_DEVICE(0x0738, 0x4740) }, /* Mad Catz Beat Pad */
        { }
 };

```

This "appears" to be correct based on several other posts I have read, and it compiles fine. 

Now, when I attempt to load the module, I get a segfault and the kernel oops citing:

```

[  607.472740] /home/rgreening/xpad/xpad.c: driver for Xbox controllers v0.1.7
[  617.290825] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  617.371283] usb 1-1: configuration #1 chosen from 1 choice
[  617.376483] input: Mad Catz Beat Pad as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input10
[  617.397233] input: Mad Catz Beat Pad as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.1/input/input11
[  617.424248] input: Mad Catz Beat Pad as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.2/input/input12
[  617.440033] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000006
[  617.440042] printing eip: f8f60a5c *pde = 00000000
[  617.440050] Oops: 0000 [#1] SMP
[  617.440055] Modules linked in: xpad snd_rtctimer binfmt_misc af_packet pktcdvd i915 drm ppdev ipv6 acpi_cpufreq cpufreq_stats cpufreq_conservative cpufreq_powersave cpufreq_userspace cpufreq_ondemand freq_table container dock sbs sbshc iptable_filter ip_tables x_tables aes_i586 dm_crypt dm_mod berry_charge parport_pc lp parport acerhk arc4 ecb blkcipher joydev pcmcia snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep battery ac iwl3945 iwlwifi_mac80211 cfg80211 snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event video output snd_seq yenta_socket rsrc_nonstatic snd_timer sdhci psmouse tifm_7xx1 snd_seq_device pcmcia_core serio_raw tifm_core mmc_core button snd acer_acpi led_class evdev wmi_acer iTCO_wdt iTCO_vendor_support pcspkr soundcore intel_agp agpgart shpchp pci_hotplug ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_acpi usbhid hid ata_piix ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore r8169 thermal processor fan fuse
[  617.440174]
[  617.440179] Pid: 1570, comm: khubd Not tainted (2.6.24-11-generic #1)
[  617.440184] EIP: 0060:[<f8f60a5c>] EFLAGS: 00010286 CPU: 0
[  617.440193] EIP is at xpad_probe+0x23c/0x4b0 [xpad]
[  617.440197] EAX: 00000000 EBX: ee94c094 ECX: f74b7080 EDX: 00000002
[  617.440202] ESI: 00000014 EDI: f7318000 EBP: f72ff400 ESP: f7695cec
[  617.440206]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[  617.440211] Process khubd (pid: 1570, ti=f7694000 task=f76a0b40 task.ti=f7694000)
[  617.440215] Stack: ee94c094 00000041 f8f60fe3 f7d1ace4 f72ff404 efbc5c1c efbc5c00 01f625b8
[  617.440227]        ee94c080 f8f625b8 efbc5c00 f8f625b8 efbc5c00 f8f62480 f72ff400 f88b65a9
[  617.440238]        00000000 efbc5c1c efbc5c94 00000000 efbc5c1c 00000000 f8f624b4 f88cf500
[  617.440249] Call Trace:
[  617.440289]  [<f88b65a9>] usb_probe_interface+0xb9/0x140 [usbcore]
[  617.440347]  [<c027ea28>] driver_probe_device+0x88/0x190
[  617.440362]  [<c0316be5>] klist_next+0x55/0xb0
[  617.440386]  [<c027dd24>] bus_for_each_drv+0x44/0x70
[  617.440410]  [<c027ebf6>] device_attach+0x86/0x90
[  617.440416]  [<c027eb30>] __device_attach+0x0/0x10
[  617.440430]  [<c027dc95>] bus_attach_device+0x45/0x90
[  617.440452]  [<c027cd28>] device_add+0x418/0x510
[  617.440487]  [<f88b44f2>] usb_set_configuration+0x392/0x5d0 [usbcore]
[  617.440570]  [<f88bc9b6>] generic_probe+0x76/0xb0 [usbcore]
[  617.440625]  [<f88b6363>] usb_probe_device+0x33/0x40 [usbcore]
[  617.440653]  [<c027ea28>] driver_probe_device+0x88/0x190
[  617.440672]  [<c0316be5>] klist_next+0x55/0xb0
[  617.440693]  [<c027dd24>] bus_for_each_drv+0x44/0x70
[  617.440712]  [<c027ebf6>] device_attach+0x86/0x90
[  617.440718]  [<c027eb30>] __device_attach+0x0/0x10
[  617.440730]  [<c027dc95>] bus_attach_device+0x45/0x90
[  617.440747]  [<c027cd28>] device_add+0x418/0x510
[  617.440775]  [<f88af2c6>] usb_new_device+0x56/0xa0 [usbcore]
[  617.440823]  [<f88b0a67>] hub_thread+0x687/0xcb0 [usbcore]
[  617.440863]  [<c02142ee>] rb_erase+0x15e/0x280
[  617.440905]  [<c0141b80>] autoremove_wake_function+0x0/0x40
[  617.440926]  [<f88b03e0>] hub_thread+0x0/0xcb0 [usbcore]
[  617.440962]  [<c01418c2>] kthread+0x42/0x70
[  617.440968]  [<c0141880>] kthread+0x0/0x70
[  617.440980]  [<c0106677>] kernel_thread_helper+0x7/0x10
[  617.440998]  =======================
[  617.441001] Code: 00 98 f0 0f ab 47 1c 83 c2 01 0f b7 84 12 ec 0e f6 f8 66 85 c0 79 ea 8b 54 24 18 8b 42 04 8b 54 24 20 8b 40 0c 8b 4a 0c 8b 55 00 <0f> b6 70 06 0f b6 40 02 c1 e2 08 c1 e0 0f 09 c2 8b 44 24 20 81
[  617.441058] EIP: [<f8f60a5c>] xpad_probe+0x23c/0x4b0 [xpad] SS:ESP 0068:f7695cec
[  617.441136] ---[ end trace 19942cb059b6a3e6 ]---

```

I don't believe it's what I have changed, and quite possibly that the kernel I'm running doesn't like this version of xpad.

Any ideas or suggestions? I am currently at a loss.

---

### Post by roderick on 2008-03-06
Oh, and here's what shows up in /proc/bus/input/devices:

```

I: Bus=0003 Vendor=0738 Product=4740 Version=3120
N: Name="Mad Catz Beat Pad"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input10
U: Uniq=
H: Handlers=event10
B: EV=3
B: KEY=81b0000 40000f 0 0 0 0 0 0 0 0

I: Bus=0003 Vendor=0738 Product=4740 Version=3120
N: Name="Mad Catz Beat Pad"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.1/input/input11
U: Uniq=
H: Handlers=event11
B: EV=3
B: KEY=81b0000 40000f 0 0 0 0 0 0 0 0

I: Bus=0003 Vendor=0738 Product=4740 Version=3120
N: Name="Mad Catz Beat Pad"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.2/input/input12
U: Uniq=
H: Handlers=event12
B: EV=3
B: KEY=81b0000 40000f 0 0 0 0 0 0 0 0


```

Looking at the dmesg output, it appears to be trying to register input 10, 11 and 12 but it should have only tried to grab one.

---

### Post by roderick on 2008-03-07
I have tried this on two different systems now with two different kernels. 

This system is Hardy Heron (latest development release from Ubuntu) running kernel 2.6.24. I also tried it on my wifes system, which is Gutsy Gibbon (7.10 Ubuntu) running kernel 2.6.22. Both exhibit the same problem.

If I do not apply the patch, the controller is not picked up. Is there some default thing I can test here?

If only apply "{ 0x0738, 0x4740, "Mad Catz Beat Pad", GAMEPAD_XBOX_MAT },", then it is still not picked up.

I've attmpted to isolate exactly where in the code it fails. After some 
further debugging, i've discovered that it successfully gets input 10, 11 and 
12 (3 successive calls to xpad_probe), it then attempts to get the next input and fails (this is the fourth call to xpad_probe).

It crashes here in the code:

        usb_fill_int_urb(xpad->irq_in, udev,
                         usb_rcvintpipe(udev,ep_irq_in->bEndpointAddress),
                         xpad->idata, XPAD_PKT_LEN, xpad_irq_in,
                         xpad, ep_irq_in->bInterval);

I've added in some test code (diff below) just before it. The code bails if ep_irq_in is NULL (undefined):

@@ -554,6 +556,13 @@

        /* init input URB for USB INT transfer from device */
        ep_irq_in = &intf->cur_altsetting->endpoint[0].desc;
+
+       // Testing for valid input
+       if (!ep_irq_in) {
+               info("ep_irq_in undefined");
+               goto fail2;
+       }
+
        usb_fill_int_urb(xpad->irq_in, udev,
                         usb_rcvintpipe(udev, ep_irq_in->bEndpointAddress),
                         xpad->idata, XPAD_PKT_LEN, xpad_irq_in,

As you can see in the dmesg output below:

[  104.270277] input: Mad Catz Beat Pad 
as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input10
[  104.285890] input: Mad Catz Beat Pad 
as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.1/input/input11
[  104.298252] input: Mad Catz Beat Pad 
as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.2/input/input12
[  104.304010] /home/rgreening/xpad/xpad.c: ep_irq_in undefined
[  104.304558] xpad: probe of 1-1:1.3 failed with error -12

It appears that the call to "ep_irq_in = &intf->cur_altsetting->endpoint[0].desc;" is returning NULL and is not caught by the code. Therefore it crashes.

I guess there's some additional checking and logic that needs to occur there, though I am at a loss as to exactly what needs to be done.

Suggestions?

I am willing to assist further in debugging, just let me know what to test.

---

### Post by roderick on 2008-03-09
Editing first post with solution.

I now have this working using the in kernel xpad.c and patching it.

---

