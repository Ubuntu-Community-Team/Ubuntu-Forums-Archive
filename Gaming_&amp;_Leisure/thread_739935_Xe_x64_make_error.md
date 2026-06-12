---
title: "Xe x64 make error"
date: 2008-03-30
forum: Gaming &amp; Leisure
---

### Post by Don Giovanni on 2008-03-30
I haven't been able to find any one else reporting this issue.

I am trying to install the Xe emulator for my 64bit ubuntu MythTV box
I'm using xe-x86-64-bin.2.13.2.tar.bz2 from the Xe homepage.

When i go to make I get the following error:
/usr/bin/ld: cannot find -lasound
collect2: ld returned 1 exit status
make: *** [xe] Error 1

I have ALSA installed so I'm not sure why I am seeing this error.  Any ideas?

*update* so i realised this is calling on an earlier version of ALSA.  Installing the older one removes the newer version...which i can see potentially causing other issues.  Anyway to get around this?

---

