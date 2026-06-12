---
title: "KDE plasma - keyboard and mouse stopped responding"
date: 2016-10-09
forum: Desktop Environments
---

### Post by VitasLoWang on 2016-10-09
Hello, (repost from another forum...)
So I recently made KDE plasma working and was so happy that it  works smoothly and nice finally. BUT today I just wanted to lock the  screen by pressing ctrl+alt+L as usually. Nothing happened (that is also  usual that I have to press it twice sometimes!) so I pressed is everal  more times and still nothing! Then I realized that pressing my keyboard  does not have any effect and I cannot click on anything! I could still  see all my windows, move the mouse cursor and see animations moving, but  it looked like the computer is locked but there was no lockscreen  displayed! That is really weird. I switched to a text console and tried  to restart the session by doing
```
DISPLAY=:0 killall plasmashell
DISPLAY=:0 kstart plasmashell
```
but  that did not help. Doing kwin --replace also did nothing. I really hate  to reboot my pc with all apps running, but this time I had to do it  again [IMG]https://forum.kde.org/images/smilies/sad.gif[/IMG]
How the heck can this happen? I am afraid to lock my screen now.
[https://goo.gl/photos/g7yGG92JugwwxZai9](https://goo.gl/photos/g7yGG92JugwwxZai9)
Ubuntu 16.04, latest KDE, Thinkpad T460 with Intel Skylake.

EDIT:  it happened again just now but differently! The computer went to  suspend and when I woke it up I cannot click on anything and  keyboard does not work except switching to a text console! I really  don't know what DE should I use anymore [IMG]https://forum.kde.org/images/smilies/sad.gif[/IMG] Can it be because of VirtualBox running?
An attempt to login via text console ended with "login timed out after 60seconds"??

I have checkeg /var/log/syslog around the time when the system went to sleep and
It is spammed a lot with something about ipv4
```
Oct   7 18:17:00 vitas-ThinkPad-T460 kernel: [27633.390231] ll header:  00000000: ff ff ff ff ff ff f0 79 59 60 ee 71 08 00         .......yY`.q..
Oct  7 18:17:00 vitas-ThinkPad-T460 kernel: [27633.390298] IPv4: martian source 192.168.0.255 from 192.168.0.10, on dev wlp4s0
Oct   7 18:17:00 vitas-ThinkPad-T460 kernel: [27633.390305] ll header:  00000000: ff ff ff ff ff ff f0 79 59 60 ee 71 08 00         .......yY`.q..
```

and with this
```
Oct  7 18:17:02 vitas-ThinkPad-T460 org.kde.KScreen[2701]: kscreen.xcb.helper: RRNotify_OutputProperty (ignored)
Oct  7 18:17:02 vitas-ThinkPad-T460 org.kde.KScreen[2701]: kscreen.xcb.helper: #011Output:  67
Oct  7 18:17:02 vitas-ThinkPad-T460 org.kde.KScreen[2701]: kscreen.xcb.helper: #011Property:  Backlight
Oct  7 18:17:02 vitas-ThinkPad-T460 org.kde.KScreen[2701]: kscreen.xcb.helper: #011State (newValue, Deleted):  0
```

The last messages before the system suspend seems to be
```
Oct  7 18:23:03 vitas-ThinkPad-T460 systemd[1]: systemd-udevd.service: State 'stop-sigterm' timed out. Killing.
Oct  7 18:23:03 vitas-ThinkPad-T460 systemd[1]: systemd-udevd.service: Main process exited, code=killed, status=9/KILL
Oct  7 18:23:03 vitas-ThinkPad-T460 systemd[1]: systemd-udevd.service: Unit entered failed state.
Oct  7 18:23:03 vitas-ThinkPad-T460 systemd[1]: systemd-udevd.service: Failed with result 'signal'.
Oct  7 18:23:03 vitas-ThinkPad-T460 systemd[1]: systemd-udevd.service: Service has no hold-off time, scheduling restart.
Oct  7 18:23:03 vitas-ThinkPad-T460 systemd[1]: Stopped udev Kernel Device Manager.
```

then later this
```
Oct   7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.467328]  [drm:intel_dp_start_link_train [i915_bpo]] *ERROR* failed to start  channel equalization
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785685] ------------[ cut here ]------------
Oct   7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785716] WARNING: CPU: 0  PID: 1411 at /build/linux-R0TiM8/linux-4.4.0/ubuntu/i915/intel_pm.c:3675  skl_update_other_pipe_wm+0x16c/0x180 [i915_bpo]()
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785717] WARN_ON(!wm_changed)
Oct   7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785743] Modules linked  in: ctr ccm msr nf_log_ipv4 nf_log_common xt_LOG xt_limit ipt_REJECT  nf_reject_ipv4 xt_tcpudp xt_conntrack iptable_nat nf_conntrack_ipv4  nf_defrag_ipv4 nf_nat_ipv4 nf_nat ip6table_filter ip6_tables  iptable_filter ip_tables x_tables cmac rfcomm bnep  symap_custom_dkms_x86_64(POE) uvcvideo videobuf2_vmalloc  videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common videodev  btusb media btrtl btbcm btintel pci_stub vboxpci(OE) vboxnetadp(OE)  vboxnetflt(OE) vboxdrv(OE) symev_custom_dkms_x86_64(OE) bluetooth arc4  intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp snd_soc_skl  snd_soc_skl_ipc kvm_intel snd_hda_ext_core snd_hda_codec_hdmi kvm  snd_soc_sst_ipc snd_hda_codec_realtek snd_soc_sst_dsp iwlmvm  snd_hda_codec_generic irqbypass snd_soc_core mac80211 snd_compress  ac97_bus snd_pcm_dmaengine dw_dmac_core snd_hda_intel snd_hda_codec  snd_seq_midi snd_hda_core snd_seq_midi_event snd_hwdep joydev iwlwifi  input_leds serio_raw snd_rawmidi rtsx_pci_ms cfg80211 thinkpad_acpi  memstick nvram snd_pcm snd_seq snd_seq_device snd_timer shpchp mei_me  mei snd soundcore mac_hid nf_conntrack_ftp nf_conntrack parport_pc ppdev  lp parport autofs4 drbg ansi_cprng algif_skcipher af_alg dm_crypt  hid_generic usbhid hid rtsx_pci_sdmmc crct10dif_pclmul crc32_pclmul  aesni_intel i915_bpo aes_x86_64 lrw gf128mul glue_helper ablk_helper  cryptd psmouse intel_ips i2c_algo_bit e1000e drm_kms_helper ptp  syscopyarea pps_core sysfillrect sysimgblt fb_sys_fops rtsx_pci drm ahci  libahci wmi video fjes
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel:  [28061.785772] CPU: 0 PID: 1411 Comm: Xorg Tainted: P        W  OE    4.4.0-38-generic #57-Ubuntu
Oct  7 18:24:09 vitas-ThinkPad-T460  kernel: [28061.785773] Hardware name: LENOVO 20FMS1R00U/20FMS1R00U, BIOS  R06ET42W (1.16 ) 09/20/2016
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785775]  0000000000040286 00000000865bc1da ffff880216dc3650 ffffffff813f1b73
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785777]  ffff880216dc3698 ffffffffc02e59a0 ffff880216dc3688 ffffffff810811c2
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785778]  ffff8802132a7000 ffff8802125ea148 ffff8802132a0000 ffff88003544b378
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785778] Call Trace:
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785784]  [<ffffffff813f1b73>] dump_stack+0x63/0x90
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785787]  [<ffffffff810811c2>] warn_slowpath_common+0x82/0xc0
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785788]  [<ffffffff8108125c>] warn_slowpath_fmt+0x5c/0x80
Oct   7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785818]   [<ffffffffc0206fec>] skl_update_other_pipe_wm+0x16c/0x180  [i915_bpo]
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785833]  [<ffffffffc0207185>] skl_update_wm+0x185/0x610 [i915_bpo]
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785852]  [<ffffffffc02511d0>] ? hsw_write16+0x10/0x10 [i915_bpo]
Oct   7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785872]   [<ffffffffc0281410>] ? skl_ddi_pll_disable+0x70/0x80 [i915_bpo]
Oct   7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785887]   [<ffffffffc020af0e>] intel_update_watermarks+0x1e/0x30 [i915_bpo]
Oct   7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785906]   [<ffffffffc0276438>] intel_atomic_commit+0x448/0x14a0 [i915_bpo]
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785924]  [<ffffffffc006abce>] ? drm_atomic_check_only+0x18e/0x590 [drm]
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785936]  [<ffffffffc006b007>] drm_atomic_commit+0x37/0x60 [drm]
Oct   7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785944]   [<ffffffffc010de1f>] restore_fbdev_mode+0x22f/0x260  [drm_kms_helper]
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel:  [28061.785956]  [<ffffffffc006978a>] ?  drm_modeset_lock_all_ctx+0x9a/0xb0 [drm]
Oct  7 18:24:09  vitas-ThinkPad-T460 kernel: [28061.785962]  [<ffffffffc010fff3>]  drm_fb_helper_restore_fbdev_mode_unlocked+0x33/0x80 [drm_kms_helper]
Oct   7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785967]   [<ffffffffc011006d>] drm_fb_helper_set_par+0x2d/0x50  [drm_kms_helper]
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel:  [28061.785971]  [<ffffffffc010ff72>]  drm_fb_helper_hotplug_event+0xd2/0x120 [drm_kms_helper]
Oct  7  18:24:09 vitas-ThinkPad-T460 kernel: [28061.785975]   [<ffffffffc0110016>]  drm_fb_helper_restore_fbdev_mode_unlocked+0x56/0x80 [drm_kms_helper]
Oct   7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.785979]   [<ffffffffc011006d>] drm_fb_helper_set_par+0x2d/0x50  [drm_kms_helper]
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786015]  [<ffffffffc02905fa>] intel_fbdev_set_par+0x1a/0x60 [i915_bpo]
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786018]  [<ffffffff81474fef>] ? fb_set_var+0x2ef/0x460
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786020]  [<ffffffff81474f36>] fb_set_var+0x236/0x460
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786022]  [<ffffffff810b4e09>] ? update_curr+0x79/0x160
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786024]  [<ffffffff8146b22f>] fbcon_blank+0x30f/0x350
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786026]  [<ffffffff810ab219>] ? ttwu_do_wakeup+0x19/0xe0
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786029]  [<ffffffff81502573>] do_unblank_screen+0xd3/0x1a0
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786032]  [<ffffffff814f7649>] complete_change_console+0x59/0xe0
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786033]  [<ffffffff814f7de0>] vt_ioctl+0x710/0x12f0
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786036]  [<ffffffff8118e36e>] ? filemap_map_pages+0xce/0x230
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786039]  [<ffffffff814eb09f>] tty_ioctl+0x35f/0xc40
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786041]  [<ffffffff811c0911>] ? handle_mm_fault+0x1131/0x1820
Oct   7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786045]   [<ffffffffc09ae836>] ? symap_event_cb+0x219/0x48c  [symap_custom_dkms_x86_64]
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786047]  [<ffffffff81224944>] ? dput+0x34/0x220
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786048]  [<ffffffff812211ff>] do_vfs_ioctl+0x29f/0x490
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786050]  [<ffffffff8106b544>] ? __do_page_fault+0x1b4/0x400
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786052]  [<ffffffff81221469>] SyS_ioctl+0x79/0x90
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786054]  [<ffffffff818306f2>] entry_SYSCALL_64_fastpath+0x16/0x71
Oct  7 18:24:09 vitas-ThinkPad-T460 kernel: [28061.786055] ---[ end trace b7c6643e69ea047d ]---
```

Looks serious to me. Does it ring anybody's bell?

---

### Post by VitasLoWang on 2016-10-12
So this is a mystery I guess...It's weird that nobody have seen any of those messages :-]

---

