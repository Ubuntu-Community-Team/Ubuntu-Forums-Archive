---
title: "Broken Java applications"
date: 2008-12-11
forum: General Help
---

### Post by Hyperion_1984 on 2008-12-11
Strangely, my java applications can't start anymore. I have the same problem whether I use OpenJDK 6, Sun-Java-6 or Sun-Java-1.5.

For example, if I try to run freemind, I get (with OpenJDK)

```
$ freemind
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/motif21/libmawt.so
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
Could not find the main class: freemind.main.FreeMind. Program will exit.

```

I get similar feedback with other JAVA version. 
I tried uninstalling and reinstalling the different JAVA package without success.

I've search for "/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/motif21/libmawt.so" but the motif21 folder doesn't exist. A libmawt.so file is located in "/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt" but I'm not sure it's the good one.

Does anyone know what could have happen?
Is there a solution?

---

### Post by pt.linux on 2008-12-11
try sudo rm -rf java-jre6 / 
and the reinstall
I had the same problem and with me it worked

---

### Post by pt.linux on 2008-12-11
and then*

---

### Post by Hyperion_1984 on 2008-12-11
> **pt.linux said:**
> try sudo rm -rf java-jre6 / 
and the reinstall
I had the same problem and with me it worked

From where do you enter this command? From the "/usr/lib/jvm" folder?

---

### Post by Thura on 2008-12-11
Can you run other programs without errors ?
If yes, post other errors too ...
Why not make a folder /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/motif21/
and put the libawt.so from /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt to test ?

---

### Post by nzadLithium on 2008-12-11
try sudo apt-get purge (java package name)

then sudo apt-get install (java package name)

That should clear all java configuration changes, which will hopefully make it work again :D

---

### Post by Hyperion_1984 on 2008-12-12
> **nzadLithium said:**
> try sudo apt-get purge (java package name)

then sudo apt-get install (java package name)

That should clear all java configuration changes, which will hopefully make it work again :D

Hmmm... It didn't work. I still have the same problem...

Was there an update recently?

---

### Post by Hyperion_1984 on 2008-12-12
> **Thura said:**
> Can you run other programs without errors ?
If yes, post other errors too ...
Why not make a folder /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/motif21/
and put the libawt.so from /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt to test ?

I tried it. However, I get the same type of error without the "Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/motif21/libmawt.so"

```
$ freemind
Exception in thread "main" java.lang.UnsatisfiedLinkError: sun.awt.motif.MToolkit.init(Ljava/lang/String;)V
	at sun.awt.motif.MToolkit.init(Native Method)
	at sun.awt.motif.MToolkit.<init>(MToolkit.java:152)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at java.lang.Class.newInstance0(Class.java:372)
	at java.lang.Class.newInstance(Class.java:325)
	at java.awt.Toolkit$2.run(Toolkit.java:861)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:841)
	at java.awt.Window.getToolkit(Window.java:1170)
	at java.awt.Window.init(Window.java:400)
	at java.awt.Window.<init>(Window.java:438)
	at java.awt.Frame.<init>(Frame.java:419)
	at javax.swing.JFrame.<init>(JFrame.java:224)
	at freemind.main.FreeMind.<init>(FreeMind.java:107)
	at freemind.main.FreeMind.main(FreeMind.java:647)
```

I get the same type of error for all java application

---

### Post by nzadLithium on 2008-12-12
Try installing sun-java6-jdk if that doesnt work, uninstall all of the sun java stuff u have and try installing 'icedtea', if they're internet based, then icedtea will be able to load them. If they're run from your pc, then openjdk (which is installed by icedtea) should be able to open them (one would hope anyways XD).

---

