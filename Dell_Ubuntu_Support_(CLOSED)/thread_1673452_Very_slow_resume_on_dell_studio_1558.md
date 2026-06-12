---
title: "Very slow resume on dell studio 1558"
date: 2011-01-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rackstar on 2011-01-22
Hey,

I'm still suffering from this bug. I did a fresh install, and resuming is sometimes instantly, but mostly takes about 2 minutes.

This is really really annoying, and I'm fed up with it. However, I do not have the skills (yet) to debug this problem. I'm computer literate though, however I have no experience with this situation.

Any ideas on how to tackle this problem? Which logs should I consult?

It could be that I'm suffering from this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658307](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658307) but this bug didn't pick up any attention.

Thanks in advance!

---

### Post by Rackstar on 2011-01-23
Ok, here goes attempt 1435 into fixing this issue.

I need some advice on the ethics of Launchpad:
- I'm commenting on a bug, thinking it is about the same issue I'm having, but I'm not sure. Should I file a new bug? As this bug isn't getting any attention
- The bug is affecting the package "linux(Ubuntu)", which is way too broad. Should I add packages, of which I think is more precise? Or should I leave this up to the big guys?

Further, I have debugged my issue somewhat further, using the command from [https://wiki.ubuntu.com/DebuggingKernelSuspend:](https://wiki.ubuntu.com/DebuggingKernelSuspend:)
```
sudo sh -c "sync; echo 1 > /sys/power/pm_trace; pm-suspend"
```. I've added this as an attachment. The last suspend triggered the slow resume, so that would be the most interesting one.

If someone could help me out on this one? Am I in the wrong subforum? If so, please move this post to the appropriate section.

```
[35209.495233] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[35209.851585] EXT4-fs (sda5): re-mounted. Opts: commit=0
[35213.993039] PM: Syncing filesystems ... done.
[35214.049252] PM: Preparing system for mem sleep
[35214.049266] Freezing user space processes ... (elapsed 0.01 seconds) done.
[35214.061012] Freezing remaining freezable tasks ... (elapsed 0.02 seconds) done.
[35214.090924] PM: Entering mem sleep
[35214.091020] Suspending console(s) (use no_console_suspend to debug)
[35214.091454] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[35214.100251] sd 0:0:0:0: [sda] Stopping disk
[35214.148442] ACPI handle has no context!
[35214.149168] HDA Intel 0000:02:00.1: PCI INT B disabled
[35214.150874] wl 0000:04:00.0: PCI INT A disabled
[35214.151045] ACPI handle has no context!
[35214.151077] sdhci-pci 0000:07:00.0: PCI INT A disabled
[35214.151149] [fglrx] IRQ 50 Disabled
[35214.151228] ehci_hcd 0000:00:1d.0: PCI INT A disabled
[35214.151260] [fglrx] Preparing suspend fglrx in kernel.
[35214.151399] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[35214.159967] async/17: page allocation failure. order:10, mode:0x4020
[35214.159970] Pid: 6868, comm: async/17 Tainted: P            2.6.35-24-generic #42-Ubuntu
[35214.159972] Call Trace:
[35214.159980]  [<ffffffff81108476>] __alloc_pages_slowpath+0x4b6/0x5a0
[35214.159983]  [<ffffffff811086fa>] __alloc_pages_nodemask+0x19a/0x1f0
[35214.159987]  [<ffffffff8113a75a>] alloc_pages_current+0x9a/0x100
[35214.159989]  [<ffffffff811075be>] __get_free_pages+0xe/0x50
[35214.159991]  [<ffffffff81143f45>] __kmalloc+0x145/0x1c0
[35214.160032]  [<ffffffffa011bbef>] ? hal_wait_CPDMA_idle+0xf/0x30 [fglrx]
[35214.160049]  [<ffffffffa00f3bfe>] KCL_MEM_SmallBufferAllocAtomic+0x1e/0x20 [fglrx]
[35214.160068]  [<ffffffffa0103c23>] firegl_save_fb+0x233/0x360 [fglrx]
[35214.160088]  [<ffffffffa0102db5>] ? firegl_pm_save_framebuffer+0x1f5/0x280 [fglrx]
[35214.160108]  [<ffffffffa010570d>] ? firegl_cail_powerdown+0x8d/0x200 [fglrx]
[35214.160122]  [<ffffffffa00ef1f7>] ? fglrx_pci_suspend+0x87/0x150 [fglrx]
[35214.160126]  [<ffffffff81036db9>] ? default_spin_lock_flags+0x9/0x10
[35214.160129]  [<ffffffff812d7a06>] ? pci_legacy_suspend+0x46/0xe0
[35214.160131]  [<ffffffff812d86e5>] ? pci_pm_suspend+0xd5/0x130
[35214.160134]  [<ffffffff8138d800>] ? dpm_wait_fn+0x0/0x20
[35214.160136]  [<ffffffff8138e3a6>] ? pm_op+0x176/0x1c0
[35214.160138]  [<ffffffff8138e758>] ? __device_suspend+0x108/0x180
[35214.160141]  [<ffffffff810702f0>] ? process_timeout+0x0/0x10
[35214.160144]  [<ffffffff81086da0>] ? async_thread+0x0/0xf0
[35214.160146]  [<ffffffff8138ea19>] ? async_suspend+0x29/0x70
[35214.160147]  [<ffffffff81086c7a>] ? run_one_entry+0x7a/0x1a0
[35214.160149]  [<ffffffff81086dfd>] ? async_thread+0x5d/0xf0
[35214.160151]  [<ffffffff81056890>] ? default_wake_function+0x0/0x20
[35214.160153]  [<ffffffff8107f1d6>] ? kthread+0x96/0xa0
[35214.160156]  [<ffffffff8100aee4>] ? kernel_thread_helper+0x4/0x10
[35214.160158]  [<ffffffff8107f140>] ? kthread+0x0/0xa0
[35214.160159]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
[35214.160161] Mem-Info:
[35214.160162] Node 0 DMA per-cpu:
[35214.160164] CPU    0: hi:    0, btch:   1 usd:   0
[35214.160165] CPU    1: hi:    0, btch:   1 usd:   0
[35214.160166] CPU    2: hi:    0, btch:   1 usd:   0
[35214.160167] CPU    3: hi:    0, btch:   1 usd:   0
[35214.160168] Node 0 DMA32 per-cpu:
[35214.160170] CPU    0: hi:  186, btch:  31 usd: 138
[35214.160171] CPU    1: hi:  186, btch:  31 usd:  58
[35214.160172] CPU    2: hi:  186, btch:  31 usd: 115
[35214.160173] CPU    3: hi:  186, btch:  31 usd: 134
[35214.160174] Node 0 Normal per-cpu:
[35214.160175] CPU    0: hi:  186, btch:  31 usd: 182
[35214.160177] CPU    1: hi:  186, btch:  31 usd: 176
[35214.160178] CPU    2: hi:  186, btch:  31 usd: 166
[35214.160179] CPU    3: hi:  186, btch:  31 usd: 148
[35214.160182] active_anon:252626 inactive_anon:167678 isolated_anon:0
[35214.160183]  active_file:117974 inactive_file:188970 isolated_file:0
[35214.160184]  unevictable:12 dirty:3 writeback:0 unstable:0
[35214.160184]  free:136227 slab_reclaimable:15894 slab_unreclaimable:6957
[35214.160185]  mapped:50564 shmem:2449 pagetables:9960 bounce:0
[35214.160186] Node 0 DMA free:15476kB min:28kB low:32kB high:40kB active_anon:0kB inactive_anon:0kB active_file:348kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15696kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:12kB slab_unreclaimable:8kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[35214.160193] lowmem_reserve[]: 0 2477 3865 3865
[35214.160195] Node 0 DMA32 free:525960kB min:5088kB low:6360kB high:7632kB active_anon:838688kB inactive_anon:288212kB active_file:246560kB inactive_file:442164kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:2536588kB mlocked:0kB dirty:36kB writeback:0kB mapped:62788kB shmem:5260kB slab_reclaimable:40376kB slab_unreclaimable:5996kB kernel_stack:1272kB pagetables:11244kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[35214.160201] lowmem_reserve[]: 0 0 1388 1388
[35214.160203] Node 0 Normal free:3472kB min:2852kB low:3564kB high:4276kB active_anon:171816kB inactive_anon:382500kB active_file:224988kB inactive_file:313716kB unevictable:48kB isolated(anon):0kB isolated(file):0kB present:1422080kB mlocked:48kB dirty:0kB writeback:0kB mapped:139468kB shmem:4536kB slab_reclaimable:23188kB slab_unreclaimable:21824kB kernel_stack:2600kB pagetables:28596kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[35214.160210] lowmem_reserve[]: 0 0 0 0
[35214.160211] Node 0 DMA: 1*4kB 0*8kB 1*16kB 1*32kB 1*64kB 2*128kB 1*256kB 1*512kB 2*1024kB 2*2048kB 2*4096kB = 15476kB
[35214.160216] Node 0 DMA32: 2342*4kB 2059*8kB 3918*16kB 5031*32kB 2792*64kB 564*128kB 70*256kB 5*512kB 3*1024kB 1*2048kB 0*4096kB = 526000kB
[35214.160220] Node 0 Normal: 868*4kB 0*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 3472kB
[35214.160225] 405310 total pagecache pages
[35214.160226] 95916 pages in swap cache
[35214.160227] Swap cache stats: add 227836, delete 131920, find 2447693/2452480
[35214.160228] Free swap  = 9891656kB
[35214.160229] Total swap = 10309628kB
[35214.162091] ACPI handle has no context!
[35214.171766] 1015792 pages RAM
[35214.171768] 85301 pages reserved
[35214.171768] 261411 pages shared
[35214.171769] 618598 pages non-shared
[35214.280800] HDA Intel 0000:00:1b.0: PCI INT A disabled
[35214.300488] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 149.398 msecs
[35214.404448] [fglrx] Suspending fglrx in kernel completed.
[35214.404450] [fglrx] Power down the ASIC .
[35214.404550] PM: suspend of drv:fglrx_pci dev:0000:02:00.0 complete after 253.946 msecs
[35214.404563] PM: suspend of drv:pcieport dev:0000:00:01.0 complete after 253.609 msecs
[35214.682411] PM: suspend of drv:sd dev:0:0:0:0 complete after 592.044 msecs
[35214.682472] PM: suspend of drv:scsi dev:target0:0:0 complete after 592.092 msecs
[35214.682492] PM: suspend of drv:scsi dev:host0 complete after 591.943 msecs
[35214.759679] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 609.649 msecs
[35214.759736] PM: suspend of drv: dev:pci0000:00 complete after 609.384 msecs
[35214.759750] PM: suspend of devices complete after 669.750 msecs
[35214.759758] PM: suspend devices took 0.680 seconds
[35214.759962] r8169 0000:09:00.0: PME# enabled
[35214.759973] r8169 0000:09:00.0: wake-up capability enabled by ACPI
[35214.819654] PM: late suspend of devices complete after 60.000 msecs
[35214.849643] ACPI: Preparing to enter system sleep state S3
[35214.850582] PM: Saving platform NVS memory
[35214.860413] Disabling non-boot CPUs ...
[35214.979260] CPU 1 is now offline
[35215.098995] CPU 2 is now offline
[35215.109104] Broke affinity for irq 9
[35215.109115] Broke affinity for irq 12
[35215.109158] Broke affinity for irq 50
[35215.218767] CPU 3 is now offline
[35215.218771] SMP alternatives: switching to UP code
[35215.223631] Extended CMOS year: 2000
[35215.223937] Back to C!
[35215.223941] PM: Restoring platform NVS memory
[35215.233263] CPU0: Thermal monitoring handled by SMI
[35215.233321] Extended CMOS year: 2000
[35215.233353] Enabling non-boot CPUs ...
[35215.233510] SMP alternatives: switching to SMP code
[35215.237764] Booting Node 0 Processor 1 APIC 0x4
[35215.398153] CPU1: Thermal monitoring handled by SMI
[35215.498425] CPU1 is up
[35215.498624] Booting Node 0 Processor 2 APIC 0x1
[35215.657680] CPU2: Thermal monitoring handled by SMI
[35215.778052] CPU2 is up
[35215.778311] Booting Node 0 Processor 3 APIC 0x5
[35215.937165] CPU3: Thermal monitoring handled by SMI
[35216.077705] CPU3 is up
[35216.079331] ACPI: Waking up from system sleep state S3
[35216.134216] pcieport 0000:00:01.0: restoring config space at offset 0xf (was 0x80100, writing 0x80105)
[35216.134222] pcieport 0000:00:01.0: restoring config space at offset 0x7 (was 0xf0, writing 0x60002020)
[35216.134224] pcieport 0000:00:01.0: restoring config space at offset 0x6 (was 0x0, writing 0x20200)
[35216.134227] pcieport 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[35216.134230] pcieport 0000:00:01.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[35216.134336] pci 0000:00:16.0: restoring config space at offset 0x1 (was 0x180002, writing 0x180006)
[35216.134428] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[35216.134445] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x4 (was 0x0, writing 0xf0b06000)
[35216.134452] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900102)
[35216.134551] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[35216.134568] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xdc000004, writing 0xf0b00004)
[35216.134573] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[35216.134578] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100102)
[35216.134677] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x40107)
[35216.134688] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0xa031a021)
[35216.134692] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xa010a000)
[35216.134697] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x20006060)
[35216.134701] pcieport 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0x30300)
[35216.134708] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[35216.134714] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[35216.134826] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x40205)
[35216.134837] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0xa051a041)
[35216.134842] pcieport 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xf050f050)
[35216.134846] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x0, writing 0x7070)
[35216.134851] pcieport 0000:00:1c.1: restoring config space at offset 0x6 (was 0x0, writing 0x40400)
[35216.134858] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[35216.134863] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[35216.134976] pcieport 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x4040a)
[35216.134987] pcieport 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xf011f001)
[35216.134992] pcieport 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xf060f060)
[35216.134996] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0x20000000, writing 0x20003030)
[35216.135001] pcieport 0000:00:1c.3: restoring config space at offset 0x6 (was 0x0, writing 0x60500)
[35216.135008] pcieport 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[35216.135014] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[35216.135126] pcieport 0000:00:1c.4: restoring config space at offset 0xf (was 0x100, writing 0x40107)
[35216.135137] pcieport 0000:00:1c.4: restoring config space at offset 0x9 (was 0x10001, writing 0xf031f021)
[35216.135141] pcieport 0000:00:1c.4: restoring config space at offset 0x8 (was 0x0, writing 0xf080f070)
[35216.135146] pcieport 0000:00:1c.4: restoring config space at offset 0x7 (was 0x20000000, writing 0x20004040)
[35216.135154] pcieport 0000:00:1c.4: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[35216.135160] pcieport 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[35216.135272] pcieport 0000:00:1c.5: restoring config space at offset 0xf (was 0x200, writing 0x40205)
[35216.135283] pcieport 0000:00:1c.5: restoring config space at offset 0x9 (was 0x10001, writing 0xf041f041)
[35216.135287] pcieport 0000:00:1c.5: restoring config space at offset 0x8 (was 0x0, writing 0xa090a060)
[35216.135292] pcieport 0000:00:1c.5: restoring config space at offset 0x7 (was 0x0, writing 0x5050)
[35216.135296] pcieport 0000:00:1c.5: restoring config space at offset 0x6 (was 0x0, writing 0x90900)
[35216.135303] pcieport 0000:00:1c.5: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[35216.135309] pcieport 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[35216.135418] ehci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[35216.135436] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x4 (was 0x0, writing 0xf0b06400)
[35216.135443] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900102)
[35216.135532] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x40000, writing 0x400ff)
[35216.135543] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[35216.135547] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
[35216.135551] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x228000f0)
[35216.135562] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[35216.135752] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[35216.135773] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[35216.135970] intel ips 0000:00:1f.6: restoring config space at offset 0xf (was 0x300, writing 0x30a)
[35216.135991] intel ips 0000:00:1f.6: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
[35216.136083] fglrx_pci 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x105)
[35216.136091] fglrx_pci 0000:02:00.0: restoring config space at offset 0x8 (was 0x1, writing 0x2001)
[35216.136095] fglrx_pci 0000:02:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xcfee0004)
[35216.136099] fglrx_pci 0000:02:00.0: restoring config space at offset 0x4 (was 0xc, writing 0xd000000c)
[35216.136102] fglrx_pci 0000:02:00.0: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[35216.136106] fglrx_pci 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x40100503)
[35216.136202] HDA Intel 0000:02:00.1: restoring config space at offset 0xf (was 0x2ff, writing 0x207)
[35216.136214] HDA Intel 0000:02:00.1: restoring config space at offset 0x4 (was 0x4, writing 0xcfedc004)
[35216.136217] HDA Intel 0000:02:00.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[35216.136221] HDA Intel 0000:02:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x40100103)
[35216.137648] wl 0000:04:00.0: restoring config space at offset 0xf (was 0x100, writing 0x107)
[35216.138740] wl 0000:04:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf0500004)
[35216.138924] wl 0000:04:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[35216.139199] wl 0000:04:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[35216.140524] sdhci-pci 0000:07:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[35216.140554] sdhci-pci 0000:07:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xf0700000)
[35216.140560] sdhci-pci 0000:07:00.0: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[35216.140568] sdhci-pci 0000:07:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[35216.140684] pci 0000:07:00.1: restoring config space at offset 0xf (was 0x200, writing 0x207)
[35216.140710] pci 0000:07:00.1: restoring config space at offset 0x4 (was 0x0, writing 0xf0800800)
[35216.140716] pci 0000:07:00.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[35216.140724] pci 0000:07:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[35216.140836] pci 0000:07:00.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
[35216.140862] pci 0000:07:00.2: restoring config space at offset 0x4 (was 0x0, writing 0xf0800c00)
[35216.140868] pci 0000:07:00.2: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[35216.140876] pci 0000:07:00.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[35216.140989] firewire_ohci 0000:07:00.3: restoring config space at offset 0xf (was 0x400, writing 0x40a)
[35216.141015] firewire_ohci 0000:07:00.3: restoring config space at offset 0x4 (was 0x0, writing 0xf0800000)
[35216.141021] firewire_ohci 0000:07:00.3: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[35216.141029] firewire_ohci 0000:07:00.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[35216.141207] r8169 0000:09:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x107)
[35216.141221] r8169 0000:09:00.0: restoring config space at offset 0x8 (was 0xc, writing 0xf040000c)
[35216.141227] r8169 0000:09:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xf040400c)
[35216.141233] r8169 0000:09:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x5001)
[35216.141238] r8169 0000:09:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[35216.141244] r8169 0000:09:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[35216.164649] PM: early resume of devices complete after 37.687 msecs
[35216.193206] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[35216.193213] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[35216.193306] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[35216.193312] HDA Intel 0000:00:1b.0: setting latency timer to 64
[35216.193353] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[35216.193784] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[35216.193789] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[35216.193881] pci 0000:00:1e.0: setting latency timer to 64
[35216.194023] ahci 0000:00:1f.2: setting latency timer to 64
[35216.194341] fglrx_pci 0000:02:00.0: setting latency timer to 64
[35216.198595] [fglrx] Power up the ASIC
[35216.198631] [fglrx] Preparing resume fglrx in kernel.
[35216.262974] [fglrx] Resuming fglrx in kernel completed.
[35216.263283] [fglrx] IRQ 50 Enabled
[35216.263369] HDA Intel 0000:02:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[35216.263374] HDA Intel 0000:02:00.1: setting latency timer to 64
[35216.263405] HDA Intel 0000:02:00.1: irq 49 for MSI/MSI-X
[35216.263654] wl 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[35216.263837] wl 0000:04:00.0: setting latency timer to 64
[35216.289701] sdhci-pci 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[35216.289704] sdhci-pci 0000:07:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[35216.289711] sdhci-pci 0000:07:00.0: setting latency timer to 64
[35216.546165] firewire_core: skipped bus generations, destroying all nodes
[35216.556154] ata5: SATA link down (SStatus 0 SControl 300)
[35216.566104] PM: resume of drv:firewire_ohci dev:0000:07:00.3 complete after 275.712 msecs
[35216.566260] r8169 0000:09:00.0: wake-up capability disabled by ACPI
[35216.566266] r8169 0000:09:00.0: PME# disabled
[35216.579793] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[35216.607126] ata2.00: configured for UDMA/100
[35216.825601] PM: resume of drv:usb dev:1-1 complete after 165.879 msecs
[35216.825944] sd 0:0:0:0: [sda] Starting disk
[35217.045257] firewire_core: rediscovered device fw0
[35218.514997] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[35218.536652] ata1.00: configured for UDMA/133
[35218.572163] PM: resume of drv:sd dev:0:0:0:0 complete after 1749.460 msecs
[35218.742041] PM: resume of drv:usb dev:2-1 complete after 169.396 msecs
[35218.822101] usb 1-1.4: reset high speed USB device using ehci_hcd and address 3
[35219.036505] PM: resume of drv:usb dev:1-1.4 complete after 294.687 msecs
[35219.301285] usb 2-1.1: reset low speed USB device using ehci_hcd and address 3
[35219.606352] PM: resume of drv:usb dev:2-1.1 complete after 570.558 msecs
[35219.626299] PM: resume of devices complete after 3467.928 msecs
[35219.626402] PM: resume devices took 3.470 seconds
[35219.626442] PM: Finishing wakeup.
[35219.626444] Restarting tasks ... done.
[35219.634963] video LNXVIDEO:00: Restoring backlight state
[35231.059369] eth1: no IPv6 routers present
[35231.682491] r8169 0000:09:00.0: eth0: link up
[35242.358603] eth0: no IPv6 routers present
[35292.989238] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[35303.456219] EXT4-fs (sda5): re-mounted. Opts: commit=0
```

Thanks!

---

### Post by Language on 2011-01-25
I have the same issue, with the same model of laptop. Sadly I found your post while googling for a solution, so I don't have much to add.

I have noticed that the slow resume seems to occur more frequently when I have something mounted via fuse (most frequently I use sshfs mounts).

Anyway, I have the same laptop, so if you or anybody else troubleshooting this issue would like me to try something, or provide logs, etc. I'd be more than happy to help. This is a frustrating issue and one of the only things keeping me from complete enjoyment of Ubuntu on my studio 1558.

edit: I'm running 10.04, 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux

---

### Post by teranex on 2011-01-28
I have the same laptop and had the same problem. However it seems to be caused by the propriety graphics drivers. Two weeks ago I disabled those (System > Administration > Additional Drivers) and now my laptop always resumes within seconds. A small inconvenience with this is that I can't enable Compiz anymore. A positive point however, is that i now have kernel mode setting enabled which din't work with the propriety drivers. Maybe give it a try, in case you are using that driver?

One other problem i'm still looking into is that my laptop freezes from time to time (with both propriety and as well as open drivers). My CPU seems to get very hot very quickly (never runs under 70 degrees C) so that might be the real cause..

---

### Post by raulfragoso on 2011-03-16
I have the Dell Studio 1735 model, and had the same thing happening during resume.

Here is the relevant information:

lsb_release -a:

```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

```

uname -a:

```
Linux raul-laptop 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 GNU/Linux

```

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
0d:00.0 Multimedia controller: Philips Semiconductors SAA7160 (rev 03)

```

But just like Rackstar have noticed, if I disable the fglrx (proprietary ATI) graphics driver, everything works fine. After following the [instructions here]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Suspend.2FHibernation") to disable compiz and adding the following to /etc/X11/xorg.conf:

```
Section "Extensions"
        Option        "Composite"        "Disable"
EndSection

Section "ServerFlags"
       Option  "AIGLX" "off" 
EndSection
```

Resume now happens almost instantaneously :) So if you don't care about not having fancy visual effects, I highly recommend going that route ;)

---

