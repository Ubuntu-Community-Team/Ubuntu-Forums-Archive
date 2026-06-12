---
title: "Won't go into suspend / lose network + tvcard"
date: 2009-02-15
forum: General Help
---

### Post by gfuggs on 2009-02-15
I installed 8.10 last week, and I have been working through process of getting my hardware working.  I seem to have hit a wall with my latest problem- trying to get suspend working.

When I try to suspend, the instant that everything is off, the computer wakes back up, sans network (EDIMAX EW-7128G - ralink) and tv card (AVer A180).

After I try to suspend, the output of dmesg keeps growing and growing with stuff like this from the tv card:
[  134.728151] nxt200x: i2c_readbytes: i2c read error (addr 0x61, err == -5)
[  134.832010] nxt2004: timeout waiting for tuner lock
[  136.124033] nxt200x: Timeout waiting for nxt2004 to init.
[  136.792146] nxt200x: i2c_writebytes: i2c write error (addr 0x61, err == -5)
[  136.792151] nxt200x: error writing to tuner
[  136.793491] nxt200x: i2c_readbytes: i2c read error (addr 0x61, err == -5)


I also see this in dmesg from when I try to suspend:
[  116.129980] PM: resume devices took 6.532 seconds
[  116.129986] ------------[ cut here ]------------
[  116.129988] WARNING: at /build/buildd/linux-2.6.27/kernel/power/main.c:176 suspend_test_finish+0x75/0x80()
[  116.129991] Modules linked in: aes_x86_64 aes_generic binfmt_misc af_packet bridge stp bnep sco rfcomm l2cap bluetooth ipv6 ppdev cpufreq_conservative cpufreq_ondemand cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave sbs video output container pci_slot sbshc battery iptable_filter ip_tables x_tables ac dvb_pll nxt200x saa7134_alsa saa7134_dvb saa7134 ir_common compat_ioctl32 videodev v4l1_compat v4l2_common tveeprom videobuf_dma_sg videobuf_dvb videobuf_core dvb_core sbp2 parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm arc4 snd_seq_dummy ecb crypto_blkcipher snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq evdev nvidia(P) pcspkr i2c_core lirc_mceusb2 snd_timer lirc_dev snd_seq_device snd soundcore snd_page_alloc shpchp pci_hotplug wmi button ext3 jbd mbcache sr_mod sd_mod crc_t10dif cdrom sg ata_generic usbhid hid pata_amd ahci pata_acpi ohci1394 libata ieee1394 sky2 scsi_mod dock ehci_hcd ohci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse [last unloaded: eeprom_93cx6]
[  116.130058] Pid: 6458, comm: pm-suspend Tainted: P          2.6.27-11-generic #1
[  116.130060] 
[  116.130061] Call Trace:
[  116.130066]  [<ffffffff8024e9c4>] warn_on_slowpath+0x64/0x90
[  116.130071]  [<ffffffff805010d6>] ? printk+0x6c/0x6e
[  116.130075]  [<ffffffff803a4927>] ? kobject_put+0x27/0x60
[  116.130078]  [<ffffffff80502179>] ? mutex_unlock+0x9/0x20
[  116.130082]  [<ffffffff80435d3a>] ? dpm_complete+0x18a/0x1a0
[  116.130085]  [<ffffffff8027e1b5>] suspend_test_finish+0x75/0x80
[  116.130088]  [<ffffffff8027e2c4>] suspend_devices_and_enter+0x104/0x1b0
[  116.130090]  [<ffffffff8027e581>] enter_state+0xe1/0x110
[  116.130093]  [<ffffffff8027e66a>] state_store+0xba/0x100
[  116.130096]  [<ffffffff803a47c7>] kobj_attr_store+0x17/0x20
[  116.130100]  [<ffffffff80349dba>] sysfs_write_file+0xca/0x140
[  116.130103]  [<ffffffff802ea1db>] vfs_write+0xcb/0x130
[  116.130105]  [<ffffffff802ea335>] sys_write+0x55/0x90
[  116.130109]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
[  116.130111] 
[  116.130113] ---[ end trace 07e8a2cffa2b1ff5 ]---
[  116.130282] PM: Finishing wakeup.

I attached the full dmesg and lspci outputs.  Any ideas where I should start?

Thanks

---

### Post by gfuggs on 2009-02-15
I'm not even sure if I should be focusing in the network/tv card issue, or trying to get it to go into suspend?  Or maybe they're related?

---

### Post by gfuggs on 2009-02-16
Well, I tried removing all the modules associated with the tv card- nxt200x and saa7134.  It still wouldn't stay in suspend, but that keeps the card from going wacky.

I'm still not sure what is making it come out of suspend, but I think I've eliminated one possibility.

---

