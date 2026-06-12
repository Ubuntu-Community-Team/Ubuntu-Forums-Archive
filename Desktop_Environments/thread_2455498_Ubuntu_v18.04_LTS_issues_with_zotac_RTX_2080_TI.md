---
title: "Ubuntu v18.04 LTS issues with zotac RTX 2080 TI"
date: 2020-12-21
forum: Desktop Environments
---

### Post by smrehan00 on 2020-12-21
Hello Everyone,

I hope this is the right place to ask for help with the problem that I am facing.

I have a couple of issues which I will explain in detail.

I am assigned to work with a custom built server with the following specifications:

1. Motherboard: MSI Z390 SLI gaming
2. Intel Core I9-9900K @ 3.6 GHz x 16
3. RAM: Corsair 64 GB
4. Graphics: Zotac RTX 2080 TI (Nvidia) 
5. Storage: M.2 2280 PCIe SSD: Lexar 250 GB (Primary) and 2 TB Toshiba HDD 7200 RPM (Secondary)
6. Networking: 1 GBe Intel 1219 NIC

Here are the problems which I am facing.

The system's graphic card is causing a lot of problems. It all started with system crashing upon working with our proprietary application which works on the principles of image processing.
 
The system was reported to work fine when not working on high end graphical application in production.

I was able to find this article on the internet regarding the graphics drivers [here]("https://medium.com/better-programming/how-to-install-nvidia-drivers-and-cuda-10-0-for-rtx-2080-ti-gpu-on-ubuntu-16-04-18-04-ce32e4edf1c0")

According to the article the stable graphics driver is 410 but when I was able to check the system before restoring the image via Clonezilla the driver being used was 440.

I would like to know whether this might have caused the graphics card to misbehave?

Moreover, the M.2 SSD has a filesystem issue which doesn't allow the system to boot normally. I am getting the recovering journal error. See attachment.

If I want to run fsck it gives the error of aborting while running fsck via recovery mode. The disk is mounted. 

This following is just an example:

root@xps:~# sudo fsck -f /
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/nvme0n1p2 is mounted.
e2fsck: Cannot continue, aborting.

This is how it looks in the actual environment.
I created a bootable usb in order to try and run fsck via the usb to fix the error but as soon as the system detects bootable usb I only get screen where I can choose run ubuntu or install it then when I run without installing the screen goes blank and the monitor goes to sleep with this message "out of range". What to do in this case?

Is there a way that I can repair the filesystem via fsck without using the bootable usb ?

Lastly, is it possible to restore disk image via Clonezilla to a blank SSD Or HDD?

I am a beginner at this so please I would request to go easy on me.

Please let me know.

Thank you very much.

---

### Post by CatKiller on 2020-12-21
> **smrehan00 said:**
> The system was reported to work fine when not working on high end graphical application in production. 

I would suspect thermals first, followed by inadequate power supply. Or a problem with the application itself. 

> According to the article the stable graphics driver is 410 but when I was able to check the system before restoring the image via Clonezilla the driver being used was 440.

I would like to know whether this might have caused the graphics card to misbehave? 

It's not likely. It's possible, but not likely. That article is two years old. The current long term Nvidia driver is 450. Having some parts of the driver from one branch and other parts of the driver from another branch can cause issues, but it causes issues all over, not just when it's under load. 

> when I run without installing the screen goes blank and the monitor goes to sleep with this message "out of range". What to do in this case? 

