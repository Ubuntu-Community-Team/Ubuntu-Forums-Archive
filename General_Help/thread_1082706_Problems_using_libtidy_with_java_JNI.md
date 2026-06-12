---
title: "Problems using libtidy with java JNI"
date: 2009-02-28
forum: General Help
---

### Post by tymtheenchanter on 2009-02-28
Hi,

I am trying to use libtidy via java JNI. I have created the .h header file for my class with javah without any problems. The c files then compile into the desired .so library without problems as well. They are linked to libtidy.so (libtidy-0.99.so.0) which was installed from the repos. The problem is that whenever I try to invoke the native code I get the following error:

```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fccfd852160, pid=18494, tid=1083865424
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (11.0-b15 mixed mode linux-amd64)
# Problematic frame:
# C  [libTidyLib.so+0x28160]  tidyBufFree+0x10
#
# An error report file with more information is saved as:
# *********/hs_err_pid18494.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
```

the hs_error is attached.

the make command to build the .so library is:
```

JAVA_INCLUDE_DIR=/usr/lib/jvm/java-6-openjdk/include
JAVAH_INCLUDE_FLAGS=-I$(JAVA_INCLUDE_DIR) -I$(JAVA_INCLUDE_DIR)/linux
LIB_TIDY_INCLUDE_FLAGS=-I/usr/include/tidy

gcc -shared -fPIC -Wall $(LIB_TIDY_INCLUDE_FLAGS) $(JAVAH_INCLUDE_FLAGS) -ltidy  src/CTidy.c -o libjnitidy.so

```

I am running intrepid with java-6-openjdk

I have also tried to install lib tidy from source (tidy.sf.net) and have the same errors.

Does anyone know what is going wrong & how to fix it please?

---

### Post by tymtheenchanter on 2009-02-28
Ok fixed it :P

The problem was in the C code (not surprisingly) where a buffer was being freed without checking that is was not empty (the empty buffer caused tidyBufFree to crash).

Just goes to show, 
 a) even though the code used to work doesn't mean that it still does
and
 b) always check your C code with JNI:redface:

---

