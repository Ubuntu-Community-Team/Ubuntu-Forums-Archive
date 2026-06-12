---
title: "python encoding"
date: 2010-11-22
forum: Desktop Environments
---

### Post by surfer on 2010-11-22
i have this python code:
```
#!/usr/bin/python
# -*- coding: utf-8 -*-

import sys
print sys.getdefaultencoding()

```
and am wondering why this is 'ascii'... and how can i set it to 'utf-8?'

---

### Post by surfer on 2010-11-22
on the other hand, when i run this
```
$ python2.6 -c "import sys; print sys.getfilesystemencoding()"
```
in the shell, i get 'utf-8'.

any ideas?

---

### Post by surfer on 2010-11-23
bump...

---

### Post by surfer on 2010-11-24
anybody?

---

### Post by benson444 on 2010-11-24
I don't know much about character encoding but, as nobody has said anything, I'll say what I can. Hopefully someone can point out any errors.

Having a look at the Python docs and sys help, getdefaultencoding() returns the default string encoding for the Unicode implementation and getfilesystemencoding() returns the encoding used to convert Unicode filenames into OS filenames. So, Python 2.6 uses ASCII and the OS uses UTF-8.

You can change Python's default encoding to UTF-8 by adding the following to /usr/lib/python2.6/sitecustomize.py:

```
import sys
sys.setdefaultencoding('utf-8')
```

... but the docs say this:

> It’s possible to set a default encoding in a file called sitecustomize.py that’s part of the Python library. However, this isn’t recommended because changing the Python-wide default encoding may cause third-party extension modules to fail.

Python 3 uses UTF-8 as the default.

---

### Post by surfer on 2010-11-24
thanks for that! ...and my mistake! i never meant to use sys.getfilesystemencoding() but only sys.getdefaultencoding().

sys.setdefaultencoding('utf-8') on the ohter hand produces
```
Traceback (most recent call last):
  File "<stdin>", line 8, in <module>
AttributeError: 'module' object has no attribute 'setdefaultencoding'
```

---

### Post by benson444 on 2010-11-24
Apparently it's a special function. From the docs:

> Set the current default string encoding used by the Unicode implementation. If name does not match any available encoding, LookupError is raised. This function is only intended to be used by the site module implementation and, where needed, by sitecustomize. Once used by the site module, it is removed from the sys module&#8217;s namespace.

Also, I believe that putting the '... coding: utf-8 ...' line in the .py file just means that you can use utf-8 strings within the code in that file. If you were to read/write outside then the default encoding of ASCII would be used.(?)

---

### Post by surfer on 2010-11-24
i guess you're right...

i ran into trouble with jinja2... my workaround so far is to read in the jinja template with
```
codecs.open(the_path,encoding='utf-8')
```
which works fine.

---

