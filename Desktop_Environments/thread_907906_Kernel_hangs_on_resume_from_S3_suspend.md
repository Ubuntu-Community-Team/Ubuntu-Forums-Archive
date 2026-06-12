---
title: "Kernel hangs on resume from S3 suspend"
date: 2008-09-01
forum: Desktop Environments
---

### Post by qhex16 on 2008-09-01
I'm running Kubuntu 8.04.1 64-bit on an Intel Core 2 Duo 8400, with ECS G31T-M motherboard. Kernel version is 2.6.24-19. Once entering S3 suspend, either by pm-suspend on the command line or through KDE, power is cut to USB and PS/2 devices, so I have to press the power button to resume.

The machine appears to start (hard drive light constantly on), but nothing else happens. No power to USB or PS/2 (mouse doesn't light, capslock doesn't work), no response to network. No VGA output. Nothing is logged in /var/log/pm-suspend.log beyond 'done running suspend hooks'.

I've tried using /sys/power/pm_trace, but the real-time clock doesn't even get changed. Any ideas how to proceed troubleshooting?

Thanks!

---

### Post by xeth_delta on 2008-09-01
> **qhex16 said:**
> I'm running Kubuntu 8.04.1 64-bit on an Intel Core 2 Duo 8400, with ECS G31T-M motherboard. Kernel version is 2.6.24-19. Once entering S3 suspend, either by pm-suspend on the command line or through KDE, power is cut to USB and PS/2 devices, so I have to press the power button to resume.

The machine appears to start (hard drive light constantly on), but nothing else happens. No power to USB or PS/2 (mouse doesn't light, capslock doesn't work), no response to network. No VGA output. Nothing is logged in /var/log/pm-suspend.log beyond 'done running suspend hooks'.

I've tried using /sys/power/pm_trace, but the real-time clock doesn't even get changed. Any ideas how to proceed troubleshooting?

Thanks!

From experience, I would say that what is causing these problems is one of the modules/drivers not behaving properly after resume. I would say that candidates are the graphics card, wireless, sound card modules.

What graphics card do you have on it and what driver are you using for it. Same for the wireless card (if you use one).

---

### Post by qhex16 on 2008-09-02
> **xeth_delta said:**
> From experience, I would say that what is causing these problems is one of the modules/drivers not behaving properly after resume. I would say that candidates are the graphics card, wireless, sound card modules.

What graphics card do you have on it and what driver are you using for it. Same for the wireless card (if you use one).

I'm using everything integrated in the motherboard; integrated Intel GMA3100 graphics, integrated Intel HD Audio (Realtec ALC662), and network is the integrated Ethernet, no wireless. I do have a 1394 card installed. Just tried rmmod'ing ieee1394 module before suspending but it doesn't fix it.

Edit: not sure what graphics driver, how can I find this?

---

### Post by xeth_delta on 2008-09-02
> **qhex16 said:**
> I'm using everything integrated in the motherboard; integrated Intel GMA3100 graphics, integrated Intel HD Audio (Realtec ALC662), and network is the integrated Ethernet, no wireless. I do have a 1394 card installed. Just tried rmmod'ing ieee1394 module before suspending but it doesn't fix it.

Edit: not sure what graphics driver, how can I find this?

I don't think the firewire would be a problem, Anyway, if you want to give it a try, blacklist the module, at resume it might get reloaded otherwise.
To blacklist it add
```
blacklist ieee1394
```
at the end of /etc/modprobe.d/blacklist

I guess you are using the "intel" open source driver. To be sure, open /etc/X11/xorg.conf, look for section "Device".

Something else you can do is start in a command line environment without X11, try to suspend from there.

Unload module one by one and try suspending again. It is tedious, but it might lead you to the problematic module, if there is one.

For now, this is what I can suggest. Maybe someone else with more knowledge on the problem can shed more light.

For what it's worth, in the case of my laptop, it was the wireless card driver that prevented it from recovering from resume. This was taken care of in 8.04, however and is now working properly.

---

### Post by coscos on 2008-09-02
I have exactly the same problem. I am running mythbuntu 8.04.1, Gigabyte GA-G33M-S2H motherboard, with onboard video (Intel GMA 3100), audio(Realtek ALC889A) and network card (Realtek 8110SC). I also have E8400 CPU as OP. The machine seems suspended fine, but the resume never works. It always hangs. I tried many ways (s2ram, apm, ...) and none of them works. :confused:

Somebody please help! Following are the log files:

