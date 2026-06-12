---
title: "kernel 2.6.27.9 issues"
date: 2009-01-14
forum: General Help
---

### Post by djbushido on 2009-01-14
when trying to boot the above listed kernel on my machine i get this message (or something very close): kinit: no resume image found, doing normal boot

Then when it is finished booting, X.org crashes, and i have to shut down. Then, since the drive was apparently shut down wrong, Xubuntu has to check the drive for errors. 

I've found that this problem does not appear in 2.6.27.7, an older kernel I had installed on my machine.

Any ideas?

NOTE: attached are outputs of lspci and lsusb. dmesg is a bz2'd text file, because of size requirements.

NOTENOTE: the results are from a boot of 2.6.27.7, not *.9, since X.org crashed and then froze my computer.

EDIT: syslog attached as well now.

[ATTACH]99753[/ATTACH]

[ATTACH]99754[/ATTACH]

[ATTACH]99760[/ATTACH]

[ATTACH]99757[/ATTACH]

---

### Post by djbushido on 2009-01-15
Turns out it isn't an issue with the kernel, so I will start a new thread.

---