At the first screen you can press a key (I think it's E) to edit the kernel parameters that it boots with. Find where it says "quiet splash" and change it so that it says "quiet splash nomodeset" and carry on booting. The nouveau driver (that the installer comes with) isn't as good at detecting resolutions as the proprietary Nvidia driver; that option tells it not to try.

---

### Post by ActionParsnip on 2020-12-21
Boot LiveCD / USB and fsck from there. You should not fsck a mounted file system

---

### Post by smrehan00 on 2020-12-23
Hello Cat!

I do have the system and kernel logs. I'll be sharing them later today. Unfortunately, I was not able to get back soon enough due to work management because of Covid-19 for which I apologize. We are working on alternate days.

---

### Post by smrehan00 on 2020-12-23
Hello Action!

The screen goes blank as soon as I try to boot via live USB drive and the monitor goes to sleep. Any remedies?

---

### Post by ActionParsnip on 2020-12-23
Try the boot option
```

nouveau.nomodeset=1

```

---

### Post by smrehan00 on 2020-12-31
Hi guys!

Sorry for the delay. 

I was going through the logs and it had 4400 pages so it took time.

Here are some of the logs which I have filtered out which I believe are alarming.


Nov 22 14:56:44 cctvserver-MS-7B17 kernel: [94555.573305] NVRM: GPU at PCI:0000:02:00: GPU-566b96ce-1c0e-55a2-e739-301b62e223b8
Nov 22 14:56:44 cctvserver-MS-7B17 kernel: [94555.573307] NVRM: GPU Board Serial Number: 
**Nov 22 14:56:44 cctvserver-MS-7B17 kernel: [94555.573310] NVRM: Xid (PCI:0000:02:00): 62, pid=1300, 203c(3090) 85020c09 ffffbd53**
**Nov 22 14:56:45 cctvserver-MS-7B17 kernel: [94556.085056] NVRM: Xid (PCI:0000:02:00): 31, pid=1300, Ch 00000035, intr 00000000. MMU Fault: ENGINE GRAPHICS GPCCLIENT_T1_0 faulted @ 0x7f92_9a53d000. Fault is of type FAULT_PDE ACCESS_TYPE_VIRT_WRITE**
**Nov 22 14:56:47 cctvserver-MS-7B17 kernel: [94558.085056] NVRM: Xid (PCI:0000:02:00): 45, pid=12723, Ch 00000000**
Nov 22 14:56:47 cctvserver-MS-7B17 kernel: [94558.087626] NVRM: Xid (PCI:0000:02:00): 45, pid=1300, Ch 00000001
Nov 22 14:56:47 cctvserver-MS-7B17 kernel: [94558.090174] NVRM: Xid (PCI:0000:02:00): 45, pid=1300, Ch 00000002
Nov 22 14:56:47 cctvserver-MS-7B17 kernel: [94558.589088] NVRM: Xid (PCI:0000:02:00): 45, pid=729, Ch 00000003
Nov 22 14:56:47 cctvserver-MS-7B17 kernel: [94558.591566] NVRM: Xid (PCI:0000:02:00): 45, pid=729, Ch 00000004
Nov 22 14:56:48 cctvserver-MS-7B17 kernel: [94559.093060] NVRM: Xid (PCI:0000:02:00): 45, pid=729, Ch 00000005
Nov 22 14:56:48 cctvserver-MS-7B17 kernel: [94559.095561] NVRM: Xid (PCI:0000:02:00): 45, pid=729, Ch 00000006
Nov 22 14:56:48 cctvserver-MS-7B17 kernel: [94559.098059] NVRM: Xid (PCI:0000:02:00): 45, pid=729, Ch 00000007
Nov 22 14:56:48 cctvserver-MS-7B17 kernel: [94559.100552] NVRM: Xid (PCI:0000:02:00): 45, pid=729, Ch 00000008
Nov 22 14:56:49 cctvserver-MS-7B17 kernel: [94560.601022] NVRM: Xid (PCI:0000:02:00): 45, pid=1300, Ch 00000009
Nov 22 14:56:49 cctvserver-MS-7B17 kernel: [94560.603464] NVRM: Xid (PCI:0000:02:00): 45, pid=1300, Ch 00000010
Nov 22 14:56:49 cctvserver-MS-7B17 kernel: [94560.605997] NVRM: Xid (PCI:0000:02:00): 45, pid=1505, Ch 00000011
Nov 22 14:56:49 cctvserver-MS-7B17 kernel: [94560.608458] NVRM: Xid (PCI:0000:02:00): 45, pid=1505, Ch 00000012
Nov 22 14:56:49 cctvserver-MS-7B17 kernel: [94560.610856] NVRM: Xid (PCI:0000:02:00): 45, pid=1505, Ch 00000013
Nov 22 14:56:49 cctvserver-MS-7B17 kernel: [94560.613302] NVRM: Xid (PCI:0000:02:00): 45, pid=1505, Ch 00000014
Nov 22 14:56:49 cctvserver-MS-7B17 kernel: [94560.615733] NVRM: Xid (PCI:0000:02:00): 45, pid=1505, Ch 00000015
Nov 22 14:56:49 cctvserver-MS-7B17 kernel: [94560.618185] NVRM: Xid (PCI:0000:02:00): 45, pid=1505, Ch 00000018
Nov 22 14:56:49 cctvserver-MS-7B17 kernel: [94560.620655] NVRM: Xid (PCI:0000:02:00): 45, pid=1993, Ch 00000019
Nov 22 14:56:49 cctvserver-MS-7B17 kernel: [94560.623070] NVRM: Xid (PCI:0000:02:00): 45, pid=1993, Ch 0000001a
Nov 22 14:56:49 cctvserver-MS-7B17 kernel: [94560.625559] NVRM: Xid (PCI:0000:02:00): 45, pid=1993, Ch 00000020
Nov 22 14:56:49 cctvserver-MS-7B17 kernel: [94560.627971] NVRM: Xid (PCI:0000:02:00): 45, pid=12723, Ch 00000021
Nov 22 14:56:49 cctvserver-MS-7B17 kernel: [94560.630432] NVRM: Xid (PCI:0000:02:00): 45, pid=12723, Ch 00000022


**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718661]  nmi_cpu_backtrace+0x94/0xa0**
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718663]  ? lapic_can_unplug_cpu+0xb0/0xb0
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718664]  nmi_trigger_cpumask_backtrace+0xe7/0x130
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718664]  arch_trigger_cpumask_backtrace+0x19/0x20
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718699]  rcu_dump_cpu_stacks+0x9e/0xd6
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718700]  rcu_sched_clock_irq+0x508/0x770
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718701]  ? tick_sched_do_timer+0x60/0x60

Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718709]  </IRQ>
**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718836] RIP: 0010:_nv030887rm+0x12/0x40 [nvidia]**
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718837] Code: e8 53 cf 91 ff 31 c0 48 83 c4 08 c3 66 90 66 2e 0f 1f 84 00 00 00 00 00 48 83 ec 08 39 4a 10 76 17 48 8b 02 c1 e9 02 8b 04 88 <48> 83 c4 08 c3 66 0f 1f 84 00 00 00 00 00 e8 bb 34 00 00 48 89 c7
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718837] RSP: 0018:ffffb1a601c13d48 EFLAGS: 00000202 ORIG_RAX: ffffffffffffff13
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718838] RAX: 0000000040000100 RBX: 0000000000002100 RCX: 0000000000000840
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718838] RDX: ffff995394e45290 RSI: ffff995394e44008 RDI: ffff9953a0ab8008
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718839] RBP: ffff995394e5ad90 R08: 0000000000000020 R09: ffff995394e5ada8
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718839] R10: ffffffffc182c200 R11: ffffffffffffffff R12: ffff995394e45290
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718839] R13: ffff9953a0ab8008 R14: ffff995394e44008 R15: 0000000000000000
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718986]  ? _nv021295rm+0x10/0x10 [nvidia]
**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718987] WARNING: kernel stack regs at 00000000d86a6490 in irq/162-nvidia:1307 has bad 'bp' value 00000000b0eacb25**
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718988] unwind stack type:0 next_sp:0000000000000000 mask:0x6 graph_idx:0
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718989] 000000008e5e272f: ffffb1a600334d90 (0xffffb1a600334d90)
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718990] 0000000092aa3705: ffffffff954359c3 (show_trace_log_lvl+0x223/0x3d0)
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718991] 0000000086c649c7: 0000000000000000 ...
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718992] 000000001e69e772: ffffffff967976aa (.LC2+0x147a/0x1648)
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.718993] 00000000b9a01c84: ffff995394c52f80 (0xffff995394c52f80)
**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719133] 00000000ea568c48: ffffffffc182c200 (_nv021295rm+0x10/0x10 [nvidia])**
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719133] 00000000ae5572d1: 0000000000000001 (0x1)
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719134] 000000002283d4cb: 0000000000000006 (0x6)
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719134] 0000000037bfd189: 0000000000000001 (0x1)
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719134] 00000000f4c17984: ffffb1a601c10000 (0xffffb1a601c10000)
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719134] 0000000043afed05: ffffb1a601c14000 (0xffffb1a601c14000)
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719135] 00000000c0a6cb87: 0000000000000000 ...
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719135] 000000000903ea00: ffffb1a601c10000 (0xffffb1a601c10000)
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719135] 00000000d0ff451f: ffffb1a601c14000 (0xffffb1a601c14000)
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719135] 000000009cb049a5: 0000000000000000 ...
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719136] 00000000964b005e: 0000000000000006 (0x6)
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719136] 000000008ef52b97: ffff995394c52f80 (0xffff995394c52f80)
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719136] 00000000260136c5: 0000010100000000 (0x10100000000)
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719136] 00000000418c31d5: 0000000000000000 ...
Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719137] 0000000072b86866: ffffb1a600334ca0 (0xffffb1a600334ca0)
**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.719217] 00000000ac27b1d8: ffffffffc1b5e542 (_nv030887rm+0x12/0x40 [nvidia])**
**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.720652] 0000000047746bb1: ffffffffc14069ef (nvidia_isr_kthread_bh+0x1f/0x40 [nvidia])**

