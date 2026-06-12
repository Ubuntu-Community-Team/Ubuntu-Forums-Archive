---
title: "R/W errors on DVD on Dell Studio XPS 8100"
date: 2010-08-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TimGJ on 2010-08-12
Hello there.

I've recently bought a Dell Studio XPS 8100 PC, on which I run Ubuntu 10.04 (Linux scally 2.6.32-24-generic-pae #39-Ubuntu SMP Wed Jul 28 07:39:26 UTC 2010 i686 GNU/Linux)

I get a lot of errors when reading and writing DVDs on its DVD-+RW drive (>90% failure rate). So I've tried swapping the drive out for one from my previous PC, but this too shows the same errors in the new Dell system. For example if I attempt to make an ISO image of a DVD using K3B I get something like p, li { white-space: pre-wrap; }  [FONT=Monospace]
[/FONT]
[FONT=Monospace]Devices[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]HL-DT-ST DVDRAM GSA-H60N CV02 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7][/FONT]
 
 [FONT=Monospace]K3b::DataTrackReader[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]reading sectors 0 to 4108865 with sector size 2048. Length: 4108866 sectors, 8414957568 bytes.[/FONT]
 [FONT=Monospace]using buffer size of 128 blocks.[/FONT]
 [FONT=Monospace]Problem while reading. Retrying from sector 78496.[/FONT]
 [FONT=Monospace]Read error in sector 78496.[/FONT]
 [FONT=Monospace]Read a total of 78496 sectors (160759808 bytes)[/FONT]
 
 [FONT=Monospace]System[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]K3b Version: 1.91.0[/FONT]
 [FONT=Monospace]KDE Version: 4.4.2 (KDE 4.4.2)[/FONT]
 [FONT=Monospace]QT Version:tim@scally:~$ dd if=/dev/dvd of=foo.iso
dd: reading `/dev/dvd': Input/output error
70880+0 records in
70880+0 records out
36290560 bytes (36 MB) copied, 8.02726 s, 4.5 MB/s
  4.6.2[/FONT]
 [FONT=Monospace]Kernel:      2.6.32-24-generic-pae[/FONT]
 
 
Equally if I try something like dd I get problems:

tim@scally:~$ dd if=/dev/dvd of=foo.iso
dd: reading `/dev/dvd': Input/output error
70880+0 records in
 70880+0 records out
 36290560 bytes (36 MB) copied, 8.02726 s, 4.5 MB/s
 
And the log shows

Aug 12 10:10:16 scally kernel: [36822.269657] UDF-fs: Partition marked readonly; forcing readonly mount
Aug 12 10:10:16 scally kernel: [36822.315826] UDF-fs INFO UDF: Mounting volume 'SKA-2010-02-17V1', timestamp 2010/02/17 15:58 (103c)
Aug 12 10:13:19 scally kernel: [37005.693479] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 12 10:13:19 scally kernel: [37005.693487] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 12 10:13:19 scally kernel: [37005.693495] sr 3:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 12 10:13:19 scally kernel: [37005.693507] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 3b ad dc 00 00 02 00
Aug 12 10:13:19 scally kernel: [37005.693525] end_request: I/O error, dev sr0, sector 15644528
Aug 12 10:13:19 scally kernel: [37005.693531] __ratelimit: 118 callbacks suppressed
Aug 12 10:13:19 scally kernel: [37005.693536] Buffer I/O error on device sr0, logical block 1955566
Aug 12 10:13:19 scally kernel: [37005.697501] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 12 10:13:19 scally kernel: [37005.697504] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 12 10:13:19 scally kernel: [37005.697507] sr 3:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 12 10:13:19 scally kernel: [37005.697511] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 3b ad dc 00 00 02 00
Aug 12 10:13:19 scally kernel: [37005.697516] end_request: I/O error, dev sr0, sector 15644528
Aug 12 10:13:19 scally kernel: [37005.697518] Buffer I/O error on device sr0, logical block 1955566
Aug 12 10:13:20 scally kernel: [37006.733669] UDF-fs: Partition marked readonly; forcing readonly mount
Aug 12 10:13:20 scally kernel: [37006.792604] UDF-fs INFO UDF: Mounting volume 'BBCDVD1602', timestamp 2007/02/04 12:51 (103c)
Aug 12 10:13:36 scally kernel: [37022.170364] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 12 10:13:36 scally kernel: [37022.170371] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 12 10:13:36 scally kernel: [37022.170378] sr 3:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 12 10:13:36 scally kernel: [37022.170387] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 45 38 00 00 40 00
Aug 12 10:13:36 scally kernel: [37022.170400] end_request: I/O error, dev sr0, sector 70880
Aug 12 10:13:36 scally kernel: [37022.170406] Buffer I/O error on device sr0, logical block 17720
Aug 12 10:13:36 scally kernel: [37022.170410] Buffer I/O error on device sr0, logical block 17721
Aug 12 10:13:36 scally kernel: [37022.170418] Buffer I/O error on device sr0, logical block 17722
Aug 12 10:13:36 scally kernel: [37022.170422] Buffer I/O error on device sr0, logical block 17723
Aug 12 10:13:36 scally kernel: [37022.170425] Buffer I/O error on device sr0, logical block 17724
Aug 12 10:13:36 scally kernel: [37022.170429] Buffer I/O error on device sr0, logical block 17725
Aug 12 10:13:36 scally kernel: [37022.170433] Buffer I/O error on device sr0, logical block 17726
Aug 12 10:13:36 scally kernel: [37022.170437] Buffer I/O error on device sr0, logical block 17727
Aug 12 10:13:36 scally kernel: [37022.170441] Buffer I/O error on device sr0, logical block 17728
Aug 12 10:13:36 scally kernel: [37022.170444] Buffer I/O error on device sr0, logical block 17729
Aug 12 10:13:36 scally kernel: [37022.240847] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug 12 10:13:36 scally kernel: [37022.240854] sr 3:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Aug 12 10:13:36 scally kernel: [37022.240860] sr 3:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
Aug 12 10:13:36 scally kernel: [37022.240869] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 45 78 00 00 40 00
Aug 12 10:13:36 scally kernel: [37022.240882] end_request: I/O error, dev sr0, sector 71136

It definitely seems to be a problem which is specific to the Dell system as the DVD drive I am now using worked fine in its predecessor which was running identical software. Does this look like a hardware problem or BIOS settings or what? I'm rapidly running out of ideas.

Cheers.

Tim.

---

