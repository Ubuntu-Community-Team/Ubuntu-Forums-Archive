---
title: "cdrom problem(s)"
date: 2006-10-02
forum: Desktop Environments
---

### Post by Lemming-by-nature on 2006-10-02
Ok after buildng my new 64 Dapper, Im having a few problems with my cdrom drive..

It sometimes will not mount the cdrom drive (sometimes it will just pretend
it isn't there until the system is restarted) - this is a bit of an issue but
not major since I can put up with it

the major issue is that it just decides it will not burn cds anymore.

the drive is a LITE-ON DVDRW SHM-165P6S and is /dev/hda
after doing dmesg and greping for "hda" "cdrom" and "ide-cd" I get:

> [   37.594998]     ide0: BM-DMA at 0xfe00-0xfe07, BIOS settings: hda:DMA, hdb:pio
[   38.331600] hda: LITE-ON DVDRW SHM-165P6S, ATAPI CD/DVD-ROM drive
[   39.598938] hda: ATAPI 12X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   55.833327] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[  146.790342] hda: lost interrupt
[  178.131840] hda: lost interrupt
[  208.073846] hda: lost interrupt
[  238.844701] hda: lost interrupt
: // many similar lines
[ 1605.749327] hda: lost interrupt
[ 1635.693363] hda: lost interrupt
[   73.662396] cdrom: This disc doesn't have any tracks I recognize!
[  146.790336] ide-cd: cmd 0x3 timed out
[  178.131834] ide-cd: cmd 0x3 timed out
: // many similar "cmd 0x3" timed out lines

---

### Post by Lemming-by-nature on 2006-10-08
bump

---

### Post by dcstar on 2006-10-08
> **Lemming-by-nature said:**
> Ok after buildng my new 64 Dapper, Im having a few problems with my cdrom drive..

It sometimes will not mount the cdrom drive (sometimes it will just pretend
it isn't there until the system is restarted) - this is a bit of an issue but
not major since I can put up with it

the major issue is that it just decides it will not burn cds anymore.

the drive is a LITE-ON DVDRW SHM-165P6S and is /dev/hda
after doing dmesg and greping for "hda" "cdrom" and "ide-cd" I get:

Your /dev/hda device seems to be using DMA where the other one is using PIO.

You may be able to set/unset the mode with the "sudo hdparm" command for /dev/hda and see if it changes its behaviour.

Even trying to set the other drive to DMA mode may make a difference (because they are on the same IDE channel), try some things out and see if it makes any difference.

---

### Post by Kinslayer on 2007-04-16
I had a problem with long startup & shutdown times.  The problem was my cd rom & dvd rom weren't mounting properly.  They were attached to the same ide cable.  How I fixed it was I shutdown the system, unplugged the cables from each, & rebooted.  It started right up.  Aha.  I shutdown again, which took less than a minute instead of the usual 5-10 minutes.  I connected one drive, started up, & it loaded quickly.  I repeated this with the second drive, with no problems.  A third time with both booted up quickly, and it hasn't been an issue since, at least for the couple of days since I've done this.

---

