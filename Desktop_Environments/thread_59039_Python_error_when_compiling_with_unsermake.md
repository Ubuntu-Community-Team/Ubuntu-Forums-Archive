---
title: "Python error when compiling with unsermake"
date: 2005-08-22
forum: Desktop Environments
---

### Post by SGC on 2005-08-22
Most kde applications start to requires unsermake to compile instead of make. I compiled a few times with unsermake, but recently started to give me this error, it is python trackback, since unsermake is written in python:
```

Traceback (most recent call last):
  File "<string>", line 1, in ?
  File "/usr/lib/python2.4/site-packages/unsermake/__init__.py", line 1303, in ?
    main()
  File "/usr/lib/python2.4/site-packages/unsermake/__init__.py", line 1162, in main
    (top_makefile, all_defines) = setup_top_makefile_wrapper( top_makefile, top_srcdir, subdir)
  File "/usr/lib/python2.4/site-packages/unsermake/__init__.py", line 810, in setup_top_makefile_wrapper
    os.path.abspath(".") + "/")
  File "/usr/lib/python2.4/site-packages/unsermake/__init__.py", line 248, in read_subdirs
    all_defines = read_subdirs(submakefile, all_defines, nsrc_prefix, nprefix)
  File "/usr/lib/python2.4/site-packages/unsermake/__init__.py", line 212, in read_subdirs
    makefile.read_deps()
  File "/usr/lib/python2.4/site-packages/unsermake/amfile.py", line 1395, in read_deps
    depdir_value = utilities.subst_vars["DEPDIR"]
KeyError: 'DEPDIR'

```

I downloaded the recent version of unsermake, but still get the same error.

---

### Post by SGC on 2005-08-22
I found the answer here:
[http://www.kde-apps.org/content/show.php?content=27313](http://www.kde-apps.org/content/show.php?content=27313)

---

