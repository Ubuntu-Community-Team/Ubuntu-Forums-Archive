---
title: "Python Coding (installation of different versions)"
date: 2009-02-27
forum: General Help
---

### Post by houseonfire on 2009-02-27
I want to start coding in Python 3. I just installed it.
I was reading in the readme that if i want to install more than one version I need to use make altinstall command when installing the versions I wont use.
So i went to symantic to uninstall the Python 2.4 and 2.5. But it wanted to uninstall a truck load of my programs.

I guess I don't understand the process.
I just want to code a program I've been needing for a while...
Can someone help me out please?


And also, is there way I can debug code (like the Python for windows) without being in the terminal?

---

### Post by justleen on 2009-02-27
What did it want to remove? Programs you wrote, or ubuntu packages?

As far as debugging goes, there are plenty of IDE's for python.  
Have a look here: [http://wiki.python.org/moin/IntegratedDevelopmentEnvironments](http://wiki.python.org/moin/IntegratedDevelopmentEnvironments)

---

### Post by houseonfire on 2009-02-27
> **justleen said:**
> What did it want to remove? Programs you wrote, or ubuntu packages?

As far as debugging goes, there are plenty of IDE's for python.  
Have a look here: [http://wiki.python.org/moin/IntegratedDevelopmentEnvironments](http://wiki.python.org/moin/IntegratedDevelopmentEnvironments)

From the readme:
```
On Unix and Mac systems if you intend to install multiple versions of Python
using the same installation prefix (--prefix argument to the configure script)
you must take care that your primary python executable is not overwritten by
the installation of a different version.  All files and directories installed
using "make altinstall" contain the major and minor version and can thus live
side-by-side.  "make install" also creates ${prefix}/bin/python which refers
to ${prefix}/bin/pythonX.Y.  If you intend to install multiple versions using
the same prefix you must decide which version (if any) is your "primary"
version.  Install that version using "make install".  Install all other
versions using "make altinstall".
```

I currently have 3 python packages installed:
2.4
2.5
3.0.1

---

