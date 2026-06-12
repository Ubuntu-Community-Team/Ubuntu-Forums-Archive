---
title: "sage 4.2.1 runnibg problem"
date: 2009-12-02
forum: Education &amp; Science
---

### Post by freeburn on 2009-12-02
i have installed sage 4.2.1. but when i give 'sage' command, it shows an warninig. the warning is :

[B]ImportError: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/local/src/sage-4.2.1-linux-Ubuntu_9.10-i686-Linux/local/lib/libgmpxx.so.3)
Error importing ipy_profile_sage - perhaps you should run %upgrade?
WARNING: Loading of ipy_profile_sage failed.

[/B]and the gui 'notebook' also crashes giving the same error message .

i have upgraded sage. my ubuntu is also upgraded. so whats wrong with it? i'm using jaunty ,is that aproblem?

---

### Post by Fuujuhi on 2009-12-11
Hello,

A solution is given in **[this thread]("http://groups.google.com/group/sage-devel/browse_thread/thread/1b05c73e974bfa07/ab0393f1b002de09?lnk=raot")** by William Stein.

It basically consists in downloading a more recent version of the library [FONT="Courier New"]libstdc++.so[/FONT] (version [FONT="Courier New"]libstdc++.so.6.0.12[/FONT]) and copy it to the folder [FONT="Courier New"]./local/lib[/FONT] in the sage directory. A version of that file is in attachment. You also need to create a symbolic link in the same folder:
```
ln -s libstdc++.so.6.0.12 libstdc++.so.6
```

I tried it on Ubuntu 9.04 Jaunty (actually on [AndLinux Beta 2]("http://www.andlinux.org/index.php")) and it worked fine...

---

### Post by sumitk7 on 2010-02-07
hello,

facing the same problem .. but the solution not working. 

using ubuntu 9.10

cheers

---

### Post by shtumf on 2010-02-13
sagemath.org
download a sage binary
extract the tar file
enter sage directory
run sage with this command 
./sage
or if you want sage with GUI
./sage --notebook

I prefer binary packages from sagemath.org rather than using apt-get install sagemath and bother with missing packages.

Sage binary files from sage math contain stuff you need to run sage. 

So maybe you can fix your problem this way 

Bye

---

### Post by InonS on 2011-04-26
bump.

I compiled Sage 4.6.2 on my Lucid 10.04, and got this:

