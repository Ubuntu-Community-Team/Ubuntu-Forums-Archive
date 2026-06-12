---
title: "How to use firmware-addon-dell?"
date: 2010-06-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by danielgrosvenor on 2010-06-04
Hi guys

I'm unable to find any step-by-step walkthroughs on flashing the BIOS of my Dell notebook.

I have downloaded the file from the website - 1370_A02.exe  - and have also installed the app firmware-addon-dell.  But I don't know how to access/open it and actually update the BIOS.

Please could someone give me a brief overview of what to actually do?  I'm very new to Linux.

---

### Post by DavePlummer on 2010-06-04
I updated the BIOS on a Dell Inspiron 1545 just a few hours ago, following the instraucions at [http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate). It worked like a charm.

---

### Post by danielgrosvenor on 2010-06-05
Thanks for the link.

Unfortunately I'm getting an error message that isn't letting me proceed.  It's similar to the error message I mention [in this thread]("http://ubuntuforums.org/showthread.php?p=9409957#post9409957") -- I have absolutely no idea what it is or how to fix it.  Don't suppose anyone can offer advice? :S

```
dan@DansDell:~$ sudo apt-get install libsmbios-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting smbios-utils instead of libsmbios-bin
smbios-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up lib32nss-mdns (0.10-3ubuntu4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing lib32nss-mdns (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of wine1.2:
 wine1.2 depends on lib32nss-mdns (>= 0.10-3); however:
  Package lib32nss-mdns is not configured yet.
dpkg: error processing wine1.2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 lib32nss-mdns
 wine1.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
dan@DansDell:~$ su getSystemId
Unknown id: getSystemId
dan@DansDell:~$ 

```

---

