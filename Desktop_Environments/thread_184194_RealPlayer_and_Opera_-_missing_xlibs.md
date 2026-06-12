---
title: "RealPlayer and Opera - missing xlibs"
date: 2006-05-29
forum: Desktop Environments
---

### Post by 40%TUX on 2006-05-29
i' tryig to install from synaptic realplayer and it tells me that realplayer needs xlibs but they are not available?! where i can get them?

thnx

(sam xlibs are requared by opera)

---

### Post by Breepee on 2006-05-29
Cedega needs them too...

---

### Post by Noelinho on 2006-05-29
Hmm, I haven't a clue really. I don't have xlibs in my repos, but I have RealPlayer installed.

However, libx11-6 replaces xlibs-data, could it be something to do with that?

---

### Post by foenz on 2006-05-29
You can install at least cedega (haven't tried the rest) with forcing to ignore the deps.
The problem afterwards is, that your apt is pretty unsatisfied with that, and wants to delete the package cause of broken deps (Does anyone know how to ignore installed packages for the package mangment ?).
If you're loading the REalplayer binarys, the installation proceeds very smoth, without  any complains.

Greetings
Foenz

---

### Post by hajk on 2006-05-29
The realplayer "package" in Synaptic expects you to download RealPlayer 8, a dated version. You can download the newer RealPlayer 10 from the Helix DNA site and install it yourself. Easiest is to download the tar.gz package, untar it and install it to the /usr/local/RealPlayer directory. If you must have a .deb package, then download the rpm-package, and convert it to deb with "fakeroot alien" and install with "sudo dpkg -i". In the latter case, you'll have to repair the /usr/bin/realplay symlink from /Realplayer/realplay to /usr/local/RealPlayer/realplay. 

RealPlayer installed this way does not rely on system files, as far as I can tell, so would even (as 32-bit) run in 64-bit AMD system.

As far as Opera goes, if you install the statically linked version, then you don't need system libraries either.

---

### Post by junior aspirin on 2006-05-29
there is a deb linked to on the wiki
[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer#head-7d2f38dce9f1934882f207ab2f4042f72033bf70](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer#head-7d2f38dce9f1934882f207ab2f4042f72033bf70)

---

### Post by 40%TUX on 2006-05-30
[QUOTE=hajk]As far as Opera goes, if you install the statically linked version, then you don't need system libraries either[/QUOTE]
from some threads on this forum i got that shared version of opera is beter choice. although i have no idea what the differencies are. i would like to ask you to explane me what are the advantages (disadvantages) of static vs shared.

thnx in advance

---

### Post by effoff on 2006-05-30
[QUOTE=40%TUX]i' tryig to install from synaptic realplayer and it tells me that realplayer needs xlibs but they are not available?! where i can get them?

thnx

(sam xlibs are requared by opera)[/QUOTE]

**xlibs-dev**

X Window System client library development files transitional package
This package smooths upgrades from Debian 3.0 by depending on libice-dev,
libsm-dev, libx11-dev, libxext-dev, libxi-dev, libxmu-dev, libxmuu-dev,
libxpm-dev, libxrandr-dev, libxt-dev, libxtrap-dev, libxtst-dev, libxv-dev,
x-dev, and xlibs-static-dev.  This transitional package is only depended upon
by packages that haven't yet corrected their dependencies to reflect the new
library arrangement.

---

### Post by hajk on 2006-05-30
[QUOTE=40%TUX]from some threads on this forum i got that shared version of opera is beter choice. although i have no idea what the differencies are. i would like to ask you to explane me what are the advantages (disadvantages) of static vs shared.

thnx in advance[/QUOTE]

The static version has the necessary library functions already compiled in the final binary, so does not need to call on the same routines in the system libraries again.
Advantage: no need to install missing libraries, and possibly a bit faster once loaded. Disadvantage: the binary is larger and takes a little longer to load. My preference is for the static version, in view of current fast processors and huge hard drives. Of course, once you start to run 32-bit applications in a 64-bit OS, the static version can be run without the need for a chroot environment.

---

### Post by kvonb on 2006-05-31
This is what I did to get cedega installed:

1)  Install xlibs-static-dev_6.8.2-77.1_i386.deb (google for that package)
     it will want to download and install 13 other packages, but they are quite small.
2)  Install xlibs_6.8.2-77.1_all.deb (again search the web for it)
3)  Install cedega

Sorry, I don't know where to get the above packages from, I already had them from Breezy so I just double clicked them in Dapper to install.  If you can't find them, let me know and I will e-mail them to you, they're quite small.

Hope this helps, regards, Kev :)

---