/var/log/pm-suspend.log:
```

Mon Sep  1 21:23:45 PDT 2008: running suspend hooks.
===== Mon Sep  1 21:23:45 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Mon Sep  1 21:23:45 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Mon Sep  1 21:23:45 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Mon Sep  1 21:23:45 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 0
===== Mon Sep  1 21:23:45 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Mon Sep  1 21:23:45 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Mon Sep  1 21:23:45 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Mon Sep  1 21:23:46 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Mon Sep  1 21:23:46 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Mon Sep  1 21:23:46 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Mon Sep  1 21:23:46 PDT 2008: done running suspend hooks.
Mon Sep  1 21:25:51 PDT 2008: running resume hooks.
===== Mon Sep  1 21:25:51 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
===== Mon Sep  1 21:25:51 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Mon Sep  1 21:25:51 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Mon Sep  1 21:25:51 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Mon Sep  1 21:25:51 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
 * Reconfiguring network interfaces...
SIOCDELRT: No such process
   ...done.
===== Mon Sep  1 21:25:51 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
 * Stopping NTP server ntpd
   ...done.
===== Mon Sep  1 21:25:51 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
===== Mon Sep  1 21:25:51 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Mon Sep  1 21:25:51 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Mon Sep  1 21:25:51 PDT 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
Mon Sep  1 21:25:51 PDT 2008: done running resume hooks.

```

