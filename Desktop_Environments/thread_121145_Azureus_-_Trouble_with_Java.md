---
title: "Azureus - Trouble with Java"
date: 2006-01-24
forum: Desktop Environments
---

### Post by Harry_Sack on 2006-01-24
Hello.

Suddenly, when I try to start Azureus, I get this message:

Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/lib/libswt-pi-gtk-3138.so: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:75)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:58)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:108)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:123)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:142)

Does anyone know how to solve it?

I also tried these commands, which I found in another thread, but they dont work:

jon@DRY:~$ which java
/usr/bin/java
jon@DRY:~$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)
jon@DRY:~$ echo $JAVA_HOME

jon@DRY:~$ update-alternatives --display java
java - status is manual.
 link currently points to /usr/lib/j2re1.5-sun/bin/java
/usr/lib/j2sdk1.5-sun/bin/java - priority 315
 slave java.1.gz: /usr/lib/j2sdk1.5-sun/man/man1/java.1.gz
/usr/lib/jvm/java-gcj/bin/java - priority 1040
 slave java.1.gz: /usr/lib/jvm/java-gcj/man/man1/java.1.gz
/usr/lib/j2re1.5-sun/bin/java - priority 315
 slave java.1.gz: /usr/lib/j2re1.5-sun/man/man1/java.1.gz
/usr/bin/gij-wrapper-4.0 - priority 40
 slave java.1.gz: /usr/share/man/man1/gij-wrapper-4.0.1.gz
 slave rmiregistry: /usr/bin/grmiregistry-4.0
 slave rmiregistry.1.gz: /usr/share/man/man1/grmiregistry-4.0.1.gz
Current `best' version is /usr/lib/jvm/java-gcj/bin/java.


I don't know what to do with them.

Anyone who knows?   [-o< 

Cheers

---

### Post by gordon33 on 2006-01-24
I have a problem with not being able to down load games from Yahoo.  Yahoo sends me a message that my computer needs java.  So what is Java?  Are their diffrent versions of Java?  It their are how would you know whitch ones to down load?

Gordon From Mich.

---

### Post by MartinG on 2006-01-24
[QUOTE=gordon33]I have a problem with not being able to down load games from Yahoo.  Yahoo sends me a message that my computer needs java.  So what is Java?  Are their diffrent versions of Java?  It their are how would you know whitch ones to down load?

Gordon From Mich.[/QUOTE]Java is a programming language used for a lot of cross-OS stuff.  Ubuntu installs an open-source emulator, but an awful lot of stuff doesn't work with it.  You need "proper" Java, and the simplest way to get it is with Automatix:
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by awi on 2006-01-24
[QUOTE=Harry_Sack]Hello.

Suddenly, when I try to start Azureus, I get this message:

Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/lib/libswt-pi-gtk-3138.so: /usr/lib/libcairo.so.2: undefined symbol: 
[/QUOTE]
Dou you have installed libcairo2 package?
Try this:
```
$ ldd -r /usr/lib/libswt-pi-gtk-3138.so
```
You should not have any "not found" entry, if you do, then you need to get the necessary libraries to satisfy the dependencies.

[QUOTE=Harry_Sack]
I also tried these commands, which I found in another thread, but they dont work:

jon@DRY:~$ which java
/usr/bin/java
jon@DRY:~$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)
jon@DRY:~$ echo $JAVA_HOME
[/QUOTE]
This tells you that you already have the last version of java available from Sun, there is no need to install another, your problem now is not "java", azureus uses SWT library, a platform dependent library, that in Linux comes for GTK2 or motiff, that comes from IBM's Eclipse project. I think that your problem resides on that domain. :)

---

### Post by Harry_Sack on 2006-01-25
Hi awi.

Thanks for the reply.

I know for sure that I had libcairo2 installed, I went and found the files referred to in  /usr/lib/libswt-pi-gtk-3138.so and /usr/lib/libcairo.so.2.

Thing is, now I'm on Demudi  :p 
I've completely reinstalled everything, so I don't have this trouble anymore.
Things change fast in the linux-world, eh...
It's hard to choose, because I wanna do audio, but on the other hand, I've found nowhere with as good support as these forums provide. 
And I sure am a noob, so I go back and forth between these two distros.

The only thing I can think of to have caused it is messing around with some Dapper packages etc. Haven't had too good experience with that yet.

Anyway, thanks for the reply.  :D

---

### Post by awi on 2006-01-25
[QUOTE=Harry_Sack]Hi awi.

Thanks for the reply.

I know for sure that I had libcairo2 installed, I went and found the files referred to in  /usr/lib/libswt-pi-gtk-3138.so and /usr/lib/libcairo.so.2.

Thing is, now I'm on Demudi  :p 
I've completely reinstalled everything, so I don't have this trouble anymore.
Things change fast in the linux-world, eh...
It's hard to choose, because I wanna do audio, but on the other hand, I've found nowhere with as good support as these forums provide. 
And I sure am a noob, so I go back and forth between these two distros.

The only thing I can think of to have caused it is messing around with some Dapper packages etc. Haven't had too good experience with that yet.

Anyway, thanks for the reply.  :D[/QUOTE]

Try this:
[http://www.linuxquestions.org/questions/showthread.php?postid=1929909#post1929909](http://www.linuxquestions.org/questions/showthread.php?postid=1929909#post1929909)

---

