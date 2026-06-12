---
title: "PyCogent problems"
date: 2008-03-31
forum: Education &amp; Science
---

### Post by querent on 2008-03-31
Hey all,

So...I'm having some strange problems installing the PyCogent packages on ubuntu 7.10.  I have python 2.5.1 and numpy 1.0.3.

Lots of error messages upon typing

python setup.py build

from the extracted folder.

here's a sampling:

/usr/include/python2.5/Python.h:37:20: error: string.h: No such file or directory
/usr/include/python2.5/Python.h:39:19: error: errno.h: No such file or directory

...

/usr/include/python2.5/object.h:309: error: field ‘tp_weaklistoffset’ declared as a function
/usr/include/python2.5/object.h:324: error: field ‘tp_dictoffset’ declared as a function

...

/usr/include/python2.5/pythonrun.h:37: error: expected ‘)’ before ‘*’ token
/usr/include/python2.5/pythonrun.h:38: error: expected ‘)’ before ‘*’ token

...

cogent/align/_compare.c:180: error: ‘PyObject’ has no member named ‘ob_refcnt’
cogent/align/_compare.c:180: error: ‘PyObject’ has no member named ‘ob_type’

...

and it exits with:

error: command 'gcc' failed with exit status 1

synaptic says I have version 4:4.1.2-9ubuntu2 of gcc installed.

Any thoughts?
q

---

### Post by justin212k on 2009-02-20
try installing python2.5-dev (looks like you're missing python header files)

"sudo apt-get install python2.5-dev" should work.

---

