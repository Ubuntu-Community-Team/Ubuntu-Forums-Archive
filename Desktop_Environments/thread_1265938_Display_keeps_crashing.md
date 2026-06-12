---
title: "Display keeps crashing"
date: 2009-09-14
forum: Desktop Environments
---

### Post by euphgeek on 2009-09-14
Recently my display has been crashing on me, showing either a completely white screen or a black or blue screen with vertical lines through it.  Nothing brings it back except a reboot, not even Ctrl-Alt-Backspace works.  This happens at least twice a day.

While it is doing this, I am able to log in using Remote Desktop for a while.  The screen shows up normally and I can shut down my applications and do a safe reboot.  Unfortunately, this only lasts temporarily.  If I wait too long, the network connection goes dead and my only option is to hit the reset button on my computer.

This has only started just recently.  Up until now I've been using Ubuntu 8.04 64-bit with no problems.  The only thing that has happened recently is that I've noticed tiny black lines across my monitor that make the icons and text look like they're jumping around.  The other thing that has happened is my 1 TB SATA hard drive appeared as if it was starting to go dead (luckily I've been able to back up my data).  Ubuntu is installed on a partition of an 80 GB IDE hard drive.

I tried running Ubuntu off of the CD I installed it from.  The tiny black lines still show up.  But if I boot from a Knoppix CD I have (version 5.1.1) the lines do not show up.

I believe this may be a hardware problem related to either my hard drive, the onboard video card or possibly the entire motherboard.  Does anybody have any suggestions of what else it might be or something else I can try?

---

### Post by krazyd on 2009-09-14
what is your graphics card / driver?

---

### Post by euphgeek on 2009-09-14
My graphics card is an onboard ATI Radeon X1250.  I'm using the ati driver for it.

---

### Post by krazyd on 2009-09-14
is that the fglrx restricted driver, or the open source radeon driver?

---

### Post by euphgeek on 2009-09-14
I'm using the open source ati driver.  It's the one I've been using pretty much the whole time.  I tried at one point to use the fglrx driver but I had issues with it so I went back to the ati driver.

---

### Post by krazyd on 2009-09-14
can you post the output of ```
grep -i error /var/log/messages
```

---

### Post by euphgeek on 2009-09-15
Here you go:

