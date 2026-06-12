---
title: "Kernel panic on ubuntu-11.10 (kernel 3.0.0.15) while ising usb based wifi card."
date: 2012-06-18
forum: Desktop Environments
---

### Post by Hari Babu on 2012-06-18
Hi,
      i am trying to use Atheros USB based wifi , and while bringing up the card "ifconfig ath0 up" i am getting the following panic.
Can anybody help me out ?

XXXXX

[ 2516.010810] BUG: scheduling while atomic: ifconfig/3411/0x00000200
[ 2516.010819] Modules linked in: atd(P) fwd(P) hif_usb adf(P) rfcomm bnep bluetooth parport_pc ppdev pl2303 usbserial snd_hda_codec_hdmi snd_hda_codec_idt joydev binfmt_misc arc4 dell_wmi sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq pcmcia dell_laptop dcdbas snd_timer snd_seq_device iwlagn yenta_socket snd pcmcia_rsrc psmouse pcmcia_core serio_raw mac80211 i915 cfg80211 drm_kms_helper drm i2c_algo_bit soundcore snd_page_alloc wmi video lp parport firewire_ohci firewire_core crc_itu_t sdhci_pci sdhci tg3 [last unloaded: adf]
[ 2516.010954] Pid: 3411, comm: ifconfig Tainted: P            3.0.0-15-generic #26-Ubuntu
[ 2516.010960] Call Trace:
[ 2516.010979]  [<c151a7a2>] ? printk+0x2d/0x2f
[ 2516.010989]  [<c151a03b>] __schedule_bug+0x5e/0x64
[ 2516.011022]  [<c152c1c4>] __schedule+0x614/0x620
[ 2516.011032]  [<c13b72a0>] ? usb_hcd_submit_urb+0x80/0x180
[ 2516.011044]  [<c10263e8>] ? default_spin_lock_flags+0x8/0x10
[ 2516.011059]  [<f8cb63f3>] ? hif_usb_check_txbuf_cnt+0xa3/0xd0 [hif_usb]
[ 2516.011071]  [<f8cb722d>] ? hif_usb_xmit+0x34d/0x580 [hif_usb]
[ 2516.011082]  [<f8cb7790>] ? hif_usb_timer+0xc0/0xc0 [hif_usb]
[ 2516.011091]  [<c152c475>] schedule+0x35/0x50
[ 2516.011100]  [<c152c99d>] schedule_timeout+0x22d/0x2a0
[ 2516.011111]  [<f8cb75f6>] ? hif_send+0x196/0x270 [hif_usb]
[ 2516.011121]  [<c152d45a>] __down_common+0x8b/0xca
[ 2516.011130]  [<c152d4f8>] __down+0x17/0x19
[ 2516.011140]  [<c106baa9>] down+0x39/0x40
[ 2516.011154]  [<f915e0fb>] wmi_cmd_send+0xdb/0x1b0 [atd]
[ 2516.011171]  [<f9105866>] ? __adf_nbuf_alloc+0x26/0x90 [adf]
[ 2516.011187]  [<f916a734>] atd_vap_cmd_set_mcast+0xb4/0x160 [atd]
[ 2516.011201]  [<f916a7e0>] ? atd_vap_cmd_set_mcast+0x160/0x160 [atd]
[ 2516.011214]  [<f916a829>] atd_vap_cmd+0x49/0x1b0 [atd]
[ 2516.011228]  [<f90ff1aa>] __adf_net_set_mcast_addr_internal+0x8a/0xd0 [adf]
[ 2516.011245]  [<f90ff217>] __adf_net_set_mcast_addr+0x27/0x40 [adf]
[ 2516.011256]  [<c143cdc4>] __dev_set_rx_mode+0x34/0xa0
[ 2516.011265]  [<c144181b>] __dev_mc_add+0x5b/0x80
[ 2516.011274]  [<c144186f>] dev_mc_add+0xf/0x20
[ 2516.011284]  [<c14dcc63>] igmp6_group_added+0xd3/0xf0
[ 2516.011295]  [<c152df86>] ? _raw_spin_unlock_bh+0x16/0x20
[ 2516.011304]  [<c14dcdde>] ? mld_del_delrec+0x8e/0x100
[ 2516.011313]  [<c14de676>] ipv6_dev_mc_inc+0x186/0x270
[ 2516.011323]  [<c14c54e6>] addrconf_join_solict+0x46/0x60
[ 2516.011332]  [<c14c5d84>] addrconf_dad_start.isra.33+0x24/0x130
[ 2516.011341]  [<c14c6311>] addrconf_add_linklocal+0x51/0x70
[ 2516.011349]  [<c14c6494>] addrconf_dev_config+0xa4/0xe0
[ 2516.011358]  [<c14c8014>] addrconf_notify+0x134/0x490
[ 2516.011369]  [<c1464e6a>] ? rt_cache_flush+0x1a/0x50
[ 2516.011378]  [<c15318a5>] notifier_call_chain+0x45/0x60
[ 2516.011388]  [<c106bbbf>] raw_notifier_call_chain+0x1f/0x30
[ 2516.011398]  [<c1437b9c>] call_netdevice_notifiers+0x2c/0x60
[ 2516.011407]  [<c143d262>] __dev_notify_flags+0x32/0x80
[ 2516.011416]  [<c143d2ea>] dev_change_flags+0x3a/0x60
[ 2516.011425]  [<c149487c>] devinet_ioctl+0x4dc/0x640
[ 2516.011433]  [<c143d75e>] ? dev_ioctl+0x1de/0x2f0
[ 2516.011441]  [<c1494d8d>] inet_ioctl+0x8d/0xb0
[ 2516.011452]  [<c142805d>] sock_ioctl+0x6d/0x290
[ 2516.011461]  [<c1427ff0>] ? move_addr_to_user+0x90/0x90
[ 2516.011484]  [<c1138e99>] do_vfs_ioctl+0x79/0x2d0
[ 2516.011492]  [<c113915f>] sys_ioctl+0x6f/0x80
[ 2516.011503]  [<c112883e>] ? sys_open+0x2e/0x40
[ 2516.011511]  [<c152e2a4>] syscall_call+0x7/0xb
[ 2516.011533] NOHZ: local_softirq_pending 40
[ 2517.540420] BUG: scheduling while atomic: avahi-daemon/784/0x00000200
[ 2517.540430] Modules linked in: atd(P) fwd(P) hif_usb adf(P) rfcomm bnep bluetooth parport_pc ppdev pl2303 usbserial snd_hda_codec_hdmi snd_hda_codec_idt joydev binfmt_misc arc4 dell_wmi sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq pcmcia dell_laptop dcdbas snd_timer snd_seq_device iwlagn yenta_socket snd pcmcia_rsrc psmouse pcmcia_core serio_raw mac80211 i915 cfg80211 drm_kms_helper drm i2c_algo_bit soundcore snd_page_alloc wmi video lp parport firewire_ohci firewire_core crc_itu_t sdhci_pci sdhci tg3 [last unloaded: adf]
[ 2517.540586] Pid: 784, comm: avahi-daemon Tainted: P            3.0.0-15-generic #26-Ubuntu
[ 2517.540593] Call Trace:
[ 2517.540611]  [<c151a7a2>] ? printk+0x2d/0x2f
[ 2517.540622]  [<c151a03b>] __schedule_bug+0x5e/0x64
[ 2517.540633]  [<c152c1c4>] __schedule+0x614/0x620
[ 2517.540644]  [<c13b72a0>] ? usb_hcd_submit_urb+0x80/0x180
[ 2517.540656]  [<c10263e8>] ? default_spin_lock_flags+0x8/0x10
[ 2517.540670]  [<f8cb63f3>] ? hif_usb_check_txbuf_cnt+0xa3/0xd0 [hif_usb]
[ 2517.540682]  [<f8cb722d>] ? hif_usb_xmit+0x34d/0x580 [hif_usb]
[ 2517.540694]  [<f8cb7790>] ? hif_usb_timer+0xc0/0xc0 [hif_usb]
[ 2517.540703]  [<c152c475>] schedule+0x35/0x50
[ 2517.540712]  [<c152c99d>] schedule_timeout+0x22d/0x2a0
[ 2517.540724]  [<f8cb75f6>] ? hif_send+0x196/0x270 [hif_usb]
[ 2517.540734]  [<c152d45a>] __down_common+0x8b/0xca
[ 2517.540744]  [<c152d4f8>] __down+0x17/0x19
[ 2517.540754]  [<c106baa9>] down+0x39/0x40
[ 2517.540768]  [<f915e0fb>] wmi_cmd_send+0xdb/0x1b0 [atd]
[ 2517.540789]  [<f9105866>] ? __adf_nbuf_alloc+0x26/0x90 [adf]
[ 2517.540804]  [<f916a734>] atd_vap_cmd_set_mcast+0xb4/0x160 [atd]
[ 2517.540818]  [<f916a7e0>] ? atd_vap_cmd_set_mcast+0x160/0x160 [atd]
[ 2517.540831]  [<f916a829>] atd_vap_cmd+0x49/0x1b0 [atd]
[ 2517.540845]  [<f90ff1aa>] __adf_net_set_mcast_addr_internal+0x8a/0xd0 [adf]
[ 2517.540863]  [<f90ff217>] __adf_net_set_mcast_addr+0x27/0x40 [adf]
[ 2517.540874]  [<c143cdc4>] __dev_set_rx_mode+0x34/0xa0
[ 2517.540884]  [<c144181b>] __dev_mc_add+0x5b/0x80
[ 2517.540893]  [<c144186f>] dev_mc_add+0xf/0x20
[ 2517.540903]  [<c14dcc63>] igmp6_group_added+0xd3/0xf0
[ 2517.540913]  [<c152df86>] ? _raw_spin_unlock_bh+0x16/0x20
[ 2517.540923]  [<c14dcdde>] ? mld_del_delrec+0x8e/0x100
[ 2517.540935]  [<c14de676>] ipv6_dev_mc_inc+0x186/0x270
[ 2517.540944]  [<c14de85d>] ipv6_sock_mc_join+0xfd/0x1b0
[ 2517.540956]  [<c14d1225>] do_ipv6_setsockopt.isra.10+0xcf5/0xe60
[ 2517.540969]  [<c1251f55>] ? apparmor_socket_sendmsg+0x15/0x20
[ 2517.540980]  [<c142773c>] ? sock_sendmsg+0xec/0x110
[ 2517.540992]  [<c1289682>] ? _copy_from_user+0x42/0x60
[ 2517.541002]  [<c1432744>] ? verify_iovec+0x44/0xb0
[ 2517.541010]  [<c14274d0>] ? sock_recvmsg_nosec+0x110/0x110
[ 2517.541021]  [<c14298fe>] ? sys_sendto+0x10e/0x150
[ 2517.541033]  [<c101bd1b>] ? lapic_next_event+0x1b/0x20
[ 2517.541043]  [<c14d140a>] ipv6_setsockopt+0x7a/0xe0
[ 2517.541051]  [<c14d4ef0>] udpv6_setsockopt+0x30/0x60
[ 2517.541060]  [<c142a927>] sock_common_setsockopt+0x27/0x40
[ 2517.541070]  [<c1429b84>] sys_setsockopt+0x64/0xb0
[ 2517.541079]  [<c142a381>] sys_socketcall+0x221/0x2c0
[ 2517.541087]  [<c152e2a4>] syscall_call+0x7/0xb
[ 2517.541125]  [<c1520000>] ? ext3_orphan_cleanup.isra.15+0x19f/0x271
[ 2526.560051] ath0: no IPv6 routers present

---