/var/log/kern.log:
```

Sep  1 21:12:05 mocha kernel: [   63.093844] ACPI: 'USE2' and 'USBE' have the same GPE, can't disable/enable one seperately
Sep  1 21:12:05 mocha kernel: [   63.093846] ACPI: 'AZAL' and 'USBE' have the same GPE, can't disable/enable one seperately
================>>>>>>> /this is when I did the suspend/ ========>> Sep  1 21:23:45 mocha kernel: [  762.246825] ACPI: PCI interrupt for device 0000:03:05.0 disabled
================>>>>>>> /here resume started/ ========>> Sep  1 21:25:51 mocha kernel: [  763.004665] Syncing filesystems ... done.
Sep  1 21:25:51 mocha kernel: [  763.005113] PM: Preparing system for mem sleep
Sep  1 21:25:51 mocha kernel: [  763.005115] Freezing user space processes ... (elapsed 0.00 seconds) done.
Sep  1 21:25:51 mocha kernel: [  763.005413] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Sep  1 21:25:51 mocha kernel: [  763.005430] PM: Entering mem sleep
Sep  1 21:25:51 mocha kernel: [  763.005430] Suspending console(s)
Sep  1 21:25:51 mocha kernel: [  763.005676] ACPI: PCI interrupt for device 0000:00:02.0 disabled
Sep  1 21:25:51 mocha kernel: [  763.019058] lirc_mceusb2[5]: suspend
Sep  1 21:25:51 mocha kernel: [  763.038004] sd 4:0:0:0: [sdb] Synchronizing SCSI cache
Sep  1 21:25:51 mocha kernel: [  763.038161] sd 4:0:0:0: [sdb] Stopping disk
Sep  1 21:25:51 mocha kernel: [  763.525508] sd 2:0:0:0: [sda] Synchronizing SCSI cache
Sep  1 21:25:51 mocha kernel: [  763.525622] sd 2:0:0:0: [sda] Stopping disk
Sep  1 21:25:51 mocha kernel: [  763.526209] ACPI handle has no context!
Sep  1 21:25:51 mocha kernel: [  763.526334] parport_pc 00:09: disabled
Sep  1 21:25:51 mocha kernel: [  763.526432] serial 00:08: disabled
Sep  1 21:25:51 mocha kernel: [  763.526479] ACPI handle has no context!
Sep  1 21:25:51 mocha kernel: [  763.557545] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Sep  1 21:25:51 mocha kernel: [  763.573516] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
Sep  1 21:25:51 mocha kernel: [  763.589514] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Sep  1 21:25:51 mocha kernel: [  763.605504] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Sep  1 21:25:51 mocha kernel: [  763.621445] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Sep  1 21:25:51 mocha kernel: [  763.621475] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Sep  1 21:25:51 mocha kernel: [  763.621505] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Sep  1 21:25:51 mocha kernel: [  763.653386] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Sep  1 21:25:51 mocha kernel: [  763.669390] ACPI: PCI interrupt for device 0000:00:1a.7 disabled
Sep  1 21:25:51 mocha kernel: [  763.685380] ACPI: PCI interrupt for device 0000:00:1a.2 disabled
Sep  1 21:25:51 mocha kernel: [  763.685410] ACPI: PCI interrupt for device 0000:00:1a.1 disabled
Sep  1 21:25:51 mocha kernel: [  763.685440] ACPI: PCI interrupt for device 0000:00:1a.0 disabled
Sep  1 21:25:51 mocha kernel: [  763.688450] Disabling non-boot CPUs ...
Sep  1 21:25:51 mocha kernel: [  763.688463] CPU0 attaching NULL sched-domain.
Sep  1 21:25:51 mocha kernel: [  763.688464] CPU1 attaching NULL sched-domain.
Sep  1 21:25:51 mocha kernel: [  763.801226] CPU 1 is now offline
Sep  1 21:25:51 mocha kernel: [  763.801229] SMP alternatives: switching to UP code
Sep  1 21:25:51 mocha kernel: [  763.802228] CPU0 attaching sched-domain:
Sep  1 21:25:51 mocha kernel: [  763.802229]  domain 0: span 01
Sep  1 21:25:51 mocha kernel: [  763.802230]   groups: 01
Sep  1 21:25:51 mocha kernel: [  763.802362] CPU1 is down
Sep  1 21:25:51 mocha kernel: [    0.745628] Back to C!
Sep  1 21:25:51 mocha kernel: [    0.745940] Enabling non-boot CPUs ...
Sep  1 21:25:51 mocha kernel: [    0.745986] CPU0 attaching NULL sched-domain.
Sep  1 21:25:51 mocha kernel: [    0.756694] SMP alternatives: switching to SMP code
Sep  1 21:25:51 mocha kernel: [    0.757517] Booting processor 1/1 eip 3000
Sep  1 21:25:51 mocha kernel: [    0.767978] Initializing CPU#1
Sep  1 21:25:51 mocha kernel: [    0.844535] Calibrating delay using timer specific routine.. 5999.81 BogoMIPS (lpj=11999621)
Sep  1 21:25:51 mocha kernel: [    0.844539] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0008e3fd 00000000 00000001 00000000
Sep  1 21:25:51 mocha kernel: [    0.844542] monitor/mwait feature present.
Sep  1 21:25:51 mocha kernel: [    0.844544] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep  1 21:25:51 mocha kernel: [    0.844545] CPU: L2 cache: 6144K
Sep  1 21:25:51 mocha kernel: [    0.844546] CPU: Physical Processor ID: 0
Sep  1 21:25:51 mocha kernel: [    0.844547] CPU: Processor Core ID: 1
Sep  1 21:25:51 mocha kernel: [    0.844548] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0008e3fd 00000000 00000001 00000000
Sep  1 21:25:51 mocha kernel: [    0.845310] CPU1: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 06
Sep  1 21:25:51 mocha kernel: [    0.845323] checking TSC synchronization [CPU#0 -> CPU#1]:
Sep  1 21:25:51 mocha kernel: [    0.865307] Measured 101526796872 cycles TSC warp between CPUs, turning off TSC clock.
Sep  1 21:25:51 mocha kernel: [    0.865308] Marking TSC unstable due to: check_tsc_sync_source failed.
Sep  1 21:25:51 mocha kernel: [    0.865313] Time: hpet clocksource has been installed.
Sep  1 21:25:51 mocha kernel: [    0.865326] CPU0 attaching sched-domain:
Sep  1 21:25:51 mocha kernel: [    0.865327]  domain 0: span 03
Sep  1 21:25:51 mocha kernel: [    0.865328]   groups: 01 02
Sep  1 21:25:51 mocha kernel: [    0.865330] CPU1 attaching sched-domain:
Sep  1 21:25:51 mocha kernel: [    0.865330]  domain 0: span 03
Sep  1 21:25:51 mocha kernel: [    0.865331]   groups: 02 01
Sep  1 21:25:51 mocha kernel: [    0.865450] CPU1 is up
Sep  1 21:25:51 mocha kernel: [    0.866793] PM: Writing back config space on device 0000:00:02.1 at offset 4 (was 0, writing f3180000)
Sep  1 21:25:51 mocha kernel: [    0.866797] PM: Writing back config space on device 0000:00:02.1 at offset 1 (was 900000, writing 900007)
Sep  1 21:25:51 mocha kernel: [    0.866808] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  1 21:25:51 mocha kernel: [    0.866812] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Sep  1 21:25:51 mocha kernel: [    0.866849] usb usb1: root hub lost power or was reset
Sep  1 21:25:51 mocha kernel: [    0.866867] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 17
Sep  1 21:25:51 mocha kernel: [    0.866871] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Sep  1 21:25:51 mocha kernel: [    0.866905] usb usb2: root hub lost power or was reset
Sep  1 21:25:51 mocha kernel: [    0.866921] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 18
Sep  1 21:25:51 mocha kernel: [    0.866925] PCI: Setting latency timer of device 0000:00:1a.2 to 64
Sep  1 21:25:51 mocha kernel: [    0.866959] usb usb3: root hub lost power or was reset
Sep  1 21:25:51 mocha kernel: [    0.869317] Switched to high resolution mode on CPU 1
Sep  1 21:25:51 mocha kernel: [    0.880508] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
Sep  1 21:25:51 mocha kernel: [    0.880513] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Sep  1 21:25:51 mocha kernel: [    0.896496] PM: Writing back config space on device 0000:00:1b.0 at offset f (was 100, writing 103)
Sep  1 21:25:51 mocha kernel: [    0.896508] PM: Writing back config space on device 0000:00:1b.0 at offset 4 (was 4, writing f3200004)
Sep  1 21:25:51 mocha kernel: [    0.896511] PM: Writing back config space on device 0000:00:1b.0 at offset 3 (was 0, writing 8)
Sep  1 21:25:51 mocha kernel: [    0.896516] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100000, writing 100002)
Sep  1 21:25:51 mocha kernel: [    0.896529] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
Sep  1 21:25:51 mocha kernel: [    0.896534] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Sep  1 21:25:51 mocha kernel: [    0.896557] PM: Writing back config space on device 0000:00:1c.0 at offset 7 (was 2000b0b0, writing b0b0)
Sep  1 21:25:51 mocha kernel: [    0.896585] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Sep  1 21:25:51 mocha kernel: [    0.896597] PM: Writing back config space on device 0000:00:1c.4 at offset f (was 100, writing 10a)
Sep  1 21:25:51 mocha kernel: [    0.896603] PM: Writing back config space on device 0000:00:1c.4 at offset 9 (was 10001, writing 1fff1)
Sep  1 21:25:51 mocha kernel: [    0.896606] PM: Writing back config space on device 0000:00:1c.4 at offset 8 (was 0, writing f0f0f000)
Sep  1 21:25:51 mocha kernel: [    0.896609] PM: Writing back config space on device 0000:00:1c.4 at offset 7 (was 0, writing c0c0)
Sep  1 21:25:51 mocha kernel: [    0.896614] PM: Writing back config space on device 0000:00:1c.4 at offset 3 (was 810000, writing 810008)
Sep  1 21:25:51 mocha kernel: [    0.896617] PM: Writing back config space on device 0000:00:1c.4 at offset 1 (was 100000, writing 100407)
Sep  1 21:25:51 mocha kernel: [    0.896636] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Sep  1 21:25:51 mocha kernel: [    0.896643] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
Sep  1 21:25:51 mocha kernel: [    0.896647] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Sep  1 21:25:51 mocha kernel: [    0.896682] usb usb4: root hub lost power or was reset
Sep  1 21:25:51 mocha kernel: [    0.896697] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
Sep  1 21:25:51 mocha kernel: [    0.896700] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Sep  1 21:25:51 mocha kernel: [    0.896735] usb usb5: root hub lost power or was reset
Sep  1 21:25:51 mocha kernel: [    0.896751] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Sep  1 21:25:51 mocha kernel: [    0.896754] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Sep  1 21:25:51 mocha kernel: [    0.896789] usb usb6: root hub lost power or was reset
Sep  1 21:25:51 mocha kernel: [    0.912475] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
Sep  1 21:25:51 mocha kernel: [    0.912481] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Sep  1 21:25:51 mocha kernel: [    0.912542] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Sep  1 21:25:51 mocha kernel: [    0.928484] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
Sep  1 21:25:51 mocha kernel: [    0.928488] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Sep  1 21:25:51 mocha kernel: [    0.944460] PM: Writing back config space on device 0000:00:1f.5 at offset 1 (was 2b00003, writing 2b00007)
Sep  1 21:25:51 mocha kernel: [    0.944473] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 20
Sep  1 21:25:51 mocha kernel: [    0.944477] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Sep  1 21:25:51 mocha kernel: [    0.960438] PM: Writing back config space on device 0000:02:00.0 at offset f (was 100, writing 10a)
Sep  1 21:25:51 mocha kernel: [    0.960453] PM: Writing back config space on device 0000:02:00.0 at offset 8 (was 1, writing c401)
Sep  1 21:25:51 mocha kernel: [    0.960458] PM: Writing back config space on device 0000:02:00.0 at offset 7 (was 1, writing c301)
Sep  1 21:25:51 mocha kernel: [    0.960463] PM: Writing back config space on device 0000:02:00.0 at offset 6 (was 1, writing c201)
Sep  1 21:25:51 mocha kernel: [    0.960468] PM: Writing back config space on device 0000:02:00.0 at offset 5 (was 1, writing c101)
Sep  1 21:25:51 mocha kernel: [    0.960473] PM: Writing back config space on device 0000:02:00.0 at offset 4 (was 1, writing c001)
Sep  1 21:25:51 mocha kernel: [    0.960478] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 8)
Sep  1 21:25:51 mocha kernel: [    0.960485] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 100000, writing 100007)
Sep  1 21:25:51 mocha kernel: [    0.960511] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  1 21:25:51 mocha kernel: [    0.960516] PCI: Setting latency timer of device 0000:02:00.0 to 64
Sep  1 21:25:51 mocha kernel: [    0.960535] PM: Writing back config space on device 0000:03:05.0 at offset f (was 40200100, writing 40200105)
Sep  1 21:25:51 mocha kernel: [    0.960546] PM: Writing back config space on device 0000:03:05.0 at offset 5 (was 0, writing f2005000)
Sep  1 21:25:51 mocha kernel: [    0.960550] PM: Writing back config space on device 0000:03:05.0 at offset 4 (was 1, writing d001)
Sep  1 21:25:51 mocha kernel: [    0.960553] PM: Writing back config space on device 0000:03:05.0 at offset 3 (was 0, writing 4008)
Sep  1 21:25:51 mocha kernel: [    0.960557] PM: Writing back config space on device 0000:03:05.0 at offset 1 (was 2b00000, writing 2b00013)
Sep  1 21:25:51 mocha kernel: [    0.976416] PM: Writing back config space on device 0000:03:07.0 at offset f (was 4020100, writing 4020109)
Sep  1 21:25:51 mocha kernel: [    0.976431] PM: Writing back config space on device 0000:03:07.0 at offset 5 (was 0, writing f2000000)
Sep  1 21:25:51 mocha kernel: [    0.976435] PM: Writing back config space on device 0000:03:07.0 at offset 4 (was 0, writing f2004000)
Sep  1 21:25:51 mocha kernel: [    0.976439] PM: Writing back config space on device 0000:03:07.0 at offset 3 (was 0, writing 2008)
Sep  1 21:25:51 mocha kernel: [    0.976444] PM: Writing back config space on device 0000:03:07.0 at offset 1 (was 2100000, writing 2100006)
Sep  1 21:25:51 mocha kernel: [    1.026022] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f2004000-f20047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Sep  1 21:25:51 mocha kernel: [    1.026395] serial 00:08: activated
Sep  1 21:25:51 mocha kernel: [    1.026737] parport_pc 00:09: activated
Sep  1 21:25:51 mocha kernel: [    1.284626] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Sep  1 21:25:51 mocha kernel: [    1.284628] ata1.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Sep  1 21:25:51 mocha kernel: [    1.456456] ata1.00: configured for UDMA/33
Sep  1 21:25:51 mocha kernel: [    1.891504] sd 2:0:0:0: [sda] Starting disk
Sep  1 21:25:51 mocha kernel: [    5.967309] ata3: port is slow to respond, please be patient (Status 0x80)
Sep  1 21:25:51 mocha kernel: [    5.980296] ata5: port is slow to respond, please be patient (Status 0x80)
Sep  1 21:25:51 mocha kernel: [    7.865533] ata3.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Sep  1 21:25:51 mocha kernel: [    7.865534] ata3.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Sep  1 21:25:51 mocha kernel: [    7.865535] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Sep  1 21:25:51 mocha kernel: [    7.877635] ata3.00: configured for UDMA/133
Sep  1 21:25:51 mocha kernel: [    7.896769] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Sep  1 21:25:51 mocha kernel: [    7.896776] sd 4:0:0:0: [sdb] Starting disk
Sep  1 21:25:51 mocha kernel: [    7.896782] sd 2:0:0:0: [sda] Write Protect is off
Sep  1 21:25:51 mocha kernel: [    7.896784] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep  1 21:25:51 mocha kernel: [    7.896802] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  1 21:25:51 mocha kernel: [   10.959188] ata5: device not ready (errno=-16), forcing hardreset
Sep  1 21:25:51 mocha kernel: [   12.889230] ata5.00: revalidation failed (errno=-2)
Sep  1 21:25:51 mocha kernel: [   12.889231] ata5: failed to recover some devices, retrying in 5 secs
Sep  1 21:25:51 mocha kernel: [   18.051084] ata5.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Sep  1 21:25:51 mocha kernel: [   18.051086] ata5.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Sep  1 21:25:51 mocha kernel: [   18.051087] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Sep  1 21:25:51 mocha kernel: [   18.076491] ata5.00: configured for UDMA/133
Sep  1 21:25:51 mocha kernel: [   18.086675] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Sep  1 21:25:51 mocha kernel: [   18.086685] sd 4:0:0:0: [sdb] Write Protect is off
Sep  1 21:25:51 mocha kernel: [   18.086687] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Sep  1 21:25:51 mocha kernel: [   18.086700] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  1 21:25:51 mocha kernel: [   18.098885] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  1 21:25:51 mocha kernel: [   18.100068] PM: Finishing wakeup.
Sep  1 21:25:51 mocha kernel: [   18.100068] Restarting tasks ... <6>usb 1-1: USB disconnect, address 4
Sep  1 21:25:51 mocha kernel: [   18.100709] done.
Sep  1 21:25:51 mocha kernel: [   18.166354] r8169 Gigabit Ethernet driver 2.2LK loaded
Sep  1 21:25:51 mocha kernel: [   18.166369] ACPI: PCI Interrupt 0000:03:05.0[A] -> GSI 21 (level, low) -> IRQ 17
Sep  1 21:25:51 mocha kernel: [   18.166652] eth0: RTL8169sc/8110sc at 0xf89cc000, 00:1a:4d:50:f2:99, XID 18000000 IRQ 17
Sep  1 21:25:51 mocha kernel: [   18.173200] r8169: eth0: link down
Sep  1 21:25:51 mocha kernel: [   18.174262] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep  1 21:25:51 mocha kernel: [   18.479470] usb 1-1: new low speed USB device using uhci_hcd and address 6
Sep  1 21:25:51 mocha kernel: [   18.661230] usb 1-1: configuration #1 chosen from 1 choice
Sep  1 21:25:51 mocha kernel: [   18.697354] input: Gyration Gyration RF Technology Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0/input/input8
Sep  1 21:25:51 mocha kernel: [   18.743255] input,hiddev96,hidraw0: USB HID v1.10 Keyboard [Gyration Gyration RF Technology Receiver] on usb-0000:00:1a.0-1
Sep  1 21:25:51 mocha kernel: [   18.769283] input: Gyration Gyration RF Technology Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.1/input/input9
Sep  1 21:25:51 mocha kernel: [   18.830161] input,hiddev97,hidraw1: USB HID v1.20 Mouse [Gyration Gyration RF Technology Receiver] on usb-0000:00:1a.0-1
Sep  1 21:25:51 mocha kernel: [   18.830222] usb 1-2: USB disconnect, address 5
Sep  1 21:25:51 mocha kernel: [   18.830313] lirc_mceusb2[5]: usb remote disconnected
Sep  1 21:25:51 mocha kernel: [   19.069871] usb 1-2: new full speed USB device using uhci_hcd and address 7
Sep  1 21:25:52 mocha kernel: [   19.224590] usb 1-2: config 1 interface 0 altsetting 0 endpoint 0x1 has an invalid bInterval 0, changing to 32
Sep  1 21:25:52 mocha kernel: [   19.224593] usb 1-2: config 1 interface 0 altsetting 0 endpoint 0x82 has an invalid bInterval 0, changing to 32
Sep  1 21:25:52 mocha kernel: [   19.256606] usb 1-2: configuration #1 chosen from 1 choice
Sep  1 21:25:52 mocha kernel: [   19.369551] usb 1-2: reset full speed USB device using uhci_hcd and address 7
Sep  1 21:25:52 mocha kernel: [   19.521337] lirc_dev: lirc_register_plugin: sample_rate: 0
Sep  1 21:25:52 mocha kernel: [   19.525295] lirc_mceusb2[7]: Topseed Technology Corp. eHome Infrared Transceiver on usb1:7
Sep  1 21:25:52 mocha kernel: [   19.801883] r8169: eth0: link up
Sep  1 21:25:52 mocha kernel: [   19.802883] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
================>>>>>>> /I have to restart the machine here/ ========>> Sep  1 21:29:13 mocha kernel: Inspecting /boot/System.map-2.6.24-19-generic    
Sep  1 21:29:13 mocha kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.


```

