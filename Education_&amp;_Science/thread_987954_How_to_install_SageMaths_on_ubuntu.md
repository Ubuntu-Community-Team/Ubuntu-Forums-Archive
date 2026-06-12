---
title: "How to install SageMaths on ubuntu"
date: 2008-11-20
forum: Education &amp; Science
---

### Post by bigbrovar on 2008-11-20
how i got to install sage on ubuntu..

Sage is a free open-source mathematics software system licensed under the GPL. It combines the power  of many existing open-source packages into a common Python-based interface. 
you can read more about sage here [http://www.sagemath.org/tour.html]("http://www.sagemath.org/tour.html") 
unfortunately sage is not available in the Ubuntu repositories and in-fact any repositories as a .deb package. ( at the time of writing this). did you say compiling? dont even go there i tried building it. and failed woefully. fortunately i found a nice and easy to install it on Ubuntu. there is a binary package already compiled for Ubuntu. which makes installation on Ubuntu quite easy and straight forward.

first we download the ubuntu binary here [http://www.sagemath.org/bin/linux/32bit/]("http://www.sagemath.org/bin/linux/32bit/"). the guide is based on version 3.1.4 so i just did

```
wget http://www.sagemath.org/bin/linux/32bit/sage-3.1.4-ubuntu32-intel-XEON-x86-i686-Linux.tar.gz
```

once downloaded . i untar it (extracted the archive)  
in my case 

```
tar xzvf sage-3.1.4-ubuntu32-intel-XEON-x86-i686-Linux.tar.gz
```

then i moved it to **/usr/local/src/**

```
sudo mv sage-3.1.4-ubuntu32-intel-XEON-x86-i686-Linux /usr/local/src
```

then i copied the sage script in to **/usr/local/bin**

```
sudo cp /usr/local/src/sage-3.1.4-ubuntu32-intel-XEON-x86-i686-Linux/sage /usr/local/bin
```

then i edited SAGE_ROOT in **/usr/local/bin/sage** to point to **/usr/local/src/sage-3.1.4-ubuntu32-intel-XEON-x86-i686-Linux**


```
gksu gedit /usr/local/bin/sage
```

modified it to look like this
```

# Set SAGE_ROOT to the location of the sage install.
SAGE_ROOT="/usr/local/src/sage-3.1.4-ubuntu32-intel-XEON-x86-i686-Linux/"
```


i modified the sage root directory permission settings
```
sudo chmod -R 755 /usr/local/src/sage-3.1.4-ubuntu32-intel-XEON-x86-i686-Linux
```

now run you can run it

```
sage
```

to get a webbased ui 
```
run notebook()
```

hope someone finds this useful

---

### Post by xounic on 2008-11-22
Thank you for the the HowTo!

I just wanted to add something about a problem I had with **jsMath** in the sage-notebook:

Allthoug I installed jsMath correctly and it was working on other sites it did not in the notebooks running my local sage server.

After a while I found the following solution:

I downloaded the Image-Font-Package from the jsMath-site : [http://sourceforge.net/project/showfiles.php?group_id=172663]("http://sourceforge.net/project/showfiles.php?group_id=172663")

Then I unzipped it (for example to /tmp) and copied the contained directory named "fonts"
to the destination sageDir/data/extcode/notebook/javascript/jsmath/

After that the pretty_print-command in the sage notebook worked!
(Before I just could see the LaTeX-like "source code" of jsMath)


Maybe this explanations helps saving some time to someone with the same problem.

Maybe I should mention, that I did not installed sage system wide. I just downloaded, unpacked and started it.

---

### Post by rajatgoel on 2010-07-13
Hi... 

i am using ubuntu 9.04 on a 32 bit sysytem....i downloaded the following version of sage..
 **[[B]sage-4.4.4-linux-32bit-ubuntu_10.04_lts-i686-Linux.tar.lzma**]("http://www.cecm.sfu.ca/sage/linux/32bit/sage-4.4.4-linux-32bit-ubuntu_10.04_lts-i686-Linux.tar.lzma")

[/B]Is their any other version of sage for ubuntu 9.04...I am getting the following error when i follow the above mentioned procedure..

----------------------------------------------------------------------
| Sage Version 4.4.4, Release Date: 2010-06-23                       |
| Type notebook() for the GUI, and license() for information.        |
----------------------------------------------------------------------
---------------------------------------------------------------------------
ImportError                               Traceback (most recent call last)

/usr/local/src/sage-4.4.4-linux-32bit-ubuntu_10.04_lts-i686-Linux/local/bin/<string> in <module>()

/usr/local/src/sage-4.4.4-linux-32bit-ubuntu_10.04_lts-i686-Linux/local/lib/python2.6/site-packages/sage/misc/preparser_ipython.py in <module>()
      6 ###########################################################################

      7 
----> 8 import sage.misc.interpreter
      9 
     10 import preparser

/usr/local/src/sage-4.4.4-linux-32bit-ubuntu_10.04_lts-i686-Linux/local/lib/python2.6/site-packages/sage/misc/interpreter.py in <module>()
    100 
    101 import os
--> 102 import log
    103 
    104 import remote_file

/usr/local/src/sage-4.4.4-linux-32bit-ubuntu_10.04_lts-i686-Linux/local/lib/python2.6/site-packages/sage/misc/log.py in <module>()
     63 
     64 import interpreter
---> 65 import latex
     66 import misc
     67 

/usr/local/src/sage-4.4.4-linux-32bit-ubuntu_10.04_lts-i686-Linux/local/lib/python2.6/site-packages/sage/misc/latex.py in <module>()
     38 import random
     39 
---> 40 from misc import tmp_dir, graphics_filename
     41 import sage_eval
     42 from sage.misc.misc import SAGE_DOC

/usr/local/src/sage-4.4.4-linux-32bit-ubuntu_10.04_lts-i686-Linux/local/lib/python2.6/site-packages/sage/misc/misc.py in <module>()
     36 
     37 import operator, os, stat, socket, sys, signal, time, weakref, resource, math
---> 38 import sage.misc.prandom as random
     39 
     40 from banner import version, banner

/usr/local/src/sage-4.4.4-linux-32bit-ubuntu_10.04_lts-i686-Linux/local/lib/python2.6/site-packages/sage/misc/prandom.py in <module>()
     54 # setting seeds should only be done through sage.misc.randstate .

     55 
---> 56 from sage.misc.randstate import current_randstate
     57 
     58 def _pyrand():

ImportError: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by /usr/local/src/sage-4.4.4-linux-32bit-ubuntu_10.04_lts-i686-Linux/local/lib/libpari-gmp.so.2)
WARNING: Failure executing code: 'import sage.misc.preparser_ipython;  sage.misc.preparser_ipython.magma_colon_equals=True'
---------------------------------------------------------------------------
ImportError                               Traceback (most recent call last)

/usr/local/src/sage-4.4.4-linux-32bit-ubuntu_10.04_lts-i686-Linux/local/lib/python2.6/site-packages/IPython/ipmaker.pyc in force_import(modname)
     64         reload(sys.modules[modname])
     65     else:
---> 66         __import__(modname)
     67 
     68 

/usr/local/src/sage-4.4.4-linux-32bit-ubuntu_10.04_lts-i686-Linux/local/bin/ipy_profile_sage.py in <module>()
      1 import os
      2 if 'SAGE_CLEAN' not in os.environ:
----> 3     import sage.misc.misc
      4     from sage.misc.interpreter import preparser, _ip
      5     preparser(True)

/usr/local/src/sage-4.4.4-linux-32bit-ubuntu_10.04_lts-i686-Linux/local/lib/python2.6/site-packages/sage/misc/misc.py in <module>()
     36 
     37 import operator, os, stat, socket, sys, signal, time, weakref, resource, math
---> 38 import sage.misc.prandom as random
     39 
     40 from banner import version, banner

/usr/local/src/sage-4.4.4-linux-32bit-ubuntu_10.04_lts-i686-Linux/local/lib/python2.6/site-packages/sage/misc/prandom.py in <module>()
     54 # setting seeds should only be done through sage.misc.randstate .

     55 
---> 56 from sage.misc.randstate import current_randstate
     57 
     58 def _pyrand():

ImportError: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by /usr/local/src/sage-4.4.4-linux-32bit-ubuntu_10.04_lts-i686-Linux/local/lib/libpari-gmp.so.2)
Error importing ipy_profile_sage - perhaps you should run %upgrade?
WARNING: Loading of ipy_profile_sage failed.

WARNING: Readline services not available on this platform.
WARNING: The auto-indent feature requires the readline library
<ERROR: name 'sage_prompt' is not defined>


What could be the possible reason for this error and how should I remove it and run sage??

---

