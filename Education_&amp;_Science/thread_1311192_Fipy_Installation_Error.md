---
title: "Fipy Installation Error"
date: 2009-11-02
forum: Education &amp; Science
---

### Post by atentik on 2009-11-02
I have been trying to install Fipy on my Ubuntu 9.10 for a while now. It seems to have been install but whenever I tried importing the program in python, I get an error message: 
> >>> from fipy import*
Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    from fipy import*
  File "/usr/local/lib/python2.6/dist-packages/FiPy-2.0.2-py2.6.egg/fipy/__init__.py", line 11, in <module>
    from solvers import *
  File "/usr/local/lib/python2.6/dist-packages/FiPy-2.0.2-py2.6.egg/fipy/solvers/__init__.py", line 35, in <module>
    raise ImportError, "Could not import any solver package. If you are using Trilinos, make sure you have all of the necessary Trilinos packages installed - Epetra, EpetraExt, AztecOO, Amesos, ML, and IFPACK."
**ImportError: Could not import any solver package.** If you are using Trilinos, make sure you have all of the necessary Trilinos packages installed - Epetra, EpetraExt, AztecOO, Amesos, ML, and IFPACK.


For your information, I installed the trilions package but the problem persist. Any idea what the problem might be. Has anybody encountered this problem and be able to come up with a remedy?

---

### Post by atentik on 2009-11-04
The problem was solved by installing *sparse*

---

