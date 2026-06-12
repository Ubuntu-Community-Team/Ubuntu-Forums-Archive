---
title: "Need help troubleshooting suspend/resume problems"
date: 2008-12-30
forum: General Help
---

### Post by ByKeLaO on 2008-12-30
(I have checked in the Intrepid known issues thread to no avail)

I am having a couple of problems with Ubuntu 8.10, specifically related to resuming from standby mode.
After resuming from standby my wireless network card ceases to work until rebooting the computer.
Also, after resuming from standby when the computer is shut down the hard disk issues a strange clicking noise and the system hangs. This issue never happens if I don't use suspend/resume.

These messages in my kernel log look suspicious:
```
Dec 31 02:53:14 james-desktop kernel: [14039.608508] ------------[ cut here ]------------
Dec 31 02:53:14 james-desktop kernel: [14039.608509] WARNING: at /build/buildd/linux-2.6.27/kernel/power/main.c:176 suspend_test_finish+0x74/0x80()
Dec 31 02:53:14 james-desktop kernel: [14039.608511] Modules linked in: aes_i586 aes_generic af_packet ipv6 binfmt_misc rfcomm bridge stp bnep sco l2cap bluetooth vboxdrv ppdev acpi_cpufreq cpufreq_userspace cpufreq_ondemand cpufreq_powersave cpufreq_conservative cpufreq_stats freq_table wmi pci_slot container sbs video output sbshc battery iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport arc4 ecb crypto_blkcipher snd_hda_intel snd_seq_dummy snd_seq_oss rt73usb crc_itu_t snd_seq_midi tvaudio snd_rawmidi snd_bt87x rt2500usb rt2x00usb rt2x00lib bttv snd_seq_midi_event snd_pcm_oss videodev v4l1_compat ir_common compat_ioctl32 joydev i2c_algo_bit rfkill snd_mixer_oss snd_seq v4l2_common led_class videobuf_dma_sg snd_pcm mac80211 videobuf_core snd_timer snd_seq_device btcx_risc cfg80211 evdev tveeprom nvidia(P) iTCO_wdt i2c_core button snd soundcore iTCO_vendor_support snd_page_alloc intel_agp agpgart shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif pata_jmicron ata_piix sg usbhid hid ata_g
Dec 31 02:53:14 james-desktop kernel: neric ohci1394 ieee1394 ahci pata_acpi skge libata sky2 scsi_mod dock ehci_hcd uhci_hcd usbcore thermal processor fan fuse vesafb fbcon tileblit font bitblit softcursor [last unloaded: pcspkr]
Dec 31 02:53:14 james-desktop kernel: [14039.608570] Pid: 11946, comm: pm-suspend Tainted: P          2.6.27-9-generic #1
Dec 31 02:53:14 james-desktop kernel: [14039.608572]  [<c037c4b6>] ? printk+0x1d/0x1f
Dec 31 02:53:14 james-desktop kernel: [14039.608576]  [<c0131de9>] warn_on_slowpath+0x59/0x90
Dec 31 02:53:14 james-desktop kernel: [14039.608580]  [<c014d255>] ? sched_clock_cpu+0xd5/0x170
Dec 31 02:53:14 james-desktop kernel: [14039.608583]  [<c014c0af>] ? down_trylock+0x2f/0x40
Dec 31 02:53:14 james-desktop kernel: [14039.608585]  [<c01324c2>] ? try_acquire_console_sem+0x12/0x40
Dec 31 02:53:14 james-desktop kernel: [14039.608588]  [<c024e580>] ? kobject_put+0x20/0x50
Dec 31 02:53:14 james-desktop kernel: [14039.608591]  [<c015d204>] suspend_test_finish+0x74/0x80
Dec 31 02:53:14 james-desktop kernel: [14039.608594]  [<c015d2f6>] suspend_devices_and_enter+0xe6/0x190
Dec 31 02:53:14 james-desktop kernel: [14039.608597]  [<c015d571>] enter_state+0xd1/0x100
Dec 31 02:53:14 james-desktop kernel: [14039.608599]  [<c015d625>] state_store+0x85/0xd0
Dec 31 02:53:14 james-desktop kernel: [14039.608601]  [<c015d5a0>] ? state_store+0x0/0xd0
Dec 31 02:53:14 james-desktop kernel: [14039.608603]  [<c024e444>] kobj_attr_store+0x24/0x30
Dec 31 02:53:14 james-desktop kernel: [14039.608605]  [<c01ff4c7>] sysfs_write_file+0x97/0x100
Dec 31 02:53:14 james-desktop kernel: [14039.608608]  [<c01b24c0>] vfs_write+0xa0/0x110
Dec 31 02:53:14 james-desktop kernel: [14039.608610]  [<c01ff430>] ? sysfs_write_file+0x0/0x100
Dec 31 02:53:14 james-desktop kernel: [14039.608613]  [<c01b2602>] sys_write+0x42/0x70
Dec 31 02:53:14 james-desktop kernel: [14039.608615]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Dec 31 02:53:14 james-desktop kernel: [14039.608617]  [<c0370000>] ? netdev_exit+0x10/0x20
Dec 31 02:53:14 james-desktop kernel: [14039.608620]  =======================
Dec 31 02:53:14 james-desktop kernel: [14039.608621] ---[ end trace 44c551d7d1d835f2 ]---
```

If I need to provide more information please let me know.

Thanks in advance for any help you can provide!

---

### Post by dcstar on 2008-12-30
> **robinjam said:**
> (I have checked in the Intrepid known issues thread to no avail)

I am having a couple of problems with Ubuntu 8.10, specifically related to resuming from standby mode.
After resuming from standby my wireless network card ceases to work until rebooting the computer.
........

Please read the sticky post at the top of this forum.

---

### Post by cdtech on 2008-12-30
> **dcstar said:**
> Please read the sticky post at the top of this forum.

Could you elaborate, I don't understand :confused:

---

### Post by dcstar on 2008-12-30
> **cdtech said:**
> Could you elaborate, I don't understand :confused:

If you read the post at the top of the forum, you will find a solution to that problem.

---

### Post by cdtech on 2008-12-30
I don't mean to sound dumb, but I know that this is a thread and the site we're on is the forum. Could you please post a link for the user and myself as well.

---

### Post by ByKeLaO on 2008-12-30
> **dcstar said:**
> Please read the sticky post at the top of this forum.

Are you referring to the Intrepid known bugs and workarounds thread? If so, I fail to see a solution to this problem on that thread. Please provide a link to the relevant post.

---

### Post by ByKeLaO on 2008-12-30
For anyone who's interested, this fixed the network issue:
**[http://ubuntuforums.org/showpost.php?p=6264243&postcount=8](http://ubuntuforums.org/showpost.php?p=6264243&postcount=8)**
Apologies to dcstar, that was linked in the intrepid known bugs thread after all.

I'm still looking for a solution to my hard disk problem though. Like I said, after resuming from standby mode when I shut down the computer my HDD makes a continuous clicking noise and the system hangs until I pull the plug. This *only* happens after resuming from standby.
Any ideas?

---