---

### Post by qhex16 on 2008-09-02
> **coscos said:**
> I have exactly the same problem. I am running mythbuntu 8.04.1, Gigabyte GA-G33M-S2H motherboard, with onboard video (Intel GMA 3100), audio(Realtek ALC889A) and network card (Realtek 8110SC). I also have E8400 CPU as OP. The machine seems suspended fine, but the resume never works. It always hangs. I tried many ways (s2ram, apm, ...) and none of them works. :confused:

Somebody please help! Following are the log files:


coscos, from my /var/log/kern.log, I'm only getting one PCI interrupt disabled message, and then...nothing, until I reboot. So it seems that your resume is getting farther than mine..

I have tried suspending from a virtual console (Ctrl-Alt-F1), but the problem is the same.

---

### Post by xeth_delta on 2008-09-02
> **qhex16 said:**
> coscos, from my /var/log/kern.log, I'm only getting one PCI interrupt disabled message, and then...nothing, until I reboot. So it seems that your resume is getting farther than mine..

I have tried suspending from a virtual console (Ctrl-Alt-F1), but the problem is the same.

I do not think the virtual console would be enough. Try booting in recovery mode and suspend in there.

---

### Post by coscos on 2008-09-02
yes, I think my resume did go farther. After the resume is "finish", or hang, the LCD monitor's back light is actually on and the receiver (I connect my mythbuntu box to LCD TV through a receiver box) detected the HDMI output is on. But the screen is blank and no response to keyboard/mouse, and no network response (ssh/ping).

