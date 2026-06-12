---
title: "Change PATH enivroment variable for java?"
date: 2009-03-10
forum: General Help
---

### Post by grivo242 on 2009-03-10
Hi all,
I'm having a problem with java.  I am new to linux, but this is by far my most successful attempt to install it.  Anyway, one thing I had awful problems with was installing Java (I wanted the Sun version, because its webstart creates a desktop icon.) It is finally installed now and works in Firefox and everything, however the "java" command in terminal seems to look for old OpenJDK files that were removed in my earlier attempts to get it working.  How do I change the path variables so that it looks in the right place?  I remember how to edit the paths in DOS, but I'm not sure where they are stored in linux.  

Here is the error that I get:

```
ben@BKthinkpad:~/programs/GoGrinder$ java -jar GoGrinder.jar
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
	at java.awt.Color.<clinit>(Color.java:279)
	at GoGrinder.Main.<clinit>(Main.java:50)
Could not find the main class: GoGrinder.Main. Program will exit.

```

P.S. This forum has been an immense help in getting me this far.  I look forward to giving back!

---

### Post by taurus on 2009-03-10
Where did you install the new version?  Assuming it is in /opt/jre-1.6.12/bin, you could edit ~/.bashrc and add these two lines to the end of it.

```
PATH=/opt/jre-1.6.12/bin:$PATH
export PATH
```
Save it.  Then run

```
source ~/.bashrc
which java
-or-
whereis java
```

---

### Post by grivo242 on 2009-03-10
Thanks, this looks like what I want.  But how do I edit bashrc?  I've made some attempts to use "vi" but I can't even move around the file.  Is there an easier way?

---

### Post by taurus on 2009-03-10
```
gedit ~/.bashrc
```
or
```
nano -Bw ~/.bashrc
```

---

### Post by grivo242 on 2009-03-10
I think I'm getting closer.

I've changed my bashrc so that the last lines are:

```
PATH=/usr/java/jre-1.6.12/bin:$PATH
export PATH
```

That's where my java is; I just used apt-get to install it and I guess that's where it put it.

I do the "source ~/.bashrc" and hit enter, but then when I type "which java" I get:

/usr/bin/java

...and there's no java in that directory.  

"whereis java" yields:

java: /usr/bin/java /etc/java /usr/share/java /usr/share/man/man1/java.1.gz

So it still doesn't appear to have the right path.  Am I missing something?

---

### Post by taurus on 2009-03-10
Which bashrc did you modify?  Can you post the outputs of these two commands from a terminal?

```
cat ~/.bashrc
ls -la /usr/java/jre-1.6.12/bin
```

p.s.  /usr/bin/java should be a file, not a directory.

```
ls -la /usr/bin/java
```

---

### Post by grivo242 on 2009-03-11
...that last ls command cleared it up, actually.  I had typed the java directory wrong.  Thanks so much!!

---

