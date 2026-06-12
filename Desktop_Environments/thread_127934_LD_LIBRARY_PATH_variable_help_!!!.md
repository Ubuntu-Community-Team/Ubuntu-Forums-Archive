---
title: "LD_LIBRARY_PATH variable help !!!"
date: 2006-02-10
forum: Desktop Environments
---

### Post by daredevil on 2006-02-10
hi all.. i tried to execute c native code using JNI in kubuntu breezy.. after i finished all the steps i was unable to execute the .class file using java command because the java.library.path varirable is not properly set. it depends on the LD_LIBRARY_PATH variable. even after setting and exporting the LD_LIBRARY_PATH variable the problem still exists.. i dunno what is wrong ..is there any file that i should edit .. help me plz..

sriram@Home:~/Desktop/HelloWorld$ ls -l
total 120
-rwxrwxrwx  1 sriram sriram   190 2006-02-10 17:00 HelloWorld.c
-rwxrwxrwx  1 sriram sriram   179 2006-02-10 17:44 HelloWorld.c~
-rwxrwxrwx  1 sriram sriram   180 2006-02-10 13:44 HelloWorld.c~~
-rwxrwxrwx  1 sriram sriram   458 2006-02-10 17:05 HelloWorld.class
-rwxrwxrwx  1 sriram sriram   377 2006-02-10 11:00 HelloWorld.h
-rwxrwxrwx  1 sriram sriram   247 2006-02-10 17:44 HelloWorld.java
-rwxrwxrwx  1 sriram sriram   247 2006-02-10 17:43 HelloWorld.java~
-rwxrwxrwx  1 sriram sriram  7144 2006-02-10 17:05 HelloWorld.so
-rw-r--r--  1 sriram sriram 71122 2006-02-10 11:42 jni.h
-rw-rw-r--  1 sriram sriram   381 1999-06-13 21:03 makefile.solaris
-rw-r--r--  1 sriram sriram   406 1999-06-13 21:03 makefile.win32
sriram@Home:~/Desktop/HelloWorld$ export LD_LIBRARY_PATH=.
sriram@Home:~/Desktop/HelloWorld$ java HelloWorld
Exception in thread "main" java.lang.UnsatisfiedLinkError: no HelloWorld.so in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:992)
        at HelloWorld.<clinit>(HelloWorld.java:Cool
sriram@Home:~/Desktop/HelloWorld$

---