**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.720802]  ? _nv021292rm+0xa3/0x140 [nvidia]**
**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.720942]  ? _nv021292rm+0xc5/0x140 [nvidia]**
**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.721079]  ? _nv018880rm+0x32/0xd0 [nvidia]**
**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.721215]  ? _nv027169rm+0x51e/0x9f0 [nvidia]**
**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.721352]  ? _nv007516rm+0x17d/0x260 [nvidia]**
**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.721488]  ? _nv027176rm+0x8d/0x180 [nvidia]**
**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.721567]  ? _nv000911rm+0x10e/0x180 [nvidia]**
**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.721568]  ? irq_finalize_oneshot.part.48+0xf0/0xf0**
**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.721646]  ? rm_isr_bh+0x1c/0x60 [nvidia]**
**Nov 22 14:57:55 cctvserver-MS-7B17 kernel: [94626.721704]  ? nvidia_isr_kthread_bh+0x1f/0x40 [nvidia]**


**Nov 22 14:59:40 cctvserver-MS-7B17 kernel: [94731.516213] INFO: task Xorg:1300 blocked for more than 120 seconds.**
**Nov 22 14:59:40 cctvserver-MS-7B17 kernel: [94731.516214]       Tainted: P           OE     5.4.0-53-generic #59~18.04.1-Ubuntu**
Nov 22 14:59:40 cctvserver-MS-7B17 kernel: [94731.516215] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
**Nov 22 14:59:40 cctvserver-MS-7B17 kernel: [94731.516215] Xorg            D    0  1300   1298 0x00400084**

