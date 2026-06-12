---
title: "zend studio 5.5"
date: 2010-02-18
forum: Desktop Environments
---

### Post by mhkonly on 2010-02-18
I installed zend studio 5.5 successfully, but when I try to open it  open as a gray screen (blank).
I cant do any thing after that (with zend studio I mean)

any solution?

---

### Post by kellemes on 2010-02-18
> **mhkonly said:**
> I installed zend studio 5.5 successfully, but when I try to open it  open as a gray screen (blank).
I cant do any thing after that (with zend studio I mean)

any solution?

Have you tried running it from the commandline?
The terminal output may shed some light on the issue..

---

### Post by mhkonly on 2010-02-18
> **kellemes said:**
> Have you tried running it from the commandline?
The terminal output may shed some light on the issue..


yes I tried it the same result!

---

### Post by Dirk Hahn on 2010-10-22
Hi there,

just to leave this question not unanswered: the trick that worked for me is described on the following site:

[http://bwyan.dk/?p=221](http://bwyan.dk/?p=221)

The author desribes that a simple additional line will do the trick:
> 
gedit ./Zend/ZendStudio-5.5.1/bin/ZDE
scroll down to line 1693. You'll find the following code there:
> 
#debugOut ""
debugOut "[7m========= VM Command Line ============================================[0m"
#debugOut "CLASSPATH=$lax_class_path"
now change line 1963 to the following:
> 

options="$options -Dawt.toolkit=sun.awt.motif.MToolkit"
#debugOut ""
debugOut "[7m========= VM Command Line ============================================[0m"
#debugOut "CLASSPATH=$lax_class_path"

Save the file you just edited and start the Zend Studio. It should work now.

---

### Post by RJARRRPCGP on 2010-10-22
Likely a missing dependency.

---

