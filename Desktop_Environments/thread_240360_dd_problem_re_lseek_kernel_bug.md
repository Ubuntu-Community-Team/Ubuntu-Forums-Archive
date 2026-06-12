---
title: "dd problem re: lseek kernel bug"
date: 2006-08-20
forum: Desktop Environments
---

### Post by TasKiNG on 2006-08-20
I have a sony SDT-5010 DDS tape drive that I am trying to use for backups.
Kdat does not like it. and due to the lack of a good gui based back-up program I am now looking at command line backup scripts.
I have found one that almost works called flexbackup.
However when I run it with sudo flexbackup -newtape I get a segmentation fault reported.
The part of the scrip that gives this is :-
dd ibs=32k obs=32k conv=noerror,sync count=1 if=/dev/nst0 2>/dev/null

removing the 2>/dev/null in order to see the output I get :-

dd: reading `/dev/nst0': Input/output error
0+0 records in
0+0 records out
%<PRIuMAX> bytes ((null)) copied, 0.003493 seconds, 0.0 kB/s
dd: warning: working around lseek kernel bug for file (/dev/nst0)
  of mt_type=0x72 -- see <sys/mtio.h> for the list of types
dd: cannot work around kernel bug after all
dd: `/dev/nst0': cannot seek
0+1 records in
1+0 records out
Segmentation fault

Any ideas ?

Any suggestions for a good gui based tape backup prog would also be gr8

Cheers

Note: I am running the i386 kernel under kubuntu 6.06.1 dapper drake

---

### Post by bkix on 2006-09-04
hi,

this should work for you:

[http://ubuntuforums.org/showthread.php?t=247624](http://ubuntuforums.org/showthread.php?t=247624)

---

