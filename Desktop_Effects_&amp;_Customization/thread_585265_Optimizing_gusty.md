---
title: "Optimizing gusty?"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by bigbang on 2007-10-21
My system seems to load up quite slow (i doubt its unnaturally slow). Before, in feisty, it was quite slow; bootchart was recording about 50 seconds. Now, in gutsy, it is even slower at 1 minute or more. Im attaching my latest bootchart, it seems to hang at the start of booting, this is what takes the longest. can people tell me what I have to do to optimise (or if there is a problem) and how they can tell that? I would like to learn how to do this myself. 
ps. I have already profiled the boot. Also, I was quite sure where to put this, I though it fitted under the heading of customisation.

---

### Post by bigbang on 2007-10-22
i just found that when i run "$ dmesg | grep -i failed" i get:
```
[    6.392000] hda: 58633344 sectors (30020 MB) w/418KiB Cache, CHS=58168/16/63<4>hda: drive side 80-wire cable detection failed, limiting max speed to UDMA33
[    6.948000] PM: Resume from disk failed.
[  152.892000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/tablet/wacom_sys.c: wacom_sys_irq - usb_submit_urb failed with result -113
[  153.556000] pnp: Failed to activate device 00:0b.
[  153.556000] pnp: Failed to activate device 00:0c.
[  154.100000] ata1.00: ACPI cmd f5/00:00:00:00:00:00 failed (Emask=0x1 Stat=0x51 Err=0x04)
[  154.100000] ata1.00: revalidation failed (errno=-5)
[  154.100000] ata1: failed to recover some devices, retrying in 5 secs
[  159.900000] ata1.00: ACPI cmd f5/00:00:00:00:00:00 failed (Emask=0x1 Stat=0x51 Err=0x04)
[  159.900000] ata1.00: ACPI on devcfg failed the second time, disabling (errno=-5)
[  159.900000] ata1.00: revalidation failed (errno=1)
[  159.900000] ata1: failed to recover some devices, retrying in 5 secs

```
does this show anything?

---

### Post by whi8esauce on 2007-12-15
i too feel that gusty has seriously slowed down my notebook. it was much faster(when booting up) when i was using feisty... i have disabled all the unneeded stuff in my gusty installation but still it is painfully slow to boot up... :confused:

---

