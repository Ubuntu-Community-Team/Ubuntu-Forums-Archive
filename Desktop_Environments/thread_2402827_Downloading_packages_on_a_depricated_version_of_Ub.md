---
title: "Downloading packages on a depricated version of Ubuntu"
date: 2018-10-04
forum: Desktop Environments
---

### Post by vysero on 2018-10-04
Hey guys, so what I want I to do is download a load of packages onto a version of Ubuntu that is no longer supported (10.04 LTS). I was wondering if anyone had and idea about how I might go about doing that?

For instance, on my 10.04 LTS VM I tried running: sudo apt-get install openssh-server and the terminal reports:

Package openssh-server is not available, but is reffered to by another package.
This may mean the package is missing, has been obsoleted, or
is only available from another source.

I am assuming the problem here is that apt-get is trying to install a version of openssh-server that will not run on 10.04 but I am also assuming that there is an archive somewhere out there that will have the correct version for 10.04 available for download? I opened Software Sources and I can choose the Download Server there but I am not sure which would be the correct one or if this is even the correct way to go about doing this.

---

### Post by steeldriver on 2018-10-04
AFAIK you will need to edit your sources.list file to point to the old-releases server (or a suitable mirror of it) - see for example

[How to install software or upgrade from an old unsupported release?]("https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release")

Hope this helps

---

### Post by vysero on 2018-10-04
Brilliant ty!

---

### Post by ajgreeny on 2018-10-04
Just make sure you do not go online using 10.04 as it will be a dreadful security hole, not having received any updated packages for about three and a half years.

---

### Post by vysero on 2018-10-04
Are you just being paranoid? I was under the impression that no one operating on Linux really had to be worried that and its a virtual machine.

---

### Post by QIII on 2018-10-04
Unfortunately, that is a common misconception.  No OS is safe, particularly when it is no longer receiving security updates.

---

### Post by oldfred on 2018-10-04
UEFI/BIOS/Kernels/support software all need updates.
       Ubuntu 18.04 Bionic
18.04.1 release July 26, 2018
mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.
Ubuntu 18.04 LTS has the Linux 4.15 kernel, GNOME Shell 3.29.1, Mesa 18.0-rc5, GCC 7.3.0, Python 2.7.15rc1, Python 3.6.5, and is mitigated for Meltdown with KPTI while for Spectre V1 it opts for __user pointer sanitization over OSB and for Spectre V2 has full Retpolines.

---

