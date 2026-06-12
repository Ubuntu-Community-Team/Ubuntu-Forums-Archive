---
title: "PySolFC install"
date: 2008-07-07
forum: Gaming &amp; Leisure
---

### Post by binarycortex on 2008-07-07
Until PySol Fan Club Edition is added to the repositories, here is what I did to get it to work in Ubuntu 8.04. Download the file (PySolFC-1.1.tar.bz2) then extract the contents. According to the readme file you should be able to run it by typing "python pysol.py" from a command line. This gave me an error similar to the following:

  File "/usr/share/PySolFC/pysol.py", line 29, in <module>
    from pysollib.main import main
  File "/usr/lib/python2.5/site-packages/pysollib/main.py", line 43, in <module>
    from util import DataLoader
  File "/usr/lib/python2.5/site-packages/pysollib/util.py", line 65, in <module>
    from mfxutil import Image
  File "/usr/lib/python2.5/site-packages/pysollib/mfxutil.py", line 60, in <module>
    import ImageTk
ImportError: No module named ImageTk

To fix this run the following command "sudo aptitude install python-imaging-tk. This should fix the problem.

Have fun,
Ian

---

### Post by K.Mandla on 2008-07-07
Moved to Gaming and Leisure.

---

### Post by chas2007 on 2008-10-15
> **binarycortex said:**
> Until PySol Fan Club Edition is added to the repositories, here is what I did to get it to work in Ubuntu 8.04. Download the file (PySolFC-1.1.tar.bz2) then extract the contents. According to the readme file you should be able to run it by typing "python pysol.py" from a command line. This gave me an error similar to the following:

  File "/usr/share/PySolFC/pysol.py", line 29, in <module>
    from pysollib.main import main
  File "/usr/lib/python2.5/site-packages/pysollib/main.py", line 43, in <module>
    from util import DataLoader
  File "/usr/lib/python2.5/site-packages/pysollib/util.py", line 65, in <module>
    from mfxutil import Image
  File "/usr/lib/python2.5/site-packages/pysollib/mfxutil.py", line 60, in <module>
    import ImageTk
ImportError: No module named ImageTk

To fix this run the following command "sudo aptitude install python-imaging-tk. This should fix the problem.

Have fun,
Ian

Thank you Ian, it worked!  :)

---

### Post by cwsnyder on 2012-06-03
PysolFc is now in the Software Center, but on a new install, it will still fail to run, requiring a package with 'tkinter' to run.  To fix this, do ```
sudo apt-get install python-tk
``` and run PysolFC again.

---

