---
title: "Backdated libc compatibility error?"
date: 2005-11-04
forum: Desktop Environments
---

### Post by hostile on 2005-11-04
I am receiving the following error:

```
error while loading shared libraries: libstdc++.so.5
```

I have looked for anything looking similar to libstdc++, and have found nothing.

Any suggestioned as to how this can be rememdied or what the appropriate package name is I should be looking for?

---

### Post by Kyral on 2005-11-04
Thats part of libc6 isn't it?

---

### Post by Curufir on 2005-11-04
sudo apt-get install libstdc++5

No, it's not part of the vanilla Breezy installation.

---

### Post by hostile on 2005-11-04
> sudo apt-get install libstdc++5

No, it's not part of the vanilla Breezy installation.

Excellent. That worked. 

Thank you!

:D

---