**Nov 22 14:59:40 cctvserver-MS-7B17 kernel: [94731.516338]  os_acquire_mutex+0x34/0x40 [nvidia]**
**Nov 22 14:59:40 cctvserver-MS-7B17 kernel: [94731.516406]  os_acquire_semaphore+0xe/0x10 [nvidia]**
**Nov 22 14:59:40 cctvserver-MS-7B17 kernel: [94731.516503]  _nv033394rm+0x15/0x20 [nvidia]**

Nov 22 14:59:40 cctvserver-MS-7B17 kernel: [94731.518531] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.

**Nov 22 14:59:40 cctvserver-MS-7B17 kernel: [94731.518556] Code: Bad RIP value.**

**Nov 22 15:01:41 cctvserver-MS-7B17 kernel: [94852.347825] INFO: task eai-main-contro:12733 blocked for more than 241 seconds.**

**Nov 22 15:01:41 cctvserver-MS-7B17 kernel: [94852.347850] RIP: 0033:0x7f946dabca5f**
**Nov 22 15:01:41 cctvserver-MS-7B17 kernel: [94852.347851] Code: Bad RIP value.**

**Nov 22 15:15:51 cctvserver-MS-7B17 kernel: [95702.692949] rcu: INFO: rcu_sched self-detected stall on CPU**
Nov 22 15:15:51 cctvserver-MS-7B17 kernel: [95702.692952] rcu:    9-....: (595 GPs behind) idle=b4e/1/0x4000000000000002 softirq=509162/509162 fqs=7499 
**Nov 22 15:15:51 cctvserver-MS-7B17 kernel: [95702.692952]   (t=15000 jiffies g=10111845 q=5516)**
**Nov 22 15:15:51 cctvserver-MS-7B17 kernel: [95702.692953] NMI backtrace for cpu 9**

