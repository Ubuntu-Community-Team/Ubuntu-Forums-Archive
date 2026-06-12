---
title: "Kernel error messages"
date: 2020-01-14
forum: Desktop Environments
---

### Post by gdesilva on 2020-01-14
Hi, I have been using Ubuntu Studio 19.04 for some time now but noticed some kernel error messages recently.

It appears the following error message gets repeated (?) a number of time before the boot process is completed.


```

Jan 14 18:07:16 HP kernel: [   58.807856] BUG: scheduling while atomic: bash/2175/0x00000002
Jan 14 18:07:16 HP kernel: [   58.807858] Modules linked in: pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) input_leds snd_hda_codec_realtek snd_hda_codec_generic joydev ledtrig_audio snd_hda_codec_hdmi snd_hda_intel intel_rapl snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq x86_pkg_temp_thermal intel_powerclamp snd_seq_device snd_timer coretemp radeon snd kvm_intel soundcore kvm ttm irqbypass crct10dif_pclmul crc32_pclmul drm_kms_helper drm i2c_algo_bit fb_sys_fops syscopyarea sysfillrect sysimgblt ghash_clmulni_intel aesni_intel aes_x86_64 mei_me mei crypto_simd cryptd hp_wmi mac_hid wmi_bmof sparse_keymap serio_raw glue_helper intel_cstate intel_rapl_perf tpm_infineon ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp sch_fq_codel
Jan 14 18:07:16 HP kernel: [   58.807876]  nf_conntrack nf_defrag_ipv6 nf_defrag_ipv4 libcrc32c cuse iptable_filter bpfilter parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_microsoft ff_memless hid_generic usbhid hid gpio_ich psmouse i2c_i801 ahci e1000e libahci lpc_ich wmi
Jan 14 18:07:16 HP kernel: [   58.807883] CPU: 0 PID: 2175 Comm: bash Tainted: G        W  OE     5.0.0-38-lowlatency #41-Ubuntu
Jan 14 18:07:16 HP kernel: [   58.807884] Hardware name: Hewlett-Packard HP Compaq 8200 Elite SFF PC/1495, BIOS J01 v02.28 03/24/2015
Jan 14 18:07:16 HP kernel: [   58.807885] Call Trace:
Jan 14 18:07:16 HP kernel: [   58.807889]  dump_stack+0x6d/0x9a
Jan 14 18:07:16 HP kernel: [   58.807891]  __schedule_bug.cold.81+0x5/0x1f
Jan 14 18:07:16 HP kernel: [   58.807893]  __schedule+0x562/0x8a0
Jan 14 18:07:16 HP kernel: [   58.807894]  ? bit_wait_timeout+0xa0/0xa0
Jan 14 18:07:16 HP kernel: [   58.807895]  schedule+0x33/0x80
Jan 14 18:07:16 HP kernel: [   58.807896]  io_schedule+0x16/0x40
Jan 14 18:07:16 HP kernel: [   58.807897]  bit_wait_io+0x11/0x50
Jan 14 18:07:16 HP kernel: [   58.807898]  __wait_on_bit+0x7b/0x90
Jan 14 18:07:16 HP kernel: [   58.807899]  out_of_line_wait_on_bit+0x90/0xb0
Jan 14 18:07:16 HP kernel: [   58.807901]  ? init_wait_var_entry+0x50/0x50
Jan 14 18:07:16 HP kernel: [   58.807903]  __wait_on_buffer+0x27/0x30
Jan 14 18:07:16 HP kernel: [   58.807905]  ext4_find_entry+0x368/0x530
Jan 14 18:07:16 HP kernel: [   58.807907]  ? d_alloc_parallel+0x249/0x500
Jan 14 18:07:16 HP kernel: [   58.807909]  ext4_lookup+0x79/0x220
Jan 14 18:07:16 HP kernel: [   58.807910]  __lookup_slow+0x9b/0x170
Jan 14 18:07:16 HP kernel: [   58.807912]  lookup_slow+0x3a/0x60
Jan 14 18:07:16 HP kernel: [   58.807913]  walk_component+0x1bf/0x330
Jan 14 18:07:16 HP kernel: [   58.807914]  ? inode_permission+0x63/0x1a0
Jan 14 18:07:16 HP kernel: [   58.807916]  link_path_walk.part.43+0x2cc/0x530
Jan 14 18:07:16 HP kernel: [   58.807917]  path_lookupat.isra.47+0x93/0x220
Jan 14 18:07:16 HP kernel: [   58.807919]  filename_lookup.part.61+0xa0/0x170
Jan 14 18:07:16 HP kernel: [   58.807921]  ? strncpy_from_user+0x57/0x1c0
Jan 14 18:07:16 HP kernel: [   58.807923]  user_path_at_empty+0x3e/0x50
Jan 14 18:07:16 HP kernel: [   58.807925]  do_faccessat+0xb3/0x250
Jan 14 18:07:16 HP kernel: [   58.807927]  __x64_sys_access+0x1b/0x20
Jan 14 18:07:16 HP kernel: [   58.807928]  do_syscall_64+0x5a/0x110
Jan 14 18:07:16 HP kernel: [   58.807930]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
Jan 14 18:07:16 HP kernel: [   58.807932] RIP: 0033:0x7f013b4fe0e7
Jan 14 18:07:16 HP kernel: [   58.807933] Code: 77 01 c3 48 8b 15 a9 6d 0d 00 f7 d8 64 89 02 48 c7 c0 ff ff ff ff c3 66 2e 0f 1f 84 00 00 00 00 00 66 90 b8 15 00 00 00 0f 05 <48> 3d 00 f0 ff ff 77 01 c3 48 8b 15 79 6d 0d 00 f7 d8 64 89 02 b8
Jan 14 18:07:16 HP kernel: [   58.807934] RSP: 002b:00007fff37b745c8 EFLAGS: 00000206 ORIG_RAX: 0000000000000015
Jan 14 18:07:16 HP kernel: [   58.807935] RAX: ffffffffffffffda RBX: 00007fff37b7d6f0 RCX: 00007f013b4fe0e7
Jan 14 18:07:16 HP kernel: [   58.807935] RDX: 00007fff37b7d70e RSI: 0000000000000004 RDI: 00007fff37b7d6f0
Jan 14 18:07:16 HP kernel: [   58.807936] RBP: 0000000000000004 R08: 0000558bee186ca0 R09: 00000000ffffffff
Jan 14 18:07:16 HP kernel: [   58.807936] R10: 00007f013b607203 R11: 0000000000000206 R12: 0000558bee198e10
Jan 14 18:07:16 HP kernel: [   58.807937] R13: 00007fff37b7d6f0 R14: 0000558bee272f96 R15: 000000000000000d
Jan 14 18:07:16 HP kernel: [   58.817196] BUG: scheduling while atomic: bash/2175/0x00000002
Jan 14 18:07:16 HP kernel: [   58.817198] Modules linked in: pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) input_leds snd_hda_codec_realtek snd_hda_codec_generic joydev ledtrig_audio snd_hda_codec_hdmi snd_hda_intel intel_rapl snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq x86_pkg_temp_thermal intel_powerclamp snd_seq_device snd_timer coretemp radeon snd kvm_intel soundcore kvm ttm irqbypass crct10dif_pclmul crc32_pclmul drm_kms_helper drm i2c_algo_bit fb_sys_fops syscopyarea sysfillrect sysimgblt ghash_clmulni_intel aesni_intel aes_x86_64 mei_me mei crypto_simd cryptd hp_wmi mac_hid wmi_bmof sparse_keymap serio_raw glue_helper intel_cstate intel_rapl_perf tpm_infineon ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp sch_fq_codel
Jan 14 18:07:16 HP kernel: [   58.817217]  nf_conntrack nf_defrag_ipv6 nf_defrag_ipv4 libcrc32c cuse iptable_filter bpfilter parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_microsoft ff_memless hid_generic usbhid hid gpio_ich psmouse i2c_i801 ahci e1000e libahci lpc_ich wmi
Jan 14 18:07:16 HP kernel: [   58.817224] CPU: 0 PID: 2175 Comm: bash Tainted: G        W  OE     5.0.0-38-lowlatency #41-Ubuntu
Jan 14 18:07:16 HP kernel: [   58.817225] Hardware name: Hewlett-Packard HP Compaq 8200 Elite SFF PC/1495, BIOS J01 v02.28 03/24/2015
Jan 14 18:07:16 HP kernel: [   58.817225] Call Trace:
Jan 14 18:07:16 HP kernel: [   58.817229]  dump_stack+0x6d/0x9a
Jan 14 18:07:16 HP kernel: [   58.817231]  __schedule_bug.cold.81+0x5/0x1f
Jan 14 18:07:16 HP kernel: [   58.817233]  __schedule+0x562/0x8a0
Jan 14 18:07:16 HP kernel: [   58.817234]  ? bit_wait_timeout+0xa0/0xa0
Jan 14 18:07:16 HP kernel: [   58.817235]  schedule+0x33/0x80
Jan 14 18:07:16 HP kernel: [   58.817236]  io_schedule+0x16/0x40
Jan 14 18:07:16 HP kernel: [   58.817237]  bit_wait_io+0x11/0x50
Jan 14 18:07:16 HP kernel: [   58.817238]  __wait_on_bit+0x7b/0x90
Jan 14 18:07:16 HP kernel: [   58.817239]  out_of_line_wait_on_bit+0x90/0xb0
Jan 14 18:07:16 HP kernel: [   58.817241]  ? init_wait_var_entry+0x50/0x50
Jan 14 18:07:16 HP kernel: [   58.817243]  __wait_on_buffer+0x27/0x30
Jan 14 18:07:16 HP kernel: [   58.817245]  ext4_find_entry+0x368/0x530
Jan 14 18:07:16 HP kernel: [   58.817248]  ? d_alloc_parallel+0x249/0x500
Jan 14 18:07:16 HP kernel: [   58.817249]  ext4_lookup+0x79/0x220
Jan 14 18:07:16 HP kernel: [   58.817251]  __lookup_slow+0x9b/0x170
Jan 14 18:07:16 HP kernel: [   58.817252]  lookup_slow+0x3a/0x60
Jan 14 18:07:16 HP kernel: [   58.817254]  walk_component+0x1bf/0x330
Jan 14 18:07:16 HP kernel: [   58.817255]  ? link_path_walk.part.43+0x2a4/0x530
Jan 14 18:07:16 HP kernel: [   58.817256]  path_lookupat.isra.47+0x6d/0x220
Jan 14 18:07:16 HP kernel: [   58.817258]  filename_lookup.part.61+0xa0/0x170
Jan 14 18:07:16 HP kernel: [   58.817260]  ? strncpy_from_user+0x57/0x1c0
Jan 14 18:07:16 HP kernel: [   58.817262]  user_path_at_empty+0x3e/0x50
Jan 14 18:07:16 HP kernel: [   58.817264]  do_faccessat+0xb3/0x250
Jan 14 18:07:16 HP kernel: [   58.817265]  __x64_sys_access+0x1b/0x20
Jan 14 18:07:16 HP kernel: [   58.817267]  do_syscall_64+0x5a/0x110
Jan 14 18:07:16 HP kernel: [   58.817269]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
Jan 14 18:07:16 HP kernel: [   58.817270] RIP: 0033:0x7f013b4fe0e7
Jan 14 18:07:16 HP kernel: [   58.817272] Code: 77 01 c3 48 8b 15 a9 6d 0d 00 f7 d8 64 89 02 48 c7 c0 ff ff ff ff c3 66 2e 0f 1f 84 00 00 00 00 00 66 90 b8 15 00 00 00 0f 05 <48> 3d 00 f0 ff ff 77 01 c3 48 8b 15 79 6d 0d 00 f7 d8 64 89 02 b8
Jan 14 18:07:16 HP kernel: [   58.817272] RSP: 002b:00007fff37b745c8 EFLAGS: 00000206 ORIG_RAX: 0000000000000015
Jan 14 18:07:16 HP kernel: [   58.817273] RAX: ffffffffffffffda RBX: 00007fff37b7d6f0 RCX: 00007f013b4fe0e7
Jan 14 18:07:16 HP kernel: [   58.817274] RDX: 00007fff37b7d70e RSI: 0000000000000004 RDI: 00007fff37b7d6f0
Jan 14 18:07:16 HP kernel: [   58.817274] RBP: 0000000000000004 R08: 0000558bee186ca0 R09: 00000000ffffffff
Jan 14 18:07:16 HP kernel: [   58.817275] R10: 00007f013b607203 R11: 0000000000000206 R12: 0000558bee198e10
Jan 14 18:07:16 HP kernel: [   58.817275] R13: 00007fff37b7d6f0 R14: 0000558bee272f96 R15: 000000000000000d
Jan 14 18:07:17 HP kernel: [   58.931522] BUG: scheduling while atomic: Xorg/1358/0x00000002
Jan 14 18:07:17 HP kernel: [   58.931534] Modules linked in: pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) input_leds snd_hda_codec_realtek snd_hda_codec_generic joydev ledtrig_audio snd_hda_codec_hdmi snd_hda_intel intel_rapl snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq x86_pkg_temp_thermal intel_powerclamp snd_seq_device snd_timer coretemp radeon snd kvm_intel soundcore kvm ttm irqbypass crct10dif_pclmul crc32_pclmul drm_kms_helper drm i2c_algo_bit fb_sys_fops syscopyarea sysfillrect sysimgblt ghash_clmulni_intel aesni_intel aes_x86_64 mei_me mei crypto_simd cryptd hp_wmi mac_hid wmi_bmof sparse_keymap serio_raw glue_helper intel_cstate intel_rapl_perf tpm_infineon ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp sch_fq_codel
Jan 14 18:07:17 HP kernel: [   58.931564]  nf_conntrack nf_defrag_ipv6 nf_defrag_ipv4 libcrc32c cuse iptable_filter bpfilter parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_microsoft ff_memless hid_generic usbhid hid gpio_ich psmouse i2c_i801 ahci e1000e libahci lpc_ich wmi
Jan 14 18:07:17 HP kernel: [   58.931578] CPU: 2 PID: 1358 Comm: Xorg Tainted: G        W  OE     5.0.0-38-lowlatency #41-Ubuntu
Jan 14 18:07:17 HP kernel: [   58.931579] Hardware name: Hewlett-Packard HP Compaq 8200 Elite SFF PC/1495, BIOS J01 v02.28 03/24/2015
Jan 14 18:07:17 HP kernel: [   58.931580] Call Trace:
Jan 14 18:07:17 HP kernel: [   58.931587]  dump_stack+0x6d/0x9a
Jan 14 18:07:17 HP kernel: [   58.931590]  __schedule_bug.cold.81+0x5/0x1f
Jan 14 18:07:17 HP kernel: [   58.931593]  __schedule+0x562/0x8a0
Jan 14 18:07:17 HP kernel: [   58.931595]  ? bit_wait_timeout+0xa0/0xa0
Jan 14 18:07:17 HP kernel: [   58.931597]  schedule+0x33/0x80
Jan 14 18:07:17 HP kernel: [   58.931599]  io_schedule+0x16/0x40
Jan 14 18:07:17 HP kernel: [   58.931600]  bit_wait_io+0x11/0x50
Jan 14 18:07:17 HP kernel: [   58.931602]  __wait_on_bit+0x7b/0x90
Jan 14 18:07:17 HP kernel: [   58.931604]  out_of_line_wait_on_bit+0x90/0xb0
Jan 14 18:07:17 HP kernel: [   58.931607]  ? init_wait_var_entry+0x50/0x50
Jan 14 18:07:17 HP kernel: [   58.931610]  __wait_on_buffer+0x27/0x30
Jan 14 18:07:17 HP kernel: [   58.931613]  ext4_find_entry+0x368/0x530
Jan 14 18:07:17 HP kernel: [   58.931618]  ? d_alloc_parallel+0x249/0x500
Jan 14 18:07:17 HP kernel: [   58.931619]  ? __d_lookup+0x81/0x150
Jan 14 18:07:17 HP kernel: [   58.931622]  ext4_lookup+0x79/0x220
Jan 14 18:07:17 HP kernel: [   58.931624]  path_openat+0x922/0x1570
Jan 14 18:07:17 HP kernel: [   58.931643]  ? drm_ioctl_kernel+0xad/0xf0 [drm]
Jan 14 18:07:17 HP kernel: [   58.931646]  ? _copy_from_user+0x60/0x60
Jan 14 18:07:17 HP kernel: [   58.931649]  do_filp_open+0x93/0x100
Jan 14 18:07:17 HP kernel: [   58.931652]  ? strncpy_from_user+0x57/0x1c0
Jan 14 18:07:17 HP kernel: [   58.931654]  ? __alloc_fd+0xb2/0x150
Jan 14 18:07:17 HP kernel: [   58.931657]  do_sys_open+0x177/0x2a0
Jan 14 18:07:17 HP kernel: [   58.931660]  __x64_sys_openat+0x20/0x30
Jan 14 18:07:17 HP kernel: [   58.931663]  do_syscall_64+0x5a/0x110
Jan 14 18:07:17 HP kernel: [   58.931665]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
Jan 14 18:07:17 HP kernel: [   58.931667] RIP: 0033:0x7f28ec49355e
Jan 14 18:07:17 HP kernel: [   58.931669] Code: 89 54 24 08 e8 a3 f4 ff ff 8b 74 24 0c 48 8b 3c 24 41 89 c0 44 8b 54 24 08 b8 01 01 00 00 89 f2 48 89 fe bf 9c ff ff ff 0f 05 <48> 3d 00 f0 ff ff 77 30 44 89 c7 89 44 24 08 e8 ce f4 ff ff 8b 44
Jan 14 18:07:17 HP kernel: [   58.931670] RSP: 002b:00007ffeae5a6cc0 EFLAGS: 00003293 ORIG_RAX: 0000000000000101
Jan 14 18:07:17 HP kernel: [   58.931672] RAX: ffffffffffffffda RBX: 000056244fff9380 RCX: 00007f28ec49355e
Jan 14 18:07:17 HP kernel: [   58.931673] RDX: 0000000000080000 RSI: 00005624507f7100 RDI: 00000000ffffff9c
Jan 14 18:07:17 HP kernel: [   58.931674] RBP: 00007ffeae5a6eb8 R08: 0000000000000000 R09: 00000000ffffffff
Jan 14 18:07:17 HP kernel: [   58.931675] R10: 0000000000000000 R11: 0000000000003293 R12: 00005624507f7100
Jan 14 18:07:17 HP kernel: [   58.931676] R13: 0000562450766944 R14: 000056244fff9380 R15: 0000000000000002
Jan 14 18:07:34 HP kernel: [   76.646205] nf_conntrack: default automatic helper assignment has been turned off for security reasons and CT-based  firewall rule not found. Use the iptables CT target to attach helpers instead.

```

