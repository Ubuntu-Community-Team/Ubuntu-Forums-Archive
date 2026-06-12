---
title: "VMware Workstation hangs when booting services"
date: 2009-06-11
forum: General Help
---

### Post by mattm591 on 2009-06-11
I have been using VMware Workstation (6.5.2) on Ubuntu (9.04) for some time now without issue.

When I booted earlier my system was hanging and the screen was filling with messages. Here is a sample
```
Jun 11 20:14:30 Y2K-PC kernel: [ 3364.965088] ata3.00: configured for UDMA/133
Jun 11 20:14:30 Y2K-PC kernel: [ 3364.980687] ata3.01: configured for UDMA/33
Jun 11 20:14:30 Y2K-PC kernel: [ 3364.980696] ata3: EH complete
Jun 11 20:14:30 Y2K-PC kernel: [ 3368.208551] ata3.00: configured for UDMA/133
Jun 11 20:14:30 Y2K-PC kernel: [ 3368.224691] ata3.01: configured for UDMA/33
Jun 11 20:14:30 Y2K-PC kernel: [ 3368.224700] ata3: EH complete
Jun 11 20:14:30 Y2K-PC kernel: [ 3371.316911] ata3.00: configured for UDMA/133
Jun 11 20:14:30 Y2K-PC kernel: [ 3371.332689] ata3.01: configured for UDMA/33
Jun 11 20:14:30 Y2K-PC kernel: [ 3371.332697] ata3: EH complete
Jun 11 20:14:30 Y2K-PC kernel: [ 3374.421224] ata3.00: configured for UDMA/133
Jun 11 20:14:30 Y2K-PC kernel: [ 3374.436186] ata3.01: configured for UDMA/33
Jun 11 20:14:30 Y2K-PC kernel: [ 3374.436193] ata3: EH complete
Jun 11 20:14:30 Y2K-PC kernel: [ 3377.525570] ata3.00: configured for UDMA/133
Jun 11 20:14:30 Y2K-PC kernel: [ 3377.540192] ata3.01: configured for UDMA/33
Jun 11 20:14:30 Y2K-PC kernel: [ 3377.540199] ata3: EH complete
Jun 11 20:14:30 Y2K-PC kernel: [ 3380.628912] ata3.00: configured for UDMA/133
Jun 11 20:14:30 Y2K-PC kernel: [ 3380.644683] ata3.01: configured for UDMA/33
Jun 11 20:14:30 Y2K-PC kernel: [ 3380.644692] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jun 11 20:14:30 Y2K-PC kernel: [ 3380.644695] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jun 11 20:14:30 Y2K-PC kernel: [ 3380.644699] Descriptor sense data with sense descriptors (in hex):
Jun 11 20:14:30 Y2K-PC kernel: [ 3380.644701]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 11 20:14:30 Y2K-PC kernel: [ 3380.644708]         04 72 c1 b0 
Jun 11 20:14:30 Y2K-PC kernel: [ 3380.644711] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jun 11 20:14:30 Y2K-PC kernel: [ 3380.644726] ata3: EH complete
Jun 11 20:14:30 Y2K-PC kernel: [ 3380.644754] sd 2:0:0:0: [sda] Write Protect is off
Jun 11 20:14:30 Y2K-PC kernel: [ 3380.646247] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 11 20:14:30 Y2K-PC kernel: [ 3380.649567] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
Jun 11 20:14:30 Y2K-PC kernel: [ 3380.650340] sd 2:0:0:0: [sda] Write Protect is off
Jun 11 20:14:30 Y2K-PC kernel: [ 3380.652213] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

I restarted into recovery mode, ran a disk check and that came back fine.

The system was failing to boot when it got to loading the VMWare services.

I removed vmware from init.d to stop it booting and got my system up again fine.

I then uninstalled VMWare and tried reinstalling, but during installation (at the stage "Configuring VMWare Player") my system freezed up and I got the same messages all over again.

Anyone have any ideas?

---

### Post by mattm591 on 2009-06-12
Apologies for bumping this, but I really need to get VMware working again and don't won't to have to do a reinstall.

Is there anything I can do to rectify this or to find out what might be the root cause?

---

### Post by mattm591 on 2009-06-13
Ok for anyone else having problems with this, I have found out it was because my harddrive was on its way out!

If you're getting this backup all your data immediately and get a new disk!

---

