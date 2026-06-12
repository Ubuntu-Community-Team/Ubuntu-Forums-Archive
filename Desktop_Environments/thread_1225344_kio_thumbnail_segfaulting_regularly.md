---
title: "kio_thumbnail segfaulting regularly"
date: 2009-07-28
forum: Desktop Environments
---

### Post by jtappin on 2009-07-28
When I look at /var/log/messages, I'm seeing large numbers of errors like:
```
Jul 28 10:22:54 gabrielle kernel: [ 9460.907801] kio_thumbnail[12517]: segfault at f68 ip 00007f0ec7ec74ef sp 00007fffd37c4330 error 4 in libgcc_s.so.1[7f0ec7eb7000+16000]

```
The numbers prior to the ip change, those after do not.

I'm running the KDE 4.3 RC3 packages from the kubuntu backports PPA, and using konqueror as my default file manager.

Has anyone else seen this? Does it look like a kio-thumbnails bug or possibly some corrupt images or thumbnails?

---

### Post by GeneralZod on 2009-07-28
Apparently this is fixed, though the fix missed RC3:

[https://bugs.kde.org/show_bug.cgi?id=199840](https://bugs.kde.org/show_bug.cgi?id=199840)

The fix should be in 4.3.0.

---

### Post by jtappin on 2009-07-28
Thanks for that info, I'll wait for the release.

---

### Post by jtappin on 2009-08-05
The problem does indeed look to be fixed in the 4.3.0 release.

---