```
Sep 14 01:19:59 honestabe kernel: [   37.176448] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 14 01:19:59 honestabe kernel: [   43.096993]          res 40/00:04:00:02:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 01:19:59 honestabe kernel: [   43.600839]          res 40/00:04:3f:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 01:19:59 honestabe kernel: [   71.663200]          res 40/00:04:00:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 01:19:59 honestabe kernel: [   72.158233]          res 40/00:04:00:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 01:19:59 honestabe kernel: [   72.687522]          res 40/00:14:a8:6d:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 01:19:59 honestabe kernel: [   72.687529]          res 40/00:14:a8:6d:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 01:19:59 honestabe kernel: [   83.707101]          res 40/00:14:ef:30:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 01:24:22 honestabe kernel: [   49.214800] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 14 01:24:22 honestabe kernel: [   55.045277]          res 40/00:0c:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 01:24:22 honestabe kernel: [   55.530271]          res 40/00:04:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 01:24:22 honestabe kernel: [   56.017506]          res 40/00:04:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 01:24:22 honestabe kernel: [   56.135874] hda: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
Sep 14 01:24:22 honestabe kernel: [   56.135878] hda: set_drive_speed_status: error=0x04 { AbortedCommand }
Sep 14 01:24:22 honestabe kernel: [   56.504210]          res 40/00:04:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 01:24:22 honestabe kernel: [   66.218977]          res 40/00:04:00:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 01:24:22 honestabe kernel: [   66.773830]          res 40/00:0c:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 01:24:22 honestabe kernel: [   70.989388]          res 40/00:04:f7:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:05:55 honestabe kernel: [   37.998080] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 14 02:05:55 honestabe kernel: [   47.377683] hda: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
Sep 14 02:05:55 honestabe kernel: [   47.377687] hda: set_drive_speed_status: error=0x04 { AbortedCommand }
Sep 14 02:05:55 honestabe kernel: [   60.557260]          res 40/00:14:81:59:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:05:55 honestabe kernel: [   60.557267]          res 40/00:14:81:59:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:05:55 honestabe kernel: [   60.557273]          res 40/00:14:81:59:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:05:55 honestabe kernel: [   61.141006]          res 40/00:14:7f:59:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:05:55 honestabe kernel: [   61.141013]          res 40/00:14:7f:59:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:05:55 honestabe kernel: [   61.141020]          res 40/00:14:7f:59:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:05:55 honestabe kernel: [   61.792530]          res 40/00:14:81:59:70/00:00:74:00:00/40 Emask 0x10 (ATA bus error)
Sep 14 02:05:55 honestabe kernel: [   61.792536]          res 41/84:00:9e:00:00/07:00:00:00:00/40 Emask 0x410 (ATA bus error) <F>
Sep 14 02:05:55 honestabe kernel: [   61.792544]          res 40/00:14:81:59:70/00:00:74:00:00/40 Emask 0x10 (ATA bus error)
Sep 14 02:06:37 honestabe kernel: [   86.328047]          res 40/00:04:67:10:3c/00:00:19:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:15:02 honestabe kernel: [   20.500955] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 14 02:15:02 honestabe kernel: [   24.134579] hda: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
Sep 14 02:15:02 honestabe kernel: [   24.134583] hda: set_drive_speed_status: error=0x04 { AbortedCommand }
Sep 14 02:15:02 honestabe kernel: [   40.604138]          res 40/00:14:b0:01:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:15:02 honestabe kernel: [   40.604145]          res 40/00:14:b0:01:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:15:02 honestabe kernel: [   40.604151]          res 40/00:14:b0:01:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:15:02 honestabe kernel: [   41.137464]          res 40/00:14:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:15:02 honestabe kernel: [   41.137470]          res 40/00:14:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:15:02 honestabe kernel: [   41.137476]          res 40/00:14:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:15:02 honestabe kernel: [   41.632751]          res 40/00:14:b0:01:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:15:02 honestabe kernel: [   41.632757]          res 40/00:14:b0:01:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:15:02 honestabe kernel: [   41.632763]          res 40/00:14:b0:01:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:15:02 honestabe kernel: [   42.119479]          res 40/00:14:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:15:02 honestabe kernel: [   42.119486]          res 40/00:14:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 02:15:02 honestabe kernel: [   42.119493]          res 40/00:14:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 11:17:02 honestabe kernel: [   36.780617] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 14 11:17:02 honestabe kernel: [   42.616355]          res 40/00:04:00:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 11:17:02 honestabe kernel: [   43.171388]          res 40/00:0c:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 11:17:02 honestabe kernel: [   43.641006] hda: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
Sep 14 11:17:02 honestabe kernel: [   43.641011] hda: set_drive_speed_status: error=0x04 { AbortedCommand }
Sep 14 11:17:02 honestabe kernel: [   43.659865]          res 40/00:04:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 11:17:02 honestabe kernel: [   66.332693]          res 40/00:04:7f:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 11:17:10 honestabe kernel: [   72.700271]          res 40/00:04:7f:59:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 11:17:51 honestabe kernel: [   89.765382]          res 40/00:04:4f:00:e4/00:00:18:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 11:18:48 honestabe kernel: [  113.921320]          res 40/00:04:3f:c0:e1/00:00:1a:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 11:31:37 honestabe kernel: [   36.633686] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 14 11:31:37 honestabe kernel: [   43.598010] hda: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
Sep 14 11:31:37 honestabe kernel: [   43.598014] hda: set_drive_speed_status: error=0x04 { AbortedCommand }
Sep 14 11:31:37 honestabe kernel: [   56.795030]          res 40/00:04:00:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 11:31:37 honestabe kernel: [   57.508773]          res 40/00:04:a0:6d:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 11:31:37 honestabe kernel: [   58.066296]          res 40/00:14:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 11:31:37 honestabe kernel: [   58.066303]          res 40/00:14:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 11:31:37 honestabe kernel: [   58.565145]          res 40/00:14:e8:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 11:31:37 honestabe kernel: [   58.565151]          res 40/00:14:e8:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 11:31:37 honestabe kernel: [   58.565158]          res 40/00:14:e8:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 12:40:43 honestabe kernel: [   36.644891] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 14 12:40:43 honestabe kernel: [   41.045182] hda: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
Sep 14 12:40:43 honestabe kernel: [   41.045186] hda: set_drive_speed_status: error=0x04 { AbortedCommand }
Sep 14 12:40:43 honestabe kernel: [   44.142449]          res 40/00:0c:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 12:40:43 honestabe kernel: [   44.646948]          res 40/00:04:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 12:40:43 honestabe kernel: [   45.134830]          res 40/00:04:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 12:40:43 honestabe kernel: [   58.776288]          res 40/00:04:3f:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 12:44:44 honestabe kernel: [   36.618618] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 14 12:44:44 honestabe kernel: [   41.643130]          res 40/00:04:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 12:44:44 honestabe kernel: [   43.574889] hda: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
Sep 14 12:44:44 honestabe kernel: [   43.574893] hda: set_drive_speed_status: error=0x04 { AbortedCommand }
Sep 14 12:44:44 honestabe kernel: [   57.158830]          res 40/00:04:70:6d:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 12:44:44 honestabe kernel: [   61.470591]          res 40/00:04:57:01:00/00:00:00:00:00/40 Emask 0x52 (ATA bus error)
Sep 14 12:46:04 honestabe kernel: [   98.028928]          res 40/00:04:3f:80:78/00:00:1c:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 13:13:37 honestabe kernel: [   36.941162] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 14 13:13:37 honestabe kernel: [   42.829143]          res 40/00:14:a8:6d:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 13:13:37 honestabe kernel: [   42.829149]          res 40/00:14:a8:6d:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 13:13:37 honestabe kernel: [   43.823159] hda: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
Sep 14 13:13:37 honestabe kernel: [   43.823163] hda: set_drive_speed_status: error=0x04 { AbortedCommand }
Sep 14 13:15:02 honestabe kernel: [  102.781917] gweather-applet[6545]: segfault at a6 rip 7f8b3fd7e27d rsp 42d8f068 error 4
Sep 14 13:15:02 honestabe kernel: [  102.781949] gweather-applet[6543]: segfault at a6 rip 7f8b3fd7e27d rsp 41d8d068 error 4
Sep 14 13:26:44 honestabe kernel: [   36.543535] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 14 13:26:44 honestabe kernel: [   42.569898] hda: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
Sep 14 13:26:44 honestabe kernel: [   42.569903] hda: set_drive_speed_status: error=0x04 { AbortedCommand }
Sep 14 13:26:44 honestabe kernel: [   55.709624]          res 40/00:0c:81:59:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 14 13:28:07 honestabe kernel: [   98.155527]          res 41/84:00:56:00:9c/07:00:29:00:00/40 Emask 0x410 (ATA bus error) <F>
Sep 15 01:03:08 honestabe kernel: [   36.857654] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 15 01:03:08 honestabe kernel: [   42.844845]          res 40/00:0c:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 15 01:03:08 honestabe kernel: [   43.338663]          res 40/00:04:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 15 01:03:08 honestabe kernel: [   43.826326]          res 40/00:04:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 15 01:03:08 honestabe kernel: [   43.829902] hda: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
Sep 15 01:03:08 honestabe kernel: [   43.829906] hda: set_drive_speed_status: error=0x04 { AbortedCommand }
Sep 15 01:03:08 honestabe kernel: [   44.313231]          res 40/00:04:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 15 01:03:08 honestabe kernel: [   61.067778]          res 40/00:04:3f:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 15 01:03:08 honestabe kernel: [   65.565957]          res 40/00:04:cf:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 15 01:17:53 honestabe kernel: [  514.186190] setiathome_enha[5743]: segfault at 40423088 rip 7f7eed95dcfe rsp 40423090 error 6
Sep 15 01:17:54 honestabe kernel: [  514.487776] wcg_hpf2_rosett[5757]: segfault at ff7fbff4 rip 87fd280 rsp ff7fbed0 error 6
Sep 15 01:23:17 honestabe kernel: [   36.094986] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 15 01:23:17 honestabe kernel: [   39.736930] hda: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
Sep 15 01:23:17 honestabe kernel: [   39.736935] hda: set_drive_speed_status: error=0x04 { AbortedCommand }
Sep 15 01:23:17 honestabe kernel: [   43.592005]          res 40/00:04:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 15 01:23:17 honestabe kernel: [   44.087595]          res 40/00:04:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 15 01:23:17 honestabe kernel: [   56.575293]          res 40/00:14:a8:6d:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 15 01:23:17 honestabe kernel: [   56.575300]          res 40/00:14:a8:6d:70/00:00:74:00:00/40 Emask 0x50 (ATA bus error)
Sep 15 01:23:17 honestabe kernel: [   57.117518]          res 40/00:0c:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 15 01:23:17 honestabe kernel: [   57.601124]          res 40/00:04:68:00:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 15 01:23:17 honestabe kernel: [   60.660342]          res 40/00:04:2f:01:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
Sep 15 01:23:17 honestabe kernel: [   61.160038]          res 40/00:04:9f:01:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
```

