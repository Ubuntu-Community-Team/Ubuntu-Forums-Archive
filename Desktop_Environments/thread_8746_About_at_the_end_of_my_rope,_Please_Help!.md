---
title: "About at the end of my rope, Please Help!"
date: 2004-12-20
forum: Desktop Environments
---

### Post by dare2dreamer on 2004-12-20
Seems like every 24-48 hours, my machine eats through all of its memory and hard-locks. I can actually watch the memory count slowly rise, and eventually bring X, and then everything else, to its knees.

This strikes me as odd because the machine in question is something of a beast:

AMD Athlon 2600XP, Barton Core
A7N8x-E mobo
1 Gig of tested ram, with 2 1/2 gigs of swap.
All SCSI drives on a 2940 adapter

Needless to say, not the sort of machine I'd expect to swap itself to death.

I've been fighting this problem for a few weeks now, and I'm hoping someone will help me sort it out. I've got ubuntu installned on three machines, and only one of them is experiencing this issue. This machie is currently running with ACPI=off, as some things I read suggested that ACPI might be part of the problem.

I took a look at /var/log/messages, and at some point I get a string of messages like these:

```
Dec 20 07:05:53 localhost kernel: Free pages:       43936kB (40208kB HighMem)
Dec 20 07:05:53 localhost kernel: Active:14137 inactive:6200 dirty:0 writeback:0 unstable:0 free:10984 slab:2736 mapped:16546 pagetables:264
Dec 20 07:05:53 localhost kernel: DMA free:1904kB min:16kB low:32kB high:48kB active:0kB inactive:0kB present:16384kB
Dec 20 07:05:53 localhost kernel: protections[]: 8 476 540
Dec 20 07:05:53 localhost kernel: Normal free:1824kB min:936kB low:1872kB high:2808kB active:876kB inactive:784kB present:901120kB
Dec 20 07:05:53 localhost kernel: protections[]: 0 468 532
Dec 20 07:05:53 localhost kernel: HighMem free:40208kB min:128kB low:256kB high:384kB active:55672kB inactive:24016kB present:131008kB
Dec 20 07:05:53 localhost kernel: protections[]: 0 0 64
Dec 20 07:05:53 localhost kernel: DMA: 6*4kB 3*8kB 2*16kB 1*32kB 0*64kB 0*128kB 1*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 1904kB
Dec 20 07:05:53 localhost kernel: Normal: 0*4kB 0*8kB 10*16kB 0*32kB 2*64kB 2*128kB 1*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1824kB
Dec 20 07:05:53 localhost kernel: HighMem: 0*4kB 1202*8kB 912*16kB 344*32kB 74*64kB 2*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 40208kB
Dec 20 07:05:53 localhost kernel: Swap cache: add 53763, delete 50475, find 15982/17940, race 0+0
Dec 20 07:10:58 localhost kernel: oom-killer: gfp_mask=0xd0
Dec 20 07:10:58 localhost kernel: DMA per-cpu:
Dec 20 07:10:58 localhost kernel: cpu 0 hot: low 2, high 6, batch 1
Dec 20 07:10:58 localhost kernel: cpu 0 cold: low 0, high 2, batch 1
Dec 20 07:10:58 localhost kernel: Normal per-cpu:
Dec 20 07:10:58 localhost kernel: cpu 0 hot: low 32, high 96, batch 16
Dec 20 07:10:58 localhost kernel: cpu 0 cold: low 0, high 32, batch 16
Dec 20 07:10:58 localhost kernel: HighMem per-cpu:
Dec 20 07:10:58 localhost kernel: cpu 0 hot: low 14, high 42, batch 7
Dec 20 07:10:58 localhost kernel: cpu 0 cold: low 0, high 14, batch 7

```

and the machine more or less locks up and keels over. Sometimes I can drop it to init 1 and reboot it, sometimes I can't even ssh in to do that.

I got rid of acpi, and it doesn't seem to be helping at all. I've also got some suspicions that it might have something to do with hotplug, because one time I was able to ps aux before it died and saw several dead hotplug processes.

Any ideas?

---

### Post by ubuntu_demon on 2004-12-20
Next time when it happens try logging in from another pc or just go to terminal mode (ctrl-alt-f1 I think) and try to find out what process is doing this using top.

Maybe it's a cronjob ?

---

### Post by dare2dreamer on 2004-12-20
Sometimes I can log in, sometimes I can't. Depends how far gone it gets before I notice it. Machine is doing something that's running through over a gig of ram...nothing in my crontabs will do that.

Either it hardlocks, or I find it sitting at an xlogin because x crashed, and then when I try to log back in it wipes out and dumps me back at the login. Going down to console shows me the error messages I listed spewing to the console to the point where I can't do much other than quickly bounce the box between errors.

Then, it'll take it upwards of 30 minutes to sort itself out and finally reboot.

---

### Post by dare2dreamer on 2005-01-04
problem solved with careful googling:

appended:
```
 pci=biosirq mem=nopentium noapic nolapic acpi=off noacpi=off apm=off
```

to kernel line in /boot/grub/menu.lst and the problems disappeared. Seems my motherboard has some serious issues with acpi and such.

---

### Post by wallijonn on 2005-01-04
Dare2Dreamer,

Congratulations. That is a great fix. But I do have to ask what kernel you were using.

---

