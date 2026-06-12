---
title: "dual boot &amp; Mbr/bcd issues"
date: 2017-07-14
forum: Desktop Environments
---

### Post by richlyn9 on 2017-07-14
I had a ubuntu 12.0 installed on a ssd and seperately have a windows 10 installed.
Now i have them both on th same PC and want the UEFI bios to point to GRUB2 (assuming its Grub2 that ubuntu 12.0 has) and not the windows BCD and recognize both OS's

Pls guide

---

### Post by oldfred on 2017-07-14
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Make sure Windows fast start up is off. And Windows on updates will probably keep turning it on.
Grub only boots working Windows or Windows that is not hibernated nor needs chkdsk.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

