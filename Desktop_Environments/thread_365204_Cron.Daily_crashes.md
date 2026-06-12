---
title: "Cron.Daily crashes"
date: 2007-02-19
forum: Desktop Environments
---

### Post by .Mo on 2007-02-19
Hey there,

ok I'm running kubuntu 6.10 on my machine,and it worked fine so far. But now I have a problem with the daily cronjob. This is since I mount a ntfs formated hd on startup. The syslog tells me this:

```
Feb 19 14:50:36 gamer anacron[4256]: Job `cron.daily' started
Feb 19 14:50:36 gamer anacron[8668]: Updated timestamp for job `cron.daily' to 2007-02-19
Feb 19 14:52:24 gamer ntfs-3g[3291]: Skipping unrepresentable filename (inode 3268)
Feb 19 14:52:25 gamer ntfs-3g[3291]: Skipping unrepresentable filename (inode 3255)
Feb 19 14:52:29 gamer kernel: [17180025.924000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 19 14:52:29 gamer kernel: [17180025.924000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=6303943, high=0, low=6303943, sector=6303919
Feb 19 14:52:29 gamer kernel: [17180025.924000] ide: failed opcode was: unknown
Feb 19 14:52:29 gamer kernel: [17180025.924000] end_request: I/O error, dev hda, sector 6303919
Feb 19 14:52:29 gamer kernel: [17180025.924000] Buffer I/O error on device hda1, logical block 6303856
Feb 19 14:52:33 gamer kernel: [17180030.028000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 19 14:52:33 gamer kernel: [17180030.028000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=6303943, high=0, low=6303943, sector=6303920
Feb 19 14:52:33 gamer kernel: [17180030.028000] ide: failed opcode was: unknown
Feb 19 14:52:33 gamer kernel: [17180030.028000] end_request: I/O error, dev hda, sector 6303920
Feb 19 14:52:33 gamer kernel: [17180030.028000] Buffer I/O error on device hda1, logical block 6303857
Feb 19 14:52:37 gamer kernel: [17180034.132000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 19 14:52:37 gamer kernel: [17180034.132000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=6303943, high=0, low=6303943, sector=6303921
Feb 19 14:52:37 gamer kernel: [17180034.132000] ide: failed opcode was: unknown
Feb 19 14:52:37 gamer kernel: [17180034.132000] end_request: I/O error, dev hda, sector 6303921
Feb 19 14:52:37 gamer kernel: [17180034.132000] Buffer I/O error on device hda1, logical block 6303858
Feb 19 14:52:41 gamer kernel: [17180038.204000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 19 14:52:41 gamer kernel: [17180038.204000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=6303943, high=0, low=6303943, sector=6303922
Feb 19 14:52:41 gamer kernel: [17180038.204000] ide: failed opcode was: unknown
Feb 19 14:52:41 gamer kernel: [17180038.204000] end_request: I/O error, dev hda, sector 6303922
Feb 19 14:52:41 gamer kernel: [17180038.204000] Buffer I/O error on device hda1, logical block 6303859
Feb 19 14:52:45 gamer kernel: [17180042.316000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 19 14:52:45 gamer kernel: [17180042.316000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=6303943, high=0, low=6303943, sector=6303923
Feb 19 14:52:45 gamer kernel: [17180042.316000] ide: failed opcode was: unknown
Feb 19 14:52:45 gamer kernel: [17180042.316000] end_request: I/O error, dev hda, sector 6303923
Feb 19 14:52:45 gamer kernel: [17180042.316000] Buffer I/O error on device hda1, logical block 6303860
```

and so on... my computer freezes when it does that. I guess the cron.daily checks the filesystem and has some problems with the ntfs hd... so how can I tell cron to just leave it alone? Because after I restart and the daily cronjob isn't executed, everything works just fine...
:confused:

---

### Post by prensing on 2007-02-19
This is almost certainly not caused by cron itself, but rather one (or more) of the programs that it runs. My guess would be slocate which walks your entire directory structure (well, almost) to create a filename index. You can test this: you can remove the executable bit on the slocate script and it should not run:
     sudo chmod -x /etc/cron.daily/slocate
If this makes it stable, then configure slocate so that it skips your NTFS partition and then turn slocate back on:
    sudo chmod +x /etc/cron.daily/slocate

Of course, this error is really telling you that the NTFS driver is not working 100% correctly and you will get a crash once in a while anyway.

---

### Post by .Mo on 2007-02-20
Yeah, taking away the right to execute from slocate did the trick... so do u think that the ntfs-3g driver is really the problem? Couldn't it be the hard drive that's broken somehow? I tried the MS - chkdsk, but that didn't fix anything (as so often :mad: ). Either way I don't care that much 'bout the ntfs drive. ;)
Well thanks for the help, I'll try to find out how to configure slocate. :) 
greetz, Mo

---

