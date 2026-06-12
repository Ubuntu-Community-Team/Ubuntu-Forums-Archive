---
title: "How do I remove a compiled software?"
date: 2009-01-04
forum: General Help
---

### Post by extruct on 2009-01-04
Hello all!
Lets say I got some source code of some program, I run:
```

./configure
make
make install

```

And now I want to remove this software totally (including its folder and etc, like it never was installed)
How do I do it?
Thanks a lot!

---

### Post by rbmorse on 2009-01-04
First...about your avitar....

Look in the directory where you did the make and check the readme file(s). A considerate developer would have included an uninstall script or a provision to 

sudo make uninstall

in the package.

---

