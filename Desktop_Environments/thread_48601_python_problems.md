---
title: "python problems"
date: 2005-07-13
forum: Desktop Environments
---

### Post by mattb_ on 2005-07-13
I have python problems....
My python install is not finding any modules, but python is installed??

---

### Post by dataw0lf on 2005-07-13
1) locate where exactly your modules are at (/usr/lib/python2.4/site-packages/ is popular)

2) go into the python interactive shell and type :

```

>>> import sys
>>> sys.path
['', '/usr/lib/python24.zip', '/usr/lib/python2.4', '/usr/lib/python2.4/plat-linux2', '/usr/lib/python2.4/lib-tk', '/usr/lib/python2.4/lib-dynload', '/usr/local/lib/python2.4/site-packages', '/usr/lib/python2.4/site-packages', '/usr/lib/python2.4/site-packages/HTMLgen', '/usr/lib/python2.4/site-packages/Nevow', '/usr/lib/python2.4/site-packages/Numeric', '/usr/lib/python2.4/site-packages/PIL', '/usr/lib/python2.4/site-packages/gtk-2.0', '/usr/lib/python2.4/site-packages/wx-2.5.3-gtk2-unicode', '/usr/lib/site-python']

``` 

That's what it shows on mine.  If the directories which you have the modules in is not in sys.path, there are several ways of adding them.  Probably the best way is to 
```
export PYTHONPATH="/some/path:/some/other/path"
``` 
This will add the specified paths to the _beginning_ of sys.path.
You can also use a temporary fix in your code with :
```
import sys
sys.path.append("/some/path:/some/other/path")
```

---