```

administrator@Inon-desktop:~/...$ ./sage

``````

----------------------------------------------------------------------
| Sage Version 4.6.2, Release Date: 2011-02-25                       |
| Type notebook() for the GUI, and license() for information.        |
----------------------------------------------------------------------
Setting permissions of DOT_SAGE directory so only you can read and write it.
---------------------------------------------------------------------------
OSError                                   Traceback (most recent call last)

/home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/bin/<string> in <module>()

/home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/lib/python2.6/site-packages/sage/misc/preparser_ipython.py in <module>()
      6 ###########################################################################

      7 
----> 8 import sage.misc.interpreter
      9 
     10 import preparser

/home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/lib/python2.6/site-packages/sage/misc/interpreter.py in <module>()
    100 
    101 import os
--> 102 import log
    103 import re
    104 

/home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/lib/python2.6/site-packages/sage/misc/log.py in <module>()
     63 
     64 import interpreter
---> 65 import latex
     66 import misc
     67 

/home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/lib/python2.6/site-packages/sage/misc/latex.py in <module>()
     38 import random
     39 
---> 40 from misc import tmp_dir, graphics_filename
     41 import sage_eval
     42 from sage.misc.misc import SAGE_DOC

/home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/lib/python2.6/site-packages/sage/misc/misc.py in <module>()
    102     print "Setting permissions of DOT_SAGE directory so only you can read and write it."
    103     # Change mode of DOT_SAGE.

--> 104     os.chmod(DOT_SAGE, _desired_mode)
    105 
    106 

OSError: [Errno 1] Operation not permitted: '/home/administrator/.sage/'
WARNING: Failure executing code: 'import sage.misc.preparser_ipython;  sage.misc.preparser_ipython.magma_colon_equals=True'
Setting permissions of DOT_SAGE directory so only you can read and write it.
---------------------------------------------------------------------------
OSError                                   Traceback (most recent call last)

/home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/lib/python2.6/site-packages/IPython/ipmaker.pyc in force_import(modname)
     64         reload(sys.modules[modname])
     65     else:
---> 66         __import__(modname)
     67 
     68 

/home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/bin/ipy_profile_sage.py in <module>()
      1 import os
      2 if 'SAGE_CLEAN' not in os.environ:
----> 3     import sage.misc.misc
      4     from sage.misc.interpreter import preparser, _ip
      5     preparser(True)

/home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/lib/python2.6/site-packages/sage/misc/misc.py in <module>()
    102     print "Setting permissions of DOT_SAGE directory so only you can read and write it."
    103     # Change mode of DOT_SAGE.

--> 104     os.chmod(DOT_SAGE, _desired_mode)
    105 
    106 

OSError: [Errno 1] Operation not permitted: '/home/administrator/.sage/'
Error importing ipy_profile_sage - perhaps you should run %upgrade?
WARNING: Loading of ipy_profile_sage failed.

<ERROR: name 'sage_prompt' is not defined>

```Any input gets debuging data and the reply 
```

IOError                                   Traceback (most recent call last)

/home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/lib/python2.6/site-packages/IPython/iplib.pyc in raw_input(self, prompt, continue_prompt)
   2185             # only entries starting at first column go to shadow history
   2186             if line.lstrip() == line:
-> 2187                 self.shadowhist.add(line.strip())
   2188         elif not continue_prompt:
   2189             self.input_hist_raw.append('\n')

/home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/lib/python2.6/site-packages/IPython/history.pyc in add(self, ent)
    233         if old is not _sentinel:
    234             return
--> 235         newidx = self.inc_idx()
    236         #print "new",newidx # dbg
    237         self.db.hset('shadowhist',ent, newidx)

/home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/lib/python2.6/site-packages/IPython/history.pyc in inc_idx(self)
    226     def inc_idx(self):
    227         idx = self.db.get('shadowhist_idx', 1)
--> 228         self.db['shadowhist_idx'] = idx + 1
    229         return idx
    230         

/home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/lib/python2.6/site-packages/IPython/Extensions/pickleshare.pyc in __setitem__(self, key, value)
     84         if parent and not parent.isdir():
     85             parent.makedirs()
---> 86         pickled = pickle.dump(value,fil.open('w'))
     87         try:
     88             self.cache[fil] = (value,fil.mtime)

/home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/lib/python2.6/site-packages/IPython/external/path.pyc in open(self, mode)
    521     def open(self, mode='r'):
    522         """ Open this file.  Return a file object. """
--> 523         return file(self, mode)
    524 
    525     def bytes(self):

IOError: [Errno 13] Permission denied: path('/home/administrator/.sage/ipython/db/shadowhist_idx')

```Does this look like a permissions error?
I compiled as a regular user (as opposed to using sudo), and I could ```
cd
``` into '/home/administrator/.sage/' with no problems. 
(Previously, I compiled using 'sudo' and had to chmod g+rX to be able to get into that directory, for instance)

I also tried
```

cp /usr/lib/libstdc++.so.6.0.13 /home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/bin/

cd /home/administrator/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/bin/

ln -s libstdc++.so.6.0.13 libstdc++.so.6
administrator@Inon-desktop:~/Downloads/sage-4.6.2-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux/local/bin$ 

```
Any help would be greatly appreciated!

==================================================================================================

System info:

> 
Linux Inon-desktop 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:25:51 UTC 2011 x86_64 GNU/Linux

