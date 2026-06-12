---
title: "java.lang.UnsatisfiedLinkError"
date: 2009-03-18
forum: Desktop Environments
---

### Post by JordBrow on 2009-03-18
Hi,

I'm trying to run a simple java program I compiled for class.  This is the first time i've run a program that imports the javax.swing.JOptionPane since I installed Ubuntu 8.10 and java.

I get this error when I try to run the program as:  java TestGCalc

```
$ java TestGCalc
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1666)
	at java.lang.Runtime.load0(Runtime.java:787)
	at java.lang.System.load(System.java:1022)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1684)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.loadLibraries(Toolkit.java:1610)
	at java.awt.Toolkit.<clinit>(Toolkit.java:1632)
	at java.awt.Component.<clinit>(Component.java:568)
	at TestGCalc.printMenu(TestGCalc.java:34)
	at TestGCalc.main(TestGCalc.java:13)

```

From what I've seen through other posts is that java isn't able to find

/usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so

when I went to check, obviously it wasn't there. Am I missing libraries that need to be installed? if so what packages are they in? 

Thanks for your help

---

### Post by snova on 2009-03-18
Handy little program:

```

$ apt-file search /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
openjdk-6-dbg: /usr/lib/debug/usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
**openjdk-6-jre**: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so

```

Try installing that.

---

### Post by JordBrow on 2009-03-18
I'm sorry, do you think you could give me a short explanation, I'm not sure what this is supposed to do.

Thanks

---

### Post by snova on 2009-03-18
> **JordBrow said:**
> I'm sorry, do you think you could give me a short explanation, I'm not sure what this is supposed to do.

Sorry, I was trying to demonstrate how I found the correct package.

First, the exception. It tells us you're missing a library, so we have to find out what package it's in. There is a handy little program called **apt-file** (I don't know of a GUI equivalent, there might be one) that can search for files even in packages you don't have installed. So I used it to search for that file:

```

$ apt-file search /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so

```

And it generated this output:

```

openjdk-6-dbg: /usr/lib/debug/usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
openjdk-6-jre: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so

```

Which simply means the file we need is in the second package, **openjdk-6-jre**.

Open System -> Administration -> Synaptic, and install this package.

Then try running your program again, it should work.

---

### Post by JordBrow on 2009-03-19
Thank you so much!  worked like a charm!

---

### Post by Orbitize on 2010-02-19
Thanks, this is just what I needed :)

I had previously installed the openjdk-6-jre-headless package, but had missed the standard jre, obviously!

---

### Post by vinan on 2010-06-13
> **snova said:**
> Handy little program:

```

$ apt-file search /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
openjdk-6-dbg: /usr/lib/debug/usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
**openjdk-6-jre**: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so

```Try installing that.



Thanks m8
solved my head bump              you   :guitar:s

---

### Post by drpjkurian on 2010-08-13
Thanks Snova

---

### Post by Azhag on 2010-08-17
Thanks a lot, Snova!

---

### Post by ledbetter on 2010-10-14
> **snova said:**
>  
  
Then try running your program again, it should work.

Thank you so so so **so** much, snova! I have been chipping away at Eclipse and Tomcat issues on 10.10 for a day (ok, only a few hours over a couple of days but still). Thank you for helping me get back to what I wanted to do -- stop messing with server foo and get back to coding foo!

=D>

---

### Post by ankit.pandey3 on 2011-05-22
> **snova said:**
> Sorry, I was trying to demonstrate how I found the correct package.

First, the exception. It tells us you're missing a library, so we have to find out what package it's in. There is a handy little program called **apt-file** (I don't know of a GUI equivalent, there might be one) that can search for files even in packages you don't have installed. So I used it to search for that file:

```

$ apt-file search /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so

```And it generated this output:

```

openjdk-6-dbg: /usr/lib/debug/usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
openjdk-6-jre: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so

```Which simply means the file we need is in the second package, **openjdk-6-jre**.

Open System -> Administration -> Synaptic, and install this package.

Then try running your program again, it should work.


Hi friend the following error 

"apt-file: command not found"

Where is problem I don't know???
Help me please..........

---

### Post by ankit.pandey3 on 2011-05-23
Yes...It works...
I just set the classpath and run XManager(passive).....and jar file executes..

---