Nov 22 15:23:59 cctvserver-MS-7B17 kernel: [96190.057312] **clocksource: timekeeping watchdog on CPU9: Marking clocksource 'tsc' as unstable because the skew is too large**:
Nov 22 15:23:59 cctvserver-MS-7B17 kernel: [96190.057313] clocksource:                       'hpet' wd_now: 80797d69 wd_last: 68a4a043 mask: ffffffff
Nov 22 15:23:59 cctvserver-MS-7B17 kernel: [96190.057314] clocksource:                       'tsc' cs_now: 13b05dc7db8ba cs_last: 135b1e5c42622 mask: ffffffffffffffff
**Nov 22 15:23:59 cctvserver-MS-7B17 kernel: [96190.057335] tsc: Marking TSC unstable due to clocksource watchdog**
**Nov 22 15:29:24 cctvserver-MS-7B17 kernel: [96515.089479] TSC found unstable after boot, most likely due to broken BIOS. Use 'tsc=unstable'.**
**Nov 22 15:29:24 cctvserver-MS-7B17 kernel: [96515.089480] sched_clock: Marking unstable (96517216474520, -2080267893)<-(96515110078049, -20599331)**

Nov 22 15:39:50 cctvserver-MS-7B17 kernel: [97141.724224] **WARNING: kernel stack frame pointer at 000000009d4ec424 in irq/162-nvidia:1307 has bad value 000000006712d099**

**Nov 22 15:59:27 cctvserver-MS-7B17 kernel: [98318.740267] RIP: 0010:read_hpet+0xab/0xd0**

Nov 22 23:16:31 cctvserver-MS-7B17 kernel: [124542.280262] **Modules linked in: rfcomm cmac bnep nvidia_uvm(OE) nvidia_drm(POE) snd_hda_codec_hdmi nvidia_modeset(POE) nvidia(POE)** intel_rapl_msr mei_hdcp iwlmvm intel_rapl_common x86_pkg_temp_thermal intel_powerclamp snd_sof_pci mac80211 snd_sof_intel_hda_common snd_soc_hdac_hda snd_sof_intel_hda snd_sof_intel_byt coretemp snd_sof_intel_ipc snd_sof snd_hda_codec_realtek snd_sof_xtensa_dsp snd_hda_ext_core snd_soc_acpi_intel_match snd_hda_codec_generic libarc4 snd_soc_acpi ledtrig_audio snd_soc_core kvm_intel btusb snd_compress cdc_ether btrtl btbcm usbnet ac97_bus btintel snd_pcm_dmaengine r8152 nls_iso8859_1 drm_kms_helper snd_hda_intel mii kvm joydev iwlwifi input_leds bluetooth snd_intel_dspcfg drm snd_hda_codec ucsi_ccg snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi typec_ucsi crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq typec ipmi_devintf crypto_simd snd_seq_device cryptd ipmi_msghandler glue_helper snd_timer rapl intel_cstate
 
 
 
 
Nov 22 23:16:31 cctvserver-MS-7B17 kernel: [124542.280262]  ecdh_generic fb_sys_fops ecc cfg80211 syscopyarea sysfillrect sysimgblt snd wmi_bmof intel_wmi_thunderbolt mxm_wmi soundcore mei_me mei intel_pch_thermal mac_hid acpi_pad acpi_tad sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_logitech_hidpp hid_logitech_dj hid_generic usbhid hid nvme e1000e **ahci nvme_core libahci i2c_nvidia_gpu wmi video**
 
