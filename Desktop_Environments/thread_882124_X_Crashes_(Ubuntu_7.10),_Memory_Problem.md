---
title: "X Crashes (Ubuntu 7.10), Memory Problem?"
date: 2008-08-06
forum: Desktop Environments
---

### Post by Highlander4880 on 2008-08-06
Hello Folks,

I am new to this Forum but I already have some experience with Ubuntu (1.5 years) and linux (3 years).

The machine has 2 GBytes of Memory and is an AMD X2 3800+ with onboard NVidia Graphics.

I have a problem that sometimes my X breaks down. After that X restarts and I see the login screen but logging in leads to an error. Only restarting the machine helps. :confused:

I hope you can give a hint. There are no other known problems. Thanks a lot! :)
High.


The log shows the following:

One message before a lot of log messages appear is:
[SIZE="1"]
Aug  6 22:29:37 workhorse kernel: [ 9750.060000] Xorg invoked oom-killer: gfp_mask=0x2d0, order=0, oomkilladj=0
[/SIZE]

Then these messages appear, I left out some as they appear several times:
[SIZE="1"]
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] Normal per-cpu:
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] CPU    0: Hot: hi:  186, btch:  31 usd:  31   Cold: hi:   62, btch:  15 usd:  51
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] CPU    1: Hot: hi:  186, btch:  31 usd: 168   Cold: hi:   62, btch:  15 usd:  50
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] HighMem per-cpu:
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] CPU    0: Hot: hi:  186, btch:  31 usd:  67   Cold: hi:   62, btch:  15 usd:   2
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] CPU    1: Hot: hi:  186, btch:  31 usd: 164   Cold: hi:   62, btch:  15 usd:   7
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] Active:74856 inactive:14087 dirty:0 writeback:0 unstable:0
Aug  6 22:29:44 workhorse kernel: [ 9750.484000]  free:195872 slab:5233 mapped:15086 pagetables:521 bounce:0
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] DMA free:3544kB min:68kB low:84kB high:100kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unr
eclaimable? yes
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] lowmem_reserve[]: 0 873 1983
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] Normal free:3660kB min:3744kB low:4680kB high:5616kB active:468kB inactive:368kB present:894080kB pages_scan
ned:1449 all_unreclaimable? yes
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] lowmem_reserve[]: 0 0 8881
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] HighMem free:776284kB min:512kB low:1700kB high:2892kB active:298956kB inactive:55980kB present:1136844kB pa
ges_scanned:0 all_unreclaimable? no
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] lowmem_reserve[]: 0 0 0
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] DMA: 0*4kB 1*8kB 1*16kB 0*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3544kB
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] Normal: 1*4kB 1*8kB 6*16kB 0*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3628kB
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] HighMem: 5874*4kB 6268*8kB 5468*16kB 4133*32kB 2637*64kB 1196*128kB 287*256kB 47*512kB 8*1024kB 1*2048kB 13*
4096kB = 776264kB
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] Swap cache: add 5268, delete 130, find 0/3, race 0+0
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] Free swap  = 1931096kB
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] Total swap = 1951888kB
Aug  6 22:29:44 workhorse kernel: [ 9750.484000] Free swap:       1931096kB
Aug  6 22:29:44 workhorse kernel: [ 9750.488000] 515824 pages of RAM
Aug  6 22:29:44 workhorse kernel: [ 9750.488000] 286448 pages of HIGHMEM
Aug  6 22:29:44 workhorse kernel: [ 9750.488000] 219427 reserved pages
Aug  6 22:29:44 workhorse kernel: [ 9750.488000] 81437 pages shared
Aug  6 22:29:44 workhorse kernel: [ 9750.488000] 5138 pages swap cached
Aug  6 22:29:44 workhorse kernel: [ 9750.488000] 0 pages dirty
Aug  6 22:29:44 workhorse kernel: [ 9750.488000] 0 pages writeback
Aug  6 22:29:44 workhorse kernel: [ 9750.488000] 15086 pages mapped
Aug  6 22:29:44 workhorse kernel: [ 9750.488000] 5233 pages slab
Aug  6 22:29:44 workhorse kernel: [ 9750.488000] 521 pages pagetables
Aug  6 22:29:44 workhorse kernel: [ 9750.492000] Out of memory: kill process 6193 (x-session-manag) score 54831 or a child
Aug  6 22:29:44 workhorse kernel: [ 9750.492000] Killed process 6260 (nautilus)
Aug  6 22:29:44 workhorse kernel: [ 9750.492000] 515824 pages of RAM
Aug  6 22:29:44 workhorse kernel: [ 9750.492000] 286448 pages of HIGHMEM
Aug  6 22:29:44 workhorse kernel: [ 9750.492000] 219427 reserved pages
Aug  6 22:29:44 workhorse kernel: [ 9750.492000] 81444 pages shared
Aug  6 22:29:44 workhorse kernel: [ 9750.492000] 5138 pages swap cached
Aug  6 22:29:44 workhorse kernel: [ 9750.492000] 0 pages dirty
Aug  6 22:29:44 workhorse kernel: [ 9750.492000] 0 pages writeback
Aug  6 22:29:44 workhorse kernel: [ 9750.492000] 14838 pages mapped
Aug  6 22:29:44 workhorse kernel: [ 9750.492000] 5233 pages slab
Aug  6 22:29:44 workhorse kernel: [ 9750.492000] 521 pages pagetables
Aug  6 22:29:44 workhorse kernel: [ 9750.492000] Out of memory: kill process 6193 (x-session-manag) score 44882 or a child
Aug  6 22:29:44 workhorse kernel: [ 9750.492000] Killed process 6363 (vino-session)
Aug  6 22:29:44 workhorse kernel: [ 9750.496000] Out of memory: kill process 6193 (x-session-manag) score 42431 or a child
Aug  6 22:29:44 workhorse kernel: [ 9750.496000] Killed process 6364 (bluetooth-apple)
Aug  6 22:29:44 workhorse kernel: [ 9750.496000] Out of memory: kill process 6193 (x-session-manag) score 40725 or a child
Aug  6 22:29:44 workhorse kernel: [ 9750.496000] Killed process 6366 (update-notifier)
Aug  6 22:29:44 workhorse kernel: [ 9750.496000] Out of memory: kill process 6193 (x-session-manag) score 37155 or a child
Aug  6 22:29:44 workhorse kernel: [ 9750.496000] Killed process 6376 (trackerd)
Aug  6 22:29:44 workhorse kernel: [ 9750.828000] Out of memory: kill process 6499 (evolution) score 30941 or a child
Aug  6 22:29:44 workhorse kernel: [ 9750.828000] Killed process 6499 (evolution)
Aug  6 22:29:44 workhorse kernel: [ 9750.828000] Out of memory: kill process 6520 (evolution) score 30941 or a child
Aug  6 22:29:44 workhorse kernel: [ 9750.828000] Killed process 6520 (evolution)
Aug  6 22:29:44 workhorse kernel: [ 9750.832000] Out of memory: kill process 6527 (evolution-alarm) score 17301 or a child
Aug  6 22:29:44 workhorse kernel: [ 9750.832000] Killed process 6527 (evolution-alarm)
Aug  6 22:29:44 workhorse kernel: [ 9750.832000] Out of memory: kill process 6438 (evolution-data-) score 16836 or a child
Aug  6 22:29:44 workhorse kernel: [ 9750.832000] Killed process 6438 (evolution-data-)
Aug  6 22:29:44 workhorse kernel: [ 9750.836000] Out of memory: kill process 6193 (x-session-manag) score 16250 or a child
Aug  6 22:29:44 workhorse kernel: [ 9750.836000] Killed process 6384 (python)
Aug  6 22:29:44 workhorse kernel: [ 9750.836000] Out of memory: kill process 6484 (deskbar-applet) score 15198 or a child
Aug  6 22:29:44 workhorse kernel: [ 9750.836000] Killed process 6484 (deskbar-applet)
Aug  6 22:29:44 workhorse kernel: [ 9750.836000] Out of memory: kill process 6490 (deskbar-applet) score 15198 or a child
Aug  6 22:29:44 workhorse kernel: [ 9750.836000] Killed process 6490 (deskbar-applet)
Aug  6 22:29:44 workhorse kernel: [ 9750.836000] Out of memory: kill process 6382 (trashapplet) score 14997 or a child
Aug  6 22:29:44 workhorse kernel: [ 9750.836000] Killed process 6382 (trashapplet)
Aug  6 22:29:44 workhorse kernel: [ 9751.040000] Out of memory: kill process 6462 (tomboy) score 14307 or a child
Aug  6 22:29:44 workhorse kernel: [ 9751.040000] Killed process 6462 (tomboy)
Aug  6 22:29:44 workhorse kernel: [ 9751.044000] Out of memory: kill process 6193 (x-session-manag) score 13371 or a child
Aug  6 22:29:44 workhorse kernel: [ 9751.044000] Killed process 6398 (nm-applet)
Aug  6 22:29:44 workhorse kernel: [ 9751.044000] Out of memory: kill process 6249 (bonobo-activati) score 10244 or a child
Aug  6 22:29:44 workhorse kernel: [ 9751.044000] Killed process 6249 (bonobo-activati)
Aug  6 22:29:44 workhorse kernel: [ 9751.044000] Out of memory: kill process 6250 (bonobo-activati) score 10244 or a child
Aug  6 22:29:44 workhorse kernel: [ 9751.044000] Killed process 6250 (bonobo-activati)
Aug  6 22:29:44 workhorse kernel: [ 9751.360000] Out of memory: kill process 6242 (gnome-settings-) score 9736 or a child
Aug  6 22:29:44 workhorse kernel: [ 9751.360000] Killed process 6242 (gnome-settings-)
Aug  6 22:29:44 workhorse kernel: [ 9751.364000] Out of memory: kill process 6193 (x-session-manag) score 9412 or a child
Aug  6 22:29:44 workhorse kernel: [ 9751.364000] Killed process 6193 (x-session-manag)
Aug  6 22:29:44 workhorse kernel: [ 9751.372000] Out of memory: kill process 6427 (evolution-excha) score 9169 or a child
Aug  6 22:29:44 workhorse kernel: [ 9751.372000] Killed process 6427 (evolution-excha)
Aug  6 22:29:44 workhorse kernel: [ 9751.372000] Out of memory: kill process 6956 (file-roller) score 8253 or a child
Aug  6 22:29:44 workhorse kernel: [ 9751.372000] Killed process 6956 (file-roller)
Aug  6 22:29:44 workhorse kernel: [ 9751.680000] Out of memory: kill process 6496 (notification-da) score 6251 or a child
Aug  6 22:29:44 workhorse kernel: [ 9751.680000] Killed process 6496 (notification-da)
Aug  6 22:29:44 workhorse kernel: [ 9751.984000] Out of memory: kill process 6401 (gnome-power-man) score 5695 or a child
Aug  6 22:29:44 workhorse kernel: [ 9751.984000] Killed process 6401 (gnome-power-man)
Aug  6 22:29:44 workhorse kernel: [ 9752.708000] Out of memory: kill process 6475 (geyes_applet2) score 5092 or a child
Aug  6 22:29:44 workhorse kernel: [ 9752.708000] Killed process 6475 (geyes_applet2)
Aug  6 22:29:44 workhorse kernel: [ 9753.232000] Out of memory: kill process 6266 (gnome-volume-ma) score 4922 or a child
Aug  6 22:29:44 workhorse kernel: [ 9753.232000] Killed process 6266 (gnome-volume-ma)
Aug  6 22:29:44 workhorse kernel: [ 9753.236000] Out of memory: kill process 6357 (gtk-window-deco) score 4612 or a child
Aug  6 22:29:44 workhorse kernel: [ 9753.236000] Killed process 6357 (gtk-window-deco)
Aug  6 22:29:44 workhorse kernel: [ 9753.240000] Out of memory: kill process 6276 (gnome-screensav) score 4167 or a child
Aug  6 22:29:44 workhorse kernel: [ 9753.240000] Killed process 6276 (gnome-screensav)
Aug  6 22:29:44 workhorse kernel: [ 9753.744000] Out of memory: kill process 6255 (vino-server) score 4154 or a child
Aug  6 22:29:44 workhorse kernel: [ 9753.744000] Killed process 6255 (vino-server)
Aug  6 22:29:44 workhorse kernel: [ 9753.748000] Out of memory: kill process 6190 (gnome-keyring-d) score 3327 or a child
Aug  6 22:29:44 workhorse kernel: [ 9753.748000] Killed process 6190 (gnome-keyring-d)
Aug  6 22:29:44 workhorse kernel: [ 9753.752000] Out of memory: kill process 6287 (gnome-vfs-daemo) score 2188 or a child
Aug  6 22:29:44 workhorse kernel: [ 9753.752000] Killed process 6287 (gnome-vfs-daemo)
Aug  6 22:29:44 workhorse kernel: [ 9754.496000] Out of memory: kill process 5235 (hald) score 1803 or a child
Aug  6 22:29:44 workhorse kernel: [ 9754.496000] Killed process 5236 (hald-runner)
Aug  6 22:29:44 workhorse kernel: [ 9754.500000] Out of memory: kill process 6238 (gconfd-2) score 1802 or a child
Aug  6 22:29:44 workhorse kernel: [ 9754.500000] Killed process 6238 (gconfd-2)
Aug  6 22:29:44 workhorse kernel: [ 9754.504000] Out of memory: kill process 5777 (avahi-daemon) score 1025 or a child
Aug  6 22:29:44 workhorse kernel: [ 9754.504000] Killed process 5778 (avahi-daemon)
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] printk: 89 messages suppressed.
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] Xorg invoked oom-killer: gfp_mask=0x2d0, order=0, oomkilladj=0
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [out_of_memory+389/448] out_of_memory+0x185/0x1c0
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [__alloc_pages+740/832] __alloc_pages+0x2e4/0x340
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [__get_free_pages+51/64] __get_free_pages+0x33/0x40
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [<f948003a>] nv_vm_malloc_pages+0x10a/0x310 [nvidia]
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [<f9481b75>] nv_alloc_pages+0x235/0x3f0 [nvidia]
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [<f9486091>] os_alloc_mem+0x71/0x90 [nvidia]
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [<f91a69e6>] _nv003431rm+0x13/0x17 [nvidia]
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [<f91a6e6e>] _nv003513rm+0x3b/0x3f [nvidia]
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [<f93da026>] _nv004905rm+0x31/0x16e [nvidia]
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [<f93d8054>] _nv003769rm+0x89f/0xa7a [nvidia]
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [<f918c875>] _nv002554rm+0x815/0x1e2a [nvidia]
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [<f91871d3>] _nv004494rm+0x61/0xea [nvidia]
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [<f91b1eb8>] _nv002642rm+0x1b8/0x5e9 [nvidia]
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [<f91aef22>] rm_ioctl+0x3e/0x6d [nvidia]
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [<f94829ee>] nv_kern_ioctl+0xfe/0x3c0 [nvidia]
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [free_pgtables+133/176] free_pgtables+0x85/0xb0
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [<f9482ce8>] nv_kern_unlocked_ioctl+0x18/0x20 [nvidia]
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [<f9482cd0>] nv_kern_unlocked_ioctl+0x0/0x20 [nvidia]
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [do_ioctl+43/192] do_ioctl+0x2b/0xc0
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [remove_vma+65/80] remove_vma+0x41/0x50
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [vfs_ioctl+92/656] vfs_ioctl+0x5c/0x290
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  =======================
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] Mem-info:
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] DMA per-cpu:
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] Normal per-cpu:
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] CPU    0: Hot: hi:  186, btch:  31 usd: 177   Cold: hi:   62, btch:  15 usd:  52
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] CPU    1: Hot: hi:  186, btch:  31 usd: 147   Cold: hi:   62, btch:  15 usd:  55
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] HighMem per-cpu:
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] CPU    0: Hot: hi:  186, btch:  31 usd: 181   Cold: hi:   62, btch:  15 usd:   1
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] CPU    1: Hot: hi:  186, btch:  31 usd: 155   Cold: hi:   62, btch:  15 usd:   7
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] Active:23753 inactive:9788 dirty:0 writeback:0 unstable:0
Aug  6 22:29:44 workhorse kernel: [ 9755.148000]  free:251575 slab:4042 mapped:4439 pagetables:183 bounce:0
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] DMA free:3544kB min:68kB low:84kB high:100kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unreclaimable? yes
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] lowmem_reserve[]: 0 873 1983
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] Normal free:3744kB min:3744kB low:4680kB high:5616kB active:420kB inactive:388kB present:894080kB pages_scanned:1427 all_unreclaimable? yes
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] lowmem_reserve[]: 0 0 8881
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] HighMem free:999012kB min:512kB low:1700kB high:2892kB active:94592kB inactive:38764kB present:1136844kB pages_scanned:0 all_unreclaimable? no
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] lowmem_reserve[]: 0 0 0
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] DMA: 0*4kB 1*8kB 1*16kB 0*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3544kB
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] Normal: 12*4kB 13*8kB 6*16kB 0*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3768kB
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] HighMem: 5056*4kB 4513*8kB 3775*16kB 3048*32kB 2300*64kB 1483*128kB 697*256kB 258*512kB 62*1024kB 6*2048kB 15*4096kB = 999032kB
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] Swap cache: add 5272, delete 138, find 0/6, race 0+0
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] Free swap  = 1931180kB
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] Total swap = 1951888kB
Aug  6 22:29:44 workhorse kernel: [ 9755.148000] Free swap:       1931180kB
Aug  6 22:29:44 workhorse kernel: [ 9755.156000] 515824 pages of RAM
Aug  6 22:29:44 workhorse kernel: [ 9755.156000] 286448 pages of HIGHMEM
Aug  6 22:29:44 workhorse kernel: [ 9755.156000] 220598 reserved pages
Aug  6 22:29:44 workhorse kernel: [ 9755.156000] 11306 pages shared
Aug  6 22:29:44 workhorse kernel: [ 9755.156000] 5134 pages swap cached
Aug  6 22:29:44 workhorse kernel: [ 9755.156000] 0 pages dirty
Aug  6 22:29:44 workhorse kernel: [ 9755.156000] 0 pages writeback
Aug  6 22:29:44 workhorse kernel: [ 9755.156000] 4439 pages mapped
Aug  6 22:29:44 workhorse kernel: [ 9755.156000] 4042 pages slab
Aug  6 22:29:44 workhorse kernel: [ 9755.156000] 183 pages pagetables
Aug  6 22:29:44 workhorse kernel: [ 9755.156000] Out of memory: kill process 5869 (gdm) score 924 or a child
Aug  6 22:29:44 workhorse kernel: [ 9755.156000] Killed process 5874 (Xorg)
Aug  6 22:29:44 workhorse gdm[5869]: WARNING: gdm_slave_xioerror_handler: Schwerwiegender X-Fehler - :0 wird neu gestartet [/SIZE]

---

### Post by DaneM on 2008-08-07
It does kind-of look like a memory problem.  You may want to run memtest from the Ubuntu CD (several passes) to make sure your hardware is OK.

--Dane

---

### Post by Highlander4880 on 2008-08-07
Thank you for your reply! It's a good idea and I will try it. 

That the log is showing something with "nv" so often made me thought it may have something to do with the nvidia graphics driver.

I will report after memtest or if the issue happens again.

Cu
High

---

