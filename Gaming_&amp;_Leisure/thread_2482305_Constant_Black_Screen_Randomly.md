---
title: "Constant Black Screen Randomly"
date: 2022-12-27
forum: Gaming &amp; Leisure
---

### Post by jebsamir24 on 2022-12-27
Hi all, 

I have been getting constant black screens at random intervals when either playing games or just browsing the internet. The screen would turn black but there would still be sound playing. I cannot open a separate TTY at all. Below are the details for my hardware configurations and also the logs from "journalctl -k -b 1" of the most recent crash

Motherboard: ASROCK B550M Phantom Gaming 4
CPU: AMD Ryzen 5 5600G
GPU: MSI Radeon RX6700XT
RAM: Hyperx 16GB x 2
Storage: 2 SSD (1 NVME, 1 SATA), 2 HDD

```

Dis 28 04:26:18 poopies kernel: snd_hda_intel 0000:03:00.1: Unable to change power state from D3hot to D0, device inaccessible
Dis 28 04:26:18 poopies kernel: snd_hda_intel 0000:03:00.1: CORB reset timeout#2, CORBRP = 65535
Dis 28 04:26:28 poopies kernel: [drm:amdgpu_job_timedout [amdgpu]] *ERROR* ring gfx_0.0.0 timeout, signaled seq=5980329, emitted seq=5980331
Dis 28 04:26:28 poopies kernel: [drm:amdgpu_job_timedout [amdgpu]] *ERROR* Process information: process InsurgencyClien pid 3794 thread dxvk-submit pid 3900
Dis 28 04:26:28 poopies kernel: amdgpu 0000:03:00.0: amdgpu: GPU reset begin!
Dis 28 04:26:28 poopies kernel: amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:41 param:0x00000000 message:DisallowGfxOff?
Dis 28 04:26:28 poopies kernel: amdgpu 0000:03:00.0: amdgpu: Failed to disable gfxoff!
Dis 28 04:26:28 poopies kernel: [drm:dc_dmub_srv_wait_idle [amdgpu]] *ERROR* Error waiting for DMUB idle: status=5
Dis 28 04:26:28 poopies kernel: [drm] REG_WAIT timeout 1us * 1000 tries - dcn20_dpp_pg_control line:438
Dis 28 04:26:28 poopies kernel: [drm] REG_WAIT timeout 1us * 1000 tries - dcn20_hubp_pg_control line:512
Dis 28 04:26:28 poopies kernel: ------------[ cut here ]------------
Dis 28 04:26:28 poopies kernel: amdgpu 0000:03:00.0: drm_WARN_ON_ONCE(cur_vblank != vblank->last)
Dis 28 04:26:28 poopies kernel: WARNING: CPU: 11 PID: 4290 at drivers/gpu/drm/drm_vblank.c:354 drm_update_vblank_count+0x30f/0x3e0 [drm]
Dis 28 04:26:28 poopies kernel: Modules linked in: rfcomm snd_seq_dummy snd_hrtimer cmac algif_hash algif_skcipher af_alg bnep binfmt_misc nls_iso8859_1 amdgpu intel_rapl_msr snd_hda_codec_realtek snd_hda_codec_generic intel_rapl_common ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg iommu_v2 snd_intel_sdw_acpi snd_usb_audio gpu_sched snd_hda_codec drm_ttm_helper snd_usbmidi_lib snd_hda_core ttm btusb mc snd_hwdep edac_mce_amd btrtl drm_display_helper snd_pcm btbcm cec btintel kvm_amd snd_seq_midi rc_core btmtk snd_seq_midi_event drm_kms_helper kvm i2c_algo_bit snd_rawmidi snd_seq fb_sys_fops bluetooth syscopyarea crct10dif_pclmul sysfillrect ghash_clmulni_intel snd_seq_device sysimgblt snd_timer aesni_intel ecdh_generic joydev input_leds crypto_simd snd ecc cryptd soundcore rapl k10temp ccp wmi_bmof mac_hid msr parport_pc ppdev lp parport pstore_blk ramoops drm reed_solomon pstore_zone efi_pstore ip_tables x_tables autofs4 hid_generic r8169 usbhid hid crc32_pclmul nvme realtek ahci
Dis 28 04:26:28 poopies kernel:  nvme_core i2c_piix4 xhci_pci libahci xhci_pci_renesas wmi video gpio_amdpt
Dis 28 04:26:28 poopies kernel: CPU: 11 PID: 4290 Comm: kworker/u64:3 Not tainted 5.19.0-26-generic #27-Ubuntu
Dis 28 04:26:28 poopies kernel: Hardware name: To Be Filled By O.E.M. B550M Phantom Gaming 4/B550M Phantom Gaming 4, BIOS P2.10 10/19/2022
Dis 28 04:26:28 poopies kernel: Workqueue: events_unbound commit_work [drm_kms_helper]
Dis 28 04:26:28 poopies kernel: RIP: 0010:drm_update_vblank_count+0x30f/0x3e0 [drm]
Dis 28 04:26:28 poopies kernel: Code: 48 8b 5f 50 48 85 db 75 03 48 8b 1f e8 fa 2d 1a f2 48 c7 c1 50 e5 3f c0 48 89 da 48 c7 c7 60 1f 40 c0 48 89 c6 e8 26 f8 67 f2 <0f> 0b e9 3f fe ff ff 48 8b 4d c8 e9 25 fe ff ff 31 ff 48 85 db 74
Dis 28 04:26:28 poopies kernel: RSP: 0018:ffffb24c0131f9a0 EFLAGS: 00010046
Dis 28 04:26:28 poopies kernel: RAX: 0000000000000000 RBX: ffff9ff681366390 RCX: 0000000000000000
Dis 28 04:26:28 poopies kernel: RDX: 0000000000000000 RSI: 0000000000000000 RDI: 0000000000000000
Dis 28 04:26:28 poopies kernel: RBP: ffffb24c0131f9f0 R08: 0000000000000000 R09: 0000000000000000
Dis 28 04:26:28 poopies kernel: R10: 0000000000000000 R11: 0000000000000000 R12: 0000000000000000
Dis 28 04:26:28 poopies kernel: R13: 0000000000000000 R14: 0000000000000003 R15: ffff9ff69ae38828
Dis 28 04:26:28 poopies kernel: FS:  0000000000000000(0000) GS:ffff9ffd9e4c0000(0000) knlGS:0000000000000000
Dis 28 04:26:28 poopies kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Dis 28 04:26:28 poopies kernel: CR2: 000000002836b000 CR3: 000000019106e000 CR4: 0000000000750ee0
Dis 28 04:26:28 poopies kernel: PKRU: 55555554
Dis 28 04:26:28 poopies kernel: Call Trace:
Dis 28 04:26:28 poopies kernel:  <TASK>
Dis 28 04:26:28 poopies kernel:  drm_vblank_enable+0x172/0x1b0 [drm]
Dis 28 04:26:28 poopies kernel:  drm_vblank_get+0xb7/0x100 [drm]
Dis 28 04:26:28 poopies kernel:  drm_crtc_vblank_get+0x17/0x30 [drm]
Dis 28 04:26:28 poopies kernel:  amdgpu_dm_commit_planes+0xc03/0x11d0 [amdgpu]
Dis 28 04:26:28 poopies kernel:  amdgpu_dm_atomic_commit_tail+0xcc7/0x1460 [amdgpu]
Dis 28 04:26:28 poopies kernel:  ? load_balance+0x57c/0x8e0
Dis 28 04:26:28 poopies kernel:  ? __slab_free+0xf1/0x310
Dis 28 04:26:28 poopies kernel:  ? __slab_free+0xf1/0x310
Dis 28 04:26:28 poopies kernel:  ? update_load_avg+0x82/0x7b0
Dis 28 04:26:28 poopies kernel:  ? newidle_balance+0x325/0x4b0
Dis 28 04:26:28 poopies kernel:  ? __wait_for_common+0x161/0x1a0
Dis 28 04:26:28 poopies kernel:  ? usleep_range_state+0xa0/0xa0
Dis 28 04:26:28 poopies kernel:  ? wait_for_completion_timeout+0x1d/0x30
Dis 28 04:26:28 poopies kernel:  commit_tail+0xc2/0x190 [drm_kms_helper]
Dis 28 04:26:28 poopies kernel:  commit_work+0x12/0x20 [drm_kms_helper]
Dis 28 04:26:28 poopies kernel:  process_one_work+0x225/0x400
Dis 28 04:26:28 poopies kernel:  worker_thread+0x50/0x3e0
Dis 28 04:26:28 poopies kernel:  ? rescuer_thread+0x3c0/0x3c0
Dis 28 04:26:28 poopies kernel:  kthread+0xe9/0x110
Dis 28 04:26:28 poopies kernel:  ? kthread_complete_and_exit+0x20/0x20
Dis 28 04:26:28 poopies kernel:  ret_from_fork+0x22/0x30
Dis 28 04:26:28 poopies kernel:  </TASK>
Dis 28 04:26:28 poopies kernel: ---[ end trace 0000000000000000 ]---
Dis 28 04:26:28 poopies kernel: [drm:dcn20_wait_for_blank_complete [amdgpu]] *ERROR* DC: failed to blank crtc!
Dis 28 04:26:28 poopies kernel: [drm:psp_ring_cmd_submit [amdgpu]] *ERROR* ring_buffer_start = 0000000025a75376; ring_buffer_end = 00000000242a228c; write_frame = 000000004e26a975
Dis 28 04:26:28 poopies kernel: [drm:psp_ring_cmd_submit [amdgpu]] *ERROR* write_frame is pointing to address out of bounds
Dis 28 04:26:28 poopies kernel: [drm] REG_WAIT timeout 10us * 10020 tries - enc1_stream_encoder_dp_blank line:945
Dis 28 04:26:28 poopies kernel: [drm:dc_dmub_srv_wait_idle [amdgpu]] *ERROR* Error waiting for DMUB idle: status=5
Dis 28 04:26:29 poopies kernel: [drm] REG_WAIT timeout 1us * 100000 tries - optc1_disable_crtc line:533
Dis 28 04:26:29 poopies kernel: amdgpu 0000:03:00.0: [drm:amdgpu_ring_test_helper [amdgpu]] *ERROR* ring kiq_2.1.0 test failed (-110)
Dis 28 04:26:29 poopies kernel: [drm:gfx_v10_0_hw_fini [amdgpu]] *ERROR* KGQ disable failed
Dis 28 04:26:29 poopies kernel: [drm:gfx_v10_0_cp_gfx_enable.isra.0 [amdgpu]] *ERROR* failed to halt cp gfx
Dis 28 04:26:29 poopies kernel: amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:7 param:0x00000000 message:DisableAllSmuFeatures?
Dis 28 04:26:29 poopies kernel: amdgpu 0000:03:00.0: amdgpu: Failed to disable smu features.
Dis 28 04:26:29 poopies kernel: amdgpu 0000:03:00.0: amdgpu: Fail to disable dpm features!
Dis 28 04:26:29 poopies kernel: [drm:amdgpu_device_ip_suspend_phase2 [amdgpu]] *ERROR* suspend of IP block <smu> failed -121
Dis 28 04:26:29 poopies kernel: [drm:psp_ring_cmd_submit [amdgpu]] *ERROR* ring_buffer_start = 0000000025a75376; ring_buffer_end = 00000000242a228c; write_frame = 000000004e26a975
Dis 28 04:26:29 poopies kernel: [drm:psp_ring_cmd_submit [amdgpu]] *ERROR* write_frame is pointing to address out of bounds
Dis 28 04:26:29 poopies kernel: [drm:psp_suspend [amdgpu]] *ERROR* Failed to terminate hdcp ta
Dis 28 04:26:29 poopies kernel: [drm:amdgpu_device_ip_suspend_phase2 [amdgpu]] *ERROR* suspend of IP block <psp> failed -22
Dis 28 04:26:29 poopies kernel: CPU: 2 PID: 4533 Comm: kworker/u64:0 Tainted: G        W         5.19.0-26-generic #27-Ubuntu
Dis 28 04:26:29 poopies kernel: Hardware name: To Be Filled By O.E.M. B550M Phantom Gaming 4/B550M Phantom Gaming 4, BIOS P2.10 10/19/2022
Dis 28 04:26:29 poopies kernel: Workqueue: amdgpu-reset-dev drm_sched_job_timedout [gpu_sched]
Dis 28 04:26:29 poopies kernel: Call Trace:
Dis 28 04:26:29 poopies kernel:  <TASK>
Dis 28 04:26:29 poopies kernel:  show_stack+0x4e/0x61
Dis 28 04:26:29 poopies kernel:  dump_stack_lvl+0x4a/0x6d
Dis 28 04:26:29 poopies kernel:  dump_stack+0x10/0x18
Dis 28 04:26:29 poopies kernel:  amdgpu_do_asic_reset+0x2b/0x45e [amdgpu]
Dis 28 04:26:29 poopies kernel:  amdgpu_device_gpu_recover_imp.cold+0x748/0x7f0 [amdgpu]
Dis 28 04:26:29 poopies kernel:  amdgpu_job_timedout+0x196/0x1d0 [amdgpu]
Dis 28 04:26:29 poopies kernel:  ? finish_task_switch.isra.0+0x85/0x290
Dis 28 04:26:29 poopies kernel:  drm_sched_job_timedout+0x70/0x120 [gpu_sched]
Dis 28 04:26:29 poopies kernel:  process_one_work+0x225/0x400
Dis 28 04:26:29 poopies kernel:  worker_thread+0x50/0x3e0
Dis 28 04:26:29 poopies kernel:  ? rescuer_thread+0x3c0/0x3c0
Dis 28 04:26:29 poopies kernel:  kthread+0xe9/0x110
Dis 28 04:26:29 poopies kernel:  ? kthread_complete_and_exit+0x20/0x20
Dis 28 04:26:29 poopies kernel:  ret_from_fork+0x22/0x30
Dis 28 04:26:29 poopies kernel:  </TASK>
Dis 28 04:26:29 poopies kernel: amdgpu 0000:03:00.0: amdgpu: MODE1 reset
Dis 28 04:26:29 poopies kernel: amdgpu 0000:03:00.0: amdgpu: GPU mode1 reset
Dis 28 04:26:29 poopies kernel: amdgpu 0000:03:00.0: amdgpu: GPU smu mode1 reset
Dis 28 04:26:29 poopies kernel: amdgpu 0000:03:00.0: amdgpu: SMU: response:0xFFFFFFFF for index:48 param:0x00000000 message:Mode1Reset?
Dis 28 04:26:29 poopies kernel: amdgpu 0000:03:00.0: amdgpu: GPU mode1 reset failed
Dis 28 04:26:29 poopies kernel: amdgpu 0000:03:00.0: amdgpu: ASIC reset failed with error, -121 for drm dev, 0000:03:00.0
Dis 28 04:26:40 poopies kernel: amdgpu 0000:03:00.0: amdgpu: GPU reset succeeded, trying to resume
Dis 28 04:26:40 poopies kernel: [drm] PCIE GART of 512M enabled (table at 0x00000080012FC000).
Dis 28 04:26:40 poopies kernel: [drm] VRAM is lost due to GPU reset!
Dis 28 04:26:40 poopies kernel: [drm] PSP is resuming...
Dis 28 04:26:40 poopies kernel: [drm:psp_hw_start [amdgpu]] *ERROR* PSP create ring failed!
Dis 28 04:26:40 poopies kernel: [drm:psp_resume [amdgpu]] *ERROR* PSP resume failed
Dis 28 04:26:40 poopies kernel: [drm:amdgpu_device_fw_loading [amdgpu]] *ERROR* resume of IP block <psp> failed -62
Dis 28 04:26:40 poopies kernel: [drm] Skip scheduling IBs!
Dis 28 04:26:40 poopies kernel: [drm] Skip scheduling IBs!
Dis 28 04:26:40 poopies kernel: [drm] Skip scheduling IBs!
Dis 28 04:26:40 poopies kernel: amdgpu 0000:03:00.0: amdgpu: GPU reset(2) failed
Dis 28 04:26:40 poopies kernel: [drm] Skip scheduling IBs!
Dis 28 04:26:40 poopies kernel: [drm] Skip scheduling IBs!
Dis 28 04:26:40 poopies kernel: [drm] Skip scheduling IBs!
Dis 28 04:26:40 poopies kernel: [drm] Skip scheduling IBs!
Dis 28 04:26:40 poopies kernel: [drm] Skip scheduling IBs!
Dis 28 04:26:40 poopies kernel: [drm] Skip scheduling IBs!
Dis 28 04:26:40 poopies kernel: [drm] Skip scheduling IBs!
Dis 28 04:26:40 poopies kernel: [drm] Skip scheduling IBs!
Dis 28 04:26:40 poopies kernel: snd_hda_intel 0000:03:00.1: Unable to change power state from D3cold to D0, device inaccessible
Dis 28 04:26:40 poopies kernel: amdgpu_cs_ioctl: 1 callbacks suppressed
Dis 28 04:26:40 poopies kernel: [drm:amdgpu_cs_ioctl [amdgpu]] *ERROR* Failed to initialize parser -125!
Dis 28 04:26:40 poopies kernel: snd_hda_intel 0000:03:00.1: CORB reset timeout#2, CORBRP = 65535
Dis 28 04:26:40 poopies kernel: amdgpu 0000:03:00.0: amdgpu: GPU reset end with ret = -62
Dis 28 04:26:40 poopies kernel: [drm:amdgpu_job_timedout [amdgpu]] *ERROR* GPU Recovery Failed: -62
Dis 28 04:29:04 poopies kernel: [drm:amdgpu_job_timedout [amdgpu]] *ERROR* ring sdma0 timeout, signaled seq=1870, emitted seq=1872
Dis 28 04:29:04 poopies kernel: [drm:amdgpu_job_timedout [amdgpu]] *ERROR* Process information: process  pid 0 thread  pid 0
Dis 28 04:29:04 poopies kernel: amdgpu 0000:03:00.0: amdgpu: GPU reset begin!
Dis 28 04:30:06 poopies kernel: INFO: task kworker/u64:3:4290 blocked for more than 120 seconds.
Dis 28 04:30:06 poopies kernel:       Tainted: G        W         5.19.0-26-generic #27-Ubuntu
Dis 28 04:30:06 poopies kernel: "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Dis 28 04:30:06 poopies kernel: task:kworker/u64:3   state:D stack:    0 pid: 4290 ppid:     2 flags:0x00004000
Dis 28 04:30:06 poopies kernel: Workqueue: events_unbound commit_work [drm_kms_helper]
Dis 28 04:30:06 poopies kernel: Call Trace:
Dis 28 04:30:06 poopies kernel:  <TASK>
Dis 28 04:30:06 poopies kernel:  __schedule+0x24b/0x5f0
Dis 28 04:30:06 poopies kernel:  schedule+0x63/0x110
Dis 28 04:30:06 poopies kernel:  schedule_preempt_disabled+0x15/0x30
Dis 28 04:30:06 poopies kernel:  __mutex_lock.constprop.0+0x516/0x790
Dis 28 04:30:06 poopies kernel:  __mutex_lock_slowpath+0x13/0x20
Dis 28 04:30:06 poopies kernel:  mutex_lock+0x3c/0x50
Dis 28 04:30:06 poopies kernel:  amdgpu_dm_commit_planes+0x805/0x11d0 [amdgpu]
Dis 28 04:30:06 poopies kernel:  amdgpu_dm_atomic_commit_tail+0xcc7/0x1460 [amdgpu]
Dis 28 04:30:06 poopies kernel:  ? load_balance+0x57c/0x8e0
Dis 28 04:30:06 poopies kernel:  ? __slab_free+0xf1/0x310
Dis 28 04:30:06 poopies kernel:  ? __slab_free+0xf1/0x310
Dis 28 04:30:06 poopies kernel:  ? update_load_avg+0x82/0x7b0
Dis 28 04:30:06 poopies kernel:  ? newidle_balance+0x325/0x4b0
Dis 28 04:30:06 poopies kernel:  ? __wait_for_common+0x161/0x1a0
Dis 28 04:30:06 poopies kernel:  ? usleep_range_state+0xa0/0xa0
Dis 28 04:30:06 poopies kernel:  ? wait_for_completion_timeout+0x1d/0x30
Dis 28 04:30:06 poopies kernel:  commit_tail+0xc2/0x190 [drm_kms_helper]
Dis 28 04:30:06 poopies kernel:  commit_work+0x12/0x20 [drm_kms_helper]
Dis 28 04:30:06 poopies kernel:  process_one_work+0x225/0x400
Dis 28 04:30:06 poopies kernel:  worker_thread+0x50/0x3e0
Dis 28 04:30:06 poopies kernel:  ? rescuer_thread+0x3c0/0x3c0
Dis 28 04:30:06 poopies kernel:  kthread+0xe9/0x110
Dis 28 04:30:06 poopies kernel:  ? kthread_complete_and_exit+0x20/0x20
Dis 28 04:30:06 poopies kernel:  ret_from_fork+0x22/0x30
Dis 28 04:30:06 poopies kernel:  </TASK>

```

---

### Post by lacrosby on 2023-01-26
[SIZE=4][FONT=arial]What Ubuntu version are you using?

lsb_release -a

What drivers are you using? 

[COLOR=#444444]glxinfo -B[/COLOR]

Are they the out of the box ones or did you using the ones from AMD.

[https://www.amd.com/en/support/linux-drivers](https://www.amd.com/en/support/linux-drivers)

You can try to update the drivers by following:

[https://www.amd.com/en/support/kb/faq/gpu-643](https://www.amd.com/en/support/kb/faq/gpu-643)
[/FONT][/SIZE]

---

### Post by mikey21 on 2023-02-02
I had a similar problem and it turned out to be a graphics card malfunction.

---

### Post by bjorn-helgaas on 2023-02-02
If you can reproduce this on a current upstream kernel, e.g., v6.1, you'll likely get more attention by posting to the linux email lists and maintainers, e.g., [email]amd-gfx@lists.freedesktop.org[/email] [email]dri-devel@lists.freedesktop.org[/email] [email]linux-kernel@vger.kernel.org[/email] Alex Deucher <alexander.deucher@amd.com> Christian König <christian.koenig@amd.com> Xinhui Pan <Xinhui.Pan@amd.com>

---

