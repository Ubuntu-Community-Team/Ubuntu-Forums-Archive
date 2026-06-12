---
title: "sond problems after the latest update"
date: 2006-01-02
forum: Desktop Environments
---

### Post by gma on 2006-01-02
Hi Guys :-)

I've got a seroius problem -- no sound. Everything worked just fine untill i installed recent kernel updates. I don't know what to do. I tried reinstalling alsa, but that didn't do the trick.

Here's my lspci:

```
gma@acer:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 (rev 01)
0000:00:02.0 PCI bridge: ATI Technologies Inc: Unknown device 5a34
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:07.0 PCI bridge: ATI Technologies Inc: Unknown device 5a39
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5653
0000:06:05.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
0000:06:06.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:06.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:06.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:06:06.4 0805: Texas Instruments: Unknown device 8034
0000:06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```

I've got an acer aspire 5024WLMi.

Help me, please.

---

### Post by giftnudel on 2006-01-02
Hi,
my crystal ball fails on this problem, there are still some questions:

Is the sound system muted? 
[INDENT]- Look in a mixer and try to raise the volume.[/INDENT]
Is the soundcard module loaded? 
[INDENT]- Enter "lsmod | grep snd" in a terminal to see it[/INDENT]
Are there error messages that you try to hide from us? 
[INDENT]- Type "dmesg"in a terminal to see the kernel messages, "less /var/log/syslog" to see others[/INDENT]
If you could give us these answers, there might be a chance that more people can help.

giftnudel

---

### Post by gma on 2006-01-02
[QUOTE=giftnudel]Hi,
my crystal ball fails on this problem, there are still some questions:

Is the sound system muted? 
[INDENT]- Look in a mixer and try to raise the volume.[/INDENT]
Is the soundcard module loaded?[/QUOTE]

typing "alsamixer" gives...

```
alsamixer: function snd_ctl_open failed for default: No such device
```

> [INDENT]- Enter "lsmod | grep snd" in a terminal to see it[/INDENT]

lsmod gives...

```

gma@acer:~$ lsmod | grep snd
snd                    50880  0
soundcore               9184  1 snd
snd_page_alloc         10120  0
```

> Are there error messages that you try to hide from us? 
[INDENT]- Type "dmesg"in a terminal to see the kernel messages, "less /var/log/syslog" to see others[/INDENT]

Certainly not :-)

dmesg returns...

