---
title: "How do I update software? (installed from source)"
date: 2009-03-07
forum: General Help
---

### Post by NeonBible on 2009-03-07
For example I want to get the latest version of "MPDScribble".

I can't remember exactly but I think I installed it from source code.

Now if I download the new tarball, what do I need to do? Do I need to uninstall the existing one first?

---

### Post by Xiong Chiamiov on 2009-03-07
I think you should be able to just build it like you did the previous one.  If you want to uninstall an old one first, you'll need to have an extracted folder of the version you have installed, then run
```

./configure
make uninstall

```
in it (might have to use sudo).

---

