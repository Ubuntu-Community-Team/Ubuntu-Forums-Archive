---
title: "Centon SD Card - Jaunty"
date: 2009-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cks4131 on 2009-04-27
I have a dell mini 9 and recently upgraded to Jaunty.  Jaunty seems slicker and smoother than Hardy.  But I have run into an odd issue with the media card reader.  For some reason it recognizes other SD cards, but will not recognize a 4 GB Centon SD Card that I purchased off woot.  Prior to the upgrade the card worked fine, any help is appreciated.  

Additionally, I was wondering if someone could recommend a portable hard drive that can be used with Ubuntu.  Thanks.

---

### Post by ytsejam1138 on 2009-04-27
There is a bug in Jaunty that causes certain SD cards to not work correctly with the Mini9.  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359323)

However, there is a workaround.

In terminal type:

```
sudo gedit /etc/modprobe.d/options
```

Paste the following into the file:

```
options sdhci debug_quirks=1
ProblemType: Bug
Architecture: i386
DistroRelease: Ubuntu 9.04
Package: linux-image-2.6.28-6-generic 2.6.28-6.17
ProcCmdLine: User Name=UUID=e309fb14-05db-4e9a-b137-c6bf63eeb6a4 ro quiet splash elevator=noop
ProcEnviron:
SHELL=/bin/bash
LANG=it_IT.UTF-8
ProcVersionSignature: Ubuntu 2.6.28-6.17-generic
SourcePackage: linux
```

Save the file and reboot.  Your card should now be able to be read.

---

### Post by cks4131 on 2009-04-30
thanks for the help.  i am leaving for spain soon and those sd cards had all my movies on them.  was going to be a long flight, so thanks a ton for the fix.

---

### Post by schimschone on 2009-08-16
> **ytsejam1138 said:**
> There is a bug in Jaunty that causes certain SD cards to not work correctly with the Mini9.  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359323)

However, there is a workaround.

In terminal type:

```
sudo gedit /etc/modprobe.d/options
```

Paste the following into the file:

```
options sdhci debug_quirks=1
ProblemType: Bug
Architecture: i386
DistroRelease: Ubuntu 9.04
Package: linux-image-2.6.28-6-generic 2.6.28-6.17
ProcCmdLine: User Name=UUID=e309fb14-05db-4e9a-b137-c6bf63eeb6a4 ro quiet splash elevator=noop
ProcEnviron:
SHELL=/bin/bash
LANG=it_IT.UTF-8
ProcVersionSignature: Ubuntu 2.6.28-6.17-generic
SourcePackage: linux
```

Save the file and reboot.  Your card should now be able to be read.

I can't read my 'SanDisk SDHC card 16gb'.. tried your trick and still nothing. Any other ideas?

---

### Post by NightCrawler03X on 2009-08-18
What about people like me who are on the AMD64 version of Ubuntu?

---

### Post by orange_roughy on 2009-10-05
Really have to reboot? There's no other way to restart the required services?

---

### Post by B Crowther on 2009-10-19
I also have a Sandisk SDHC disk, which I cannot read in AMD64 Jaunty on my desktop, or I386 on my netbook.

Thank goodness I still have XP in dual boot on the netbook! I have still to try the cure above on the netbook: it is now so close to the release of 9.10 that I may try that and see if anything magical happens with my card first.

---

### Post by PapaRaven on 2010-01-21
In fact only "options sdhci debug_quirks=1" is required.

(ytsejam1138 (#2) has a cut-n-paste error from the original post on danilogurovich.wordpress.com...)

---

