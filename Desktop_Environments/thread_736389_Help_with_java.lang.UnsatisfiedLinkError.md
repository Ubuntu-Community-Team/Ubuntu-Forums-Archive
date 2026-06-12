---
title: "Help with java.lang.UnsatisfiedLinkError"
date: 2008-03-26
forum: Desktop Environments
---

### Post by ubuntogenius on 2008-03-26
Greetings,
I am coding a Java program to read information from a PIC microcontroller using a Java app coded in Eclipse.  However, I am receiving the following error:

java.lang.UnsatisfiedLinkError: no rxtxSerial in java.library.path thrown while loading gnu.io.RXTXCommDriver
Exception in thread "main" java.lang.UnsatisfiedLinkError: no rxtxSerial in java.library.path

I managed to make this code work for Eclipse on windows by copying the rxtx.jar to the System.Windows32 file, but I am confused on where to put it on a Ubuntu 7.10 build to mitigate this error.  Any support is appreciated.

Sincerely,

---

### Post by spupy on 2008-03-26
If you put the jar in the same dir with your program, and additionally add "." the the CLASSPATH, i think it would work. Actually, it should work in any dir you have it in your classpath:
```
export CLASSPATH=.:otherdirshere"
```
TO check what you have in your classpath now:
```
env | grep -i classpath
```


[http://linuxlab.dk/tipsntricks/classpath](http://linuxlab.dk/tipsntricks/classpath)

---

