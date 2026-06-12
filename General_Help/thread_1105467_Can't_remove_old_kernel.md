---
title: "Can't remove old kernel"
date: 2009-03-24
forum: General Help
---

### Post by charlescarroll1 on 2009-03-24
I'm trying to remove an old kernel through synaptic, "linux-image-2.6.27-9-generic".  I mark the package for removal, and hit apply, but I get the following error:

> E: linux-image-2.6.27-9-generic: subprocess pre-removal script returned error exit status 2

Then...

> (Reading database ... 169116 files and directories currently installed.)
Removing linux-image-2.6.27-9-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
run-parts: executing /etc/kernel/prerm.d/last-good-boot
/etc/kernel/prerm.d/last-good-boot: 3: /usr/sbin/kernel-helper: not found
run-parts: /etc/kernel/prerm.d/last-good-boot exited with return code 127
Failed to process /etc/kernel/prerm.d at /var/lib/dpkg/info/linux-image-2.6.27-9-generic.prerm line 267.
dpkg: error processing linux-image-2.6.27-9-generic (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.27-9-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:

What's the deal?

---

### Post by zvacet on 2009-03-25
Try with 

```
sudo apt-get --purge remove linux-image-2.6.27-9-generic
```

---

### Post by charlescarroll1 on 2009-03-25
Nope, didn't work.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  stardict-common stardict-plugin-festival stardict-plugin-espeak stardict-gtk
  libestools1.2 stardict-plugin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-2.6.27-9-generic*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 94.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 169116 files and directories currently installed.)
Removing linux-image-2.6.27-9-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
run-parts: executing /etc/kernel/prerm.d/last-good-boot
/etc/kernel/prerm.d/last-good-boot: 3: /usr/sbin/kernel-helper: not found
run-parts: /etc/kernel/prerm.d/last-good-boot exited with return code 127
Failed to process /etc/kernel/prerm.d at /var/lib/dpkg/info/linux-image-2.6.27-9-generic.prerm line 267.
dpkg: error processing linux-image-2.6.27-9-generic (--purge):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.27-9-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


That's strange I'm not able to remove it.  I'm using 2.6.27-11-generic.  

It is a nuisance though.  In Grub 1.96, kernel version 2.6.27-9 is at the top of the list.  Is there any way to at least remove that kernel entry from the grub list?

---

### Post by cajunaggie on 2009-03-30
I removed some unused software today and I got the same error message for a different package.

```
Removing octave-symbolic ...
/var/lib/dpkg/info/octave-symbolic.postrm: 9: octave3.0: not found
dpkg: error processing octave-symbolic (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 octave-symbolic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Running```
sudo apt-get --purge remove octave-symbolic
``` yields the same error. It's also blocking my ability to run any other apt-get commands, since it comes up first in the command line.

---

### Post by zoomy942 on 2009-07-07
i started having this problem after updating my kernel

---

