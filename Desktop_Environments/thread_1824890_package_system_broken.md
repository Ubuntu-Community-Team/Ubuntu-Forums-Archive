---
title: "package system broken"
date: 2011-08-14
forum: Desktop Environments
---

### Post by bruce herdman on 2011-08-14
Did clean install of 11.04 on Dell Inspiron 518 and everything worked until the first update session. Now I get the notice "package system broken". I tried  apt-get install -f  as suggested by the machine and it returned:

After this operation, 96.0 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 157546 files and directories currently installed.)
Preparing to replace libreoffice-writer 1:3.3.2-1ubuntu4 (using .../libreoffice-writer_1%3a3.3.2-1ubuntu5_i386.deb) ...
Unpacking replacement libreoffice-writer ...
xz: (stdin): Compressed data is corrupt
dpkg-deb: error: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/libreoffice-writer_1%3a3.3.2-1ubuntu5_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/libreoffice/basis3.3/program/libswli.so'
dpkg: regarding .../libreoffice-core_1%3a3.3.2-1ubuntu5_i386.deb containing libreoffice-core:
 libreoffice-core conflicts with libreoffice-writer (<< 1:3.3.2-1ubuntu5)
  libreoffice-writer (version 1:3.3.2-1ubuntu4) is present and installed.
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.3.2-1ubuntu5_i386.deb (--unpack):
 conflicting packages - not installing libreoffice-core
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-writer_1%3a3.3.2-1ubuntu5_i386.deb
 /var/cache/apt/archives/libreoffice-core_1%3a3.3.2-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (

In the terminal I found instructions to try apt-get autoremove because there were files no longer needed but still in the system. It didn't help.

What now? Wife's machine! I'm needing to get it working properly. Also, the Ubuntu Software Center doesn't work and returns error signals about broken programs and offers to repair them---repairs fail to fix the problem.

:confused:

---

### Post by bruce herdman on 2011-08-14
I tried installing Flash using Syn.Pkg. Mgr. and it returned an incomplete installation message as follows:


E: /var/cache/apt/archives/smbclient_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2 

I tried using SPM to repair or replace smbclient.... and received the following error msg:

Unpacking replacement smbclient ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/smbclient_2%3a3.5.8~dfsg-1ubuntu2.3_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2

---

### Post by Frogs Hair on 2011-08-14
You could try recovery mode from the Grub menu .There is a repair broken packages option .

---

### Post by bruce herdman on 2011-08-14
> **Frogs Hair said:**
> You could try recovery mode from the Grub menu .There is a repair broken packages option .
I did that too, without success---a few minutes ago I found a new bug report about smbclient.....error msgs and wonder if it is the same problem? This appears to have started following a use of the Update Manager.

Addendum:

This also appeared while working on the problem:

E: Sub-process /usr/bin/dpkg returned an error code (1)

Since the errors occur on several program changes (librewriter and flash plugin) as well as when doing -f operations, I'm wondering if the dpkg file was corrupted during the update operation and how to fix it, is the problem. 

Could I re-install from the .iso cd without losing the data already in the system or will it reformat the entire partition regardless?
Thanks for your time and interest.

---

### Post by bruce herdman on 2011-08-15
Ah well, the wife's P&L file wouldn't open in LibreOffice Suite because of the bollixed update and broken (whatever) so I abandoned Natty and installed a new copy of Lucid----not a pretty fix, but it got me out of trouble on her birthday.

Thanks to all who have worked so diligently to assist me in the problems I have encountered.
Bruce

---

