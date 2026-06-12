---
title: "System hangs after long idle"
date: 2014-06-05
forum: Desktop Environments
---

### Post by xubuntu84 on 2014-06-05
Good evening,

I have been having a system hang issue since I upgraded to 14.04 Xubuntu.  When I sit down and move the mouse or press a key to wake the computer, all I get is a blinking cursor in the top left of a black screen. Switching to a different session does not work (Ctrl+Alt+F4, for example).  The only thing I can do is Alt+PrScr+REISUB to emergency sync and reboot.  During the "S" part of REISUB, some text appears, and it is flashing as fast as the cursor would flash.

I have attached log files of anything I could think that would be appropriate.  In kern.log, I noticed

```
Jun  3 18:52:29 xubuntu-server kernel: [ 2140.040845] perf samples too long (2506 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
```

as one of the last entries before I force reboot.  When I run smartctl for /dev/sda I get many errors, and have already ordered a replacement drive.  I have run 

```
[COLOR=#000000][FONT=Courier New]sudo echo 'check' > /sys/block/md0/md/sync_action[/FONT][/COLOR]
```

to see if the RAID was messing up (which sda is a part of), and it returned 0 for the mismatch count.  My system drive is sdf, so I wouldn't think a failing drive that is part of my RAID would affect it.  Is there anything else I can do to figure out what exactly is going on?  I have considered failing and removing sda with mdadm, but I kind of wanted to wait until the new drive arrived in order to maintain redundancy (RAID5).

Thanks,
Ben

EDIT: I have noticed that if I lock the computer manually (Ctrl+Alt+L) it will also do the same thing with a blinking cursor.  This must be something to do with lightdm or xfce lock.  I still don't have a clue how to fix it yet...

Edit 2: OK, so I left the computer on overnight without manually locking it and disabling automatic lock, and it did not hang the way previously described.  So it definitely appears to be a problem with the locker in Xubuntu 14.04.  Are there any alternative lockers available, or does anyone know how to fix this issue?

---

