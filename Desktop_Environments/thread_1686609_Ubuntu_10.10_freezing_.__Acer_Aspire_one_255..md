---
title: "Ubuntu 10.10 freezing .  Acer Aspire one 255."
date: 2011-02-12
forum: Desktop Environments
---

### Post by philm1983 on 2011-02-12
Hi,

I have a week old Acer Aspire one D255 which I have installed Ubuntu 10.10 onto.

Everything installed smoothly and all seems to be working as expected but about once a day the system just freezes and loses network connectivity and the only way to recover is to hold the power button down and restart it.

One thing that I do notice is that the wireless led is flashing constantly after it freezes but it is unresponsive to pings - so maybe the wireless has something to do with it.

It doesn't seem to be a specific piece of s/w causing it to freeze and there doesn't seem to be anything in the log around the time it failed (tonight it was 12/02/2011 20:15)

I have copied in the logs below from around the time it failed. The last entry is when the system came back up at 20:17.

I'm hoping this is going to be an easy fix as I bought this netbook specifically to use linux on it.

I appreciate your help with this.  Any more info let me know.

```
Feb 12 20:03:21 netbook wpa_supplicant[1256]: WPA: Group rekeying completed with 30:46:9a:7e:29:cc [GTK=TKIP]
Feb 12 20:03:21 netbook NetworkManager[1228]: <info> (wlan0): supplicant connection state:  completed -> group handshake
Feb 12 20:03:21 netbook NetworkManager[1228]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Feb 12 20:08:23 netbook kernel: [ 2387.985514] iwlagn 0000:02:00.0: Microcode SW error detected.  Restarting 0x92000000.
Feb 12 20:08:23 netbook kernel: [ 2387.985536] iwlagn 0000:02:00.0: Loaded firmware version: 128.50.3.1 build 13488
Feb 12 20:08:23 netbook kernel: [ 2387.985574] iwlagn 0000:02:00.0: Start IWL Error Log Dump:
Feb 12 20:08:23 netbook kernel: [ 2387.985584] iwlagn 0000:02:00.0: Status: 0x000312E4, count: 5
Feb 12 20:08:23 netbook kernel: [ 2387.985835] iwlagn 0000:02:00.0: Desc                               Time       data1      data2      line
Feb 12 20:08:23 netbook kernel: [ 2387.985852] iwlagn 0000:02:00.0: NMI_INTERRUPT_WDG            (#04) 1644552220 0x00000002 0x02030000 302
Feb 12 20:08:23 netbook kernel: [ 2387.985862] iwlagn 0000:02:00.0: pc      blink1  blink2  ilink1  ilink2  hcmd
Feb 12 20:08:23 netbook kernel: [ 2387.985875] iwlagn 0000:02:00.0: 0x006D0 0x00596 0x006D4 0x00892 0x02154 0x4C400A8
Feb 12 20:08:23 netbook kernel: [ 2387.985884] iwlagn 0000:02:00.0: CSR values:
Feb 12 20:08:23 netbook kernel: [ 2387.985892] iwlagn 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
Feb 12 20:08:23 netbook kernel: [ 2387.985927] iwlagn 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
Feb 12 20:08:23 netbook kernel: [ 2387.985961] iwlagn 0000:02:00.0:          CSR_INT_COALESCING: 0X0000ff40
Feb 12 20:08:23 netbook kernel: [ 2387.985994] iwlagn 0000:02:00.0:                     CSR_INT: 0X80000000
Feb 12 20:08:23 netbook kernel: [ 2387.986028] iwlagn 0000:02:00.0:                CSR_INT_MASK: 0X00000000
Feb 12 20:08:23 netbook kernel: [ 2387.986062] iwlagn 0000:02:00.0:           CSR_FH_INT_STATUS: 0X40010000
Feb 12 20:08:23 netbook kernel: [ 2387.986096] iwlagn 0000:02:00.0:                 CSR_GPIO_IN: 0X00000000
Feb 12 20:08:23 netbook kernel: [ 2387.986130] iwlagn 0000:02:00.0:                   CSR_RESET: 0X00000000
Feb 12 20:08:23 netbook kernel: [ 2387.986163] iwlagn 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
Feb 12 20:08:23 netbook kernel: [ 2387.986197] iwlagn 0000:02:00.0:                  CSR_HW_REV: 0X0000006c
Feb 12 20:08:23 netbook kernel: [ 2387.986231] iwlagn 0000:02:00.0:              CSR_EEPROM_REG: 0X007a08e5
Feb 12 20:08:23 netbook kernel: [ 2387.986265] iwlagn 0000:02:00.0:               CSR_EEPROM_GP: 0X90000001
Feb 12 20:08:23 netbook kernel: [ 2387.986299] iwlagn 0000:02:00.0:              CSR_OTP_GP_REG: 0X00010001
Feb 12 20:08:23 netbook kernel: [ 2387.986333] iwlagn 0000:02:00.0:                 CSR_GIO_REG: 0X00080042
Feb 12 20:08:23 netbook kernel: [ 2387.986367] iwlagn 0000:02:00.0:            CSR_GP_UCODE_REG: 0X000017e0
Feb 12 20:08:23 netbook kernel: [ 2387.986401] iwlagn 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
Feb 12 20:08:23 netbook kernel: [ 2387.986435] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
Feb 12 20:08:23 netbook kernel: [ 2387.986468] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
Feb 12 20:08:23 netbook kernel: [ 2387.986502] iwlagn 0000:02:00.0:                 CSR_LED_REG: 0X00000058
Feb 12 20:08:23 netbook kernel: [ 2387.986536] iwlagn 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X88033010
Feb 12 20:08:23 netbook kernel: [ 2387.986570] iwlagn 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
Feb 12 20:08:23 netbook kernel: [ 2387.986604] iwlagn 0000:02:00.0:             CSR_ANA_PLL_CFG: 0X00880300
Feb 12 20:08:23 netbook kernel: [ 2387.986638] iwlagn 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
Feb 12 20:08:23 netbook kernel: [ 2387.986672] iwlagn 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
Feb 12 20:08:23 netbook kernel: [ 2387.986680] iwlagn 0000:02:00.0: FH register values:
Feb 12 20:08:23 netbook kernel: [ 2387.986724] iwlagn 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0339c600
Feb 12 20:08:23 netbook kernel: [ 2387.986768] iwlagn 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X002f1960
Feb 12 20:08:23 netbook kernel: [ 2387.986813] iwlagn 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000058
Feb 12 20:08:23 netbook kernel: [ 2387.986858] iwlagn 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
Feb 12 20:08:23 netbook kernel: [ 2387.986902] iwlagn 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
Feb 12 20:08:23 netbook kernel: [ 2387.986947] iwlagn 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07430000
Feb 12 20:08:23 netbook kernel: [ 2387.986992] iwlagn 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
Feb 12 20:08:23 netbook kernel: [ 2387.987037] iwlagn 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
Feb 12 20:08:23 netbook kernel: [ 2387.987081] iwlagn 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
Feb 12 20:08:23 netbook kernel: [ 2387.987172] iwlagn 0000:02:00.0: Start IWL Event Log Dump: display last 1 entries
Feb 12 20:08:23 netbook kernel: [ 2387.987224] iwlagn 0000:02:00.0: EVT_LOGT:0624607664:0x000000d7:0123
Feb 12 20:17:01 netbook kernel: imklog 4.2.0, log source = /proc/kmsg started.
Feb 12 20:17:01 netbook rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="468" x-info="http://www.rsyslog.com"] (re)sta
```