---

### Post by krazyd on 2009-09-15
hmm. looks like it could be a hardware problem, but hard to tell without the full log.

could you upload /var/log/messages to [http://pastebin.com/](http://pastebin.com/), and post a link?

---

### Post by euphgeek on 2009-09-15
Sure, here you go:

[/var/log/messages]("http://pastebin.com/f7955c2d1")

---

### Post by euphgeek on 2009-09-15
My screen just went white again, so I took a look at the last 10 lines of /var/log/messages:

```
Sep 15 10:03:17 honestabe -- MARK --
Sep 15 10:23:17 honestabe -- MARK --
Sep 15 10:43:17 honestabe -- MARK --
Sep 15 11:03:17 honestabe -- MARK --
Sep 15 11:23:17 honestabe -- MARK --
Sep 15 11:43:18 honestabe -- MARK --
Sep 15 12:03:18 honestabe -- MARK --
Sep 15 12:15:27 honestabe kernel: [16582.757952] setiathome_enha[5727]: segfault at 40d9d088 rip 7f640ddc6cfe rsp 40d9d090 error 6
Sep 15 12:15:27 honestabe kernel: [16583.299264] wcg_hpf2_rosett[5741]: segfault at ff3fbff4 rip 87fd280 rsp ff3fbed0 error 6
Sep 15 12:43:59 honestabe -- MARK --
```

The white screen happened at around 12:53, so I'm thinking /var/log/messages isn't going to show us why this is happening.

---

### Post by krazyd on 2009-09-15
hmm, that log doesn't seem to show anything suspicious.

All I can think is some kind of hardware error (graphics card maybe?)

Perhaps try booting another distro (or even windows) and see if you get any problems - that would indicate hardware issues.

Aside from that I don't think I can help much :(

---

### Post by euphgeek on 2009-09-16
I thought it might be a hardware problem.  The graphics card is embedded in the motherboard, so I may have to replace the entire motherboard if that's the issue.  I'll try checking for bulged capacitors, I believe I may have seen one the last time I had the case open.

---

