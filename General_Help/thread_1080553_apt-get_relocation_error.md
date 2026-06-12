---
title: "apt-get: relocation error"
date: 2009-02-25
forum: General Help
---

### Post by rintimtim on 2009-02-25
Hello,

I've got an error when I'm starting apt-get

```

sudo apt-get
apt-get: relocation error: /usr/lib/libapt-pkg-libc6.8-6.so.4.6: symbol _cxa_pu`e_virtual, version CXXABI_1.3 not defined in file libstdc++.so.6 with link time reference

```

Can you help me with this one ?

---

### Post by smani on 2009-02-25
You could try and downloading the "apt" package manually, extract it's contents with the file-roller, and then replace the problematic file manually, since I guess telling apt-get to reinstall the package would not help much;) Be careful to use the same package as the one installed, i.e. check with apt-cache policy apt and compare the versions. This would help in case the file got corrupted for some reason.

---

### Post by rintimtim on 2009-02-25
Checking the file with apt-cache policy apt doesn't work:

```
apt-cache policy apt
apt-cache: relocation error: /usr/lib/libapt-pkg-libc6.8-6.so.4.6: symbol _cxa_pu`e_virtual, version CXXABI_1.3 not defined in file libstdc++.so.6 with link time reference
```

Can't i just manually download the .tar.gz file and configure/make/make install everything?

---

### Post by snova on 2009-02-25
Found an old thread: [http://ubuntuforums.org/showthread.php?t=873357](http://ubuntuforums.org/showthread.php?t=873357)

Which suggested to follow instructions in this bug report: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/180160](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/180160)

But I don't know whether the problem was ever actually solved.

---