---

### Post by wandalalakers on 2011-02-12
Maybe this is a similar model.
[http://linuxhcl.com/browse/product+acer-aspire-one-d250?id=7410](http://linuxhcl.com/browse/product+acer-aspire-one-d250?id=7410)

---

### Post by philm1983 on 2011-02-13
Yeah it looks like a similar model but they say there are no issue's on that one.

I ran a memtest this morning and that passed fine.

I used it for about 2 hours this morning so far with no problems so I am going to keep testing it to see if I can find a pattern of what may be causing it.

I can't seem to replicate the fault at the moment with any specific software.

When it failed last I was using Terminal Server viewer, so maybe it's to do with networking.

Phil.

---

### Post by Copper Bezel on 2011-02-13
Is the screen completely frozen, as in unresponsive & not updating at all, or does, say, the mouse pointer still move?

If you don't have the keystroke to kill the X server active, in the options for your chosen layout under Preferences - > Keyboard -> Layouts tab, switch that on. If it happens again, see if the system will respond to that keystroke. (This serves two purposes - one, if it works, it means you'll log out and be able to log back in, saving you a bit of time over restarting, and two, whether or not it works tells us a bit about where to look for the problem itself.)

---

### Post by philm1983 on 2011-02-13
Hi, thanks for the reply.

The screen becomes totally unresponsive and the mouse doesn't work.  I tried alt-F1 etc to try and get a console but no joy.

I will turn on the keystroke that allows me to kill the X server and then test.  I am planning on using it for a few hours now so I will re-post when/if it fails again.

Thanks again for taking the time to look at this.

---

### Post by philm1983 on 2011-02-13
System just froze again before I could enter the key combination to kill the X server.  I have now enabled that and am waiting for the next freeze.

One thing I do notice is that there wasn't any entries in the log near the time of the freeze.

The system froze at 17.40.  I have added the logs from around that time below.