> **qhex16 said:**
> coscos, from my /var/log/kern.log, I'm only getting one PCI interrupt disabled message, and then...nothing, until I reboot. So it seems that your resume is getting farther than mine..

I have tried suspending from a virtual console (Ctrl-Alt-F1), but the problem is the same.

---

### Post by qhex16 on 2008-09-02
> **xeth_delta said:**
> I do not think the virtual console would be enough. Try booting in recovery mode and suspend in there.

Just tried it; same result. No LCD backlight, no power to USB or PS/2 devices.  I'm going to try upgrading to the latest kernel 2.6.27-1, at [http://kernel.ubuntu.com/pub/next/2.6.27-rc3/hardy/](http://kernel.ubuntu.com/pub/next/2.6.27-rc3/hardy/)

**Update:** no luck, same problem...

---

### Post by coscos on 2008-09-02
Your running a 64bit system, which can have extra troubles ... Let us know what's going on with your test.

> **qhex16 said:**
> Just tried it; same result. No LCD backlight, no power to USB or PS/2 devices.  I'm going to try upgrading to the latest kernel 2.6.27-1, at [http://kernel.ubuntu.com/pub/next/2.6.27-rc3/hardy/](http://kernel.ubuntu.com/pub/next/2.6.27-rc3/hardy/)

