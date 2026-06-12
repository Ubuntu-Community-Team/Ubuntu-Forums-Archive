---
title: "System keeps running but nothing works"
date: 2009-01-03
forum: General Help
---

### Post by clockworksaint on 2009-01-03
I have today twice encountered a rather strange hang, and I'm not even sure how to go about diagnosing the problem. At the moment I'm not sure I know enough to even get help, but I'm hoping that someone can tell me what to do next time it happens to at least get some useful information.

In both cases, the first I have noticed something is wrong is when I'm web browsing and it times out waiting for a page. Then I notice the networking icon in the top right shows I'm disconnected, and I click on it, but all that appears in the menu is something like "networking disabled". After that I open a terminal, which works, but when I try to enter a command like "iwconfig" or "ifconfig" to try to see what's going on, nothing happens: when I hit enter the cursor moves to the next line and continues blinking, but no output appears. If I press CTRL+C then I just see "^C" appear and still nothing happens. I can open further terminal windows from the Applications menu, but all will hang if I do the same thing.

The first time it happened, I managed to shut down the laptop by using the command in the top-right menu. The shut-down sequence appeared to complete, but at the end instead of shutting down the screen showed a garbled mess with faint pieces of text barely visible, a little like a much brighter version of what you get on an old burned-in monitor.

The second time it was rather similar, except that I tried to shut-down from a console first, but "sudo shutdown -r now" did the same as when I tried to run "ifconfig". However, it went ahead and shut-down when I pressed CTRL+ALT+DEL while on one of the text consoles. (The ones you get to when you press CTRL+ALT+F1-F6.) Again it displayed the same (or similar) garbled screen.

I installed Ubuntu on this laptop only a few days ago. It's a Philips 15NB8611 with a Core 2 Duo P7350, 4GB of RAM and some kind of NVIDIA graphics card. I had a different problem that caused it to fail to resume from suspend, but that seems to have been fixed since I changed the hard-disk controller in the BIOS from AHCI to IDE.

If this happens again, what should I do a) while it is happening, and b) after rebooting, in order to start tracking down the problem?

---

### Post by ByKeLaO on 2009-01-03
Take a peek in the system logs (System->Administration->System Log) and post anything you think looks like an error or warning here. Someone is bound to know what's wrong.

---

### Post by clockworksaint on 2009-01-03
Aha. Thanks! This looks like it happened at about the time of the problem. It comes shortly after resuming from hibernation, so I'm not sure if I've accidentally included messages from that at the beginning, but it does look like an error. This is from the "messages" log:

```

Jan  3 14:45:57 dischord kernel: [ 7103.411832] r8169: eth0: link down
Jan  3 14:45:57 dischord kernel: [ 7103.413703] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  3 14:45:57 dischord kernel: [ 7103.417522] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  3 14:45:57 dischord kernel: [ 7103.428197] CPU 1 
Jan  3 14:45:57 dischord kernel: [ 7103.428357] Modules linked in: ipv6 aes_x86_64 aes_generic af_packet binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev acpi_cpufreq cpufreq_ondemand cpufreq_powersave cpufreq_userspace cpufreq_conservative cpufreq_stats freq_table pci_slot sbs container sbshc wmi iptable_filter ip_tables x_tables parport_pc lp parport joydev snd_hda_intel uvcvideo serio_raw snd_pcm_oss compat_ioctl32 psmouse arc4 videodev snd_mixer_oss ecb pcspkr snd_pcm crypto_blkcipher v4l1_compat evdev nvidia(P) snd_seq_dummy i2c_core iwlagn iwlcore snd_seq_oss rfkill snd_seq_midi led_class video mac80211 output snd_rawmidi snd_seq_midi_event cfg80211 ac snd_seq button battery snd_timer snd_seq_device shpchp pci_hotplug intel_agp snd soundcore snd_page_alloc ext3 jbd mbcache usb_storage sr_mod cdrom sd_mod crc_t10dif sg ata_generic libusual ata_piix pata_acpi libata scsi_mod dock r8169 ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Jan  3 14:45:57 dischord kernel: [ 7103.431843] Pid: 5274, comm: NetworkManager Tainted: P          2.6.27-9-generic #1
Jan  3 14:45:57 dischord kernel: [ 7103.431843] RIP: 0010:[<ffffffffa02a9360>]  [<ffffffffa02a9360>] iwl_eeprom_query16+0x10/0x20 [iwlcore]
Jan  3 14:45:57 dischord kernel: [ 7103.431843] RSP: 0018:ffff88013a57b728  EFLAGS: 00010046
Jan  3 14:45:57 dischord kernel: [ 7103.431843] RAX: 7fff88013d077000 RBX: 0000000000000246 RCX: 00000000800200f0
Jan  3 14:45:57 dischord kernel: [ 7103.431843] RDX: ffffc2000064c03c RSI: 0000000000000090 RDI: ffff88013c081a00
Jan  3 14:45:57 dischord kernel: [ 7103.431843] RBP: ffff88013a57b728 R08: 0000000000000001 R09: ffff88013a57b6fc
Jan  3 14:45:57 dischord kernel: [ 7103.431843] R10: 0000000000000000 R11: ffff88013a57b6f8 R12: ffff88013c081a00
Jan  3 14:45:57 dischord kernel: [ 7103.431843] R13: ffff88013c081a00 R14: ffff88013c082448 R15: 0000000000000246
Jan  3 14:45:57 dischord kernel: [ 7103.431843] FS:  00007f7e7572a730(0000) GS:ffff88013fc02980(0000) knlGS:0000000000000000
Jan  3 14:45:57 dischord kernel: [ 7103.431843] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jan  3 14:45:57 dischord kernel: [ 7103.431843] CR2: 000000000041d160 CR3: 0000000135d6a000 CR4: 00000000000006a0
Jan  3 14:45:57 dischord kernel: [ 7103.431843] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jan  3 14:45:57 dischord kernel: [ 7103.431843] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jan  3 14:45:57 dischord kernel: [ 7103.431843] Process NetworkManager (pid: 5274, threadinfo ffff88013a57a000, task ffff8801349159c0)
Jan  3 14:45:57 dischord kernel: [ 7103.431843] Stack:  ffff88013a57b778 ffffffffa02d0a90 0000000000000246 ffffffffffffff10
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  40ffffff805026d8 0000000000000246 ffff88013c081a00 ffff88013c082448
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  ffff88013c082b50 ffff88013c080060 ffff88013a57b7a8 ffffffffa02a7dbb
Jan  3 14:45:57 dischord kernel: [ 7103.431843] Call Trace:
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffffa02d0a90>] iwl5000_nic_config+0x70/0x200 [iwlagn]
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffffa02a7dbb>] iwl_hw_nic_init+0x9b/0x160 [iwlcore]
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffffa02c6e3a>] __iwl4965_up+0xba/0x2d0 [iwlagn]
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffffa02c7544>] iwl4965_mac_start+0xe4/0x350 [iwlagn]
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff80485d58>] ? __nla_reserve+0x58/0x70
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffffa02446a2>] ieee80211_open+0x152/0x690 [mac80211]
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff8045c2ad>] ? skb_put+0xd/0xa0
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff80466c22>] dev_open+0xb2/0xf0
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff804662eb>] dev_change_flags+0x9b/0x1e0
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff80470654>] do_setlink+0x214/0x3b0
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff8046fe76>] ? rtnl_fill_ifinfo+0x2f6/0x420
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff8048617b>] ? nla_parse+0x3b/0x110
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff80470905>] rtnl_setlink+0x115/0x160
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff80234059>] ? __phys_addr+0x9/0x50
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff8046f8ce>] rtnetlink_rcv_msg+0x18e/0x240
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff8046f740>] ? rtnetlink_rcv_msg+0x0/0x240
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff804846a9>] netlink_rcv_skb+0x89/0xb0
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff8046f72c>] rtnetlink_rcv+0x2c/0x40
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff804843b5>] netlink_unicast+0x2c5/0x2e0
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff80485674>] netlink_sendmsg+0x204/0x2f0
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff803836f0>] ? aa_revalidate_sk+0x20/0xd0
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff80456cac>] sock_sendmsg+0x10c/0x140
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff80267050>] ? autoremove_wake_function+0x0/0x40
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff8045659c>] ? move_addr_to_kernel+0x5c/0x60
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff8045f434>] ? verify_iovec+0x44/0xd0
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff80456e6e>] sys_sendmsg+0x18e/0x320
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff8021425e>] ? math_state_restore+0xe/0xb0
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff805006a4>] ? thread_return+0x37/0x3c3
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Jan  3 14:45:57 dischord kernel: [ 7103.431843] 
Jan  3 14:45:57 dischord kernel: [ 7103.431843] 
Jan  3 14:45:57 dischord kernel: [ 7103.431843]  RSP <ffff88013a57b728>
Jan  3 14:45:57 dischord kernel: [ 7103.431843] ---[ end trace fb2e1bb9bbe0c9b0 ]---
Jan  3 14:46:11 dischord kernel: [ 7117.416153] usb 3-1: reset high speed USB device using ehci_hcd and address 2
Jan  3 14:48:24 dischord kernel: [ 7250.022657] atkbd.c: Unknown key released (translated set 2, code 0xf3 on isa0060/serio0).
Jan  3 14:48:24 dischord kernel: [ 7250.022673] atkbd.c: Use 'setkeycodes e073 <keycode>' to make it known.
Jan  3 14:48:30 dischord kernel: [ 7256.576980] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Jan  3 14:50:33 dischord kernel: [ 7379.355138] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jan  3 14:50:36 dischord exiting on signal 15

```

