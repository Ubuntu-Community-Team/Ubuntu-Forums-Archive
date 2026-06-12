---
title: "Firefox crashing.. Out of memory?!"
date: 2005-12-16
forum: Desktop Environments
---

### Post by dolson on 2005-12-16
I have nothing but Gnome, XMMS, and Firefox running. If I open a few tabs and surf around, etc. then it just closes on it's own sometimes... As soon as it did this, I checked out dmesg, and I see this:

[5240226.169000] oom-killer: gfp_mask=0xd0
[5240226.169000] DMA per-cpu:
[5240226.169000] cpu 0 hot: low 2, high 6, batch 1
[5240226.169000] cpu 0 cold: low 0, high 2, batch 1
[5240226.169000] Normal per-cpu:
[5240226.169000] cpu 0 hot: low 62, high 186, batch 31
[5240226.169000] cpu 0 cold: low 0, high 62, batch 31
[5240226.169000] HighMem per-cpu: empty
[5240226.169000]
[5240226.169000] Free pages:        4676kB (0kB HighMem)
[5240226.169000] Active:102986 inactive:965 dirty:0 writeback:0 unstable:0 free:1169 slab:4085 mapped:101362 pagetables:498
[5240226.169000] DMA free:2036kB min:88kB low:108kB high:132kB active:11008kB inactive:0kB present:16384kB pages_scanned:13653 all_unreclaimable? yes
[5240226.169000] lowmem_reserve[]: 0 487 487
[5240226.169000] Normal free:2640kB min:2776kB low:3468kB high:4164kB active:400936kB inactive:3860kB present:499136kB pages_scanned:433042 all_unreclaimable? yes
[5240226.169000] lowmem_reserve[]: 0 0 0
[5240226.169000] HighMem free:0kB min:128kB low:160kB high:192kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
[5240226.169000] lowmem_reserve[]: 0 0 0
[5240226.169000] DMA: 1*4kB 0*8kB 1*16kB 1*32kB 1*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 2036kB
[5240226.169000] Normal: 0*4kB 0*8kB 1*16kB 0*32kB 13*64kB 0*128kB 1*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 2640kB
[5240226.169000] HighMem: empty
[5240226.169000] Swap cache: add 190714, delete 184516, find 174212/182133, race 0+0
[5240226.169000] Free swap  = 1812564kB
[5240226.169000] Total swap = 1951888kB
[5240226.169000] Out of Memory: Killed process 26339 (firefox-bin).

What can I do to fix this?

---

### Post by aysiu on 2005-12-17
Try this and see if you have the same problem:
[http://www.ubuntuforums.org/showthread.php?t=103930](http://www.ubuntuforums.org/showthread.php?t=103930)

---

### Post by dolson on 2005-12-19
[QUOTE=aysiu]Try this and see if you have the same problem:
[http://www.ubuntuforums.org/showthread.php?t=103930](http://www.ubuntuforums.org/showthread.php?t=103930)[/QUOTE]

That didn't help.

---

### Post by McQuaid on 2006-02-17
I get a similar error with epiphany, and I believe I've had it with firefox, and definitely with thunar (xfce file manager).  Wondering if it's gamin related?

---