Elsewhere, I noted a message stating AMD CPUs are affected by this problem and advising to include "mds=full,nosmt" option on grub command line which I have already done but these messages haven't gone away.

I have no clue as to what this could be related to, so would appreciate if anyone can comment on this.


Many thanks.

EDIT : forgot to mention that apart from slightly slower boot time, so far I have not found any issues with the system operations.

---

### Post by CatKiller on 2020-01-14
> **gdesilva said:**
> I have no clue as to what this could be related to, so would appreciate if anyone can comment on this.

It's exactly what it says it is: a warning about a bug. Atomic operations shouldn't be subjected to a scheduler. I expect that the generic kernel doesn't use as many atomic operations as the lowlatency kernel does. 

If you were experiencing issues you could boot into an older kernel to avoid them, but you say that you aren't. I'm sure it'll get fixed in an update at some point.

---

### Post by gdesilva on 2020-01-14
@CatKiller, many thanks for shedding some light on this.

---

### Post by karoo2 on 2020-03-23
I have Ubuntu Studio 19.04.  When I tried to upgrade to 19.10 a couple of months ago, I clicked the button and absolutely nothing happened.  (I had shutdown all programs and whatnot before trying to update, so there were no processes running as far as I know.)  But ever since then my system has slowed and often everything just freezes with the hard drive/fan working overtime.  If I shut down or restart the machine, I get pages of "scheduling while atomic" error messages, but it goes by so fast that I can't screenshot it or anything and my system is shutting down anyway, so there's no way to capture this behaviour.