**Nov 22 23:17:59 cctvserver-MS-7B17 kernel: [124630.280245] watchdog: BUG: soft lockup - CPU#9 stuck for 22s! [irq/162-nvidia:1307]**
Nov 22 23:17:59 cctvserver-MS-7B17 kernel: [124630.280247] **Modules linked in: rfcomm cmac bnep nvidia_uvm(OE) nvidia_drm(POE) snd_hda_codec_hdmi nvidia_modeset(POE) nvidia(POE)** intel_rapl_msr mei_hdcp iwlmvm intel_rapl_common x86_pkg_temp_thermal intel_powerclamp snd_sof_pci mac80211 snd_sof_intel_hda_common snd_soc_hdac_hda snd_sof_intel_hda snd_sof_intel_byt coretemp snd_sof_intel_ipc snd_sof snd_hda_codec_realtek snd_sof_xtensa_dsp snd_hda_ext_core snd_soc_acpi_intel_match snd_hda_codec_generic libarc4 snd_soc_acpi ledtrig_audio snd_soc_core kvm_intel btusb snd_compress cdc_ether btrtl btbcm usbnet ac97_bus btintel snd_pcm_dmaengine r8152 nls_iso8859_1 drm_kms_helper snd_hda_intel mii kvm joydev iwlwifi input_leds bluetooth snd_intel_dspcfg drm snd_hda_codec ucsi_ccg snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi typec_ucsi crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel snd_seq typec ipmi_devintf crypto_simd snd_seq_device cryptd ipmi_msghandler glue_helper snd_timer rapl intel_cstate


**Nov 23 15:00:03 cctvserver-MS-7B17 kernel: [15885.717809] NVRM: Xid (PCI:0000:02:00): 62, pid=1294, 203c(3090) 00000000 00000000**
Nov 23 15:00:03 cctvserver-MS-7B17 kernel: [15886.225009] NVRM: Xid (PCI:0000:02:00): 32, pid=1294, Channel ID 00000036 intr 00008000
Nov 23 15:00:03 cctvserver-MS-7B17 kernel: [15886.227633] NVRM: Xid (PCI:0000:02:00): 32, pid=4091, Channel ID 00000036 intr 00008000
Nov 23 15:00:04 cctvserver-MS-7B17 kernel: [15886.728358] NVRM: Xid (PCI:0000:02:00): 13, pid=4091, Graphics Exception - DMA_READ_FIFOED_FROM_PB
 
Nov 23 15:03:09 cctvserver-MS-7B17 kernel: [16071.614503]  ? entry_SYSCALL_64_after_hwframe+0x44/0xa9

Nov 23 18:15:24 cctvserver-MS-7B17 kernel: [ 2246.380785] NVRM: Xid (PCI:0000:02:00): 43, pid=1293, Ch 00000034
 
 
**Nov 23 18:47:29 cctvserver-MS-7B17 kernel: [    0.178159] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])**
**Nov 23 18:47:29 cctvserver-MS-7B17 kernel: [    0.178160] ACPI: LAPIC_NMI (acpi_id[0x09] high edge lint[0x1])**
**Nov 23 18:47:29 cctvserver-MS-7B17 kernel: [    0.178160] ACPI: LAPIC_NMI (acpi_id[0x0a] high edge lint[0x1])**
**Nov 23 18:47:29 cctvserver-MS-7B17 kernel: [    0.178161] ACPI: LAPIC_NMI (acpi_id[0x0b] high edge lint[0x1])**
**Nov 23 18:47:29 cctvserver-MS-7B17 kernel: [    0.178161] ACPI: LAPIC_NMI (acpi_id[0x0c] high edge lint[0x1])**
**Nov 23 18:47:29 cctvserver-MS-7B17 kernel: [    0.178161] ACPI: LAPIC_NMI (acpi_id[0x0d] high edge lint[0x1])**
**Nov 23 18:47:29 cctvserver-MS-7B17 kernel: [    0.178162] ACPI: LAPIC_NMI (acpi_id[0x0e] high edge lint[0x1])**
**Nov 23 18:47:29 cctvserver-MS-7B17 kernel: [    0.178162] ACPI: LAPIC_NMI (acpi_id[0x0f] high edge lint[0x1])**
**Nov 23 18:47:29 cctvserver-MS-7B17 kernel: [    0.178163] ACPI: LAPIC_NMI (acpi_id[0x10] high edge lint[0x1])**


**Nov 23 19:27:01 cctvserver-MS-7B17 kernel: [    1.187259] acpi PNP0C14:03: duplicate WMI GUID 05901221-D566-11D1-B2F0-00A0C9062910 (first instance was on PNP0C14:02)**
**Nov 23 19:27:01 cctvserver-MS-7B17 kernel: [    1.187310] acpi PNP0C14:04: duplicate WMI GUID 05901221-D566-11D1-B2F0-00A0C9062910 (first instance was on PNP0C14:02)**