```
Feb 13 17:21:21 netbook kernel: [    0.757172] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb 13 17:21:21 netbook kernel: [    0.828300] ACPI: AC Adapter [AC] (off-line)
Feb 13 17:21:21 netbook kernel: [    0.828484] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Feb 13 17:21:21 netbook kernel: [    0.828497] ACPI: Power Button [PWRB]
Feb 13 17:21:21 netbook kernel: [    0.828626] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
Feb 13 17:21:21 netbook kernel: [    0.828637] ACPI: Sleep Button [SLPB]
Feb 13 17:21:21 netbook kernel: [    0.828748] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
Feb 13 17:21:21 netbook kernel: [    0.828855] ACPI: Lid Switch [LID0]
Feb 13 17:21:21 netbook kernel: [    0.829004] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Feb 13 17:21:21 netbook kernel: [    0.829015] ACPI: Power Button [PWRF]
Feb 13 17:21:21 netbook kernel: [    0.829343] ACPI: Fan [FAN] (on)
Feb 13 17:21:21 netbook kernel: [    0.908284] thermal LNXTHERM:01: registered as thermal_zone0
Feb 13 17:21:21 netbook kernel: [    0.908328] ACPI: Thermal Zone [THRM] (30 C)
Feb 13 17:21:21 netbook kernel: [    0.908852] ERST: Table is not found!
Feb 13 17:21:21 netbook kernel: [    0.909058] isapnp: Scanning for PnP cards...
Feb 13 17:21:21 netbook kernel: [    0.910139] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Feb 13 17:21:21 netbook kernel: [    0.917892] brd: module loaded
Feb 13 17:21:21 netbook kernel: [    0.921122] loop: module loaded
Feb 13 17:21:21 netbook kernel: [    0.924262] Fixed MDIO Bus: probed
Feb 13 17:21:21 netbook kernel: [    0.924480] PPP generic driver version 2.4.2
Feb 13 17:21:21 netbook kernel: [    0.924697] tun: Universal TUN/TAP device driver, 1.6
Feb 13 17:21:21 netbook kernel: [    0.924708] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Feb 13 17:21:21 netbook kernel: [    0.925183] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb 13 17:21:21 netbook kernel: [    0.925309] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 22 (level, low) -> IRQ 22
Feb 13 17:21:21 netbook kernel: [    0.925388] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Feb 13 17:21:21 netbook kernel: [    0.925598] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Feb 13 17:21:21 netbook kernel: [    0.925680] ehci_hcd 0000:00:1d.7: using broken periodic workaround
Feb 13 17:21:21 netbook kernel: [    0.925711] ehci_hcd 0000:00:1d.7: debug port 1
Feb 13 17:21:21 netbook kernel: [    0.929695] ehci_hcd 0000:00:1d.7: irq 22, io mem 0x58204400
Feb 13 17:21:21 netbook kernel: [    0.949081] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Feb 13 17:21:21 netbook kernel: [    0.949700] hub 1-0:1.0: USB hub found
Feb 13 17:21:21 netbook kernel: [    0.949726] hub 1-0:1.0: 8 ports detected
Feb 13 17:21:21 netbook kernel: [    0.950053] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb 13 17:21:21 netbook kernel: [    0.950143] uhci_hcd: USB Universal Host Controller Interface driver
Feb 13 17:21:21 netbook kernel: [    0.950309] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb 13 17:21:21 netbook kernel: [    0.950353] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Feb 13 17:21:21 netbook kernel: [    0.950574] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Feb 13 17:21:21 netbook kernel: [    0.950681] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00006080
Feb 13 17:21:21 netbook kernel: [    0.951309] hub 2-0:1.0: USB hub found
Feb 13 17:21:21 netbook kernel: [    0.951342] hub 2-0:1.0: 2 ports detected
Feb 13 17:21:21 netbook kernel: [    0.951652] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
Feb 13 17:21:21 netbook kernel: [    0.951694] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Feb 13 17:21:21 netbook kernel: [    0.951891] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Feb 13 17:21:21 netbook kernel: [    0.951986] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00006060
Feb 13 17:21:21 netbook kernel: [    0.952608] hub 3-0:1.0: USB hub found
Feb 13 17:21:21 netbook kernel: [    0.952633] hub 3-0:1.0: 2 ports detected
Feb 13 17:21:21 netbook kernel: [    0.952932] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
Feb 13 17:21:21 netbook kernel: [    0.952975] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Feb 13 17:21:21 netbook kernel: [    0.953224] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Feb 13 17:21:21 netbook kernel: [    0.953328] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00006040
Feb 13 17:21:21 netbook kernel: [    0.954001] hub 4-0:1.0: USB hub found
Feb 13 17:21:21 netbook kernel: [    0.954026] hub 4-0:1.0: 2 ports detected
Feb 13 17:21:21 netbook kernel: [    0.954280] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 22 (level, low) -> IRQ 22
Feb 13 17:21:21 netbook kernel: [    0.954326] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Feb 13 17:21:21 netbook kernel: [    0.954563] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Feb 13 17:21:21 netbook kernel: [    0.954630] uhci_hcd 0000:00:1d.3: irq 22, io base 0x00006020
Feb 13 17:21:21 netbook kernel: [    0.955254] hub 5-0:1.0: USB hub found
Feb 13 17:21:21 netbook kernel: [    0.955279] hub 5-0:1.0: 2 ports detected
Feb 13 17:21:21 netbook kernel: [    0.955793] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
Feb 13 17:21:21 netbook kernel: [    0.969544] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 13 17:21:21 netbook kernel: [    0.969594] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 13 17:21:21 netbook kernel: [    0.969994] mice: PS/2 mouse device common for all mice
Feb 13 17:21:21 netbook kernel: [    0.970819] rtc_cmos 00:03: RTC can wake from S4
Feb 13 17:21:21 netbook kernel: [    0.971022] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Feb 13 17:21:21 netbook kernel: [    0.971087] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Feb 13 17:21:21 netbook kernel: [    0.971678] device-mapper: uevent: version 1.0.3
Feb 13 17:21:21 netbook kernel: [    0.972251] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
Feb 13 17:21:21 netbook kernel: [    0.972716] device-mapper: multipath: version 1.1.1 loaded
Feb 13 17:21:21 netbook kernel: [    0.972730] device-mapper: multipath round-robin: version 1.0.0 loaded
Feb 13 17:21:21 netbook kernel: [    0.973406] EISA: Probing bus 0 at eisa.0
Feb 13 17:21:21 netbook kernel: [    0.973421] EISA: Cannot allocate resource for mainboard
Feb 13 17:21:21 netbook kernel: [    0.973436] Cannot allocate resource for EISA slot 1
Feb 13 17:21:21 netbook kernel: [    0.973450] Cannot allocate resource for EISA slot 2
Feb 13 17:21:21 netbook kernel: [    0.973463] Cannot allocate resource for EISA slot 3
Feb 13 17:21:21 netbook kernel: [    0.973476] Cannot allocate resource for EISA slot 4
Feb 13 17:21:21 netbook kernel: [    0.973489] Cannot allocate resource for EISA slot 5
Feb 13 17:21:21 netbook kernel: [    0.973501] Cannot allocate resource for EISA slot 6
Feb 13 17:21:21 netbook kernel: [    0.973514] Cannot allocate resource for EISA slot 7
Feb 13 17:21:21 netbook kernel: [    0.973528] Cannot allocate resource for EISA slot 8
Feb 13 17:21:21 netbook kernel: [    0.973538] EISA: Detected 0 cards.
Feb 13 17:21:21 netbook kernel: [    0.975199] cpuidle: using governor ladder
Feb 13 17:21:21 netbook kernel: [    0.976593] cpuidle: using governor menu
Feb 13 17:21:21 netbook kernel: [    0.978094] TCP cubic registered
Feb 13 17:21:21 netbook kernel: [    0.978868] NET: Registered protocol family 10
Feb 13 17:21:21 netbook kernel: [    0.980669] lo: Disabled Privacy Extensions
Feb 13 17:21:21 netbook kernel: [    0.981796] NET: Registered protocol family 17
Feb 13 17:21:21 netbook kernel: [    0.984811] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Feb 13 17:21:21 netbook kernel: [    0.987847] Using IPI No-Shortcut mode
Feb 13 17:21:21 netbook kernel: [    0.988240] registered taskstats version 1
Feb 13 17:21:21 netbook kernel: [    0.988793]   Magic number: 15:576:390
Feb 13 17:21:21 netbook kernel: [    0.988956] rtc_cmos 00:03: setting system clock to 2011-02-13 17:21:08 UTC (1297617668)
Feb 13 17:21:21 netbook kernel: [    0.988967] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb 13 17:21:21 netbook kernel: [    0.988973] EDD information not available.
Feb 13 17:21:21 netbook kernel: [    1.152163] Freeing initrd memory: 10504k freed
Feb 13 17:21:21 netbook kernel: [    1.260081] usb 1-4: new high speed USB device using ehci_hcd and address 2
Feb 13 17:21:21 netbook kernel: [    1.263629] isapnp: No Plug & Play device found
Feb 13 17:21:21 netbook kernel: [    1.263694] Freeing unused kernel memory: 688k freed
Feb 13 17:21:21 netbook kernel: [    1.264417] Write protecting the kernel text: 4936k
Feb 13 17:21:21 netbook kernel: [    1.264517] Write protecting the kernel read-only data: 1976k
Feb 13 17:21:21 netbook kernel: [    1.306830] udev[100]: starting version 163
Feb 13 17:21:21 netbook kernel: [    1.548472] ACPI: Battery Slot [BAT0] (battery present)
Feb 13 17:21:21 netbook kernel: [    1.979370] atl1c 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 13 17:21:21 netbook kernel: [    2.037877] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Feb 13 17:21:21 netbook kernel: [    2.038088] ahci: SSS flag set, parallel bus scan disabled
Feb 13 17:21:21 netbook kernel: [    2.038154] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
Feb 13 17:21:21 netbook kernel: [    2.038167] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pmp pio slum part 
Feb 13 17:21:21 netbook kernel: [    2.039015] scsi0 : ahci
Feb 13 17:21:21 netbook kernel: [    2.039463] scsi1 : ahci
Feb 13 17:21:21 netbook kernel: [    2.039802] scsi2 : ahci
Feb 13 17:21:21 netbook kernel: [    2.040080] scsi3 : ahci
Feb 13 17:21:21 netbook kernel: [    2.040700] ata1: SATA max UDMA/133 abar m1024@0x58204000 port 0x58204100 irq 42
Feb 13 17:21:21 netbook kernel: [    2.040710] ata2: SATA max UDMA/133 abar m1024@0x58204000 port 0x58204180 irq 42
Feb 13 17:21:21 netbook kernel: [    2.040717] ata3: DUMMY
Feb 13 17:21:21 netbook kernel: [    2.040721] ata4: DUMMY
Feb 13 17:21:21 netbook kernel: [    2.109699] atl1c 0000:01:00.0: version 1.0.0.2-NAPI
Feb 13 17:21:21 netbook kernel: [    2.532172] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 13 17:21:21 netbook kernel: [    2.533205] ata1.00: unexpected _GTF length (4)
Feb 13 17:21:21 netbook kernel: [    2.533593] ata1.00: ATA-8: WDC WD2500BEVT-22A23T0, 01.01A01, max UDMA/133
Feb 13 17:21:21 netbook kernel: [    2.533604] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Feb 13 17:21:21 netbook kernel: [    2.534752] ata1.00: unexpected _GTF length (4)
Feb 13 17:21:21 netbook kernel: [    2.535110] ata1.00: configured for UDMA/133
Feb 13 17:21:21 netbook kernel: [    2.548478] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-2 01.0 PQ: 0 ANSI: 5
Feb 13 17:21:21 netbook kernel: [    2.549072] sd 0:0:0:0: Attached scsi generic sg0 type 0
Feb 13 17:21:21 netbook kernel: [    2.549096] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Feb 13 17:21:21 netbook kernel: [    2.549280] sd 0:0:0:0: [sda] Write Protect is off
Feb 13 17:21:21 netbook kernel: [    2.549383] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 13 17:21:21 netbook kernel: [    2.550152]  sda: sda1 sda2 < sda5 >
Feb 13 17:21:21 netbook kernel: [    2.619575] sd 0:0:0:0: [sda] Attached SCSI disk
Feb 13 17:21:21 netbook kernel: [    2.619725] CE: hpet increased min_delta_ns to 7500 nsec
Feb 13 17:21:21 netbook kernel: [    2.868182] ata2: SATA link down (SStatus 0 SControl 300)
Feb 13 17:21:21 netbook kernel: [    3.268454] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Feb 13 17:21:21 netbook kernel: [   13.429980] udev[350]: starting version 163
Feb 13 17:21:21 netbook kernel: [   13.481082] lp: driver loaded but no devices found
Feb 13 17:21:21 netbook kernel: [   13.566808] EXT4-fs (sda1): warning: maximal mount count reached, running e2fsck is recommended
Feb 13 17:21:21 netbook kernel: [   13.567253] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Feb 13 17:21:21 netbook kernel: [   14.086152] Linux agpgart interface v0.103
Feb 13 17:21:21 netbook kernel: [   14.165263] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
Feb 13 17:21:21 netbook kernel: [   14.166390] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Feb 13 17:21:21 netbook kernel: [   14.189742] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
Feb 13 17:21:21 netbook kernel: [   14.205268] Linux video capture interface: v2.00
Feb 13 17:21:21 netbook kernel: [   14.326088] uvcvideo: Found UVC 1.00 device 1.3M WebCam (04f2:b1d8)
Feb 13 17:21:21 netbook kernel: [   14.398963] cfg80211: Calling CRDA to update world regulatory domain
Feb 13 17:21:21 netbook kernel: [   14.403434] input: 1.3M WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input5
Feb 13 17:21:21 netbook kernel: [   14.403638] usbcore: registered new interface driver uvcvideo
Feb 13 17:21:21 netbook kernel: [   14.403646] USB Video Class driver (v0.1.0)
Feb 13 17:21:21 netbook kernel: [   14.462131] cfg80211: World regulatory domain updated:
Feb 13 17:21:21 netbook kernel: [   14.462142]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb 13 17:21:21 netbook kernel: [   14.462155]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 13 17:21:21 netbook kernel: [   14.462165]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb 13 17:21:21 netbook kernel: [   14.462175]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb 13 17:21:21 netbook kernel: [   14.462185]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 13 17:21:21 netbook kernel: [   14.462195]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 13 17:21:21 netbook kernel: [   14.469353] type=1400 audit(1297617681.978:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=711 comm="apparmor_parser"
Feb 13 17:21:21 netbook kernel: [   14.470126] type=1400 audit(1297617681.978:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=711 comm="apparmor_parser"
Feb 13 17:21:21 netbook kernel: [   14.471959] type=1400 audit(1297617681.978:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=711 comm="apparmor_parser"
Feb 13 17:21:21 netbook kernel: [   14.484306] [drm] Initialized drm 1.1.0 20060810
Feb 13 17:21:22 netbook kernel: [   14.533988] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb 13 17:21:22 netbook kernel: [   14.703591] type=1400 audit(1297617682.210:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=794 comm="apparmor_parser"
Feb 13 17:21:22 netbook kernel: [   14.707063] type=1400 audit(1297617682.214:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=795 comm="apparmor_parser"
Feb 13 17:21:22 netbook kernel: [   14.707983] type=1400 audit(1297617682.214:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=795 comm="apparmor_parser"
Feb 13 17:21:22 netbook kernel: [   14.708535] type=1400 audit(1297617682.218:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=795 comm="apparmor_parser"
Feb 13 17:21:22 netbook kernel: [   14.716345] type=1400 audit(1297617682.226:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=799 comm="apparmor_parser"
Feb 13 17:21:22 netbook kernel: [   14.718650] type=1400 audit(1297617682.226:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=798 comm="apparmor_parser"
Feb 13 17:21:22 netbook kernel: [   14.719510] type=1400 audit(1297617682.226:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=798 comm="apparmor_parser"
Feb 13 17:21:22 netbook kernel: [   14.747873] nf_conntrack version 0.5.0 (15858 buckets, 63432 max)
Feb 13 17:21:22 netbook kernel: [   14.750338] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Feb 13 17:21:22 netbook kernel: [   14.750348] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Feb 13 17:21:22 netbook kernel: [   14.750356] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Feb 13 17:21:22 netbook kernel: [   14.905724] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 13 17:21:22 netbook kernel: [   14.914892] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Feb 13 17:21:22 netbook kernel: [   14.914904] iwlagn: Copyright(c) 2003-2010 Intel Corporation
Feb 13 17:21:22 netbook kernel: [   14.915055] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 13 17:21:22 netbook kernel: [   14.915156] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
Feb 13 17:21:22 netbook kernel: [   14.935660] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
Feb 13 17:21:22 netbook kernel: [   14.990649] ip6_tables: (C) 2000-2006 Netfilter Core Team
Feb 13 17:21:22 netbook kernel: [   15.012297] [drm] set up 7M of stolen space
Feb 13 17:21:22 netbook kernel: [   15.038484] iwlagn 0000:02:00.0: loaded firmware version 128.50.3.1 build 13488
Feb 13 17:21:22 netbook kernel: [   15.121977] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Feb 13 17:21:22 netbook kernel: [   15.122351] [drm] initialized overlay support
Feb 13 17:21:22 netbook kernel: [   15.235254] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000/0xa0000
Feb 13 17:21:22 netbook kernel: [   15.301189] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
Feb 13 17:21:22 netbook kernel: [   15.437070] Skipping EDID probe due to cached edid
Feb 13 17:21:23 netbook kernel: [   15.513462] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 13 17:21:23 netbook kernel: [   15.834079] Console: switching to colour frame buffer device 128x37
Feb 13 17:21:23 netbook kernel: [   15.841477] fb0: inteldrmfb frame buffer device
Feb 13 17:21:23 netbook kernel: [   15.841483] drm: registered panic notifier
Feb 13 17:21:23 netbook kernel: [   15.841495] Slow work thread pool: Starting up
Feb 13 17:21:23 netbook kernel: [   15.841698] Slow work thread pool: Ready
Feb 13 17:21:23 netbook kernel: [   15.986394] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 13 17:21:23 netbook kernel: [   16.148308] acpi device:27: registered as cooling_device5
Feb 13 17:21:23 netbook kernel: [   16.149524] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
Feb 13 17:21:23 netbook kernel: [   16.149722] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
Feb 13 17:21:23 netbook kernel: [   16.149815] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Feb 13 17:21:23 netbook kernel: [   16.150016] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Feb 13 17:21:23 netbook kernel: [   16.216614] Skipping EDID probe due to cached edid
Feb 13 17:21:23 netbook kernel: [   16.227218] hda_codec: ALC272X: BIOS auto-probing.
Feb 13 17:21:24 netbook kernel: [   16.667978] ppdev: user-space parallel port driver
Feb 13 17:21:25 netbook kernel: [   17.506051] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Feb 13 17:21:25 netbook kernel: [   17.540779] Skipping EDID probe due to cached edid
Feb 13 17:21:25 netbook kernel: [   17.684263] Skipping EDID probe due to cached edid
Feb 13 17:21:26 netbook kernel: [   19.160124] Skipping EDID probe due to cached edid
Feb 13 17:21:26 netbook kernel: [   19.196125] Skipping EDID probe due to cached edid
Feb 13 17:21:26 netbook kernel: [   19.232628] Skipping EDID probe due to cached edid
Feb 13 17:21:26 netbook kernel: [   19.272107] Skipping EDID probe due to cached edid
Feb 13 17:21:28 netbook kernel: [   20.612145] Skipping EDID probe due to cached edid
Feb 13 17:21:28 netbook kernel: [   21.313476] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
Feb 13 17:21:34 netbook kernel: [   26.566524] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb 13 17:21:34 netbook kernel: [   26.599407] padlock: VIA PadLock not detected.
Feb 13 17:21:35 netbook kernel: [   27.864144] Skipping EDID probe due to cached edid
Feb 13 17:21:35 netbook kernel: [   27.908149] Skipping EDID probe due to cached edid
Feb 13 17:21:35 netbook kernel: [   27.952166] Skipping EDID probe due to cached edid
Feb 13 17:21:35 netbook kernel: [   27.992066] Skipping EDID probe due to cached edid
Feb 13 17:21:35 netbook kernel: [   28.192181] Skipping EDID probe due to cached edid
Feb 13 17:21:41 netbook kernel: [   33.625326] Skipping EDID probe due to cached edid
Feb 13 17:21:46 netbook kernel: [   38.954958] lo: Disabled Privacy Extensions
Feb 13 17:22:05 netbook kernel: [   57.889088] CE: hpet increased min_delta_ns to 11250 nsec
Feb 13 17:42:57 netbook kernel: imklog 4.2.0, log source = /proc/kmsg started.
```

