---
title: "Can't Get Alice To Work"
date: 2008-05-05
forum: Education &amp; Science
---

### Post by SimonHalliday on 2008-05-05
I am trying to get [Alice]("http://www.alice.org") to work in order to teach myself to program.  

Anyway, I have done exactly as the instructions say.  
Extracted and unzipped the download file.  
mkdir the file into which I was installing it
ran the ./alice-run file. 

Keep on getting the following output:
attempting to register mp3 capability... 
Registered succesfully
*sys-package-mgr*: processing modified jar, '/usr/share/java/libgcj-4.2.jar'
*sys-package-mgr*: can't write cache file for '/usr/share/java/libgcj-4.2.jar'
java.lang.ExceptionInInitializerError
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at edu.cmu.cs.stage3.alice.authoringtool.JAlice.main(JAlice.java:129)
Caused by: Traceback (innermost last):
  File "/home/ubuntu/Games/Alice/Required/resources/Alice Style.py", line 461, in ?
  File "/home/ubuntu/Games/Alice/Required/resources/common/ResourceTransfer.py", line 42, in ?
java.lang.ClassNotFoundException: edu.cmu.cs.stage3.alice.core.Model
   at java.lang.Class.forName(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.python.core.PyReflectedFunction.__call__(PyReflectedFunction.java)
   at org.python.core.PyReflectedFunction.__call__(PyReflectedFunction.java)
   at org.python.core.PyObject.__call__(PyObject.java)
   at org.python.core.PyObject.invoke(PyObject.java)
   at org.python.pycode._pyx2.f$0(/home/ubuntu/Games/Alice/Required/resources/common/ResourceTransfer.py:42)
   at org.python.pycode._pyx2.call_function(/home/ubuntu/Games/Alice/Required/resources/common/ResourceTransfer.py)
   at org.python.core.PyTableCode.call(PyTableCode.java)
   at org.python.core.PyCode.call(PyCode.java)
   at org.python.core.Py.runCode(Py.java)
   at org.python.core.__builtin__.execfile_flags(__builtin__.java)
   at org.python.core.__builtin__.execfile(__builtin__.java)
   at org.python.core.__builtin__.execfile(__builtin__.java)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.python.core.PyReflectedFunction.__call__(PyReflectedFunction.java)
   at org.python.core.PyReflectedFunction.__call__(PyReflectedFunction.java)
   at org.python.core.PyObject.__call__(PyObject.java)
   at org.python.pycode._pyx0.f$0(/home/ubuntu/Games/Alice/Required/resources/Alice Style.py:461)
   at org.python.pycode._pyx0.call_function(/home/ubuntu/Games/Alice/Required/resources/Alice Style.py)
   at org.python.core.PyTableCode.call(PyTableCode.java)
   at org.python.core.PyCode.call(PyCode.java)
   at org.python.core.Py.runCode(Py.java)
   at org.python.core.__builtin__.execfile_flags(__builtin__.java)
   at org.python.core.__builtin__.execfile(__builtin__.java)
   at edu.cmu.cs.stage3.alice.authoringtool.AuthoringToolResources.loadResourcesPy(AuthoringToolResources.java:199)
   at edu.cmu.cs.stage3.alice.authoringtool.AuthoringToolResources.<clinit>(AuthoringToolResources.java:108)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at edu.cmu.cs.stage3.alice.authoringtool.JAlice.main(JAlice.java:129)

java.lang.ClassNotFoundException: java.lang.ClassNotFoundException: edu.cmu.cs.stage3.alice.core.Model

   at org.python.core.Py.JavaError(Py.java)
   at org.python.core.Py.JavaError(Py.java)
   at org.python.core.PyReflectedFunction.__call__(PyReflectedFunction.java)
   at org.python.core.PyReflectedFunction.__call__(PyReflectedFunction.java)
   at org.python.core.PyObject.__call__(PyObject.java)
   at org.python.core.PyObject.invoke(PyObject.java)
   at org.python.pycode._pyx2.f$0(/home/ubuntu/Games/Alice/Required/resources/common/ResourceTransfer.py:42)
   at org.python.pycode._pyx2.call_function(/home/ubuntu/Games/Alice/Required/resources/common/ResourceTransfer.py)
   at org.python.core.PyTableCode.call(PyTableCode.java)
   at org.python.core.PyCode.call(PyCode.java)
   at org.python.core.Py.runCode(Py.java)
   at org.python.core.__builtin__.execfile_flags(__builtin__.java)
   at org.python.core.__builtin__.execfile(__builtin__.java)
   at org.python.core.__builtin__.execfile(__builtin__.java)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.python.core.PyReflectedFunction.__call__(PyReflectedFunction.java)
   at org.python.core.PyReflectedFunction.__call__(PyReflectedFunction.java)
   at org.python.core.PyObject.__call__(PyObject.java)
   at org.python.pycode._pyx0.f$0(/home/ubuntu/Games/Alice/Required/resources/Alice Style.py:461)
   at org.python.pycode._pyx0.call_function(/home/ubuntu/Games/Alice/Required/resources/Alice Style.py)
   at org.python.core.PyTableCode.call(PyTableCode.java)
   at org.python.core.PyCode.call(PyCode.java)
   at org.python.core.Py.runCode(Py.java)
   at org.python.core.__builtin__.execfile_flags(__builtin__.java)
   at org.python.core.__builtin__.execfile(__builtin__.java)
   at edu.cmu.cs.stage3.alice.authoringtool.AuthoringToolResources.loadResourcesPy(AuthoringToolResources.java:199)
   at edu.cmu.cs.stage3.alice.authoringtool.AuthoringToolResources.<clinit>(AuthoringToolResources.java:108)
   at java.lang.Class.initializeClass(libgcj.so.81)
   ...3 more


I don't really know what all of this means.  But nothing starts up. 

I have updated my java environment to ensure that Java isn't the problem.  Any suggestions would be helpful. 

Thanks, 
Simon

---

### Post by hubie on 2008-05-09
I have not tried to install Alice (in fact, I didn't even know what it was until I followed your link), but since it is Java-based you might want to make sure which Java you are running.  It might be a case where it runs well only on the official Sun Java.

I ran into this problem with running [JabRef]("http://jabref.sourceforge.net/index.php").  You might find their [FAQ page]("http://jabref.sourceforge.net/faq.php") helpful on working through the Java types.

---

### Post by Promaster91 on 2008-05-11
Do you have the jdk or the jre?

---

