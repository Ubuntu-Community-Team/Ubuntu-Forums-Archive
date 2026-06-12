---
title: "Problem burning CDs XUbuntu 12.04"
date: 2012-06-21
forum: Desktop Environments
---

### Post by dnotman3 on 2012-06-21
Problems burning CD-ROM using Ubuntu 12.04 and XUbuntu 12.04.

My burner is quite new, and this was the first time I tried to burn a disk with it.  Burning failed on Ubuntu 12.04 with the default burner (whatever that was).  I tried using both a freshly CD-RW (freshly blanked on another machine with a known good burner), and a CD-R.  In both cases, the program started burning, but failed part way through.  Sorry - I didn't note the message at the time.   I blamed the new drive and proceeded to install XUbuntu 12.04, completely replacing my copy of Ubuntu 12.04.  Now that more important issues are out of the way I decided to try to track down the problem with the drive.  It reads CD-RWs perfectly, however xfburn's blank-disk function won't work at all.  It just says "operation complete", but the disk hasn't been touched, and can still be mounted.  The failure isn't because the disk is mounted - I checked that straight away.

And the problem isn't the drive hardware either.  I was able to boot WinDoze and burn and verify a CD-RW (the same disk, in fact).

The system appears to correctly identify the drive.  Here's a dmesg extract:

[    1.124922] scsi 4:0:0:0: CD-ROM            PHILIPS  DVD+-RW SDVD8441 PA48 PQ: 0 ANSI: 5
[    1.128095] sr0: scsi3-mmc drive: 12x/24x writer cd/rw xa/form2 cdda tray
[    1.128103] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.128445] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.128634] sr 4:0:0:0: Attached scsi generic sg1 type 5

There weren't any additional messages pertaining to the drive or xfburn at the tail end of the dmesg report.

Does anyone have any ideas about how to proceed?

---

### Post by Jose Catre-Vandis on 2012-06-21
I've not had  much luck with xfburn (PC crash) and brasero (just didn't work) so I always end up installing **K3b** and this always works fine. I know this pulls in a lot of kde / qt stuff, but it solves the problem.

---

### Post by dnotman3 on 2012-06-22
Some more clues:

* When I boot the system with a formatted CD-ROM in the drive, an icon for it appears on the desktop.  If I eject that disk and re-insert it, no icon ever appears.

* To check out the hardware I booted Puppy Linux 4.3.1.  Puppy is able to detect when a CD-ROM has been inserted after booting, so I'm guessing that the hardware is working ok.

* Back to XUbuntu 12.04 - insert a disk after booting.  Wait a while - no icon.  So I go to mount it manually:
                       sudo mount | grep sr0            ... drive isn't mounted
                       sudo mount -t iso9660 /dev/sr0 /mnt/sr0

  The system responds with an error message "Drive in use" (or maybe it was "already mounted"), followed by another message that the disk has been mounted as /media/.... (not as /mnt/sr0 as I requested!), and the CD-ROM icon appears on my desktop!

So it looks to me like the hardware is working OK, but the communication between the hardware and the desktop agent isn't.

---