**Update:** no luck, same problem...

---

### Post by xeth_delta on 2008-09-02
> **qhex16 said:**
> Just tried it; same result. No LCD backlight, no power to USB or PS/2 devices.  I'm going to try upgrading to the latest kernel 2.6.27-1, at [http://kernel.ubuntu.com/pub/next/2.6.27-rc3/hardy/](http://kernel.ubuntu.com/pub/next/2.6.27-rc3/hardy/)

**Update:** no luck, same problem...

Did you try also unloading several modules? Try to have the minimum necessary, check with lsmod, and then load one by one the ones that might be at the root of the problem.

---

### Post by coscos on 2008-09-02
Do you mean unload modules before the suspend? There are tens of them, how do I know where to start?

> **xeth_delta said:**
> Did you try also unloading several modules? Try to have the minimum necessary, check with lsmod, and then load one by one the ones that might be at the root of the problem.

---

### Post by xeth_delta on 2008-09-02
> **coscos said:**
> Do you mean unload modules before the suspend? There are tens of them, how do I know where to start?

if you start with a recovery mode terminal there should be a lot less modules loaded than in a virtual terminal, or X session.

Start with sound modules, video driver, network, firewire...

If you manage to identify the problematic one, there is a way to force it to be unloaded before sleep, and reload after resume.