**Nov 25 15:34:36 cctvserver-MS-7B17 kernel: [158878.529274] NVRM: Xid (PCI:0000:02:00): 13, pid=25450, Graphics SM Warp Exception on (GPC 0, TPC 0, SM 0): Illegal Instruction Encoding**
**Nov 25 15:34:36 cctvserver-MS-7B17 kernel: [158878.529281] NVRM: Xid (PCI:0000:02:00): 13, pid=25450, Graphics SM Global Exception on (GPC 0, TPC 0, SM 0): Multiple Warp Errors**
**Nov 25 15:34:36 cctvserver-MS-7B17 kernel: [158878.529287] NVRM: Xid (PCI:0000:02:00): 13, pid=25450, Graphics Exception: ESR 0x504730=0xe0009 0x504734=0x4 0x504728=0x4c1eb72 0x50472c=0x174**
**Nov 25 15:34:36 cctvserver-MS-7B17 kernel: [158878.529415] NVRM: Xid (PCI:0000:02:00): 13, pid=25450, Graphics SM Warp Exception on (GPC 0, TPC 0, SM 1): Illegal Instruction Encoding**
**Nov 25 15:34:36 cctvserver-MS-7B17 kernel: [158878.529421] NVRM: Xid (PCI:0000:02:00): 13, pid=25450, Graphics SM Global Exception on (GPC 0, TPC 0, SM 1): Multiple Warp Errors**
 
**Nov 25 15:34:36 cctvserver-MS-7B17 kernel: [158878.529427] NVRM: Xid (PCI:0000:02:00): 13, pid=25450, Graphics Exception: ESR 0x5047b0=0xf0009 0x5047b4=0x24 0x5047a8=0x4c1eb72 0x5047ac=0x174**
**Nov 25 15:34:36 cctvserver-MS-7B17 kernel: [158878.530012] NVRM: Xid (PCI:0000:02:00): 13, pid=25450, Graphics SM Warp Exception on (GPC 0, TPC 1, SM 0): Illegal Instruction Encoding**
**Nov 25 15:34:36 cctvserver-MS-7B17 kernel: [158878.530015] NVRM: Xid (PCI:0000:02:00): 13, pid=25450, Graphics SM Global Exception on (GPC 0, TPC 1, SM 0): Multiple Warp Errors**
**Nov 25 15:34:36 cctvserver-MS-7B17 kernel: [158878.530017] NVRM: Xid (PCI:0000:02:00): 13, pid=25450, Graphics Exception: ESR 0x504f30=0xc0009 0x504f34=0x4 0x504f28=0x4c1eb72 0x504f2c=0x174**
**Nov 25 15:34:36 cctvserver-MS-7B17 kernel: [158878.530063] NVRM: Xid (PCI:0000:02:00): 13, pid=25450, Graphics SM Warp Exception on (GPC 0, TPC 1, SM 1): Illegal Instruction Encoding**
**Nov 25 15:34:36 cctvserver-MS-7B17 kernel: [158878.530066] NVRM: Xid (PCI:0000:02:00): 13, pid=25450, Graphics SM Global Exception on (GPC 0, TPC 1, SM 1): Multiple Warp Errors**

