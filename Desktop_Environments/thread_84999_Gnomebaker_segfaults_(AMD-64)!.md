---
title: "Gnomebaker segfaults (AMD-64)!"
date: 2005-11-01
forum: Desktop Environments
---

### Post by jvictor on 2005-11-01
Hi guys 
Gnomebaker segfaults whenever i try to blank a CDRW.. Does anyone have similar issues? I use AMD 64

**dmesg o/p::**
gnomebaker[7897]: segfault at 00007fff00000000 rip 00002aaab05a1b30 rsp 00007fffffcab040 error 4

**/var/log/messages:**

gnomebaker[7897]: segfault at 00007fff00000000 rip 00002aaab05a1b30 rsp 00007fffffcab040 error 4

**cdrecord -scanbus**

cdrecord -scanbus
Cdrecord-Clone 2.01.01a01 (x86_64-unknown-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-9-amd64-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

**cdrecord -dev=ATAPI -scanbus**
Cdrecord-Clone 2.01.01a01 (x86_64-unknown-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-9-amd64-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: 'ATAPI'
devname: 'ATAPI'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related Linux kernel interface code seems to be unmaintained.
Warning: There is absolutely NO DMA, operations thus are slow.
cdrecord: No such file or directory. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .us

---

### Post by jvictor on 2005-11-05
The latest deb version from [http://packages.debian.org/unstable/gnome/gnomebaker](http://packages.debian.org/unstable/gnome/gnomebaker)

does not segfault and works perfectly :-) 

Should I log a bug against the default 0.4 distributed for AMD64/Breezy ?


cheers

---

### Post by manicka on 2005-11-05
[QUOTE=jvictor]
Should I log a bug against the default 0.4 distributed for AMD64/Breezy ?
[/QUOTE]

I would :)

---