```

gma@acer:~$ dmesg
97.766000] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[4294697.766000] snd_ac97_codec: Unknown symbol snd_ctl_new1
[4294697.766000] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[4294697.766000] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[4294697.766000] snd_ac97_codec: disagrees about version of symbol snd_component_add
[4294697.766000] snd_ac97_codec: Unknown symbol snd_component_add
[4294697.766000] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[4294697.766000] snd_ac97_codec: disagrees about version of symbol snd_iprintf
[4294697.766000] snd_ac97_codec: Unknown symbol snd_iprintf
[4294697.766000] snd_ac97_codec: disagrees about version of symbol snd_device_new
[4294697.766000] snd_ac97_codec: Unknown symbol snd_device_new
[4294697.766000] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[4294697.766000] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[4294697.766000] snd_ac97_codec: disagrees about version of symbol snd_info_unregister
[4294697.766000] snd_ac97_codec: Unknown symbol snd_info_unregister
[4294697.766000] snd_atiixp: Unknown symbol snd_ac97_pcm_close
[4294697.766000] snd_atiixp: Unknown symbol snd_ac97_resume
[4294697.766000] snd_atiixp: Unknown symbol snd_pcm_new
[4294697.766000] snd_atiixp: Unknown symbol snd_pcm_limit_hw_rates
[4294697.766000] snd_atiixp: disagrees about version of symbol snd_card_register[4294697.766000] snd_atiixp: Unknown symbol snd_card_register
[4294697.766000] snd_atiixp: disagrees about version of symbol snd_card_free
[4294697.766000] snd_atiixp: Unknown symbol snd_card_free
[4294697.766000] snd_atiixp: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[4294697.766000] snd_atiixp: disagrees about version of symbol snd_card_proc_new[4294697.766000] snd_atiixp: Unknown symbol snd_card_proc_new
[4294697.766000] snd_atiixp: Unknown symbol snd_ac97_pcm_open
[4294697.766000] snd_atiixp: Unknown symbol snd_pcm_stop
[4294697.767000] snd_atiixp: Unknown symbol snd_pcm_format_physical_width
[4294697.767000] snd_atiixp: Unknown symbol snd_ac97_update_bits
[4294697.767000] snd_atiixp: Unknown symbol snd_ac97_mixer
[4294697.767000] snd_atiixp: Unknown symbol snd_card_pci_resume
[4294697.767000] snd_atiixp: Unknown symbol snd_ac97_bus
[4294697.767000] snd_atiixp: disagrees about version of symbol snd_card_new
[4294697.767000] snd_atiixp: Unknown symbol snd_card_new
[4294697.767000] snd_atiixp: Unknown symbol snd_ac97_suspend
[4294697.767000] snd_atiixp: disagrees about version of symbol snd_iprintf
[4294697.767000] snd_atiixp: Unknown symbol snd_iprintf
[4294697.767000] snd_atiixp: Unknown symbol snd_pcm_lib_malloc_pages
[4294697.767000] snd_atiixp: Unknown symbol snd_pcm_lib_ioctl
[4294697.767000] snd_atiixp: Unknown symbol snd_pcm_lib_free_pages
[4294697.767000] snd_atiixp: Unknown symbol snd_card_pci_suspend
[4294697.767000] snd_atiixp: Unknown symbol snd_pcm_set_ops
[4294697.767000] snd_atiixp: Unknown symbol snd_card_set_pm_callback
[4294697.767000] snd_atiixp: disagrees about version of symbol snd_device_new
[4294697.767000] snd_atiixp: Unknown symbol snd_device_new
[4294697.767000] snd_atiixp: Unknown symbol snd_ac97_get_short_name
[4294697.767000] snd_atiixp: Unknown symbol snd_pcm_suspend_all
[4294697.767000] snd_atiixp: Unknown symbol snd_ac97_pcm_assign
[4294697.767000] snd_atiixp: Unknown symbol snd_pcm_hw_constraint_integer
[4294697.767000] snd_atiixp: Unknown symbol snd_pcm_period_elapsed
[4294697.767000] snd_atiixp: Unknown symbol snd_pcm_hw_constraint_step
[4294697.767000] snd_atiixp: Unknown symbol snd_ac97_tune_hardware
[4294698.016000] Linux Kernel Card Services
[4294698.016000]   options:  [pci] [cardbus] [pm]
[4294698.027000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[4294698.027000] ACPI: PCI Interrupt 0000:06:06.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[4294698.027000] Yenta: CardBus bridge found at 0000:06:06.0 [1025:0080]
[4294698.027000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294698.027000] Yenta: Routing CardBus interrupts to PCI
[4294698.027000] Yenta TI: socket 0000:06:06.0, mfunc 0x010a1b22, devctl 0x64
[4294698.248000] Yenta: ISA IRQ mask 0x00f8, PCI irq 11
[4294698.248000] Socket status: 30000006
[4294698.340000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294698.340000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[4294698.340000] ACPI: PCI Interrupt 0000:06:06.2[C] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[4294698.394000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[c0208000-c02087ff]  Max Packet=[2048]
[4294700.423000] Real Time Clock Driver v1.12
[4294700.477000] input: PC Speaker
[4294701.357000] r8169: eth0: link up
[4294701.366000] NET: Registered protocol family 17
[4294703.318000] pnp: Device 00:09 disabled.
[4294703.319000] pnp: Device 00:09 activated.
[4294703.337000] irda_init()
[4294703.337000] NET: Registered protocol family 23
[4294703.341000] nsc-ircc, Found chip at base=0x02e
[4294703.341000] nsc-ircc, driver loaded (Dag Brattli)
[4294703.344000] IrDA: Registered device irda0
[4294703.344000] nsc-ircc, Found dongle: HP HSDL-1100/HSDL-2100
[4294704.829000] spurious 8259A interrupt: IRQ7.
[4294705.095000] NET: Registered protocol family 10
[4294705.096000] Disabled Privacy Extensions on device c02eb280(lo)
[4294705.096000] IPv6 over IPv4 tunneling driver
[4294706.307000] ACPI: AC Adapter [ADP1] (on-line)
[4294706.530000] ACPI: Battery Slot [BAT0] (battery present)
[4294706.547000] ACPI: Power Button (FF) [PWRF]
[4294706.547000] ACPI: Lid Switch [LID0]
[4294706.547000] ACPI: Sleep Button (CM) [SLPB]
[4294706.637000] ibm_acpi: ec object not found
[4294706.736000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294706.737000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294711.689000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294711.691000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[4294711.692000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294711.692000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294711.692000] [fglrx] module loaded - fglrx 8.19.10 [Nov  9 2005] on minor 0
[4294711.698000] [fglrx] ACPI power management is initialized.
[4294712.711000] [fglrx] free  PCIe = 51118080
[4294712.711000] [fglrx] max   PCIe = 51118080
[4294712.711000] [fglrx] free  LFB = 119762944
[4294712.711000] [fglrx] max   LFB = 119762944
[4294712.711000] [fglrx] free  Inv = 0
[4294712.711000] [fglrx] max   Inv = 0
[4294712.711000] [fglrx] total Inv = 0
[4294712.711000] [fglrx] total TIM = 0
[4294712.711000] [fglrx] total FB  = 0
[4294712.711000] [fglrx] total PCIe = 16384
[4294715.884000] eth0: no IPv6 routers present
[4294717.795000] apm: BIOS not found.
[4294717.970000] ip_tables: (C) 2000-2002 Netfilter core team
[4294718.008000] ip_conntrack version 2.1 (4085 buckets, 32680 max) - 248 bytes per conntrack
[4294719.358000] irlap_change_speed(), setting speed to 9600
[4294720.797000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294720.800000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[4294720.801000] cs: IO port probe 0xa00-0xaff: clean.
[4294721.005000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[4294721.005000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4 (1450 mV)
[4294721.005000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6 (1400 mV)
[4294721.005000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[4294721.006000] cpu_init done, current fid 0xa, vid 0x4
[4294721.662000] Bluetooth: Core ver 2.7
[4294721.662000] NET: Registered protocol family 31
[4294721.662000] Bluetooth: HCI device and connection manager initialized
[4294721.662000] Bluetooth: HCI socket layer initialized
[4294721.711000] Bluetooth: L2CAP ver 2.7
[4294721.711000] Bluetooth: L2CAP socket layer initialized
[4294721.753000] Bluetooth: RFCOMM ver 1.5
[4294721.753000] Bluetooth: RFCOMM socket layer initialized
[4294721.753000] Bluetooth: RFCOMM TTY layer initialized
[4294722.501000] /dev/vmmon[8053]: Module vmmon: registered with major=10 minor=165
[4294722.501000] /dev/vmmon[8053]: Module vmmon: initialized
[4294722.826000] /dev/vmnet: open called by PID 8087 (vmnet-bridge)
[4294722.826000] /dev/vmnet: hub 0 does not exist, allocating memory.
[4294722.826000] /dev/vmnet: port on hub 0 successfully opened
[4294722.826000] bridge-eth0: enabling the bridge
[4294722.826000] bridge-eth0: up
[4294722.826000] bridge-eth0: already up
[4294722.826000] bridge-eth0: attached
[4294722.847000] /dev/vmnet: open called by PID 8101 (vmnet-natd)
[4294722.847000] /dev/vmnet: hub 8 does not exist, allocating memory.
[4294722.847000] /dev/vmnet: port on hub 8 successfully opened
[4294732.937000] /dev/vmnet: open called by PID 8166 (vmnet-netifup)
[4294732.937000] /dev/vmnet: hub 1 does not exist, allocating memory.
[4294732.937000] /dev/vmnet: port on hub 1 successfully opened
[4294732.940000] /dev/vmnet: open called by PID 8167 (vmnet-netifup)
[4294732.940000] /dev/vmnet: port on hub 8 successfully opened
[4294733.095000] /dev/vmnet: open called by PID 8215 (vmnet-dhcpd)
[4294733.095000] /dev/vmnet: port on hub 8 successfully opened
[4294733.143000] /dev/vmnet: open called by PID 8187 (vmnet-dhcpd)
[4294733.143000] /dev/vmnet: port on hub 1 successfully opened
[4294743.345000] vmnet8: no IPv6 routers present
[4294743.350000] vmnet1: no IPv6 routers present
[4294744.331000] input: AT Translated Set 2 keyboard on isa0060/serio0
```