---

### Post by philm1983 on 2011-02-14
> **Copper Bezel said:**
> Is the screen completely frozen, as in unresponsive & not updating at all, or does, say, the mouse pointer still move?

If you don't have the keystroke to kill the X server active, in the options for your chosen layout under Preferences - > Keyboard -> Layouts tab, switch that on. If it happens again, see if the system will respond to that keystroke. (This serves two purposes - one, if it works, it means you'll log out and be able to log back in, saving you a bit of time over restarting, and two, whether or not it works tells us a bit about where to look for the problem itself.)

System froze again tonight and the kill X server keystroke didn't work.  

I left it playing video all night last night to test and I have been browsing the net for the last 5 hours and it worked flawlessly and then all of a sudden it froze while browsing using chrome.

I am going to try just using firefox now and testing.  Again, I can't see anything in the logs but I have included them below.

If this keeps up I am going to have to try another O/S to see if it is Ubuntu causing it.  I will probably try Windows 7 as that is what was originally installed but I would prefer to have the system running linux. 

The freeze happened 14/02/2011 at 21.45(ish)

```
Feb 14 20:17:01 netbook CRON[3868]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 14 20:30:05 netbook kernel: [11315.213144] lo: Disabled Privacy Extensions
Feb 14 20:32:07 netbook kernel: [11437.791260] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.77.102 DST=192.168.0.12 LEN=354 TOS=0x00 PREC=0x00 TTL=49 ID=23924 PROTO=TCP SPT=80 DPT=53510 WINDOW=169 RES=0x00 ACK PSH URGP=0 
Feb 14 20:32:17 netbook kernel: [11447.791280] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.77.102 DST=192.168.0.12 LEN=354 TOS=0x00 PREC=0x00 TTL=49 ID=23924 PROTO=TCP SPT=80 DPT=53510 WINDOW=169 RES=0x00 ACK PSH URGP=0 
Feb 14 20:36:45 netbook kernel: [11715.654562] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.77.102 DST=192.168.0.12 LEN=396 TOS=0x00 PREC=0x00 TTL=50 ID=742 PROTO=TCP SPT=80 DPT=53571 WINDOW=148 RES=0x00 ACK PSH URGP=0 
Feb 14 20:36:54 netbook kernel: [11725.107349] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.77.102 DST=192.168.0.12 LEN=396 TOS=0x00 PREC=0x00 TTL=49 ID=32277 PROTO=TCP SPT=80 DPT=53569 WINDOW=324 RES=0x00 ACK PSH URGP=0 
Feb 14 20:36:55 netbook kernel: [11725.654844] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.77.102 DST=192.168.0.12 LEN=396 TOS=0x00 PREC=0x00 TTL=50 ID=742 PROTO=TCP SPT=80 DPT=53571 WINDOW=148 RES=0x00 ACK PSH URGP=0 
Feb 14 20:59:01 netbook kernel: [13051.992158] iwlagn 0000:02:00.0: Microcode SW error detected.  Restarting 0x92000000.
Feb 14 20:59:01 netbook kernel: [13051.992171] iwlagn 0000:02:00.0: Loaded firmware version: 128.50.3.1 build 13488
Feb 14 20:59:01 netbook kernel: [13051.992195] iwlagn 0000:02:00.0: Start IWL Error Log Dump:
Feb 14 20:59:01 netbook kernel: [13051.992202] iwlagn 0000:02:00.0: Status: 0x000312E4, count: 5
Feb 14 20:59:01 netbook kernel: [13051.992384] iwlagn 0000:02:00.0: Desc                               Time       data1      data2      line
Feb 14 20:59:01 netbook kernel: [13051.992394] iwlagn 0000:02:00.0: NMI_INTERRUPT_WDG            (#04) 1488893009 0x00000002 0x02030000 302
Feb 14 20:59:01 netbook kernel: [13051.992401] iwlagn 0000:02:00.0: pc      blink1  blink2  ilink1  ilink2  hcmd
Feb 14 20:59:01 netbook kernel: [13051.992409] iwlagn 0000:02:00.0: 0x006D0 0x00596 0x006D4 0x00892 0x0215E 0x44D0048
Feb 14 20:59:01 netbook kernel: [13051.992416] iwlagn 0000:02:00.0: CSR values:
Feb 14 20:59:01 netbook kernel: [13051.992421] iwlagn 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
Feb 14 20:59:01 netbook kernel: [13051.992452] iwlagn 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
Feb 14 20:59:01 netbook kernel: [13051.992481] iwlagn 0000:02:00.0:          CSR_INT_COALESCING: 0X0000ff40
Feb 14 20:59:01 netbook kernel: [13051.992533] iwlagn 0000:02:00.0:                     CSR_INT: 0X80000000
Feb 14 20:59:01 netbook kernel: [13051.992565] iwlagn 0000:02:00.0:                CSR_INT_MASK: 0X00000000
Feb 14 20:59:01 netbook kernel: [13051.992598] iwlagn 0000:02:00.0:           CSR_FH_INT_STATUS: 0X40010000
Feb 14 20:59:01 netbook kernel: [13051.992631] iwlagn 0000:02:00.0:                 CSR_GPIO_IN: 0X00000000
Feb 14 20:59:01 netbook kernel: [13051.992664] iwlagn 0000:02:00.0:                   CSR_RESET: 0X00000000
Feb 14 20:59:01 netbook kernel: [13051.992697] iwlagn 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
Feb 14 20:59:01 netbook kernel: [13051.992729] iwlagn 0000:02:00.0:                  CSR_HW_REV: 0X0000006c
Feb 14 20:59:01 netbook kernel: [13051.992763] iwlagn 0000:02:00.0:              CSR_EEPROM_REG: 0X007a08e5
Feb 14 20:59:01 netbook kernel: [13051.992796] iwlagn 0000:02:00.0:               CSR_EEPROM_GP: 0X90000001
Feb 14 20:59:01 netbook kernel: [13051.992828] iwlagn 0000:02:00.0:              CSR_OTP_GP_REG: 0X00010001
Feb 14 20:59:01 netbook kernel: [13051.992860] iwlagn 0000:02:00.0:                 CSR_GIO_REG: 0X00080042
Feb 14 20:59:01 netbook kernel: [13051.992893] iwlagn 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000cb1
Feb 14 20:59:01 netbook kernel: [13051.992926] iwlagn 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
Feb 14 20:59:01 netbook kernel: [13051.992961] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
Feb 14 20:59:01 netbook kernel: [13051.992995] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
Feb 14 20:59:01 netbook kernel: [13051.993029] iwlagn 0000:02:00.0:                 CSR_LED_REG: 0X00000058
Feb 14 20:59:01 netbook kernel: [13051.993064] iwlagn 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X880348f6
Feb 14 20:59:01 netbook kernel: [13051.993098] iwlagn 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
Feb 14 20:59:01 netbook kernel: [13051.993133] iwlagn 0000:02:00.0:             CSR_ANA_PLL_CFG: 0X00880300
Feb 14 20:59:01 netbook kernel: [13051.993168] iwlagn 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
Feb 14 20:59:01 netbook kernel: [13051.993202] iwlagn 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
Feb 14 20:59:01 netbook kernel: [13051.993212] iwlagn 0000:02:00.0: FH register values:
Feb 14 20:59:01 netbook kernel: [13051.993257] iwlagn 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X03407200
Feb 14 20:59:01 netbook kernel: [13051.993302] iwlagn 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00340730
Feb 14 20:59:01 netbook kernel: [13051.993350] iwlagn 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000a0
Feb 14 20:59:01 netbook kernel: [13051.993397] iwlagn 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
Feb 14 20:59:01 netbook kernel: [13051.993443] iwlagn 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
Feb 14 20:59:01 netbook kernel: [13051.993508] iwlagn 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07430000
Feb 14 20:59:01 netbook kernel: [13051.993564] iwlagn 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
Feb 14 20:59:01 netbook kernel: [13051.993610] iwlagn 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
Feb 14 20:59:01 netbook kernel: [13051.993657] iwlagn 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
Feb 14 20:59:01 netbook kernel: [13051.993762] iwlagn 0000:02:00.0: Start IWL Event Log Dump: display last 1 entries
Feb 14 20:59:01 netbook kernel: [13051.993815] iwlagn 0000:02:00.0: EVT_LOGT:3770831051:0x000000d7:0123
Feb 14 20:59:01 netbook kernel: [13051.994117] iwlagn 0000:02:00.0: Command POWER_TABLE_CMD failed: FW Error
Feb 14 21:00:26 netbook kernel: [13051.994130] iwlagn 0000:02:00.0: set power fail, ret = -5
Feb 14 21:00:26 netbook kernel: [13136.269479] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.77.101 DST=192.168.0.12 LEN=420 TOS=0x00 PREC=0x00 TTL=50 ID=48473 PROTO=TCP SPT=80 DPT=43135 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:00:36 netbook kernel: [13146.270559] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.77.101 DST=192.168.0.12 LEN=420 TOS=0x00 PREC=0x00 TTL=50 ID=43488 PROTO=TCP SPT=80 DPT=43135 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:03:22 netbook wpa_supplicant[791]: WPA: Group rekeying completed with 30:46:9a:7e:29:cc [GTK=TKIP]
Feb 14 21:03:22 netbook NetworkManager[752]: <info> (wlan0): supplicant connection state:  completed -> group handshake
Feb 14 21:03:22 netbook NetworkManager[752]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Feb 14 21:13:58 netbook kernel: [13948.273738] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.101 DST=192.168.0.12 LEN=428 TOS=0x00 PREC=0x00 TTL=50 ID=29083 PROTO=TCP SPT=80 DPT=48742 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:14:01 netbook kernel: [13951.807010] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.101 DST=192.168.0.12 LEN=495 TOS=0x00 PREC=0x00 TTL=49 ID=5464 PROTO=TCP SPT=80 DPT=48743 WINDOW=147 RES=0x00 ACK PSH URGP=0 
Feb 14 21:14:02 netbook kernel: [13952.453809] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.101 DST=192.168.0.12 LEN=496 TOS=0x00 PREC=0x00 TTL=50 ID=49478 PROTO=TCP SPT=80 DPT=48745 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:14:08 netbook kernel: [13958.274010] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.101 DST=192.168.0.12 LEN=428 TOS=0x00 PREC=0x00 TTL=50 ID=29084 PROTO=TCP SPT=80 DPT=48742 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:14:11 netbook kernel: [13961.807978] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.101 DST=192.168.0.12 LEN=495 TOS=0x00 PREC=0x00 TTL=49 ID=5465 PROTO=TCP SPT=80 DPT=48743 WINDOW=147 RES=0x00 ACK PSH URGP=0 
Feb 14 21:14:12 netbook kernel: [13962.454205] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.101 DST=192.168.0.12 LEN=496 TOS=0x00 PREC=0x00 TTL=50 ID=49479 PROTO=TCP SPT=80 DPT=48745 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:17:01 netbook CRON[4479]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 14 21:21:24 netbook kernel: [14394.979063] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=209.85.143.104 DST=192.168.0.12 LEN=321 TOS=0x00 PREC=0x00 TTL=51 ID=30851 PROTO=TCP SPT=80 DPT=47935 WINDOW=314 RES=0x00 ACK PSH URGP=0 
Feb 14 21:21:34 netbook kernel: [14404.979096] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=209.85.143.104 DST=192.168.0.12 LEN=321 TOS=0x00 PREC=0x00 TTL=51 ID=30851 PROTO=TCP SPT=80 DPT=47935 WINDOW=314 RES=0x00 ACK PSH URGP=0 
Feb 14 21:21:55 netbook kernel: [14425.454727] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=209.85.143.104 DST=192.168.0.12 LEN=321 TOS=0x00 PREC=0x00 TTL=50 ID=20949 PROTO=TCP SPT=80 DPT=48037 WINDOW=160 RES=0x00 ACK PSH URGP=0 
Feb 14 21:22:05 netbook kernel: [14435.454559] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=209.85.143.104 DST=192.168.0.12 LEN=321 TOS=0x00 PREC=0x00 TTL=50 ID=20949 PROTO=TCP SPT=80 DPT=48037 WINDOW=160 RES=0x00 ACK PSH URGP=0 
Feb 14 21:27:55 netbook kernel: [14785.900302] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.102 DST=192.168.0.12 LEN=424 TOS=0x00 PREC=0x00 TTL=49 ID=21675 PROTO=TCP SPT=80 DPT=50963 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:27:56 netbook kernel: [14786.226071] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.102 DST=192.168.0.12 LEN=415 TOS=0x00 PREC=0x00 TTL=50 ID=58987 PROTO=TCP SPT=80 DPT=50964 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:28:05 netbook kernel: [14795.899824] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.102 DST=192.168.0.12 LEN=424 TOS=0x00 PREC=0x00 TTL=49 ID=21676 PROTO=TCP SPT=80 DPT=50963 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:28:06 netbook kernel: [14796.227202] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.102 DST=192.168.0.12 LEN=415 TOS=0x00 PREC=0x00 TTL=50 ID=58988 PROTO=TCP SPT=80 DPT=50964 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:28:09 netbook kernel: [14799.284248] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.102 DST=192.168.0.12 LEN=403 TOS=0x00 PREC=0x00 TTL=50 ID=17707 PROTO=TCP SPT=80 DPT=50966 WINDOW=149 RES=0x00 ACK PSH URGP=0 
Feb 14 21:28:10 netbook kernel: [14800.782865] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.102 DST=192.168.0.12 LEN=408 TOS=0x00 PREC=0x00 TTL=51 ID=4190 PROTO=TCP SPT=80 DPT=50967 WINDOW=179 RES=0x00 ACK PSH URGP=0 
Feb 14 21:28:19 netbook kernel: [14809.282432] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.102 DST=192.168.0.12 LEN=403 TOS=0x00 PREC=0x00 TTL=50 ID=17708 PROTO=TCP SPT=80 DPT=50966 WINDOW=149 RES=0x00 ACK PSH URGP=0 
Feb 14 21:28:20 netbook kernel: [14810.783233] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.102 DST=192.168.0.12 LEN=408 TOS=0x00 PREC=0x00 TTL=51 ID=4191 PROTO=TCP SPT=80 DPT=50967 WINDOW=179 RES=0x00 ACK PSH URGP=0 
Feb 14 21:30:15 netbook kernel: [14925.689086] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.101 DST=192.168.0.12 LEN=421 TOS=0x00 PREC=0x00 TTL=50 ID=26137 PROTO=TCP SPT=80 DPT=35576 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:30:15 netbook kernel: [14926.181209] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.101 DST=192.168.0.12 LEN=442 TOS=0x00 PREC=0x00 TTL=51 ID=5130 PROTO=TCP SPT=80 DPT=35578 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:30:15 netbook kernel: [14926.187923] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.101 DST=192.168.0.12 LEN=429 TOS=0x00 PREC=0x00 TTL=49 ID=39553 PROTO=TCP SPT=80 DPT=35577 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:30:18 netbook kernel: [14928.566970] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.101 DST=192.168.0.12 LEN=474 TOS=0x00 PREC=0x00 TTL=50 ID=4604 PROTO=TCP SPT=80 DPT=35579 WINDOW=177 RES=0x00 ACK PSH URGP=0 
Feb 14 21:30:25 netbook kernel: [14935.689853] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.101 DST=192.168.0.12 LEN=421 TOS=0x00 PREC=0x00 TTL=50 ID=26138 PROTO=TCP SPT=80 DPT=35576 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:30:25 netbook kernel: [14936.182301] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.101 DST=192.168.0.12 LEN=442 TOS=0x00 PREC=0x00 TTL=51 ID=5131 PROTO=TCP SPT=80 DPT=35578 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:30:25 netbook kernel: [14936.187828] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.101 DST=192.168.0.12 LEN=429 TOS=0x00 PREC=0x00 TTL=49 ID=39554 PROTO=TCP SPT=80 DPT=35577 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:30:28 netbook kernel: [14938.402236] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.101 DST=192.168.0.12 LEN=474 TOS=0x00 PREC=0x00 TTL=50 ID=4605 PROTO=TCP SPT=80 DPT=35579 WINDOW=177 RES=0x00 ACK PSH URGP=0 
Feb 14 21:30:35 netbook kernel: [14946.153208] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=74.125.79.101 DST=192.168.0.12 LEN=450 TOS=0x00 PREC=0x00 TTL=49 ID=9174 PROTO=TCP SPT=80 DPT=35580 WINDOW=118 RES=0x00 ACK PSH URGP=0 
Feb 14 21:43:53 netbook kernel: [15743.876706] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=209.85.146.113 DST=192.168.0.12 LEN=431 TOS=0x00 PREC=0x00 TTL=51 ID=46224 PROTO=TCP SPT=80 DPT=51867 WINDOW=322 RES=0x00 ACK PSH URGP=0 
Feb 14 21:44:03 netbook kernel: [15753.819839] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:c7:c2:a8:92:30:46:9a:c8:bc:0d:08:00 SRC=209.85.146.113 DST=192.168.0.12 LEN=431 TOS=0x00 PREC=0x00 TTL=51 ID=46225 PROTO=TCP SPT=80 DPT=51867 WINDOW=322 RES=0x00 ACK PSH URGP=0 
Feb 14 21:44:36 netbook kernel: [15786.683876] lo: Disabled Privacy Extensions
Feb 14 21:46:42 netbook kernel: imklog 4.2.0, log source = /proc/kmsg started.
Feb 14 21:46:42 netbook rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="550" x-info="http://www.rsyslog.com"] (re)start
Feb 14 21:46:42 netbook rsyslogd: rsyslogd's groupid changed to 103
Feb 14 21:46:43 netbook rsyslogd: rsyslogd's userid changed to 101
```

