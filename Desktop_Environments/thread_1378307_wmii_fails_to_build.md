---
title: "wmii fails to build"
date: 2010-01-11
forum: Desktop Environments
---

### Post by octoberdan on 2010-01-11
Whenever I try to "make deb" in wmii3.9b1 or latest from trunk, the build fails. 

```

dgreen@dgreen-desktop:~/Desktop/wmii$ make deb --debug
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i486-pc-linux-gnu
Reading makefiles...
Updating goal targets....
 File `deb' does not exist.
Must remake target `deb'.
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package wmii-hg
dpkg-buildpackage: source version hg2594
dpkg-buildpackage: source changed by Anselm R Garbe <anselm@garbe.us>
dpkg-buildpackage: host architecture i386
 debian/rules build
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i486-pc-linux-gnu
Reading makefiles...
dh: Unknown sequence .depend (choose from: binary binary-arch binary-indep build clean install)
Updating goal targets....
 File `build' does not exist.
   File `patch' does not exist.
  Must remake target `patch'.
  Successfully remade target file `patch'.
Must remake target `build'.
Successfully remade target file `build'.
 fakeroot debian/rules binary
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i486-pc-linux-gnu
Reading makefiles...
dh: Unknown sequence .depend (choose from: binary binary-arch binary-indep build clean install)
Updating goal targets....
 File `binary' does not exist.
Must remake target `binary'.
Successfully remade target file `binary'.
 dpkg-genchanges -b >../wmii-hg_hg2594_i386.changes
dpkg-genchanges: binary-only upload - not including any source code
 signfile wmii-hg_hg2594_i386.changes
gpg: skipped "Anselm R Garbe <anselm@garbe.us>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

dpkg-buildpackage: binary only upload (no source included)
dpkg-buildpackage: warning: Failed to sign .changes file
make: *** [deb] Error 1

```

Anyone have an idea about what's going on? The last bit looks suspicious, but it should only be a warning, right? I try make with -i and -k, but the .deb file is still not generated.

Thank you for at least reading this,
Daniel.

---

### Post by octoberdan on 2010-01-11
The solution was to run 

```
dpkg-buildpackage -us -uc -b
```

---

