---
title: "burn VCDs under Ubuntu"
date: 2005-12-07
forum: General Help
---

### Post by RikoW on 2005-12-07
Hi all,

since some time I unsuccessfully try to burn a VCD from miniDV videos I took.

I use Kino to capture the clips from the camera and convert them to mpeg files.

Then, I tun tovid to put several clips on one vcd and do the menues etc.

tovid creates then for me .cue and .bin files. Those I try to burn either via k3b or cdrdao, so far without success:

```
> sudo cdrdao write --device /dev/hdc vcd.xml.cue
Cdrdao version 1.1.9 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.

Using libscg version 'ubuntu-0.8ubuntu1'

/dev/hdc: HL-DT-ST RW/DVD GCC-4241N     Rev: A100
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)

Burning entire 79 mins disc.
Starting write at speed 10...
Pausing 10 seconds - hit CTRL-C to abort.
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
cmd finished after 0.002s timeout 180s
ERROR: Write data failed.
ERROR: Writing failed.
```

A similar error message comes when using k3b. 

I googled and searched various forums, but they all tell me, in principle I do the write thing. Unfortunately, the error message above us not very illuminating.
 
Otherwise, cds burn just fine with k3b, be it iso images, data cds, audio cds ...

Any idea, how I could try to fix that? I hate to boot to XP just to burn a VCD (which works as I tried yesterday).

Thanks and cheers,
             Riko

---

### Post by RikoW on 2005-12-09
Nobody? :(

Does that mean, nobody is actually trying to burn VCDs under Breezy or am I the only one who has problems here?

Cheers,

               Riko

---

### Post by vinil on 2006-01-11
hi... i have the same problem... but i think that it is about with the vcdimager.. because it seem to vcdimager create invalid cue files...  because i convert to iso  
and when i try to burn , nautilus say me . "invalid iso image or something"


can help with this...???

thanks

---

### Post by kingsidy on 2006-01-11
you can burn .bin and .cue images using nerolinux. Google for nerolinux. there is a debian package that install in ubuntu without any problems.

---

### Post by RikoW on 2006-01-12
actually, very recently (I think two days ago), i figured out the problem was actually with combination of the cd-writer hardware and the cdrdao driver. after putting in a different cd-rw drive, k3b burns VCDs would like a charm.

I created them with tovid, which also uses vcdimager to create the image files (as far as I recall).

I also tried nerolinux, which indeed would burn the bin file to the disk (with the old cd-rw drive), but unfortunately, my dvd player would not play them.

Cheers,

              Riko

---

### Post by jtpratt on 2006-03-16
I had some of the same problems, and found a few fixes.

try my help page for converting video in Ubuntu 5.10 and see if it helps:
[http://smorgasbord.net/convert_video_linux]("http://smorgasbord.net/convert_video_linux")

---

