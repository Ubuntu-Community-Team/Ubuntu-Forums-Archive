---
title: "[n00b] CD burning under Nautilus"
date: 2005-10-25
forum: Desktop Environments
---

### Post by James_Nostack on 2005-10-25
Hi - I am trying to burn a CD using the instructions in the desktop Help.  (Help - Desktop - Desktop User Guide - Nautilus File Manager - Writing a CD.)  

When I do that, however, the process runs for a little bit, and then spits out this error message:

[i]cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
cdrecord: fifo had 64 puts and 0 gets.
cdrecord: OPC failed.
cmd finished after 60.041s timeout 60s
status: 0x4 (CONDITION MET/GOOD)
CDB:  54 01 00 00 00 00 00 00 00 00
cdrecord: Success. send opc: scsi sendcmd: no error
cdrecord: WARNING: This causes a high risk for buffer underruns.
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
SCSI buffer size: 64512
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
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
cdrecord: No write mode specified.[/i]

This was a brand-new blank CD.  I did not format it beforehand (because I'm not sure how to do that under Ubuntu).  

Any advice would be appreciated.  Thanks!

---

