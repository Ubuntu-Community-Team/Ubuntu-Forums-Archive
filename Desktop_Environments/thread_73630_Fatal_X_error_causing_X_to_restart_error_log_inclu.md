---
title: "Fatal X error causing X to restart? error log included."
date: 2005-10-09
forum: Desktop Environments
---

### Post by Mustard on 2005-10-09
I'll be happily playing on my computer, when suddenly the whole desktop shuts down (screen goes black), and next thing I find myself at the gnome login prompt.  Any ideas on what might be causing this?

This is from my syslog.

```
Oct 10 05:54:10 localhost kernel: Unable to handle kernel NULL pointer dereference at virtual address 0000006c
Oct 10 05:54:10 localhost kernel:  printing eip:
Oct 10 05:54:10 localhost kernel: c0102913
Oct 10 05:54:10 localhost kernel: *pde = 0adb0067
Oct 10 05:54:10 localhost kernel: *pte = 00000000
Oct 10 05:54:10 localhost kernel: Oops: 0002 [#1]
Oct 10 05:54:10 localhost kernel: PREEMPT
Oct 10 05:54:10 localhost kernel: Modules linked in: ipt_limit iptable_mangle ipt_LOG ipt_MASQUERADE iptable_nat ipt_TOS ipt_REJECT ip_conntrack_irc ip_conntrack_ftp ipt_state ip_conntrack iptable_filter ip_tables ppp_deflate zlib_deflate bsd_comp nls_utf8 nls_cp437 vfat fat ppp_async ppp_generic slhc ipv6 af_packet proc_intf freq_table cpufreq_userspace cpufreq_powersave cpufreq_ondemand video sony_acpi pcc_acpi container button battery ac sd_mod i2c_viapro i2c_core via_ircc irda crc_ccitt usb_storage scsi_mod tsdev usbhid ehci_hcd uhci_hcd usbcore snd_ens1371 snd_rawmidi snd_seq_device snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc gameport shpchp pci_hotplug via_agp floppy pcspkr rtc evdev md dm_mod capability commoncap nvidia agpgart psmouse mousedev parport_pc lp parport ide_cd cdrom ext3 jbd ide_generic via82cxxx ide_disk ide_core unix thermal processor fan fbcon font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
Oct 10 05:54:10 localhost kernel: CPU:    0
Oct 10 05:54:10 localhost kernel: EIP:    0060:[setup_frame+618/624]    Tainted: P      VLI
Oct 10 05:54:10 localhost kernel: EFLAGS: 00013282   (2.6.10-5-386)
Oct 10 05:54:10 localhost kernel: EIP is at setup_frame+0x26a/0x270
Oct 10 05:54:10 localhost kernel: eax: cc493ea4   ebx: 0000000e   ecx: cc493f08   edx: cc493f08
Oct 10 05:54:10 localhost kernel: esi: bffff350   edi: cc493fc4   ebp: 00000000   esp: cc493ea4
Oct 10 05:54:10 localhost kernel: ds: 007b   es: 007b   ss: 0068
Oct 10 05:54:10 localhost kernel: Process Xorg (pid: 6076, threadinfo=cc492000 task=cf39b0e0)
Oct 10 05:54:10 localhost kernel: Stack: 80cd3f28 00000077 b858b0e0 ffffe420 00000000 0000000e cf39b554 cc493f08
Oct 10 05:54:10 localhost kernel:        0000000e cc493f28 c0102d6a 0000000e cc493f08 cf39b554 cc493fc4 cc493fc4
Oct 10 05:54:10 localhost kernel:        cc492000 cf39b554 cc493f28 c0102e39 0000000e cc493f28 cc493f08 cf39b554
Oct 10 05:54:10 localhost kernel: Call Trace:
Oct 10 05:54:10 localhost kernel:  [handle_signal+118/200] handle_signal+0x76/0xc8
Oct 10 05:54:10 localhost kernel:  [do_signal+125/208] do_signal+0x7d/0xd0
Oct 10 05:54:10 localhost kernel:  [__pollwait+0/154] __pollwait+0x0/0x9a
Oct 10 05:54:10 localhost kernel:  [sys_select+1110/1122] sys_select+0x456/0x462
Oct 10 05:54:10 localhost kernel:  [do_notify_resume+39/56] do_notify_resume+0x27/0x38
Oct 10 05:54:10 localhost kernel:  [work_notifysig+19/21] work_notifysig+0x13/0x15
Oct 10 05:54:10 localhost kernel: Code: 7b 00 00 00 8b 40 08 a8 10 74 1e 6a 05 e8 cb c8 01 00 59 eb 14 b8 00 e0 ff ff 21 e0 ff 30 ff 74 24 30 e8 37 c2 01 00 58 5a 83 c4 <18> 5b 5e 5f 5d c3 55 57 56 53 83 ec 44 8b 54 24 5c 8b 6c 24 68
Oct 10 05:54:14 localhost udev[15096]: removing device node '/dev/vcs7'
Oct 10 05:54:15 localhost udev[15098]: removing device node '/dev/vcsa7'
Oct 10 05:54:17 localhost gconfd (mustard-7308): Received signal 15, shutting down cleanly
Oct 10 05:54:17 localhost gdm[6039]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Oct 10 05:54:17 localhost gconfd (mustard-7308): Exiting
Oct 10 05:54:18 localhost udev[15115]: creating device node '/dev/vcs7'
Oct 10 05:54:18 localhost udev[15119]: creating device node '/dev/vcs8'
Oct 10 05:54:18 localhost udev[15117]: creating device node '/dev/vcsa7'
Oct 10 05:54:18 localhost udev[15121]: creating device node '/dev/vcsa8'
Oct 10 05:54:19 localhost udev[15152]: removing device node '/dev/vcs8'
Oct 10 05:54:19 localhost udev[15158]: removing device node '/dev/vcsa8'
Oct 10 05:54:19 localhost udev[15170]: creating device node '/dev/vcs8'
Oct 10 05:54:19 localhost udev[15172]: creating device node '/dev/vcsa8'
Oct 10 05:54:40 localhost gconfd (mustard-15245): starting (version 2.10.0), pid 15245 user 'mustard'
Oct 10 05:54:40 localhost gconfd (mustard-15245): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Oct 10 05:54:40 localhost gconfd (mustard-15245): Resolved address "xml:readwrite:/home/mustard/.gconf" to a writable configuration source at position 1
Oct 10 05:54:40 localhost gconfd (mustard-15245): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Oct 10 05:54:49 localhost gconfd (mustard-15245): Resolved address "xml:readwrite:/home/mustard/.gconf" to a writable configuration source at position 0

```

---

