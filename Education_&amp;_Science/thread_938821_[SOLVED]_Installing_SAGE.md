---
title: "[SOLVED] Installing SAGE"
date: 2008-10-05
forum: Education &amp; Science
---

### Post by Tart on 2008-10-05
Hi All,

I downloaded pre-built binary for ubuntu. unpacked it and run ./sage
However I got the following error. I'm not sure that it all means. Am I missing some packages?

Did anyone else have similar problem?

How to fix it?

Thank you!

```

----------------------------------------------------------------------
| SAGE Version 3.1.2, Release Date: 2008-09-19                       |
| Type notebook() for the GUI, and license() for information.        |
----------------------------------------------------------------------
The SAGE install tree may have moved.
Regenerating Python.pyo and .pyc files that hardcode the install PATH (please wait at most a few minutes)...
Please do not interrupt this.
---------------------------------------------------------------------------
ImportError                               Traceback (most recent call last)

/home/ilya/sage-3.1.2-ubuntu-64bit-opteron-x86_64-Linux/local/bin/<string> in <module>()

/home/ilya/sage-3.1.2-ubuntu-64bit-opteron-x86_64-Linux/local/lib/python2.5/site-packages/sage/misc/preparser_ipython.py in <module>()
      6 ###########################################################################
      7 
----> 8 import sage.misc.interpreter
      9 
     10 import preparser

/home/ilya/sage-3.1.2-ubuntu-64bit-opteron-x86_64-Linux/local/lib/python2.5/site-packages/sage/misc/interpreter.py in <module>()
    102 
    103 import os
--> 104 import log
    105 
    106 import remote_file

/home/ilya/sage-3.1.2-ubuntu-64bit-opteron-x86_64-Linux/local/lib/python2.5/site-packages/sage/misc/log.py in <module>()
     56 
     57 import interpreter
---> 58 import latex
     59 import misc
     60 

/home/ilya/sage-3.1.2-ubuntu-64bit-opteron-x86_64-Linux/local/lib/python2.5/site-packages/sage/misc/latex.py in <module>()
     41 import random
     42 
---> 43 from misc import tmp_dir
     44 import sage_eval
     45 

/home/ilya/sage-3.1.2-ubuntu-64bit-opteron-x86_64-Linux/local/lib/python2.5/site-packages/sage/misc/misc.py in <module>()
     23 
     24 import operator, os, stat, socket, sys, signal, time, weakref, resource, math
---> 25 import sage.misc.prandom as random
     26 
     27 from banner import version, banner

/home/ilya/sage-3.1.2-ubuntu-64bit-opteron-x86_64-Linux/local/lib/python2.5/site-packages/sage/misc/prandom.py in <module>()
     54 # setting seeds should only be done through sage.misc.randstate .
     55 
---> 56 from sage.misc.randstate import current_randstate
     57 
     58 def _pyrand():

ImportError: libcsage.so: cannot open shared object file: No such file or directory
WARNING: Failure executing code: 'import sage.misc.preparser_ipython;  sage.misc.preparser_ipython.magma_colon_equals=True'
---------------------------------------------------------------------------
ImportError                               Traceback (most recent call last)

/home/ilya/sage-3.1.2-ubuntu-64bit-opteron-x86_64-Linux/local/bin/<ipython console> in <module>()

/home/ilya/sage-3.1.2-ubuntu-64bit-opteron-x86_64-Linux/local/lib/python2.5/site-packages/sage/misc/misc.py in <module>()
     23 
     24 import operator, os, stat, socket, sys, signal, time, weakref, resource, math
---> 25 import sage.misc.prandom as random
     26 
     27 from banner import version, banner

/home/ilya/sage-3.1.2-ubuntu-64bit-opteron-x86_64-Linux/local/lib/python2.5/site-packages/sage/misc/prandom.py in <module>()
     54 # setting seeds should only be done through sage.misc.randstate .
     55 
---> 56 from sage.misc.randstate import current_randstate
     57 
     58 def _pyrand():

ImportError: libcsage.so: cannot open shared object file: No such file or directory
<ERROR: name 'sage_prompt' is not defined>


```

---

### Post by Tart on 2008-10-07
Problem was resolved by downloading different version of SAGE (6.06.LTS)

---

