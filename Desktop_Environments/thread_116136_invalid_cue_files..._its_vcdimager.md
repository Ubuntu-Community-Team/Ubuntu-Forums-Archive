---
title: "invalid cue files... its vcdimager???"
date: 2006-01-12
forum: Desktop Environments
---

### Post by vinil on 2006-01-12
hi... i try to burn cue and bin files... and it seems to be invalid... i tried with k3b,gnomebaker,nerolinux ... and also converted into a iso file... nero tell me that the iso is invalid...

thi is the output of the failed burn

```
Cdrdao version 1.1.9 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.

Using libscg version 'ubuntu-0.8ubuntu1'

/dev/hdc: HL-DT-ST RW/DVD GCC-4243N        Rev: A102
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)

Burning entire 79 mins disc.
Starting write at speed 4...
Process can be aborted with QUIT signal (usually CTRL-\).
Turning BURN-Proof on
Executing power calibration...
Power calibration successful.
cdrdao: Success.  : scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1A 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 60736
cmd finished after 0.001s timeout 180s
ERROR: Write data failed.
ERROR: Writing failed.
```


here is my cue file...

```
FILE "videocd.bin" BINARY

  TRACK 01 MODE2/2352

    FLAGS DCP

    INDEX 01 00:00:00

  TRACK 02 MODE2/2352

    FLAGS DCP

    INDEX 00 00:04:00

    INDEX 01 00:06:00
```

thanks ...

---

