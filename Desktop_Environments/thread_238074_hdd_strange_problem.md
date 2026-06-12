---
title: "hdd strange problem"
date: 2006-08-17
forum: Desktop Environments
---

### Post by matko on 2006-08-17
hello.

i have in /var/log/dmesg this strange things

```
[4294679.520000] hda: set_drive_speed_status: status=0xd0 { Busy }
[4294679.520000] ide: failed opcode was: unknown
[4294682.521000] hda: channel busy
[4294699.510000] hda: dma_timer_expiry: dma status == 0x60
[4294699.510000] hda: DMA timeout retry
[4294699.510000] hda: timeout waiting for DMA
[4294704.711000] hda: status timeout: status=0xd0 { Busy }
[4294704.711000] ide: failed opcode was: unknown
[4294704.711000] hdb: DMA disabled
[4294704.711000] hda: drive not ready for command
```

i cant find any good solution for it. why is this happend? does it mean i dont have DMA on?

---

### Post by jordilin on 2006-08-17
Leaving apart these messages, are you experiencing strange behaviours with your Linux box?

---

### Post by matko on 2006-08-17
before i got this result
```
matko@dapper:~$ sudo hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (on)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 160836480, start = 0

```

after i modified /etc/hdparm.conf 
like this
```
/dev/hda {
	mult_sect_io = 32
	keep_settings_over_reset = on
	io32_support = 1
}
```
it solved problem. mistake is no more in log and sudo hdparm /dev/hda
 is
```
matko@dapper:~$ sudo hdparm /dev/hda
Password:

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  1 (on)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 160836480, start = 0

```

so it looks like i tried to turn on DMA two times.
so the solution is remove 
dma = on
from hdparm.conf

---