**Nov 25 15:40:58 cctvserver-MS-7B17 kernel: [159259.989773] NVRM: GPU 0000:02:00.0: RmInitAdapter failed! (0x24:0x65:1185)**
**Nov 25 15:40:58 cctvserver-MS-7B17 kernel: [159259.989815] NVRM: GPU 0000:02:00.0: rm_init_adapter failed, device minor number 0**
**Nov 25 15:41:02 cctvserver-MS-7B17 kernel: [159264.341796] NVRM: GPU 0000:02:00.0: RmInitAdapter failed! (0x24:0x65:1185)**
**Nov 25 15:41:02 cctvserver-MS-7B17 kernel: [159264.341814] NVRM: GPU 0000:02:00.0: rm_init_adapter failed, device minor number 0**
**Nov 25 15:41:06 cctvserver-MS-7B17 kernel: [159268.681591] NVRM: GPU 0000:02:00.0: RmInitAdapter failed! (0x24:0x65:1185)**
**Nov 25 15:41:06 cctvserver-MS-7B17 kernel: [159268.681631] NVRM: GPU 0000:02:00.0: rm_init_adapter failed, device minor number 0**
**Nov 25 15:41:11 cctvserver-MS-7B17 kernel: [159273.057614] NVRM: GPU 0000:02:00.0: RmInitAdapter failed! (0x24:0x65:1185)**
**Nov 25 15:41:11 cctvserver-MS-7B17 kernel: [159273.057629] NVRM: GPU 0000:02:00.0: rm_init_adapter failed, device minor number 0**
**Nov 25 15:41:15 cctvserver-MS-7B17 kernel: [159277.417461] NVRM: GPU 0000:02:00.0: RmInitAdapter failed! (0x24:0x65:1185)**
**Nov 25 15:41:15 cctvserver-MS-7B17 kernel: [159277.417499] NVRM: GPU 0000:02:00.0: rm_init_adapter failed, device minor number 0**
**Nov 25 15:41:19 cctvserver-MS-7B17 kernel: [159281.737426] NVRM: GPU 0000:02:00.0: RmInitAdapter failed! (0x24:0x65:1185)**
**Nov 25 15:41:19 cctvserver-MS-7B17 kernel: [159281.737463] NVRM: GPU 0000:02:00.0: rm_init_adapter failed, device minor number 0**
**Nov 25 15:41:24 cctvserver-MS-7B17 kernel: [159286.089262] NVRM: GPU 0000:02:00.0: RmInitAdapter failed! (0x24:0x65:1185)**
**Nov 25 15:41:24 cctvserver-MS-7B17 kernel: [159286.089301] NVRM: GPU 0000:02:00.0: rm_init_adapter failed, device minor number 0**
**Nov 25 15:41:28 cctvserver-MS-7B17 kernel: [159290.417191] NVRM: GPU 0000:02:00.0: RmInitAdapter failed! (0x24:0x65:1185)**
**Nov 25 15:41:28 cctvserver-MS-7B17 kernel: [159290.417259] NVRM: GPU 0000:02:00.0: rm_init_adapter failed, device minor number 0**
**Nov 25 15:41:32 cctvserver-MS-7B17 kernel: [159294.801160] NVRM: GPU 0000:02:00.0: RmInitAdapter failed! (0x24:0x65:1185)**
**Nov 25 15:41:32 cctvserver-MS-7B17 kernel: [159294.801173] NVRM: GPU 0000:02:00.0: rm_init_adapter failed, device minor number 0**
**Nov 25 15:41:37 cctvserver-MS-7B17 kernel: [159299.156937] NVRM: GPU 0000:02:00.0: RmInitAdapter failed! (0x24:0x65:1185)**
**Nov 25 15:41:37 cctvserver-MS-7B17 kernel: [159299.156977] NVRM: GPU 0000:02:00.0: rm_init_adapter failed, device minor number 0**
**Nov 25 15:41:41 cctvserver-MS-7B17 kernel: [159303.524890] NVRM: GPU 0000:02:00.0: RmInitAdapter failed! (0x24:0x65:1185)**

**Nov 25 19:21:27 cctvserver-MS-7B17 kernel: [    4.774224] nvidia: module verification failed: signature and/or required key missing - tainting kernel**
**Nov 25 19:21:27 cctvserver-MS-7B17 kernel: [    4.778128] nvidia-nvlink: Nvlink Core is being initialized, major device number 236**
**Nov 25 19:21:27 cctvserver-MS-7B17 kernel: [    4.778482] nvidia 0000:02:00.0: vgaarb: changed VGA decodes:olddecodes=io+mem,decodes=none:owns=io+mem**

I understand these logs are filtered to accommodate limits. Any insight or help is much appreciated.

Happy new year guys!

---

### Post by smrehan00 on 2021-01-08
Hi Guys!

I have finally managed to figure it out.

The GPU was in fact faulty and I got a replacement GPU Zotac RTX 2080 Ti Twin fan.

The system is working fine and GPU temperature is varying from 28-30 degrees Celsius.

The current driver I am using is 455.38 and cuda version is 11.1

---