I have tried to upgrade to 19.10 a couple of times since the first time, but nothing happens :-(

I don't know if this is related, but when the software updater shows me the updateable stuff, there is Calf Plugin pack for Jack, but I cannot update it (the checkmark will not take) ever since I updated from 18.10 to 19.04.  I don't use it, but I thought there might be problems associated with it.

Thank you for your time.

---

### Post by mörgæs on 2020-03-23
I guess the fastest and most secure solution is a fresh install of 19.10. When support runs out in July then another fresh install of 20.04, no upgrades.

---

### Post by karoo2 on 2020-03-23
Thank you for your answer, mörgæs.  I think then I'll just wait for 20.04 and do a fresh install then.

---

### Post by karoo2 on 2020-03-23
Or, could I try a dist-upgrade?  Might that work, or would it more likely pile more problems on top of the pile I already have?

---

### Post by mörgæs on 2020-03-23
```
sudo apt dist-upgrade
``` updates all packages including kernel within the same release number. In spite of the name it does not upgrade to next release.

I run the command after ```
sudo apt update
``` every day. 

The two commands are safe to run but I doubt that they solve your problem.

---

### Post by karoo2 on 2020-03-24
Ah, I see.  Thank you again for your help.  I will wait for 20.04 then.

---

### Post by mörgæs on 2020-03-24
If you are running 19.04 I recommend that you install 19.10 right away. 19.04 has not received security updates since January.

---

