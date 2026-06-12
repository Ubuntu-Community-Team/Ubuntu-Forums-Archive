---
title: "How do I install this patch?"
date: 2009-03-17
forum: General Help
---

### Post by Dr.Suave on 2009-03-17
Hi - I'm having sound troubles, but I've found a patch that might fix my problem.

The thing is, the patch was written for Mandriva.

The other thing is, I don't even know how to install patches written for ubuntu.

The patch is attached to the first comment of this bug report: [https://qa.mandriva.com/show_bug.cgi?id=41385](https://qa.mandriva.com/show_bug.cgi?id=41385)

I would be really grateful if someone told me what to do here.

Thanks!

Wilf

---

### Post by prince_niceguy on 2009-03-17
which version of ubuntu are you using? try to upgrade to jaunty with caution as it is still in beta, see if it resolves the issue...

---

### Post by Yellow Pasque on 2009-03-17
Using a patch like that would involve re-compiling a kernel or at least ALSA.

Have you tried adding this to /etc/modprobe.d/alsa-base ?
```
options snd-hda-intel model=dell-d21
```
Restart system. In terminal, run this and make sure everything's unmuted:
```
alsamixer
```

---

