---
title: "Resuming from suspend in kubuntu gutsy restart my X session"
date: 2008-02-15
forum: Desktop Environments
---

### Post by erlguta on 2008-02-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/157395](https://bugs.launchpad.net/ubuntu/+bug/157395) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello.
Resuming from suspend in a fresh installed kubuntu gutsy restart my X session prompting again the kdm login.
In Feisty it worked ok.
Info:
- Kubuntu gutsy 7.10 updated (2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux)
- Dell dimension 8300, Intel(R) Pentium(R) 4 CPU 2.60GHz, 1GB Ram
- Nvidia FX5200 with nvidia dirver (in the oficial way) properly installed
dpkg -l nvidia*
ii nvidia-glx-new 100.14.19+2.6.22.4-14.9 NVIDIA binary XFree86 4.x/X.Org 'new' driver
- In BIOS enabled Suspend mode= S3 (with the other option S1, does not works)

Here is my dmesg:

```

- dmesg:
[ 9434.349907] PM: Preparing system for mem sleep
[ 9434.349915] Stopping tasks ... done.
[ 9434.992451] Suspending console(s)
[ 9435.056650] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 9435.362103] sd 0:0:0:0: [sda] Stopping disk
[ 9435.529937] usb_device usbdev5.1: PM: suspend 0->2, parent usb5 already 2
[ 9435.529940] usb_endpoint usbdev5.1_ep81: PM: suspend 0->2, parent 5-0:1.0 already 2
[ 9435.529943] hub 5-0:1.0: PM: suspend 2->2, parent usb5 already 2
[ 9435.529946] usb_endpoint usbdev5.1_ep00: PM: suspend 0->2, parent usb5 already 2
[ 9435.529949] usb_device usbdev4.1: PM: suspend 0->2, parent usb4 already 2
[ 9435.529952] usb_endpoint usbdev4.1_ep81: PM: suspend 0->2, parent 4-0:1.0 already 2
[ 9435.529955] hub 4-0:1.0: PM: suspend 2->2, parent usb4 already 2
[ 9435.529957] usb_endpoint usbdev4.1_ep00: PM: suspend 0->2, parent usb4 already 2
[ 9435.529976] usb_device usbdev2.1: PM: suspend 0->2, parent usb2 already 2
[ 9435.529979] usb_endpoint usbdev2.1_ep81: PM: suspend 0->2, parent 2-0:1.0 already 2
[ 9435.529981] hub 2-0:1.0: PM: suspend 2->2, parent usb2 already 2
[ 9435.529984] usb_endpoint usbdev2.1_ep00: PM: suspend 0->2, parent usb2 already 2
[ 9435.530837] pnp: Device 00:08 disabled.
[ 9435.531280] pnp: Device 00:07 disabled.
[ 9435.540155] ACPI: PCI interrupt for device 0000:02:01.0 disabled
[ 9435.555623] NVRM: RmPowerManagement: 3
[ 9435.641406] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[ 9435.641411] pci_set_power_state(): 0000:00:1f.2: state=3, current state=5
[ 9435.641489] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[ 9435.641493] pci_set_power_state(): 0000:00:1f.1: state=3, current state=5
[ 9435.641593] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[ 9435.655443] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
[ 9435.655474] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[ 9435.655504] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[ 9435.655534] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[ 9435.656331] Disabling non-boot CPUs ...
[ 9435.669496] CPU 1 is now offline
[ 9435.669500] SMP alternatives: switching to UP code
[ 9435.670074] CPU1 is down
[ 9435.670078] PM: Entering mem sleep
[ 0.251798] Back to C!
[ 0.252569] PM: Finishing wakeup.
[ 0.252571] Enabling non-boot CPUs ...
[ 0.273868] SMP alternatives: switching to SMP code
[ 0.274069] Booting processor 1/1 eip 3000
[ 0.284113] Initializing CPU#1
[ 0.361608] Calibrating delay using timer specific routine.. 5187.29 BogoMIPS (lpj=10374591)
[ 0.361617] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[ 0.361629] CPU: Trace cache: 12K uops, L1 D cache: 8K
[ 0.361632] CPU: L2 cache: 512K
[ 0.361635] CPU: Physical Processor ID: 0
[ 0.361637] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[ 0.361900] CPU1: Intel(R) Pentium(R) 4 CPU 2.60GHz stepping 09
[ 0.361921] checking TSC synchronization [CPU#0 -> CPU#1]:
[ 0.381886] Measured 27634397504 cycles TSC warp between CPUs, turning off TSC clock.
[ 9444.972000] Marking TSC unstable due to: check_tsc_sync_source failed.
[ 9444.992000] Time: acpi_pm clocksource has been installed.
[ 9444.992000] CPU1 is up
[ 9444.996000] Switched to high resolution mode on CPU 1
[ 9444.996000] PM: Writing back config space on device 0000:00:00.0 at offset 1 (was 900006, writing 20900106)
[ 9444.996000] PM: Writing back config space on device 0000:00:01.0 at offset 3 (was 10000, writing 14000)
[ 9444.996000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 9444.996000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[ 9444.996000] PM: Writing back config space on device 0000:00:1d.0 at offset f (was 100, writing 10b)
[ 9444.996000] usb usb1: root hub lost power or was reset
[ 9444.996000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[ 9444.996000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[ 9444.996000] PM: Writing back config space on device 0000:00:1d.1 at offset f (was 200, writing 20a)
[ 9444.996000] usb usb2: root hub lost power or was reset
[ 9444.996000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[ 9444.996000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[ 9444.996000] PM: Writing back config space on device 0000:00:1d.2 at offset f (was 300, writing 309)
[ 9444.996000] usb usb3: root hub lost power or was reset
[ 9444.996000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[ 9444.996000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[ 9444.996000] PM: Writing back config space on device 0000:00:1d.3 at offset f (was 100, writing 10b)
[ 9444.996000] usb usb4: root hub lost power or was reset
[ 9445.012000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[ 9445.012000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[ 9445.012000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[ 9445.012000] PM: Writing back config space on device 0000:00:1d.7 at offset f (was 400, writing 405)
[ 9445.012000] PM: Writing back config space on device 0000:00:1d.7 at offset 4 (was 0, writing ffa80800)
[ 9445.012000] PM: Writing back config space on device 0000:00:1d.7 at offset 1 (was 2900006, writing 2900106)
[ 9445.012000] PM: Writing back config space on device 0000:00:1e.0 at offset f (was 0, writing 20000)
[ 9445.012000] PM: Writing back config space on device 0000:00:1e.0 at offset 8 (was fff0, writing fcf0fcf0)
[ 9445.012000] PM: Writing back config space on device 0000:00:1e.0 at offset 7 (was 28000f0, writing 280d0d0)
[ 9445.012000] PM: Writing back config space on device 0000:00:1e.0 at offset 6 (was 20200, writing 20020200)
[ 9445.012000] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 800005, writing 800107)
[ 9445.012000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[ 9445.012000] PM: Writing back config space on device 0000:00:1f.0 at offset 1 (was 280000f, writing 280010f)
[ 9445.012000] PM: Writing back config space on device 0000:00:1f.1 at offset f (was 100, writing 109)
[ 9445.012000] PM: Writing back config space on device 0000:00:1f.1 at offset 9 (was 0, writing febffc00)
[ 9445.012000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[ 9445.012000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[ 9445.012000] PM: Writing back config space on device 0000:00:1f.2 at offset f (was 100, writing 109)
[ 9445.012000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[ 9445.012000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[ 9445.012000] PM: Writing back config space on device 0000:00:1f.3 at offset f (was 200, writing 203)
[ 9445.012000] PM: Writing back config space on device 0000:00:1f.3 at offset 8 (was 8c1, writing efe1)
[ 9445.016000] NVRM: RmPowerManagement: 4
[ 9445.296000] PM: Writing back config space on device 0000:02:01.0 at offset f (was 14020100, writing 1402010a)
[ 9445.296000] PM: Writing back config space on device 0000:02:01.0 at offset 4 (was 1, writing df21)
[ 9445.296000] PM: Writing back config space on device 0000:02:01.0 at offset 3 (was 800000, writing 804000)
[ 9445.296000] PM: Writing back config space on device 0000:02:01.0 at offset 1 (was 2900000, writing 2900101)
[ 9445.296000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 22 (level, low) -> IRQ 21
[ 9445.304000] PM: Writing back config space on device 0000:02:01.1 at offset 4 (was 1, writing df19)
[ 9445.304000] PM: Writing back config space on device 0000:02:01.1 at offset 3 (was 800000, writing 804000)
[ 9445.304000] PM: Writing back config space on device 0000:02:01.1 at offset 1 (was 2900000, writing 2900105)
[ 9445.304000] PM: Writing back config space on device 0000:02:03.0 at offset f (was 1c0a0100, writing 1c0a010a)
[ 9445.304000] PM: Writing back config space on device 0000:02:03.0 at offset 4 (was 0, writing fcff0000)
[ 9445.304000] PM: Writing back config space on device 0000:02:03.0 at offset 3 (was 0, writing a810)
[ 9445.304000] PM: Writing back config space on device 0000:02:03.0 at offset 1 (was 2900000, writing 2900112)
[ 9445.304000] PM: Writing back config space on device 0000:02:08.0 at offset f (was 38080100, writing 38080105)
[ 9445.304000] PM: Writing back config space on device 0000:02:08.0 at offset 5 (was 1, writing df41)
[ 9445.304000] PM: Writing back config space on device 0000:02:08.0 at offset 4 (was 0, writing fcfef000)
[ 9445.304000] PM: Writing back config space on device 0000:02:08.0 at offset 3 (was 0, writing 4010)
[ 9445.304000] PM: Writing back config space on device 0000:02:08.0 at offset 1 (was 2900000, writing 2900113)
[ 9445.308000] pnp: Device 00:07 activated.
[ 9445.312000] pnp: Device 00:08 activated.
[ 9445.472000] usb_endpoint usbdev5.1_ep00: PM: resume from 0, parent usb5 still 2
[ 9445.472000] usb_endpoint usbdev5.1_ep81: PM: resume from 0, parent 5-0:1.0 still 2
[ 9445.472000] usb_device usbdev5.1: PM: resume from 0, parent usb5 still 2
[ 9445.472000] sd 0:0:0:0: [sda] Starting disk
[ 9446.176000] ata2.00: configured for UDMA/66
[ 9448.608000] ata1.00: configured for UDMA/133
[ 9448.628000] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
[ 9448.628000] usb_endpoint usbdev3.2_ep00: PM: resume from 0, parent 3-1 still 2
[ 9448.628000] usbhid 3-1:1.0: PM: resume from 2, parent 3-1 still 2
[ 9448.628000] usb_endpoint usbdev3.2_ep81: PM: resume from 0, parent 3-1:1.0 still 2
[ 9448.628000] usb_device usbdev3.2: PM: resume from 0, parent 3-1 still 2
[ 9448.628000] sd 0:0:0:0: [sda] Write Protect is off
[ 9448.628000] usb_endpoint usbdev3.3_ep00: PM: resume from 0, parent 3-2 still 2
[ 9448.628000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 9448.628000] usbhid 3-2:1.0: PM: resume from 2, parent 3-2 still 2
[ 9448.628000] usb_endpoint usbdev3.3_ep81: PM: resume from 0, parent 3-2:1.0 still 2
[ 9448.628000] usb_device usbdev3.3: PM: resume from 0, parent 3-2 still 2
[ 9448.628000] usb_endpoint usbdev1.4_ep00: PM: resume from 0, parent 1-1 still 2
[ 9448.628000] hci_usb 1-1:1.0: PM: resume from 2, parent 1-1 still 2
[ 9448.628000] usb_endpoint usbdev1.4_ep81: PM: resume from 0, parent 1-1:1.0 still 2
[ 9448.628000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 9448.628000] usb_endpoint usbdev1.4_ep82: PM: resume from 0, parent 1-1:1.0 still 2
[ 9448.628000] usb_endpoint usbdev1.4_ep02: PM: resume from 0, parent 1-1:1.0 still 2
[ 9448.628000] hci_usb 1-1:1.1: PM: resume from 2, parent 1-1 still 2
[ 9448.628000] usb 1-1:1.2: PM: resume from 2, parent 1-1 still 2
[ 9448.628000] usb_endpoint usbdev1.4_ep84: PM: resume from 0, parent 1-1:1.2 still 2
[ 9448.628000] usb_endpoint usbdev1.4_ep04: PM: resume from 0, parent 1-1:1.2 still 2
[ 9448.628000] usb_device usbdev1.4: PM: resume from 0, parent 1-1 still 2
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset f (was ffffffff, writing 0)
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset e (was ffffffff, writing 0)
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset d (was ffffffff, writing 0)
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset c (was ffffffff, writing 0)
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset b (was ffffffff, writing 0)
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset a (was ffffffff, writing 0)
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset 9 (was ffffffff, writing 0)
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset 8 (was ffffffff, writing 0)
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset 7 (was ffffffff, writing 0)
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset 6 (was ffffffff, writing 0)
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset 5 (was ffffffff, writing 0)
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset 4 (was ffffffff, writing fecf0000)
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset 3 (was ffffffff, writing 0)
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset 2 (was ffffffff, writing 8800002)
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset 1 (was ffffffff, writing 800002)
[ 9448.628000] PM: Writing back config space on device 0000:00:06.0 at offset 0 (was ffffffff, writing 257e8086)
[ 9448.628000] usb_endpoint usbdev1.4_ep83: PM: resume from 0, parent 1-1:1.1 still 2
[ 9448.628000] usb_endpoint usbdev1.4_ep03: PM: resume from 0, parent 1-1:1.1 still 2
[ 9448.628000] bluetooth hci0: PM: resume from 0, parent 1-1:1.0 still 2
[ 9448.632000] Restarting tasks ... <6>usb 1-1: USB disconnect, address 4
[ 9448.636000] done.
[ 9449.420000] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 9449.660000] ath_pci: 0.9.4.5 (0.9.3.2)
[ 9449.660000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> IRQ 17
[ 9449.848000] usb 1-1: configuration #1 chosen from 1 choice
[ 9449.864000] usb 3-1: USB disconnect, address 2
[ 9449.916000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[ 9449.916000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 9449.916000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 9449.916000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[ 9449.916000] wifi0: mac 5.6 phy 4.1 radio 4.6
[ 9449.916000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[ 9449.916000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[ 9449.916000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[ 9449.916000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[ 9449.916000] wifi0: Use hw queue 8 for CAB traffic
[ 9449.916000] wifi0: Use hw queue 9 for beacons
[ 9450.104000] usb 3-1: new low speed USB device using uhci_hcd and address 4
[ 9450.160000] wifi0: Atheros 5212: mem=0xfcff0000, irq=17
[ 9450.204000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[ 9450.204000] e100: Copyright(c) 1999-2006 Intel Corporation
[ 9450.208000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[ 9450.232000] e100: eth0: e100_probe: addr 0xfcfef000, irq 20, MAC addr 00:0C:F1:75:26:34
[ 9450.276000] usb 3-1: configuration #1 chosen from 1 choice
[ 9450.296000] input: Dell Dell USB Keyboard as /class/input/input6
[ 9450.296000] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.2-1
[ 9450.296000] usb 3-2: USB disconnect, address 3
[ 9450.300000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9450.564000] usb 3-2: new low speed USB device using uhci_hcd and address 5
[ 9450.740000] usb 3-2: configuration #1 chosen from 1 choice
[ 9450.756000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input7
[ 9450.756000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.2-2
[ 9451.268000] input: Power Button (FF) as /class/input/input8
[ 9451.268000] ACPI: Power Button (FF) [PWRF]
[ 9451.268000] input: Power Button (CM) as /class/input/input9
[ 9451.272000] ACPI: Power Button (CM) [VBTN]
[ 9460.112000] NVRM: Xid (0001:00): 5, Ch 00000000 M 00000ffc D 008c4480 intr 00000100
[ 9460.116000] Clocksource tsc unstable (delta = 4686672670 ns)
[ 9465.120000] ath0: no IPv6 routers present
[ 9467.020000] NVRM: Xid (0001:00): 8, Channel 00000000

```

Ask me me for more info

I would apreciate some help

Thank for your help

PD: I have put one bug in launchpad monnths ago with no reply at all (why resolve bugs in ubuntu works so bad?).

---

### Post by vprasaj on 2008-03-29
I have the same problem. After resume i get GDM (gnome version). :shock: :^o ](*,) After that i get some violent thoughts... not good. [-X

OK, info...

I use Mint Daryna (it's ubuntu for me). :-\"
2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
ii  nvidia-glx-new 100.14.19+2.6.22.4-14.10 NVIDIA binary XFree86 4.x/X.Org 'new' driver
NV 6600 gt
AMD3000+ 64
matherboard gigabyte
(yes, yes, old box...)
dmesg is too long to display...so i wont bother.

Beer from me for solution... [-o<

---

