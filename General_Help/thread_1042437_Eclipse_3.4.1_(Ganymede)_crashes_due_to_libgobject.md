---
title: "Eclipse 3.4.1 (Ganymede) crashes due to libgobject (repeatable)"
date: 2009-01-17
forum: General Help
---

### Post by thekonstantin on 2009-01-17
Hello @ all!

I'm using Ubuntu 8.04.

I've downloaded and unzipped Eclipse 3.4.1 from eclipse.org (I've tried different Distros) to /opt as root. After this I've installed the [openArchitectureWare]("http://www.openarchitectureware.org/") plug-in.

When I create a new openArchitectureWare project, Eclipse crashes with the following messages:

```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb547ebe2, pid=14081, tid=3084790672
#
# Java VM: Java HotSpot(TM) Client VM (11.2-b01 mixed mode, sharing linux-x86)
# Problematic frame:
# C  [libgobject-2.0.so.0+0x27be2]  g_type_check_instance_cast+0x22
#
# An error report file with more information is saved as:
# /tmp/hs_err_pid14081.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

```

I've pasted the log file [here]("http://pastebin.com/f25612fd7").

I've tried this with different java versions (java-6-sun, java-6-openjdk, java-1.5.0-sun, and jdk1.6.0_12 (downloaded from sun)) without success.

Has somebody an idea what I can do now?

Konstantin

---

### Post by thekonstantin on 2009-01-18
Originally I didn't want upgrade to 8.10 (because 8.04 is LTS and "never change a running system" ...). But an upgrade to 8.10 has fixed the problem described above.

---

### Post by linyunfeng on 2009-04-07
I have the same problem on Eclipse 3.4.2 for ubuntu 9.04 64 bit version. Anyone have solution for that?

---

### Post by mb0108 on 2009-04-12
Same here ... 3.4.2 with Jaunty all updates...

---

### Post by mb0108 on 2009-04-12
I found my problem... Eclipse does not work right with the globalmenu 0.7.3 available for jaunty... When I uninstalled globalmenu, Eclipse does start normally... Hope this will be fixed soon cause I like the Globalmenu !

---

### Post by mb0108 on 2009-04-20
With the latest Jaunty updates it works for me now ... Very good :-)

---

### Post by wariows on 2009-10-23
Hello boys,

This problem occurs when you have gnome-globalmenu activated... to fix it just create a bash script:

#!/bin/bash
unset GTK_MODULES
./eclipse

eclipse works and globalmenu works on other windows either.

[]'s

---

