---
title: "CDRecord Problem"
date: 2005-07-01
forum: Desktop Environments
---

### Post by YaAqoB on 2005-07-01
Hello all.
I'm keen to learn how to burn a cd from the trminal using the cdrecord command.
When I run cdrecord -scanbus I get the following error.
Any ideas to get me burning?

james@YaAqoB:~$ sudo cdrecord -scanbus Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI dr iver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
james@YaAqoB:~$

---

### Post by Lunde on 2005-07-01
I have the same problem from Gnomebaker.

---

### Post by superhac007 on 2005-07-01
[QUOTE=YaAqoB]Hello all.
I'm keen to learn how to burn a cd from the trminal using the cdrecord command.
When I run cdrecord -scanbus I get the following error.
Any ideas to get me burning?

james@YaAqoB:~$ sudo cdrecord -scanbus Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI dr iver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
james@YaAqoB:~$[/QUOTE]

Thats normal on Ubuntu.  CdRecord now uses /dev targets instead of the -dev ones.

e.g. /dev/hdb instead of the dev=0,6,0 

If you want to know all the command line options then man cdrecord.  

If you dont want to waste your time then use k3b.  Its a great burning program.

---

