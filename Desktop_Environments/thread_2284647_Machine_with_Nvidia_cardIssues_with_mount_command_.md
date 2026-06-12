---
title: "Machine with Nvidia card:Issues with mount command on ubuntu using hostname"
date: 2015-07-01
forum: Desktop Environments
---

### Post by kishore3 on 2015-07-01
[COLOR=#111111][FONT=Ubuntu]OS: Ubuntu14.04 64 bit I have a strange problem occuring on machines with Nvidia cards running Ubuntu 14.04 64 bit. the mount command works when using the IPAddress but fails when using the host name[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Not-working command :sudo -S mount -t cifs //share.test.com/LAB/Testing/Path1/Path2/Requisite/ -o username=blabla,password=blabla /mnt/src_shar_lnx the error being mount: wrong fs type, bad option, bad superblock on //share.test.com/LAB/Testing/Path1/Path2/Requisite/ , missing codepage or helper program, or other error (for several filesystems (e.g. nfs, cifs) you might need a /sbin/mount. helper program) In some cases useful info is found in syslog - try dmesg | tail or so[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The above command works seamlessly on other machines without Nvidia cards.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Working command :sudo -S mount -t cifs //192.168.200.1/LAB/Testing/Path1/Path2/Requisite/ -o username=blabla,password=blabla /mnt/src_shar_lnx[/FONT][/COLOR]

---

### Post by kishore3 on 2015-07-01
[FONT=Helvetica Neue]Resolved. installing cifs-utils solved the problem


[/FONT]

---

