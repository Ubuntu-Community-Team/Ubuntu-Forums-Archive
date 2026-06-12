---
title: "Problems with my  My Book"
date: 2010-01-25
forum: Desktop Environments
---

### Post by skaramanger on 2010-01-25
Greetings,

I have a 1TB My Book that has both a 1394 connector and an USB connector.  While connected via the Firewire connector.  The drive is not reconized by the system. I have a splurge of dmesg output as follows:

```
[454963.825290] EXT3-fs error (device sdc5): ext3_find_entry: reading directory #2 offset 0
[454963.825478] ------------[ cut here ]------------
[454963.825486] WARNING: at /build/buildd/linux-2.6.31/fs/buffer.c:1152 mark_buffer_dirty+0x86/0xb0()
[454963.825488] Hardware name: System Product Name
[454963.825490] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat uvcvideo videodev v4l1_compat v4l2_compat_ioctl32 binfmt_misc vboxnetadp vboxnetflt vboxdrv snd_usb_audio snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_usb_lib snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer ppdev snd_seq_device hwmon_vid snd lp soundcore parport_pc amd64_edac_mod i2c_nforce2 nvidia(P) iptable_filter parport psmouse k8temp edac_core asus_atk0110 ip_tables x_tables joydev serio_raw ses enclosure hid_microsoft sbp2 usbhid usb_storage floppy ohci1394 forcedeth ieee1394
[454963.825526] Pid: 17798, comm: gvfs-gdu-volume Tainted: P        W  2.6.31-17-generic #54-Ubuntu
[454963.825529] Call Trace:
[454963.825536]  [<ffffffff8105e7d8>] warn_slowpath_common+0x78/0xb0
[454963.825540]  [<ffffffff8105e81f>] warn_slowpath_null+0xf/0x20
[454963.825543]  [<ffffffff81146026>] mark_buffer_dirty+0x86/0xb0
[454963.825546]  [<ffffffff81198742>] T.851+0x52/0x80
[454963.825549]  [<ffffffff811987ea>] ext3_handle_error+0x7a/0xc0
[454963.825552]  [<ffffffff81198c1d>] ext3_error+0x7d/0x90
[454963.825555]  [<ffffffff81146b43>] ? ll_rw_block+0x133/0x140
[454963.825558]  [<ffffffff811958f3>] ext3_find_entry+0x383/0x420
[454963.825562]  [<ffffffff81529be9>] ? _spin_lock+0x9/0x10
[454963.825565]  [<ffffffff8152888f>] ? __mutex_lock_slowpath+0x11f/0x160
[454963.825568]  [<ffffffff811959dd>] ext3_lookup+0x4d/0x130
[454963.825571]  [<ffffffff8112888a>] real_lookup+0xda/0x150
[454963.825575]  [<ffffffff8112a480>] do_lookup+0xb0/0xe0
[454963.825577]  [<ffffffff8112b02d>] __link_path_walk+0x6ad/0xdc0
[454963.825580]  [<ffffffff8112b927>] path_walk+0x57/0xb0
[454963.825583]  [<ffffffff8112b9d3>] do_path_lookup+0x53/0xa0
[454963.825586]  [<ffffffff81120a6c>] ? get_empty_filp+0x9c/0x170
[454963.825589]  [<ffffffff8112ca2e>] do_filp_open+0xfe/0xac0
[454963.825593]  [<ffffffff810f1a55>] ? __inc_zone_page_state+0x25/0x30
[454963.825595]  [<ffffffff810e56ec>] ? lru_cache_add_lru+0x1c/0x40
[454963.825598]  [<ffffffff810f4240>] ? do_anonymous_page+0x170/0x1d0
[454963.825602]  [<ffffffff81036419>] ? default_spin_lock_flags+0x9/0x10
[454963.825606]  [<ffffffff8127cf02>] ? __strncpy_from_user+0x22/0x60
[454963.825609]  [<ffffffff81137672>] ? alloc_fd+0x102/0x150
[454963.825613]  [<ffffffff8111d074>] do_sys_open+0x64/0x160
[454963.825615]  [<ffffffff8111d19b>] sys_open+0x1b/0x20
[454963.825619]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b
[454963.825621] ---[ end trace dd14ad066eb3bf38 ]---
```

I have read a few posts regarding the beginning of the output regarding the EXT3-fs message and potential drive failure. This again occurs when connected via firewire.  Now I changed the connector to the usb and the unit was reconized and I mounted it w/o incidence. 

My question is do I have a unit with a failing firewire interface, main board or kernel module?

Tia

---

### Post by skaramanger on 2010-02-01
Just an update.  I realized not soon enough after my post that the kernel messages I posted more than likely had nothing to do with my My_Books problem.  However, leaving a small telescopic magnetic pickup near the unit might be a cause of problems. UGH! So one might call this problem [solved}.

Sorry to waste the bandwith.

---