continued...

---

### Post by gma on 2006-01-02
and here is "less /var/log/syslog"...

```

Jan  2 15:43:49 localhost syslogd 1.4.1#17ubuntu3: restart.
Jan  2 15:43:49 localhost kernel: Inspecting /boot/System.map-2.6.12-10-386
Jan  2 15:43:49 localhost kernel: Loaded 29010 symbols from /boot/System.map-2.6.12-10-386.
Jan  2 15:43:49 localhost kernel: Symbols match kernel version 2.6.12.
Jan  2 15:43:49 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Jan  2 15:43:49 localhost kernel: nd address 2
Jan  2 15:43:49 localhost kernel: [4294676.721000] usbcore: registered new driver hiddev
Jan  2 15:43:49 localhost kernel: [4294676.733000] input: USB HID v1.10 Mouse [1241:1177] on usb-0000:00:13.1-2
Jan  2 15:43:49 localhost kernel: [4294676.733000] usbcore: registered new driver usbhid
Jan  2 15:43:49 localhost kernel: [4294676.733000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
Jan  2 15:43:49 localhost kernel: [4294677.087000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Jan  2 15:43:49 localhost kernel: [4294677.137000] ACPI: Thermal Zone [TZS0] (50 C)
Jan  2 15:43:49 localhost kernel: [4294677.189000] ACPI: Thermal Zone [TZS1] (37 C)
Jan  2 15:43:49 localhost kernel: [4294677.241000] ACPI: Thermal Zone [TZSV] (44 C)
Jan  2 15:43:49 localhost kernel: [4294677.507000] Attempting manual resume
Jan  2 15:43:49 localhost kernel: [4294677.507000] swsusp: Suspend partition has wrong signature?
Jan  2 15:43:49 localhost kernel: [4294677.526000] kjournald starting.  Commit interval 5 seconds
Jan  2 15:43:49 localhost kernel: [4294677.526000] EXT3-fs: mounted filesystem with ordered data mode.
Jan  2 15:43:49 localhost kernel: [4294678.834000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Jan  2 15:43:49 localhost kernel: [4294682.038000] Adding 1510036k swap on /dev/hda6.  Priority:-1 extents:1
Jan  2 15:43:49 localhost kernel: [4294682.326000] EXT3 FS on hda2, internal journal
Jan  2 15:43:49 localhost kernel: [4294688.861000] lp: driver loaded but no devices found
Jan  2 15:43:49 localhost kernel: [4294688.895000] mice: PS/2 mouse device common for all mice
Jan  2 15:43:49 localhost kernel: [4294688.934000] ieee1394: Initialized config rom entry `ip1394'
Jan  2 15:43:49 localhost kernel: [4294688.939000] SCSI subsystem initialized
Jan  2 15:43:49 localhost kernel: [4294688.943000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Jan  2 15:43:49 localhost kernel: [4294689.655000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
Jan  2 15:43:49 localhost kernel: [4294689.657000] input: SynPS/2 Synaptics TouchPad on isa0060/serio4
Jan  2 15:43:49 localhost kernel: [4294689.691000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Jan  2 15:43:49 localhost kernel: [4294689.999000] ts: Compaq touchscreen protocol output
Jan  2 15:43:49 localhost kernel: [4294691.618000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
Jan  2 15:43:49 localhost kernel: [4294692.635000] cdrom: open failed.
Jan  2 15:43:49 localhost kernel: [4294693.872000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
Jan  2 15:43:49 localhost kernel: [4294695.467000] Linux agpgart interface v0.101 (c) Dave Jones
Jan  2 15:43:49 localhost kernel: [4294695.551000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan  2 15:43:50 localhost kernel: [4294695.566000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: disagrees about version of symbol snd_info_register
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: Unknown symbol snd_info_register
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: Unknown symbol snd_info_create_module_entry
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: disagrees about version of symbol snd_info_free_entry
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: Unknown symbol snd_info_free_entry
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: disagrees about version of symbol snd_iprintf
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: Unknown symbol snd_iprintf
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: disagrees about version of symbol snd_unregister_device
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: Unknown symbol snd_unregister_device
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: disagrees about version of symbol snd_device_new
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: Unknown symbol snd_device_new
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: Unknown symbol snd_kmalloc_strdup
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: disagrees about version of symbol snd_info_unregister
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: Unknown symbol snd_info_unregister
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: disagrees about version of symbol snd_register_device
Jan  2 15:43:50 localhost kernel: [4294695.959000] snd_timer: Unknown symbol snd_register_device
Jan  2 15:43:50 localhost kernel: [4294695.963000] snd_timer: disagrees about version of symbol snd_info_register
Jan  2 15:43:50 localhost kernel: [4294695.963000] snd_timer: Unknown symbol snd_info_register
Jan  2 15:43:50 localhost kernel: [4294695.963000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
Jan  2 15:43:50 localhost kernel: [4294695.963000] snd_timer: Unknown symbol snd_info_create_module_entry
Jan  2 15:43:50 localhost kernel: [4294695.963000] snd_timer: disagrees about version of symbol snd_info_free_entry
Jan  2 15:43:50 localhost kernel: [4294695.963000] snd_timer: Unknown symbol snd_info_free_entry
Jan  2 15:43:50 localhost kernel: [4294695.963000] snd_timer: disagrees about version of symbol snd_iprintf
Jan  2 15:43:50 localhost kernel: [4294695.963000] snd_timer: Unknown symbol snd_iprintf
Jan  2 15:43:50 localhost kernel: [4294695.963000] snd_timer: disagrees about version of symbol snd_unregister_device
Jan  2 15:43:50 localhost kernel: [4294695.963000] snd_timer: Unknown symbol snd_unregister_device
Jan  2 15:43:50 localhost kernel: [4294695.963000] snd_timer: disagrees about version of symbol snd_device_new
Jan  2 15:43:50 localhost kernel: [4294695.964000] snd_timer: Unknown symbol snd_device_new
Jan  2 15:43:50 localhost kernel: [4294695.964000] snd_timer: Unknown symbol snd_kmalloc_strdup
Jan  2 15:43:50 localhost kernel: [4294695.964000] snd_timer: disagrees about version of symbol snd_info_unregister
Jan  2 15:43:50 localhost kernel: [4294695.964000] snd_timer: Unknown symbol snd_info_unregister
Jan  2 15:43:50 localhost kernel: [4294695.964000] snd_timer: disagrees about version of symbol snd_register_device
Jan  2 15:43:50 localhost kernel: [4294695.964000] snd_timer: Unknown symbol snd_register_device
Jan  2 15:43:50 localhost kernel: [4294695.964000] snd_pcm: Unknown symbol snd_timer_notify
Jan  2 15:43:50 localhost kernel: [4294695.964000] snd_pcm: Unknown symbol snd_timer_interrupt

```

I've cropped it a bit to fit into the 30K chars limit per post.

Very big thanks in advance :-)

---

### Post by giftnudel on 2006-01-02
Ok, this was far more useful. I think it's obvious to see, that there is something wrong with the sound modules. I don't really have a hint for that.

I would suggest you search in [bugzilla.ubuntu.com]("http://bugzilla.ubuntu.com") and open a new bug, if there is none, that matches your problem. 

I can't help you anymore, this is a kernel related bug and I don't have a clue. 
giftnudel

---

### Post by gma on 2006-01-02
Problem solved... unfortunately in an unpretty way. Upgrading to dapper solved all my problems with sound and also... with suspending and hibernation :-D

Everyone, who has an Acer Aspire 5024WLMi should be happy to know about that :-) (although upgrading the whole system seems to be too much -- compiling the newest kernel should also do the trick).

Acer owners be warned -- suspend and hibernation work in dapper, but upgarding broke other features, like main menu (it dissapears) and banshee (doesn't even start).

---