Linux version 2.6.32-31-generic (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #61-Ubuntu SMP Fri Apr 8 18:25:51 UTC 2011


GNU Fortran (Ubuntu 4.4.3-4ubuntu5) 4.4.3
Copyright (C) 2010 Free Software Foundation, Inc.

g++ (Ubuntu 4.4.3-4ubuntu5) 4.4.3
Copyright (C) 2009 Free Software Foundation, Inc.

GNU Make 3.81
  Copyright (C) 2006  Free Software Foundation, Inc.
  This is free software; see the source for copying conditions.
  There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
  PARTICULAR PURPOSE.
  
  This program built for x86_64-pc-linux-gnu
for
processor    : 0
and
processor    : 1

> vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
stepping    : 6
cpu MHz        : 1596.000
cache size    : 3072 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm
bogomips    : 5066.48
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

---

### Post by cully5 on 2011-08-16
I see this is an old thread but it still comes up high in google :)
For anyone trying to figure it out, follow the instructions below ensuring you not only copy [FONT=Courier New]libstdc++.so.6.0.12[/FONT]
 to the ./local/lib dir of sage but also create a link to the file under an alternate name ( libstdc++.so.6 ) as instructed.
Thanks Fuujuhi and Willian Stein

> **Fuujuhi said:**
> Hello,

A solution is given in **[this thread]("http://groups.google.com/group/sage-devel/browse_thread/thread/1b05c73e974bfa07/ab0393f1b002de09?lnk=raot")** by William Stein.

It basically consists in downloading a more recent version of the library [FONT=Courier New]libstdc++.so[/FONT] (version [FONT=Courier New]libstdc++.so.6.0.12[/FONT]) and copy it to the folder [FONT=Courier New]./local/lib[/FONT] in the sage directory. A version of that file is in attachment. You also need to create a symbolic link in the same folder:
```
ln -s libstdc++.so.6.0.12 libstdc++.so.6
```I tried it on Ubuntu 9.04 Jaunty (actually on [AndLinux Beta 2]("http://www.andlinux.org/index.php")) and it worked fine...

---

### Post by grappler on 2011-10-06
Has anyone succeeded in installing sage 4.7.1 on oneiric (64bit)?  

The binary:

[**sage-4.7.1-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux.tar.lzma**]("http://mirrors.xmission.com/sage/linux/64bit/sage-4.7.1-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux.tar.lzma")


reports a missing module _md5 when I try to run it. When I try to build sage from source I get the error 

> 
 no acceptable C compiler found in $PATHeven though both gcc and g++ 4.6.1 are installed.

---

### Post by surfer on 2011-10-17
same problem here. the first sage run (as root) on oneiric reports the following:

```
$ sudo ./sage/sage 
----------------------------------------------------------------------
| Sage Version 4.7.1, Release Date: 2011-08-11                       |
| Type notebook() for the GUI, and license() for information.        |
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/opt/sage/local/bin/sage-ipython", line 18, in <module>
    import IPython
  File "/opt/sage/local/lib/python2.6/site-packages/IPython/__init__.py", line 58, in <module>
    __import__(name,glob,loc,[])
  File "/opt/sage/local/lib/python2.6/site-packages/IPython/ipstruct.py", line 22, in <module>
    from IPython.genutils import list2dict2
  File "/opt/sage/local/lib/python2.6/site-packages/IPython/genutils.py", line 59, in <module>
    from IPython.external.path import path
  File "/opt/sage/local/lib/python2.6/site-packages/IPython/external/path.py", line 35, in <module>
    import md5
  File "/opt/sage/local/lib/python/md5.py", line 10, in <module>
    from hashlib import md5
  File "/opt/sage/local/lib/python/hashlib.py", line 136, in <module>
    md5 = __get_builtin_constructor('md5')
  File "/opt/sage/local/lib/python/hashlib.py", line 63, in __get_builtin_constructor
    import _md5
ImportError: No module named _md5

```

any ideas?

---

### Post by surfer on 2011-10-18
posted my issue as a [new thread]("http://ubuntuforums.org/showthread.php?t=1863653") as it does not really belong here.

---

