---
title: "read raw data from bad cd?"
date: 2009-03-30
forum: General Help
---

### Post by thebigkevdogg on 2009-03-30
Hi all,

I'm not quite sure the best place (forum/list) to ask this question (any ideas?) but thought someone here  might have ideas.

Basically what I have is a bad audio CD (from a live performance of my band, only copy). Basically it looks like the CD writer started writing a little ways into the disk by looking at the bottom of the CD (it's a CD-R). When you put it into a computer it thinks it's a blank CD, but there really is data on there...it just starts in the wrong place. It looks like the data starts about 0.5 cm into the data portion of the disk.

I really want to get the data off of this disk, and I can worry about converting it to audio files when I get it, but I am just trying to get access to the raw binary right now. This is the error that I get with trying to use dd:

```
kevin@milner:~$ dd if=/dev/cdrom of=/tmp/cdimg1.iso
dd: reading `/dev/cdrom': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.0209529 s, 0.0 kB/s
```

Does anyone have any ideas about a way to access this data, or a better place to ask the question?

Thanks!

~Kevin

---

### Post by aeiah on 2009-03-30
try adding some arguments to your command. perhaps:

conv=noerror

may ignore the input/output error, although i think it only ignores read errors. worth a try.

perhaps add notrunc in there too...

dd if=/dev/cdrom of=/tmp/cdimg1.iso conv=noerror,notrunc


it seems like your biggest problem is that it sees that the start of the cd is empty, and doesn't get any further. you need to find a way to force it to read every single bit of the cd, even the bits that are completely empty...

---

### Post by aeiah on 2009-03-30
perhaps the program 'readcd' could help as well. ive never used it but there may be an option to force it to dump everything despite ubuntu thinking it's empty. its in the repos

---

### Post by rjl6591 on 2009-03-30
Another thing that may be worth a try is cdparanoia. There's an ubuntu package for it.

---

### Post by thebigkevdogg on 2009-03-30
> **aeiah said:**
> perhaps the program 'readcd' could help as well. ive never used it but there may be an option to force it to dump everything despite ubuntu thinking it's empty. its in the repos

It looks like readcd is now readom. I feel like I'm getting closer, but still no success:

```
kevin@milner:~$ readom -noerror -nocorr -notrunc dev=/dev/cdrom -f /tmp/cd.raw
Read  speed:  4234 kB/s (CD  24x, DVD  3x).
Write speed:  1764 kB/s (CD  10x, DVD  1x).
Capacity: 1 Blocks = 2 kBytes = 0 MBytes = 0 prMB
Sectorsize: 2048 Bytes
Copy from SCSI (1,0,0) disk to file '/tmp/cd.raw'
end:         1
Errno: 5 (Input/output error), read_g1 scsi sendcmd: no error
CDB:  28 00 00 00 00 00 00 00 01 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 25 00 00 00 00 0A 28 0A 01 80 64 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0
Sense flags: Blk 0 (valid) illegal block length 
cmd finished after 0.002s timeout 40s
readom: Input/output error. Cannot read source disk
readom: Retrying from sector 0.
.~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~
readom: Input/output error. Error on sector 0 not corrected. Total of 1 errors.
readom: -noerror set, continuing ...
addr:        1
Time total: 0.854sec
Read 2.00 kB at 2.3 kB/sec.
Max corected retry count was 0 (limited to 128).
The following 1 sector(s) could not be read correctly:
0
```

also the additional flags to dd made it keep spitting out the same error message infinitely, but didn't make it progress on the disk...it wasn't even spinning.

I guess a possible solution would be to start writing to the disk, which I assume would fail when it got to the portion that has already been written to. Then I could image the disk and find the place where what I was writing (which would be either pure 0's or maybe some binary pattern) ended and the audio began. I assume i'd have to write it in CDROM mode 2 with 2336 bytes per sector though: [http://en.wikipedia.org/wiki/CD-ROM#CD_sector_contents](http://en.wikipedia.org/wiki/CD-ROM#CD_sector_contents)

What do you think?

---

### Post by shaggy999 on 2009-03-30
There are a number of packages you might want to look into:

rdd
ddrescue
dcfldd

There is a GUI intterface to ddrescue in the package gddrescue

---

### Post by thebigkevdogg on 2009-03-30
> **shaggy999 said:**
> There are a number of packages you might want to look into:

rdd
ddrescue
dcfldd

There is a GUI intterface to ddrescue in the package gddrescue

I tried all of those tools without success. I'm beginning to believe that it's impossible without writing something at the driver level. I also tried writing silence to it, but no luck (with gui tools or cdrecord):

```
kevin@milner:~$ cdrecord -ignsize -audio data/silence.raw 
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.Device was not specified. Trying to find an appropriate drive...
Looking for a CD-R drive to store 302.81 MiB...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-U10N '
Revision       : '1.05'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
wodim: WARNING: Data may not fit on current disk.
wodim: Notice: Overburning active. Trying to write more than the official disk capacity.
Speed set to 1764 KB/s
Starting to write CD/DVD at speed  10.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 05 A8 81 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 34 1D 04 80 10 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x10 Qual 0x00 (id crc or ecc error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 13.871s timeout 40s
write track data: error after 145678176 bytes
wodim: A write error occured.
wodim: Please properly read the error message above.
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 5B 02 00 80 72 03 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x03 (session fixation error - incomplete track in session) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.857s timeout 480s
cmd finished after 0.857s timeout 480s
wodim: Cannot fixate disk.
```

---

