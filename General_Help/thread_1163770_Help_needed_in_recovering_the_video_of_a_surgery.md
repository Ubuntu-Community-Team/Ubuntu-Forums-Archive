---
title: "Help needed in recovering the video of a surgery"
date: 2009-05-19
forum: General Help
---

### Post by Wydarr on 2009-05-19
Good day everybody!
I am in need of immediate assistance to recover some data from a DVD. To make a long story short:
My wife had surgery a couple of days ago, and it was recorded on a DVD recorder in the OR. The problem is that the DVD is unreadable on anything except the machine that recorded it. Tried it on 4 different computers, and nothing. On the windows machine (yeah I know, God forbid, but I was desperate :) ) I've tried ISO Buster and CDRoller. ISO Buster "pretends to work very hard, it produces images of the tracks, but the ISOs are empty. CDRoller... doesn't even bother. 

In Linux (Kubuntu 9.04) I get the following output when inserting the DVD into the drive (dmesg |tail -n20)

[569918.067561] cdrom: This disc doesn't have any tracks I recognize!
[569925.354157] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[569925.354166] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current]
[569925.354173] Info fld=0x0
[569925.354176] sr 5:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[569925.354184] end_request: I/O error, dev sr0, sector 0
[569925.354192] Buffer I/O error on device sr0, logical block 0
[569932.353076] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[569932.353084] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current]
[569932.353092] Info fld=0x0
[569932.353094] sr 5:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[569932.353102] end_request: I/O error, dev sr0, sector 0
[569932.353110] Buffer I/O error on device sr0, logical block 0


I've tried to copy the content with dd even using the noerror option, but again failure.
 
When using dvdisaster I get a "Reading aborted Invalid or damaged ecc file" error at the very beginning when I try to read the DVD. (Even after editing the preferences to ignore fatal errors). Upon further tweaking I have ONCE managed to read the disk, but it reports 100% Unreadable / skipped sectors, and when I try to create the image it aborts with "unrecoverable error" and we're back at square one. 

I have tried dares, dares_qt, dd_rescue and all of them are reporting only 2Kb of working data. 

Dares-qt:

dares 0.6.5 started at Tue May 19 08:54:43 2009
opening image /dev/cdrom: ok
Could not load file magic database file 'magic', using default database
, 0: Warning: using regular magic file `/etc/magic'
finished: scanned 0 2K blocks, found 0 files


dd_rescue

dd_rescue -v /dev/cdrom /media/Storage/project/operatie.iso
dd_rescue: (info): about to transfer 0.0 kBytes from /dev/cdrom to /media/Storage/project/operatie.iso
dd_rescue: (info): blocksizes: soft 65536, hard 512
dd_rescue: (info): starting positions: in 0.0k, out 0.0k
dd_rescue: (info): Logfile: (none), Maxerr: 0
dd_rescue: (info): Reverse: no , Trunc: no , interactive: no
dd_rescue: (info): abort on Write errs: no , spArse write: if err
dd_rescue: (info): ipos:         0.0k, opos:         0.0k, xferd:         0.0k
                   errs:      0, errxfer:         0.0k, succxfer:         0.0k
             +curr.rate:        0kB/s, avg.rate:        0kB/s, avg.load:  0.0%
dd_rescue: (info): /dev/cdrom (0.0k): EOF


I have tried to view the content of the first few sectors, and the only intelligible thing I've managed to extract is a line that says "Sonata DVD-R", which upon further reading seems to be a kind of tamper proof format used in sensitive areas to prevent altering the video content. 

Right about now, I have run out of ideas, so anything you may suggest would be welcomed. Thank you in advance for your assistance.

---

### Post by KhurramM on 2009-05-19
To the information of all, if u write a Cd/DVD at higher X rate not available on other machines, then u cant read it on other machines.

Best option to write a Cd is at 16x or 18x max

Try Dvd at max 1x or 2x.

U may have the option of 20x, just dont use it.

Such media fail to run on lower ability hardwares.

Always, Keep your all work in hand to be backwards compatible. ;)


If the windows is reading it, try to copy the file(s) onto hard and re-write at a slower rate. Hope u get recover your data.

Or try a computer repair technician, he will probably do something for u.

---

### Post by geraldvillorente on 2009-05-19
What is the current extension of that file? Do you have a backup of that file aside from DVD?

EDIT: If the original file is available try to burn it in a lower speed as mentioned above by KhurramM. The slower the better!

---

### Post by lisati on 2009-05-19
Are you able to open up the DVD as if it were a DVD-ROM? If so, the contents might provide some clues as to the format. Regular DVDs usually have a folder named VIDEO_TS and sometimes a folder AUDIO_TS

---

### Post by Wydarr on 2009-05-19
First and foremost, let me restate this: The DVD that I am trying to view / recover was recorded IN SURGERY, by the DVD recorder in the OR (Operating Room), kinda like the way footage is recorded from a security camera. Hence I don't have the file to burn it again, I cannot keep my work to be backwards compatible, I cannot choose the DVD writing speed, or apply any technique regarding RECORDING the data. 

Second: I cannot mount the disk. Here is the output of the mount command:

sudo mount -t iso9660 /dev/scd0 /media/cdrom
[sudo] password for wydarr:
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and here's once more the output of dmesg | tail, this time from the failed mount attempt:

[   55.042894] cdrom: This disc doesn't have any tracks I recognize!
[   61.672172] Marking TSC unstable due to cpufreq changes
[   62.144028] Clocksource tsc unstable (delta = -211176557 ns)
[  402.289395] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  402.289404] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current]
[  402.289411] Info fld=0x10
[  402.289414] sr 5:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  402.289422] end_request: I/O error, dev sr0, sector 64
[  402.289459] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

I get the same errors when attempting to mount it as a udf filesystem. 

Third: In ISO Buster I have managed to view the structure of the DVD: It consists of 6 tracks, on track 4 which is about 600 MB, there is a folder which looks like a regular DVD (with VideoTS and AudioTS and a couple of tracks that are a couple of hundred MB each). There is also Track 6, which has 2 GB but there is no subdirectory or file in its structure. 

I have also tried viewing it "as is" in VLC Media Player, but no luck there too. 

So, to sum it up: the disk I have is the MASTER disk, the only one that gets to be recorded "LIVE", in the operating room, with video feed from the miniature camera that captures the procedure itself. No way am I asking my wife to repeat surgery all over again. I have tried beginner and intermediate methods of recovering the data from the disk, which, I say again, CAN BE VIEWED on the master recorder (the one in the OR), which rules out physical damage to the disk, or loss of data due to faulty recording. I suspect one of two things: either Track 0 of the disk is written in an unorthodox way, to prevent tampering or duplication, or the file format is a bit strange altogether. 

I am most eagerly waiting for your feedback and solutions.

---