---

### Post by qhex16 on 2008-09-02
> **xeth_delta said:**
> if you start with a recovery mode terminal there should be a lot less modules loaded than in a virtual terminal, or X session.

Start with sound modules, video driver, network, firewire...

If you manage to identify the problematic one, there is a way to force it to be unloaded before sleep, and reload after resume.

I've done this, with many, many modules

From recovery mode:
```
rmmod usbhid hid usbcore visor usbserial usbhid ehci_hcd uhci_hcd parport parport_pc lp ieee1394 ohci1394 sr_mod sbp2 cdrom
rmmod snd_pcsp snd_seq_dummy snd_seq_oss snd_hda_intel snd_seq_midi snd_pcm_oss snd_mixer_oss snd_rawmidi snd_seq_midi_event snd_pcm snd_seq snd_timer snd_seq_device snd_seq_dummy snd snd_page_alloc soundcore
rmmod shpchp pci_hotplug
```

Still fails to resume, with the hard drive light on. I think there is something much lower-level in the kernel suspend process that is going wrong, but I have no idea how to begin troubleshooting that! No log file reveals anything going wrong!

---

### Post by xeth_delta on 2008-09-02
> **qhex16 said:**
> I've done this, with many, many modules

From recovery mode:
```
rmmod usbhid hid usbcore visor usbserial usbhid ehci_hcd uhci_hcd parport parport_pc lp ieee1394 ohci1394 sr_mod sbp2 cdrom
rmmod snd_pcsp snd_seq_dummy snd_seq_oss snd_hda_intel snd_seq_midi snd_pcm_oss snd_mixer_oss snd_rawmidi snd_seq_midi_event snd_pcm snd_seq snd_timer snd_seq_device snd_seq_dummy snd snd_page_alloc soundcore
rmmod shpchp pci_hotplug
```

