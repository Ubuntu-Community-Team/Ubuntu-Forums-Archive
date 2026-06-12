---
title: "[n00b] Burning Data CD's"
date: 2005-11-04
forum: Desktop Environments
---

### Post by James_Nostack on 2005-11-04
I am having trouble burning CD's in Breezy: *An Error Occurred While Writing*.  There's no more data supplied.  Unfortunately I'm too clueless about Linux to figure out possible problems.

(a) I did not format the CD beforehand, just opened from shrinkwrap.

(b) I had this trouble using Hoary too--but discovered it after Breezy came out, so the problem-solvers had all migrated to the new version! ;)   Under Hoary, however, I got a detailed error message (I'll post it in a moment).  

Any advice?  I am generally quite happy with Ubuntu, but I need to be able to burn CD's.

---

### Post by James_Nostack on 2005-11-04
For reference, this is the error message I used to get under Hoary.  It may not be relevant under Breezy--

[i]cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
cdrecord: fifo had 64 puts and 0 gets.
cdrecord: OPC failed.
cmd finished after 60.041s timeout 60s
status: 0x4 (CONDITION MET/GOOD)
CDB: 54 01 00 00 00 00 00 00 00 00
cdrecord: Success. send opc: scsi sendcmd: no error
cdrecord: WARNING: This causes a high risk for buffer underruns.
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
SCSI buffer size: 64512
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Linux sg driver version: 3.5.27
Warning: Open by 'devname' is unintentional and not supported.
scsibus: -2 target: -2 lun: -2
devname: '/dev/hdc'
scsidev: '/dev/hdc'
cdrecord: WARNING: This causes a high risk for buffer underruns.
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: Continuing in 5 seconds...
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Asuming -tao mode.
cdrecord: No write mode specified.
[/i]

---

### Post by James_Nostack on 2005-11-05
(bump)

---

### Post by Remmelas on 2005-11-05
the permission denied line is kinda worrysome, have you tried burning with root priveledges to see if you get the same error?

---

### Post by James_Nostack on 2005-11-05
No - how would I go about doing that?  I'm sorry, I'm still kind of new to Linux.

I installed Gnomebaker, since it sounds like some people have been using that instead of Nautilus.  It seems to work, at least for a small sample file.  I'm still kind of curious why the "regular" CD burning function doesn't work though....

thanks for the suggestion, I'm willing to try it but not sure how,
James

---

