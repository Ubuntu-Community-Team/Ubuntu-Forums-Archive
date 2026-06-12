---
title: "How to apply patch in ubuntu"
date: 2009-01-11
forum: General Help
---

### Post by yinglcs2 on 2009-01-11
[http://www.damonkohler.com/2008/12/python-on-android.html](http://www.damonkohler.com/2008/12/python-on-android.html)

I save the patch in to a file called 'Python2.4.5_xcompile.patch' and put that in the same level as the top directory of Python-2.4.5
```

#cd Python-2.4.5
#patch -p1 < ../Python2.4.5_xcompile.patchpatching file Makefile.pre.in
Hunk #1 FAILED at 166.
Hunk #2 FAILED at 193.
Hunk #3 FAILED at 326.
Hunk #4 FAILED at 457.
Hunk #5 FAILED at 750.
Hunk #6 FAILED at 858.
6 out of 6 hunks FAILED -- saving rejects to file Makefile.pre.in.rej
patching file Modules/pwdmodule.c
Hunk #1 FAILED at 77.
1 out of 1 hunk FAILED -- saving rejects to file Modules/pwdmodule.c.rej
patching file Modules/socketmodule.c
patching file Objects/fileobject.c
patching file Python/pystrtod.c
Hunk #1 FAILED at 54.
Hunk #2 FAILED at 218.
2 out of 2 hunks FAILED -- saving rejects to file Python/pystrtod.c.rej
patching file setup.py
patch unexpectedly ends in middle of line
Hunk #2 succeeded at 211 with fuzz 1.


```

But i get a bunch of 'Hunk #1'.  Does this make sense?

Thank you for any help.

---

### Post by spiderbatdad on 2009-01-11
possibly try with patch -p0 >  or just patch >
but it appears to be some other problem with the patch itself?
Maybe better to save the patch as a gz and unzip it in the Python directory.

---

