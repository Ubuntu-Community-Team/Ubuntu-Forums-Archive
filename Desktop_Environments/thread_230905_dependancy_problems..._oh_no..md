---
title: "dependancy problems... oh no."
date: 2006-08-06
forum: Desktop Environments
---

### Post by machs_fuel42 on 2006-08-06
so i was trying to install the newest xmame deb from the debian repository.. it said i needed libc6 ver >2.3.6. so i grabbed 2.3.6-15..
i tryed to install the whole mess with dpkg and got some errors
libc6 needed tzdata_2006g and i grabed that too..
trying to install tzdata with dpkg game me this error;

```
 sudo dpkg -i tzdata_2006g-2_all.deb
(Reading database ... 110103 files and directories currently installed.)
Unpacking tzdata (from tzdata_2006g-2_all.deb) ...
dpkg: error processing tzdata_2006g-2_all.deb (--install):
 trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package locales
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 tzdata_2006g-2_all.deb

```

and now that when i try apt-get i seem to have some outstanding issues...

```

sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-15 is installed
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-15 is installed
  xmame-svga: Depends: libsvga1 but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

Help!?

---

### Post by machs_fuel42 on 2006-08-07
phew... glad thats over...

after much mucking, 
in Synaptic used package==> force version to get my libc6 back to ubuntu20.

note to self, **don't muck with libc6**

---

