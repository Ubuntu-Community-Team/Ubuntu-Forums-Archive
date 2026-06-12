---
title: "[SOLVED] Ubuntu freeze during a disk write"
date: 2007-07-18
forum: Dell  Ubuntu Support
---

### Post by arielUBA on 2007-07-18
Hello,

I have a Dell Precision 690, and I've decided to install Ubuntu Feisty.
While I was installing, ubuntu freeze (near 34%), but some minutes later it continues. At that moment I thought that it might be related with cdrom drive.
But... the problem persists when an application tries to write to disk

When the computer got freeze, the /var/log/messages had a lot of kernel errors like:
[I]command: Write(10): 2a 00 0f 14 df 6a 00 00 08 00
[ 4055.440000] mptscsih: ioc0: task abort: FAILED (sc=f50166c0)
[ 4055.440000] mptscsih: ioc0: attempting task abort! (sc=f575fa80)
[/I]

LSI SAS Firmware v. 00.10.49.00
BIOS v. 06.12.02.00

Can anyone help me to solve this problem?

Sorry my poor English!

$ uname -a
Linux gmartinepc 2.6.20-16-server-bigiron #2 SMP Thu Jun 7 20:29:34 UTC 2007 i686 GNU/Linux

$ cat /proc/mpt/summary 
ioc0: LSISAS1068, FwRev=000a3100h, Ports=1, MaxQ=286, IRQ=21

$ cat /proc/mpt/version 
mptlinux-3.04.03
  Fusion MPT base driver
  Fusion MPT SAS host driver

$ cat /proc/scsi/scsi 
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: HITACHI  Model: HUS151473VLS300  Rev: A48B
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: HITACHI  Model: HUS151473VLS300  Rev: A48B
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi0 Channel: 01 Id: 00 Lun: 00
  Vendor: Dell     Model: VIRTUAL DISK     Rev: 1028
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi7 Channel: 00 Id: 00 Lun: 00
  Vendor: TSSTcorp Model: DVD-ROM TS-H352C Rev: DE02
  Type:   CD-ROM                           ANSI SCSI revision: 05
Host: scsi7 Channel: 00 Id: 01 Lun: 00
  Vendor: PHILIPS  Model: DVD+-RW DVD8801  Rev: AD21
  Type:   CD-ROM                           ANSI SCSI revision: 05


$ cat /var/log/messages
....
Jul 12 11:49:02 gmartinepc kernel: [ 4054.540000]         command: Write(10): 2a 00 0f 14 d7 6a 00 04 00 00
Jul 12 11:49:02 gmartinepc kernel: [ 4054.840000] mptscsih: ioc0: task abort: FAILED (sc=f5016300)
Jul 12 11:49:02 gmartinepc kernel: [ 4054.840000] mptscsih: ioc0: attempting task abort! (sc=f5016e40)
Jul 12 11:49:02 gmartinepc kernel: [ 4054.840000] sd 6:1:0:0: 
Jul 12 11:49:02 gmartinepc kernel: [ 4054.840000]         command: Write(10): 2a 00 0f 14 db 6a 00 04 00 00
Jul 12 11:49:02 gmartinepc kernel: [ 4055.140000] mptscsih: ioc0: task abort: FAILED (sc=f5016e40)
Jul 12 11:49:02 gmartinepc kernel: [ 4055.140000] mptscsih: ioc0: attempting task abort! (sc=f50166c0)
Jul 12 11:49:02 gmartinepc kernel: [ 4055.140000] sd 6:1:0:0: 
Jul 12 11:49:02 gmartinepc kernel: [ 4055.140000]         command: Write(10): 2a 00 0f 14 df 6a 00 00 08 00
Jul 12 11:49:02 gmartinepc kernel: [ 4055.440000] mptscsih: ioc0: task abort: FAILED (sc=f50166c0)
Jul 12 11:49:02 gmartinepc kernel: [ 4055.440000] mptscsih: ioc0: attempting task abort! (sc=f575fa80)
Jul 12 11:49:02 gmartinepc kernel: [ 4055.440000] sd 6:1:0:0: 
Jul 12 11:49:02 gmartinepc kernel: [ 4055.440000]         command: Write(10): 2a 00 0f 14 df 72 00 04 00 00
Jul 12 11:49:02 gmartinepc kernel: [ 4055.740000] mptscsih: ioc0: task abort: FAILED (sc=f575fa80)
Jul 12 11:49:02 gmartinepc kernel: [ 4055.740000] mptscsih: ioc0: attempting task abort! (sc=f575fe40)
Jul 12 11:49:02 gmartinepc kernel: [ 4055.740000] sd 6:1:0:0: 
Jul 12 11:49:02 gmartinepc kernel: [ 4055.740000]         command: Write(10): 2a 00 0f 14 e3 72 00 00 e0 00
Jul 12 11:49:02 gmartinepc kernel: [ 4056.040000] mptscsih: ioc0: task abort: FAILED (sc=f575fe40)
Jul 12 11:49:02 gmartinepc kernel: [ 4056.040000] mptscsih: ioc0: attempting task abort! (sc=f575fbc0)
Jul 12 11:49:02 gmartinepc kernel: [ 4056.040000] sd 6:1:0:0: 
Jul 12 11:49:02 gmartinepc kernel: [ 4056.040000]         command: Write(10): 2a 00 0f 14 e7 12 00 01 68 00
Jul 12 11:49:02 gmartinepc kernel: [ 4056.340000] mptscsih: ioc0: task abort: FAILED (sc=f575fbc0)
Jul 12 11:49:02 gmartinepc kernel: [ 4056.340000] mptscsih: ioc0: attempting target reset! (sc=f3f86800)
Jul 12 11:49:02 gmartinepc kernel: [ 4056.340000] sd 6:1:0:0: 
Jul 12 11:49:02 gmartinepc kernel: [ 4056.340000]         command: Write(10): 2a 00 0f 0d 63 ca 00 00 38 00
Jul 12 11:49:02 gmartinepc kernel: [ 4057.210000] mptbase: ioc0: LogInfo(0x31140000): Originator={PL}, Code={IO Executed}, SubCode(0x0000)
Jul 12 11:49:02 gmartinepc last message repeated 6 times
Jul 12 11:49:02 gmartinepc kernel: [ 4057.220000] mptbase: ioc0: LogInfo(0x31140000): Originator={PL}, Code={IO Executed}, SubCode(0x0000)
Jul 12 11:49:02 gmartinepc last message repeated 16 times
Jul 12 11:49:02 gmartinepc kernel: [ 4057.420000] mptscsih: ioc0: target reset: SUCCESS (sc=f3f86800)

---

### Post by vmikalinis on 2007-07-30
There is some issue with this controller.

I am running the same version of ubuntu on a poweredge sc440 and it is EXTREMELY slow.  Painfully slow.  The bios of the controller has no options.  So I'm stuck at this point.

---

### Post by arielUBA on 2007-08-03
Yes, you are right. After some calls to Technical Support they offered me to change hard disk's.

The new disks are Maxtor, and the problem disappear.
---------------
Dell now is distributing a hard dirk firmware upgrade
[http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R162996&formatcnt=1&libid=0&fileid=218832](http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R162996&formatcnt=1&libid=0&fileid=218832)

---