---

### Post by Horaci on 2011-02-20
my wife's Acer Aspire one 255 has the same issue; somehow randomly (sometimes 1 a week, sometimes two days in a row) it completely freezes and nothing seems to work until power button is held to force it to shut down.
Ctrl-alt-fX does nothing. So far I haven't been able to identify any special behaviour; sometimes it happens web browsing, some other times not.

I'll keep you posted if I see anything.

---

### Post by Horaci on 2011-02-20
@philm1983, did you try this?
[http://en.kioskea.net/forum/affich-511572-please-help-acer-aspire-d255-freezing](http://en.kioskea.net/forum/affich-511572-please-help-acer-aspire-d255-freezing)

apparently a bios upgrade may fix the issue. I'll try and see.

---

### Post by Horaci on 2011-02-27
after the BIOS upgrade the system is still freezing randomly :(

any suggestions, anyone?

---

### Post by driftless on 2011-04-09
I am having the same issue - 

Any solutions found (folks above) the fact that this thread died off gives me hope.

Ubuntu 10.10
Acer Aspire One D255-N558QKK
(Model #: PAV70)

Fresh Install (side-by-side with Windows 7) freezes randomly - no discernible pattern. Freeze is total (ie, no mouse, no keyboard. If I am downloading (or updating) internet gets dropped.

I updated the Acer BIOS, and have updated to the latest kernels (2.6.35-28-generic) ... 

Thinking I might need to downgrade to Ubuntu 10.04 LT. Or try some other Linux flavor-flav.

---

### Post by russ553 on 2011-04-10
I have a Toshiba Tecra that experiences the same problem.  Many freezes when using Firefox and Skype at the same time.  Sometimes the mouse will move, jerky, but no clicking is allowed.  No keyboard shortcut works either.  Hard shutdown is the only answer.

I have found that if I just leave everything alone, it will mostly unfreeze itself, however that may take 10 minutes.  The hard drive light keeps blinking.

---

