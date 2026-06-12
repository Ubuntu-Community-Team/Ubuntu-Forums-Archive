---
title: "Install LDOCE5 on Ubuntu 64-bit"
date: 2015-06-20
forum: Debian
---

### Post by toopho on 2015-06-20
I am using Debian 8.0 which went freeze in early Nov 2015 so I guess I am using a distro very similar to the official Ubuntu 14.10 release.

I have followed the instructions here and after creating a copy of x86 folder called amd64 next to it the error became:

```
./setup.sh: 201: ./setup.sh: /home/un/.setup5401: not found
The setup program seems to have failed on amd64/unknown

Fatal error, no tech support email configured in this setup
```

Then, I installed the package “libc6-i386”. But I couldn't find anything similar to “glibc-2.1”.

After that, I launched setup.sh again and the installation begun, I accepted the licence, and it seemed to go well through all the installation process until the last few lines:

```
(...)
 100% - /home/un/ldoce5//ldoce5.data/exa_pron.skn/dirs.skn/FILES.skn/FILES.dat
 Fixing data
 Install fonts
cp: cannot stat ‘setup.data/AWLPhonetics3U.TTF’: No such file or directory
 Install desktop shortcut

Installation complete.
```

When I tried to start the dictionary the following error message prompts:

```
./ldoce5/ldoce5-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
```

I am wondering if I can still find those old libraries in the newer versions of Ubuntu and Debian. Or, how are they called now?

---

### Post by howefield on 2015-06-20
Post moved to its own thread and to the "*Debian*" forum.

---

### Post by arochester on 2015-07-19
[http://forums.debian.net/viewtopic.php?f=16&t=61147](http://forums.debian.net/viewtopic.php?f=16&t=61147)

---