Still fails to resume, with the hard drive light on. I think there is something much lower-level in the kernel suspend process that is going wrong, but I have no idea how to begin troubleshooting that! No log file reveals anything going wrong!

Yeah, but it's strange though, as your system seems standard, nothing exotic that could couse problems.
In any case if something comes to my mind I'll let you know, and hopefully someone else who knows more will come and help.

---

### Post by coscos on 2008-09-02
Is there a way to find out which module caused the resume failure? For example, some log files or adding some boot configurations ... Test module one by one is really time consuming ... :(

---

### Post by qhex16 on 2008-09-02
> **coscos said:**
> Is there a way to find out which module caused the resume failure? For example, some log files or adding some boot configurations ... Test module one by one is really time consuming ... :(

I found this guide on using pm_trace, although it did not work for me. (resume is not getting far enough to trigger this functionality, I believe.) [http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-advanced.html](http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-advanced.html)

It's supposed to set your RTC (Real Time Clock) to encode which was the last module that was being loaded. Then when you reboot, it will compare the hash in the RTC to the hashes of your modules and tell you which one it failed on.

---

### Post by coscos on 2008-09-03
After re-exam my log files, I found following lines in my dmesg:

```

[   22.753601] Using IPI No-Shortcut mode
[   22.753642] swsusp: Resume From Partition /dev/sda3
[   22.753643] PM: Checking swsusp image.
[   22.753648] swsusp: Error -6 check for resume file
[   22.753649] PM: Resume from disk failed.

```

Searching on google and I found this article: 
[http://www.columbia.edu/~ariel/acpi/acpi_howto.txt]("http://www.columbia.edu/~ariel/acpi/acpi_howto.txt")

and the author claims:
> If you see this message: swsusp: Error -6 check for resume file, it means that your swap is not on a physical partition or that you have underlying modules that need to be loaded before the partition can be found. Check that IDE and/or SCSI support is built in directly to the kernel, and try again until this message goes away.


But I don't understand how possibly that my ubuntu 8.04 could not support IDE or SATA. And I don't how to check that either. 

anybody has a clue?

**Update: I do realize that the swap usage is always 0. anything wrong?**
```

coscos@mocha:~$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda3                               partition       2996112 0       -1

```

---

### Post by coscos on 2008-09-03
I tried it, but failed again. I got this in log:
```

[   22.753721]   Magic number: 0:716:196
[   22.753723]   hash matches /build/buildd/linux-2.6.24/drivers/base/power/main.c:97
[   22.753727]   hash matches device ttys8
[   22.753728]   hash matches device ttypb

```

Anybody know what is the devide "ttypb"?

> **qhex16 said:**
> I found this guide on using pm_trace, although it did not work for me. (resume is not getting far enough to trigger this functionality, I believe.) [http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-advanced.html](http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-advanced.html)

It's supposed to set your RTC (Real Time Clock) to encode which was the last module that was being loaded. Then when you reboot, it will compare the hash in the RTC to the hashes of your modules and tell you which one it failed on.

---

### Post by coscos on 2008-09-03
bump for help!

---

### Post by coscos on 2008-09-04
OK, finally I give up. But I found the s2both/s2disk package is working fine. Check this instruction out:

[http://en.opensuse.org/S2ram]("http://en.opensuse.org/S2ram")

The new package doesn't have s2ram though (replaced by s2both). I just need to unload a module "lirc" before running "s2both", ohterwise there is kernel panic.

Give it a try.

---

### Post by sk545 on 2008-10-01
I am having this problem as well, but its a bit different.  Majority of the time (90%), it resumes fine (pressing the power button on computer), but every now and then during resume the hard drive light stays lit with no video, but the mouse and keyboard have a light.  Only way to get it back is by rebooting.

Specs: Ubunto 8.10
mobo: MSI K8N Neo4 Platinum
Video: 6600GT Nvidia

Where do I look for errors?  There are tons of logs, which one should I be looking at after reboot?

---