Does this look like the root cause of my problem? Would such an error cause stuff to become unresponsive like I observed? I'm not really Linux-savvy enough to tell anything more than it appears the NetworkManager process died and output a stack trace.

---

### Post by ByKeLaO on 2009-01-03
I really don't think networkmanager crashing should bring the whole system down like that.
You may be able to fix that particular problem by following this guide:
**[http://ubuntuforums.org/showpost.php?p=6264243&postcount=8](http://ubuntuforums.org/showpost.php?p=6264243&postcount=8)**
Although I doubt that would stop your computer from crashing. Perhaps someone else can help you out :(

---

### Post by clockworksaint on 2009-01-03
In case it's relevant, here's what lspci has to say about the wireless card:
```

02:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]
	Subsystem: Intel Corporation Device [8086:1201]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 2298
	Region 0: Memory at d8100000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
		Address: 00000000fee0300c  Data: 41a9
	Capabilities: [e0] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset+
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ FLReset-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <128ns, L1 <32us
			ClockPM+ Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 1c-93-48-ff-ff-ea-16-00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

```

---

### Post by ByKeLaO on 2009-01-03
OK, try this:
```
sudo gedit /etc/pm/config.d/00sleep_module
```
Add this to the end of the file:
```
SUSPEND_MODULES="iwlagn"
```

---

### Post by clockworksaint on 2009-01-03
Thank you very much, I'll try that. Sadly I'm not really sure how to reliably trigger the problem, so I'll just have to wait and see if it happens again. Could you tell me what that setting does? It looks like maybe it causes the wireless network driver to be handled specially during standby or hibernation?

---

### Post by ByKeLaO on 2009-01-03
I'm not entirely sure what it does, all I know is that it fixed my wireless cutting out after suspend/resume, so I thought I'd suggest it to you in case it solved your problem too.

---

### Post by clockworksaint on 2009-01-05
Okay, it didn't work, the problem happened again. It happened a few minutes after I resumed from suspend. Here's the messages file from the moment I opened the lid:

```

Jan  5 19:21:28 dischord kernel: [19421.082073] PM: Syncing filesystems ... done.
Jan  5 19:21:28 dischord kernel: [19421.082112] Freezing user space processes ... (elapsed 0.00 seconds) done.
Jan  5 19:21:28 dischord kernel: [19421.083402] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Jan  5 19:21:28 dischord kernel: [19421.083461] Suspending console(s) (use no_console_suspend to debug)
Jan  5 19:21:28 dischord kernel: [19421.100120] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jan  5 19:21:28 dischord kernel: [19421.342864] sd 0:0:0:0: [sda] Stopping disk
Jan  5 19:21:28 dischord kernel: [19422.284251] NVRM: RmPowerManagement: 4
Jan  5 19:21:28 dischord kernel: [19422.794052] ata_piix 0000:00:1f.5: PCI INT B disabled
Jan  5 19:21:28 dischord kernel: [19422.808238] ata_piix 0000:00:1f.2: PCI INT B disabled
Jan  5 19:21:28 dischord kernel: [19422.824245] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Jan  5 19:21:28 dischord kernel: [19422.840148] uhci_hcd 0000:00:1d.3: PCI INT C disabled
Jan  5 19:21:28 dischord kernel: [19422.840203] uhci_hcd 0000:00:1d.2: PCI INT D disabled
Jan  5 19:21:28 dischord kernel: [19422.840249] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Jan  5 19:21:28 dischord kernel: [19422.840296] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Jan  5 19:21:28 dischord kernel: [19422.856120] HDA Intel 0000:00:1b.0: PCI INT A disabled
Jan  5 19:21:28 dischord kernel: [19422.872156] ehci_hcd 0000:00:1a.7: PCI INT D disabled
Jan  5 19:21:28 dischord kernel: [19422.888146] uhci_hcd 0000:00:1a.1: PCI INT B disabled
Jan  5 19:21:28 dischord kernel: [19422.888201] uhci_hcd 0000:00:1a.0: PCI INT A disabled
Jan  5 19:21:28 dischord kernel: [19422.888297] PM: suspend devices took 1.808 seconds
Jan  5 19:21:28 dischord kernel: [19422.888707] ACPI: Preparing to enter system sleep state S3
Jan  5 19:21:28 dischord kernel: [19423.128100] Disabling non-boot CPUs ...
Jan  5 19:21:28 dischord kernel: [19423.232034] CPU 1 is now offline
Jan  5 19:21:28 dischord kernel: [19423.232038] SMP alternatives: switching to UP code
Jan  5 19:21:28 dischord kernel: [19423.252244] CPU1 is down
Jan  5 19:21:28 dischord kernel: [19423.252244] Enabling non-boot CPUs ...
Jan  5 19:21:28 dischord kernel: [19423.252244] SMP alternatives: switching to SMP code
Jan  5 19:21:28 dischord kernel: [19423.261329] Booting processor 1/1 ip 6000
Jan  5 19:21:28 dischord kernel: [19423.132226] Initializing CPU#1
Jan  5 19:21:28 dischord kernel: [19423.132226] Calibrating delay using timer specific routine.. 3997.61 BogoMIPS (lpj=7995239)
Jan  5 19:21:28 dischord kernel: [19423.132226] CPU: L1 I cache: 32K, L1 D cache: 32K
Jan  5 19:21:28 dischord kernel: [19423.132226] CPU: L2 cache: 3072K
Jan  5 19:21:28 dischord kernel: [19423.132226] CPU 1/1 -> Node 0
Jan  5 19:21:28 dischord kernel: [19423.132226] CPU: Physical Processor ID: 0
Jan  5 19:21:28 dischord kernel: [19423.132226] CPU: Processor Core ID: 1
Jan  5 19:21:28 dischord kernel: [19423.356949] CPU1: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz stepping 06
Jan  5 19:21:28 dischord kernel: [19423.372574] CPU1 is up
Jan  5 19:21:28 dischord kernel: [19423.372577] ACPI: Waking up from system sleep state S3
Jan  5 19:21:28 dischord kernel: [19424.852520] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jan  5 19:21:28 dischord kernel: [19424.876675] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  5 19:21:28 dischord kernel: [19424.876737] usb usb1: root hub lost power or was reset
Jan  5 19:21:28 dischord kernel: [19424.876756] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jan  5 19:21:28 dischord kernel: [19424.876817] usb usb2: root hub lost power or was reset
Jan  5 19:21:28 dischord kernel: [19424.892106] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jan  5 19:21:28 dischord kernel: [19424.908157] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jan  5 19:21:28 dischord kernel: [19424.908431] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jan  5 19:21:28 dischord kernel: [19424.908493] usb usb4: root hub lost power or was reset
Jan  5 19:21:28 dischord kernel: [19424.908510] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan  5 19:21:28 dischord kernel: [19424.908572] usb usb5: root hub lost power or was reset
Jan  5 19:21:28 dischord kernel: [19424.908590] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Jan  5 19:21:28 dischord kernel: [19424.908650] usb usb6: root hub lost power or was reset
Jan  5 19:21:28 dischord kernel: [19424.908667] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan  5 19:21:28 dischord kernel: [19424.908728] usb usb7: root hub lost power or was reset
Jan  5 19:21:28 dischord kernel: [19424.924101] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jan  5 19:21:28 dischord kernel: [19424.940146] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan  5 19:21:28 dischord kernel: [19424.956148] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan  5 19:21:28 dischord kernel: [19424.957363] NVRM: RmPowerManagement: 5
Jan  5 19:21:28 dischord kernel: [19425.289112] ata4: SATA link down (SStatus 0 SControl 300)
Jan  5 19:21:28 dischord kernel: [19425.396781] ata3: SATA link down (SStatus 4 SControl 300)
Jan  5 19:21:28 dischord kernel: [19425.428648] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan  5 19:21:28 dischord kernel: [19425.453274] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Jan  5 19:21:28 dischord kernel: [19425.453277] ata2.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Jan  5 19:21:28 dischord kernel: [19425.493269] ata2.00: configured for UDMA/100
Jan  5 19:21:28 dischord kernel: [19425.696553] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan  5 19:21:28 dischord kernel: [19425.697436] pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  5 19:21:28 dischord kernel: [19425.744644] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Jan  5 19:21:28 dischord kernel: [19425.744646] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Jan  5 19:21:28 dischord kernel: [19425.769529] ata1.00: configured for UDMA/133
Jan  5 19:21:28 dischord kernel: [19425.769630] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Jan  5 19:21:28 dischord kernel: [19425.769649] sd 0:0:0:0: [sda] Write Protect is off
Jan  5 19:21:28 dischord kernel: [19425.769681] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  5 19:21:28 dischord kernel: [19425.956078] sd 0:0:0:0: [sda] Starting disk
Jan  5 19:21:28 dischord kernel: [19426.076105] usb 3-4: reset high speed USB device using ehci_hcd and address 3
Jan  5 19:21:28 dischord kernel: [19426.226513] uvcvideo 3-4:1.0: no reset_resume for driver uvcvideo?
Jan  5 19:21:28 dischord kernel: [19426.226516] uvcvideo 3-4:1.1: no reset_resume for driver uvcvideo?
Jan  5 19:21:28 dischord kernel: [19426.237178] uvcvideo: Found UVC 1.00 device USB Webcam (0408:20ba)
Jan  5 19:21:28 dischord kernel: [19426.241968] input: USB Webcam as /devices/pci0000:00/0000:00:1a.7/usb3/3-4/3-4:1.0/input/input12
Jan  5 19:21:28 dischord kernel: [19426.256385] PM: resume devices took 2.804 seconds
Jan  5 19:21:28 dischord kernel: [19426.256406] Restarting tasks ... done.
Jan  5 19:21:29 dischord kernel: [19426.796910] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
Jan  5 19:21:29 dischord kernel: [19426.796917] iwlagn: Copyright(c) 2003-2008 Intel Corporation
Jan  5 19:21:29 dischord kernel: [19426.797392] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  5 19:21:29 dischord kernel: [19426.797429] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
Jan  5 19:21:29 dischord kernel: [19426.827064] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
Jan  5 19:21:29 dischord kernel: [19427.713630] r8169: eth0: link down
Jan  5 19:21:29 dischord kernel: [19427.719903] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  5 19:21:34 dischord kernel: [19431.736799] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  5 19:21:34 dischord kernel: [19431.737046] firmware: requesting iwlwifi-5000-1.ucode
Jan  5 19:21:36 dischord kernel: [19433.862018] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Jan  5 19:21:36 dischord kernel: [19433.883811] Registered led device: iwl-phy0:radio
Jan  5 19:21:36 dischord kernel: [19433.885067] Registered led device: iwl-phy0:assoc
Jan  5 19:21:36 dischord kernel: [19433.885200] Registered led device: iwl-phy0:RX
Jan  5 19:21:36 dischord kernel: [19433.885306] Registered led device: iwl-phy0:TX
Jan  5 19:21:36 dischord kernel: [19433.910480] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  5 19:25:49 dischord bonobo-activation-server (weeble-14146): could not associate with desktop session: Failed to connect to socket /tmp/dbus-HBfFXqmV98: Connection refused
Jan  5 19:26:23 dischord kernel: [19721.324734] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jan  5 19:26:25 dischord exiting on signal 15

```
The problem happened some time shortly after 19:21:36.
Here's syslog over the same period:
```

Jan  5 19:21:29 dischord NetworkManager: <info>  Waking up... 
Jan  5 19:21:29 dischord NetworkManager: <info>  (eth0): now managed 
Jan  5 19:21:29 dischord NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jan  5 19:21:29 dischord NetworkManager: <info>  (eth0): bringing up device. 
Jan  5 19:21:29 dischord kernel: [19427.713630] r8169: eth0: link down
Jan  5 19:21:29 dischord NetworkManager: <info>  (eth0): preparing device. 
Jan  5 19:21:29 dischord kernel: [19427.719903] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  5 19:21:30 dischord NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Jan  5 19:21:30 dischord NetworkManager: <info>  wlan0: driver is 'iwlagn'. 
Jan  5 19:21:30 dischord NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Jan  5 19:21:30 dischord NetworkManager: <info>  Found new 802.11 WiFi device 'wlan0'. 
Jan  5 19:21:30 dischord NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_16_ea_48_93_1c_0 
Jan  5 19:21:30 dischord NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jan  5 19:21:30 dischord NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Jan  5 19:21:30 dischord acpid: client connected from 10313[0:0] 
Jan  5 19:21:31 dischord acpid: client connected from 10313[0:0] 
Jan  5 19:21:34 dischord NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Jan  5 19:21:34 dischord NetworkManager: <info>  (wlan0): bringing up device. 
Jan  5 19:21:34 dischord kernel: [19431.736799] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  5 19:21:34 dischord kernel: [19431.737046] firmware: requesting iwlwifi-5000-1.ucode
Jan  5 19:21:36 dischord kernel: [19433.862018] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Jan  5 19:21:36 dischord kernel: [19433.883811] Registered led device: iwl-phy0:radio
Jan  5 19:21:36 dischord kernel: [19433.885067] Registered led device: iwl-phy0:assoc
Jan  5 19:21:36 dischord kernel: [19433.885200] Registered led device: iwl-phy0:RX
Jan  5 19:21:36 dischord kernel: [19433.885306] Registered led device: iwl-phy0:TX
Jan  5 19:21:36 dischord kernel: [19433.910480] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  5 19:21:36 dischord NetworkManager: <info>  (wlan0): preparing device. 
Jan  5 19:21:36 dischord NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Jan  5 19:21:36 dischord NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Jan  5 19:21:36 dischord NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2. 
Jan  5 19:21:37 dischord NetworkManager: <info>  Activation (wlan0) starting connection 'Auto solstice' 
Jan  5 19:21:37 dischord NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Jan  5 19:21:37 dischord NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  5 19:21:37 dischord NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jan  5 19:21:37 dischord NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jan  5 19:21:37 dischord NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jan  5 19:21:37 dischord NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jan  5 19:21:37 dischord NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Jan  5 19:21:37 dischord NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto solstice' has security, and secrets exist.  No new secrets needed. 
Jan  5 19:21:37 dischord NetworkManager: <info>  Config: added 'ssid' value 'solstice' 
Jan  5 19:21:37 dischord NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jan  5 19:21:37 dischord NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jan  5 19:21:37 dischord NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jan  5 19:21:37 dischord NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Jan  5 19:21:37 dischord NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Jan  5 19:21:37 dischord NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Jan  5 19:21:37 dischord NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jan  5 19:21:37 dischord NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 0 
Jan  5 19:21:37 dischord NetworkManager: <info>  Config: set interface ap_scan to 1 
Jan  5 19:21:42 dischord NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Jan  5 19:21:44 dischord NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Jan  5 19:21:44 dischord kernel: [19442.397145] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:21:44 dischord kernel: [19442.399301] wlan0: authenticated
Jan  5 19:21:44 dischord kernel: [19442.399312] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:21:44 dischord kernel: [19442.402258] wlan0: RX AssocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:21:44 dischord kernel: [19442.402267] wlan0: associated
Jan  5 19:21:49 dischord kernel: [19447.403361] wlan0: deauthenticated
Jan  5 19:21:50 dischord kernel: [19448.400517] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:21:50 dischord kernel: [19448.402229] wlan0: authenticated
Jan  5 19:21:50 dischord kernel: [19448.402235] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:21:50 dischord kernel: [19448.404716] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:21:50 dischord kernel: [19448.404721] wlan0: associated
Jan  5 19:21:54 dischord kernel: [19452.553379] wlan0: deauthenticated
Jan  5 19:21:55 dischord kernel: [19453.552027] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:21:55 dischord kernel: [19453.553727] wlan0: authenticated
Jan  5 19:21:55 dischord kernel: [19453.553733] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:21:55 dischord kernel: [19453.556235] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:21:55 dischord kernel: [19453.556242] wlan0: associated
Jan  5 19:21:59 dischord kernel: [19457.708026] wlan0: deauthenticated
Jan  5 19:22:00 dischord kernel: [19458.708045] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:00 dischord kernel: [19458.713188] wlan0: authenticated
Jan  5 19:22:00 dischord kernel: [19458.713195] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:00 dischord kernel: [19458.717246] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:22:00 dischord kernel: [19458.717257] wlan0: associated
Jan  5 19:22:05 dischord kernel: [19462.853455] wlan0: deauthenticated
Jan  5 19:22:06 dischord kernel: [19463.852122] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:06 dischord kernel: [19463.867380] wlan0: authenticated
Jan  5 19:22:06 dischord kernel: [19463.867389] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:06 dischord kernel: [19463.869916] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:22:06 dischord kernel: [19463.869922] wlan0: associated
Jan  5 19:22:10 dischord kernel: [19468.003496] wlan0: deauthenticated
Jan  5 19:22:11 dischord kernel: [19469.000039] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:11 dischord kernel: [19469.001796] wlan0: authenticated
Jan  5 19:22:11 dischord kernel: [19469.001802] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:11 dischord kernel: [19469.004330] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:22:11 dischord kernel: [19469.004335] wlan0: associated
Jan  5 19:22:15 dischord kernel: [19473.153540] wlan0: deauthenticated
Jan  5 19:22:16 dischord kernel: [19474.152187] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:16 dischord kernel: [19474.153932] wlan0: authenticated
Jan  5 19:22:16 dischord kernel: [19474.153939] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:16 dischord kernel: [19474.156616] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:22:16 dischord kernel: [19474.156621] wlan0: associated
Jan  5 19:22:20 dischord kernel: [19478.304330] wlan0: deauthenticated
Jan  5 19:22:21 dischord kernel: [19479.304031] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:21 dischord kernel: [19479.305958] wlan0: authenticated
Jan  5 19:22:21 dischord kernel: [19479.305964] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:21 dischord kernel: [19479.308377] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:22:21 dischord kernel: [19479.308384] wlan0: associated
Jan  5 19:22:25 dischord kernel: [19483.453748] wlan0: deauthenticated
Jan  5 19:22:26 dischord kernel: [19484.452026] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:26 dischord kernel: [19484.453720] wlan0: authenticated
Jan  5 19:22:26 dischord kernel: [19484.453726] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:26 dischord kernel: [19484.456224] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:22:26 dischord kernel: [19484.456230] wlan0: associated
Jan  5 19:22:30 dischord kernel: [19488.603643] wlan0: deauthenticated
Jan  5 19:22:31 dischord kernel: [19489.600041] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:31 dischord kernel: [19489.601796] wlan0: authenticated
Jan  5 19:22:31 dischord kernel: [19489.601802] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:31 dischord kernel: [19489.605073] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:22:31 dischord kernel: [19489.605079] wlan0: associated
Jan  5 19:22:36 dischord kernel: [19493.753743] wlan0: deauthenticated
Jan  5 19:22:37 dischord kernel: [19494.752039] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:37 dischord kernel: [19494.753723] wlan0: authenticated
Jan  5 19:22:37 dischord kernel: [19494.753729] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:37 dischord kernel: [19494.757792] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:22:37 dischord kernel: [19494.757797] wlan0: associated
Jan  5 19:22:41 dischord kernel: [19498.903720] wlan0: deauthenticated
Jan  5 19:22:42 dischord kernel: [19499.900047] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:42 dischord kernel: [19499.901732] wlan0: authenticated
Jan  5 19:22:42 dischord kernel: [19499.901738] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:42 dischord kernel: [19499.906374] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:22:42 dischord kernel: [19499.906381] wlan0: associated
Jan  5 19:22:46 dischord kernel: [19504.053758] wlan0: deauthenticated
Jan  5 19:22:47 dischord kernel: [19505.052044] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:47 dischord kernel: [19505.053740] wlan0: authenticated
Jan  5 19:22:47 dischord kernel: [19505.053746] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:47 dischord kernel: [19505.056320] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:22:47 dischord kernel: [19505.056325] wlan0: associated
Jan  5 19:22:51 dischord kernel: [19509.203793] wlan0: deauthenticated
Jan  5 19:22:52 dischord kernel: [19510.200064] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:52 dischord kernel: [19510.201940] wlan0: authenticated
Jan  5 19:22:52 dischord kernel: [19510.201947] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:52 dischord kernel: [19510.204357] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:22:52 dischord kernel: [19510.204363] wlan0: associated
Jan  5 19:22:56 dischord kernel: [19514.353806] wlan0: deauthenticated
Jan  5 19:22:57 dischord kernel: [19515.352041] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:57 dischord kernel: [19515.353720] wlan0: authenticated
Jan  5 19:22:57 dischord kernel: [19515.353726] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:22:57 dischord kernel: [19515.356502] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:22:57 dischord kernel: [19515.356508] wlan0: associated
Jan  5 19:23:01 dischord kernel: [19519.503854] wlan0: deauthenticated
Jan  5 19:23:02 dischord kernel: [19520.500067] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:02 dischord kernel: [19520.501771] wlan0: authenticated
Jan  5 19:23:02 dischord kernel: [19520.501778] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:02 dischord kernel: [19520.504365] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:23:02 dischord kernel: [19520.504370] wlan0: associated
Jan  5 19:23:06 dischord kernel: [19524.653895] wlan0: deauthenticated
Jan  5 19:23:07 dischord kernel: [19525.652041] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:07 dischord kernel: [19525.653718] wlan0: authenticated
Jan  5 19:23:07 dischord kernel: [19525.653724] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:07 dischord kernel: [19525.656348] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:23:07 dischord kernel: [19525.656355] wlan0: associated
Jan  5 19:23:12 dischord kernel: [19529.805612] wlan0: deauthenticated
Jan  5 19:23:13 dischord kernel: [19530.804050] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:13 dischord kernel: [19530.805928] wlan0: authenticated
Jan  5 19:23:13 dischord kernel: [19530.805937] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:13 dischord kernel: [19530.808350] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:23:13 dischord kernel: [19530.808357] wlan0: associated
Jan  5 19:23:17 dischord kernel: [19534.953939] wlan0: deauthenticated
Jan  5 19:23:18 dischord kernel: [19535.952518] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:18 dischord kernel: [19535.954283] wlan0: authenticated
Jan  5 19:23:18 dischord kernel: [19535.954289] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:18 dischord kernel: [19535.956741] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:23:18 dischord kernel: [19535.956747] wlan0: associated
Jan  5 19:23:22 dischord kernel: [19540.103979] wlan0: deauthenticated
Jan  5 19:23:23 dischord kernel: [19541.101287] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:23 dischord kernel: [19541.103083] wlan0: authenticated
Jan  5 19:23:23 dischord kernel: [19541.103090] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:23 dischord kernel: [19541.105682] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:23:23 dischord kernel: [19541.105688] wlan0: associated
Jan  5 19:23:27 dischord kernel: [19545.254141] wlan0: deauthenticated
Jan  5 19:23:28 dischord kernel: [19546.252185] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:28 dischord kernel: [19546.253869] wlan0: authenticated
Jan  5 19:23:28 dischord kernel: [19546.253876] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:28 dischord kernel: [19546.256476] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:23:28 dischord kernel: [19546.256481] wlan0: associated
Jan  5 19:23:32 dischord kernel: [19550.404082] wlan0: deauthenticated
Jan  5 19:23:33 dischord kernel: [19551.404041] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:33 dischord kernel: [19551.405732] wlan0: authenticated
Jan  5 19:23:33 dischord kernel: [19551.405739] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:33 dischord kernel: [19551.408158] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:23:33 dischord kernel: [19551.408163] wlan0: associated
Jan  5 19:23:37 dischord kernel: [19555.554083] wlan0: deauthenticated
Jan  5 19:23:38 dischord kernel: [19556.552240] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:38 dischord kernel: [19556.553923] wlan0: authenticated
Jan  5 19:23:38 dischord kernel: [19556.553930] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:38 dischord kernel: [19556.556470] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:23:38 dischord kernel: [19556.556477] wlan0: associated
Jan  5 19:23:42 dischord kernel: [19560.704203] wlan0: deauthenticated
Jan  5 19:23:43 dischord kernel: [19561.704156] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:43 dischord kernel: [19561.705848] wlan0: authenticated
Jan  5 19:23:43 dischord kernel: [19561.705855] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:43 dischord kernel: [19561.714110] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:23:43 dischord kernel: [19561.714116] wlan0: associated
Jan  5 19:23:48 dischord kernel: [19565.856860] wlan0: deauthenticated
Jan  5 19:23:49 dischord kernel: [19566.856026] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:49 dischord kernel: [19566.857773] wlan0: authenticated
Jan  5 19:23:49 dischord kernel: [19566.857779] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:49 dischord kernel: [19566.860262] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:23:49 dischord kernel: [19566.860268] wlan0: associated
Jan  5 19:23:53 dischord kernel: [19571.004347] wlan0: deauthenticated
Jan  5 19:23:54 dischord kernel: [19572.004041] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:54 dischord kernel: [19572.005803] wlan0: authenticated
Jan  5 19:23:54 dischord kernel: [19572.005809] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:54 dischord kernel: [19572.008316] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:23:54 dischord kernel: [19572.008322] wlan0: associated
Jan  5 19:23:58 dischord kernel: [19576.154330] wlan0: deauthenticated
Jan  5 19:23:59 dischord kernel: [19577.152079] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:59 dischord kernel: [19577.153756] wlan0: authenticated
Jan  5 19:23:59 dischord kernel: [19577.153762] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:23:59 dischord kernel: [19577.156734] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:23:59 dischord kernel: [19577.156740] wlan0: associated
Jan  5 19:24:03 dischord kernel: [19581.304291] wlan0: deauthenticated
Jan  5 19:24:04 dischord kernel: [19582.304033] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:04 dischord kernel: [19582.305723] wlan0: authenticated
Jan  5 19:24:04 dischord kernel: [19582.305730] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:04 dischord kernel: [19582.309805] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:24:04 dischord kernel: [19582.309811] wlan0: associated
Jan  5 19:24:08 dischord kernel: [19586.454352] wlan0: deauthenticated
Jan  5 19:24:09 dischord kernel: [19587.452117] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:09 dischord kernel: [19587.453824] wlan0: authenticated
Jan  5 19:24:09 dischord kernel: [19587.453830] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:09 dischord kernel: [19587.458941] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:24:09 dischord kernel: [19587.458948] wlan0: associated
Jan  5 19:24:13 dischord kernel: [19591.604316] wlan0: deauthenticated
Jan  5 19:24:14 dischord kernel: [19592.604704] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:14 dischord kernel: [19592.606478] wlan0: authenticated
Jan  5 19:24:14 dischord kernel: [19592.606484] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:14 dischord kernel: [19592.608908] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:24:14 dischord kernel: [19592.608914] wlan0: associated
Jan  5 19:24:19 dischord kernel: [19596.756524] wlan0: deauthenticated
Jan  5 19:24:20 dischord kernel: [19597.756029] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:20 dischord kernel: [19597.775674] wlan0: authenticated
Jan  5 19:24:20 dischord kernel: [19597.775684] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:20 dischord kernel: [19597.778376] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:24:20 dischord kernel: [19597.778381] wlan0: associated
Jan  5 19:24:24 dischord kernel: [19601.904361] wlan0: deauthenticated
Jan  5 19:24:25 dischord kernel: [19602.904040] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:25 dischord kernel: [19602.905733] wlan0: authenticated
Jan  5 19:24:25 dischord kernel: [19602.905738] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:25 dischord kernel: [19602.909076] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:24:25 dischord kernel: [19602.909081] wlan0: associated
Jan  5 19:24:29 dischord kernel: [19607.054409] wlan0: deauthenticated
Jan  5 19:24:30 dischord kernel: [19608.052044] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:30 dischord kernel: [19608.054259] wlan0: authenticated
Jan  5 19:24:30 dischord kernel: [19608.054265] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:30 dischord kernel: [19608.056686] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:24:30 dischord kernel: [19608.056691] wlan0: associated
Jan  5 19:24:34 dischord kernel: [19612.204443] wlan0: deauthenticated
Jan  5 19:24:35 dischord kernel: [19613.204644] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:35 dischord kernel: [19613.206387] wlan0: authenticated
Jan  5 19:24:35 dischord kernel: [19613.206393] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:35 dischord kernel: [19613.208819] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:24:35 dischord kernel: [19613.208825] wlan0: associated
Jan  5 19:24:39 dischord kernel: [19617.354492] wlan0: deauthenticated
Jan  5 19:24:40 dischord kernel: [19618.352026] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:40 dischord kernel: [19618.358056] wlan0: authenticated
Jan  5 19:24:40 dischord kernel: [19618.358063] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:40 dischord kernel: [19618.360540] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:24:40 dischord kernel: [19618.360546] wlan0: associated
Jan  5 19:24:44 dischord kernel: [19622.504512] wlan0: deauthenticated
Jan  5 19:24:45 dischord kernel: [19623.504037] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:45 dischord kernel: [19623.505709] wlan0: authenticated
Jan  5 19:24:45 dischord kernel: [19623.505716] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:45 dischord kernel: [19623.508244] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:24:45 dischord kernel: [19623.508249] wlan0: associated
Jan  5 19:24:49 dischord kernel: [19627.654526] wlan0: deauthenticated
Jan  5 19:24:50 dischord kernel: [19628.652046] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:50 dischord kernel: [19628.653727] wlan0: authenticated
Jan  5 19:24:50 dischord kernel: [19628.653733] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:50 dischord kernel: [19628.656160] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:24:50 dischord kernel: [19628.656165] wlan0: associated
Jan  5 19:24:55 dischord kernel: [19632.804560] wlan0: deauthenticated
Jan  5 19:24:56 dischord kernel: [19633.804045] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:56 dischord kernel: [19633.805748] wlan0: authenticated
Jan  5 19:24:56 dischord kernel: [19633.805754] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:24:56 dischord kernel: [19633.808178] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:24:56 dischord kernel: [19633.808184] wlan0: associated
Jan  5 19:25:00 dischord kernel: [19637.954727] wlan0: deauthenticated
Jan  5 19:25:01 dischord kernel: [19638.952030] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:01 dischord kernel: [19638.953766] wlan0: authenticated
Jan  5 19:25:01 dischord kernel: [19638.953771] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:01 dischord kernel: [19638.956594] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:25:01 dischord kernel: [19638.956599] wlan0: associated
Jan  5 19:25:05 dischord kernel: [19643.104754] wlan0: deauthenticated
Jan  5 19:25:06 dischord kernel: [19644.104030] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:06 dischord kernel: [19644.105801] wlan0: authenticated
Jan  5 19:25:06 dischord kernel: [19644.105806] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:06 dischord kernel: [19644.108291] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:25:06 dischord kernel: [19644.108299] wlan0: associated
Jan  5 19:25:10 dischord kernel: [19648.255517] wlan0: deauthenticated
Jan  5 19:25:11 dischord kernel: [19649.252042] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:11 dischord kernel: [19649.253796] wlan0: authenticated
Jan  5 19:25:11 dischord kernel: [19649.253802] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:11 dischord kernel: [19649.256272] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:25:11 dischord kernel: [19649.256285] wlan0: associated
Jan  5 19:25:15 dischord kernel: [19653.409479] wlan0: deauthenticated
Jan  5 19:25:16 dischord kernel: [19654.408498] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:16 dischord kernel: [19654.410248] wlan0: authenticated
Jan  5 19:25:16 dischord kernel: [19654.410254] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:16 dischord kernel: [19654.412672] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:25:16 dischord kernel: [19654.412678] wlan0: associated
Jan  5 19:25:20 dischord kernel: [19658.554685] wlan0: deauthenticated
Jan  5 19:25:21 dischord kernel: [19659.552040] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:21 dischord kernel: [19659.554263] wlan0: authenticated
Jan  5 19:25:21 dischord kernel: [19659.554269] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:21 dischord kernel: [19659.556714] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:25:21 dischord kernel: [19659.556719] wlan0: associated
Jan  5 19:25:25 dischord kernel: [19663.704725] wlan0: deauthenticated
Jan  5 19:25:26 dischord kernel: [19664.704767] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:26 dischord kernel: [19664.710932] wlan0: authenticated
Jan  5 19:25:26 dischord kernel: [19664.710939] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:26 dischord kernel: [19664.716635] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:25:26 dischord kernel: [19664.716641] wlan0: associated
Jan  5 19:25:31 dischord kernel: [19668.854804] wlan0: deauthenticated
Jan  5 19:25:32 dischord kernel: [19669.852043] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:32 dischord kernel: [19669.866578] wlan0: authenticated
Jan  5 19:25:32 dischord kernel: [19669.866584] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:32 dischord kernel: [19669.869135] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:25:32 dischord kernel: [19669.869141] wlan0: associated
Jan  5 19:25:36 dischord kernel: [19674.004779] wlan0: deauthenticated
Jan  5 19:25:37 dischord kernel: [19675.004037] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:37 dischord kernel: [19675.005723] wlan0: authenticated
Jan  5 19:25:37 dischord kernel: [19675.005729] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:37 dischord kernel: [19675.009883] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:25:37 dischord kernel: [19675.009888] wlan0: associated
Jan  5 19:25:41 dischord kernel: [19679.154949] wlan0: deauthenticated
Jan  5 19:25:42 dischord kernel: [19680.152080] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:42 dischord kernel: [19680.153874] wlan0: authenticated
Jan  5 19:25:42 dischord kernel: [19680.153880] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:42 dischord kernel: [19680.156330] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:25:42 dischord kernel: [19680.156335] wlan0: associated
Jan  5 19:25:46 dischord kernel: [19684.304845] wlan0: deauthenticated
Jan  5 19:25:47 dischord kernel: [19685.304026] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:47 dischord kernel: [19685.305760] wlan0: authenticated
Jan  5 19:25:47 dischord kernel: [19685.305767] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:47 dischord kernel: [19685.308284] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:25:47 dischord kernel: [19685.308290] wlan0: associated
Jan  5 19:25:49 dischord init: tty1 main process (5544) killed by TERM signal
Jan  5 19:25:49 dischord bonobo-activation-server (weeble-14146): could not associate with desktop session: Failed to connect to socket /tmp/dbus-HBfFXqmV98: Connection refused
Jan  5 19:25:51 dischord kernel: [19689.454911] wlan0: deauthenticated
Jan  5 19:25:52 dischord kernel: [19690.452034] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:52 dischord kernel: [19690.453798] wlan0: authenticated
Jan  5 19:25:52 dischord kernel: [19690.453804] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:52 dischord kernel: [19690.456246] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:25:52 dischord kernel: [19690.456251] wlan0: associated
Jan  5 19:25:56 dischord kernel: [19694.604877] wlan0: deauthenticated
Jan  5 19:25:57 dischord kernel: [19695.604034] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:57 dischord kernel: [19695.605783] wlan0: authenticated
Jan  5 19:25:57 dischord kernel: [19695.605788] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:25:57 dischord kernel: [19695.609745] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:25:57 dischord kernel: [19695.609750] wlan0: associated
Jan  5 19:26:02 dischord kernel: [19699.754892] wlan0: deauthenticated
Jan  5 19:26:03 dischord kernel: [19700.752023] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:26:03 dischord kernel: [19700.753776] wlan0: authenticated
Jan  5 19:26:03 dischord kernel: [19700.753782] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:26:03 dischord kernel: [19700.756384] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:26:03 dischord kernel: [19700.756389] wlan0: associated
Jan  5 19:26:07 dischord kernel: [19704.904962] wlan0: deauthenticated
Jan  5 19:26:08 dischord kernel: [19705.904033] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:26:08 dischord kernel: [19705.905798] wlan0: authenticated
Jan  5 19:26:08 dischord kernel: [19705.905803] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:26:08 dischord kernel: [19705.912331] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:26:08 dischord kernel: [19705.912336] wlan0: associated
Jan  5 19:26:12 dischord kernel: [19710.054950] wlan0: deauthenticated
Jan  5 19:26:13 dischord kernel: [19711.052033] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:26:13 dischord kernel: [19711.055669] wlan0: authenticated
Jan  5 19:26:13 dischord kernel: [19711.055675] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:26:13 dischord kernel: [19711.058287] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:26:13 dischord kernel: [19711.058292] wlan0: associated
Jan  5 19:26:17 dischord kernel: [19715.204979] wlan0: deauthenticated
Jan  5 19:26:18 dischord kernel: [19716.204033] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:26:18 dischord kernel: [19716.205809] wlan0: authenticated
Jan  5 19:26:18 dischord kernel: [19716.205815] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:26:18 dischord kernel: [19716.208248] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:26:18 dischord kernel: [19716.208254] wlan0: associated
Jan  5 19:26:22 dischord kernel: [19720.354987] wlan0: deauthenticated
Jan  5 19:26:23 dischord kernel: [19721.324734] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jan  5 19:26:23 dischord kernel: [19721.352109] wlan0: authenticate with AP 00:14:78:ed:4a:b8
Jan  5 19:26:23 dischord kernel: [19721.368628] wlan0: authenticated
Jan  5 19:26:23 dischord kernel: [19721.368636] wlan0: associate with AP 00:14:78:ed:4a:b8
Jan  5 19:26:23 dischord kernel: [19721.374445] wlan0: RX ReassocResp from 00:14:78:ed:4a:b8 (capab=0x431 status=0 aid=1)
Jan  5 19:26:23 dischord kernel: [19721.374450] wlan0: associated
Jan  5 19:26:25 dischord avahi-daemon[4862]: Got SIGTERM, quitting.
Jan  5 19:26:25 dischord exiting on signal 15

```

While it was breaking, I opened a few consoles. The console would hang if I tried to sudo anything, even just "sudo ls". It didn't even ask me for my password, it just moved the cursor to the next line and sat there. But it seemed okay to do simple stuff that didn't require a sudo. Next time I might try a more thorough analysis of what works and what doesn't.

I'm not sure whether the problem is actually related to the wifi driver or not. Perhaps it's just getting affected by some other root cause.

The only common factor seems to be that it will always happen shortly after the system comes up, but I think it's happened after a regular boot, after a hibernation and after a resume from suspend.

Can anybody suggest what my next step should be? What information can I gather that might shed some light on the problem?

EDIT-TO-ADD:
I looked more closely at the weird garbage screen that appears when the system attempts to restart from its zombie state. It appears that it *is* burn-in, of a sort. This machine was ex-display, and the blurry text is the text that appeared on the screen-saver in the shop. I've got no idea how that works. It's clearly not "real" burn-in, because the screen looks fine normally, even when blank. Perhaps it's some artefact of how the LCD display works? Maybe if it's powered but has no signal it can somehow drift towards the biased state? I don't imagine that's a lot of help to solving the problem, but I thought it worth mentioning.

---

### Post by clockworksaint on 2009-01-09
Okay, I am 90% sure the source of the problem is to do with the wireless networking. It seems that any process that attempts to access the network will block forever. This is why sudo does not work, because I understand now that it does something network-related to make sure your user account is really allowed to sudo. If I do "su" and then enter my root password it works and I can then run commands as root so long as they don't do network stuff, but if they do the entire console will hang. I think this bug might be the same thing:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289584](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289584)

Next time it happens I might try the workaround described by the last commenter:

rmmod iwlagn
modprobe iwlagn

and see what happens.

---

### Post by clockworksaint on 2009-01-19
I installed kernel 2.6.27-11, which didn't fix the problem, but seemed to log slightly more information, including a "no space for new kew" (typo for "key", I think) warning. I can't find it now, but something I read suggested this problem (the wifi drivers running out of space for encryption keys on resume) was fixed in more recent kernels, so I set about installing kernel 2.6.28-4, and for the past few days I've had no problems resuming from suspend. I hope this is useful to anybody else with this problem.

---

