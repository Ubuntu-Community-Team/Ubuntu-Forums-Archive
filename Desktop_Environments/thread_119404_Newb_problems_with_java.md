---
title: "Newb problems with java"
date: 2006-01-19
forum: Desktop Environments
---

### Post by excelsior on 2006-01-19
I've no idea how to run a .jar file. Help!
 When I do this:

darren@DCO6019-A:~/Turnin$ gij -jar TurninClient.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.tk() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.getPeerFromToolkit(java.lang.String, java.util.Map) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.Font(java.lang.String, int, int) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.FontUIResource.FontUIResource(java.lang.String, int, int) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.metal.MetalLookAndFeel.MetalLookAndFeel() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.UIManager.<clinit>() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at TurninClient.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:TurninClient.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...13 more

What does it mean?

---

### Post by brk3 on 2006-01-19
It means I hate the opensource version of java! Try installing the proper java from [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)

---

### Post by jag164 on 2006-01-19
It pretty much says that the GNU clean room java version has numerous bugs, espicially in the windowing toolkit (AWT) and is (and probably never will be IMHO) not ready for prime time.  It could also mean a few other things, but I'd rule that possibility out right now. 

 Unless you have a dire need to use the GNU cleanroom java,  remove those packages from you system and install [Sun's]("java.sun.com")  or [IBM's Java Implementation]("http://www.ibm.com/developerworks/java/jdk/linux/download.html")

---

### Post by excelsior on 2006-01-19
OK guys thanks, I'll try that now.
Though it's a dark day when linux users admit that an open source version of something is inferior...

---

### Post by excelsior on 2006-01-19
I got sun java, and now i have this error:


darren@DCO6019-A:~/Turnin$ java -jar TurninClient.jar
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.

---

### Post by jag164 on 2006-01-19
respond with the output of these commands

```
which java
java -version
echo $JAVA_HOME
update-alternatives --display java
```

---

### Post by jag164 on 2006-01-19
in the mean time, give this a whirl

Make note where you installed Suns javaVM
(i.e. for me it un /usr/local/java)
Then run the command (changin /usr/local/java to you sun java install base )

```
sudo update-alternatives --install /usr/bin/java java /usr/local/java/bin/java 3
sudo update-alternatives --config java
```

And then select your Sun version from the list

---

### Post by brk3 on 2006-01-30
[QUOTE=excelsior]Though it's a dark day when linux users admit that an open source version of something is inferior...[/QUOTE]

Well you cant win everything, but in my opinion they shouldnt have bothered trying to program another java. If someone wanted to give it a go thats fair enough, but operating systems definatly shouldnt be including it in its current state.

---

### Post by ulgor on 2006-07-01
Hi there,
it looks like you know what to do to fix my problem, too. 

This is my output from the commands you mentioned:
```
ubuntu@ubuntu:~$ which java
/usr/bin/java

ubuntu@ubuntu:~$ java -version
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.

ubuntu@ubuntu:~$ echo $JAVA_HOME

ubuntu@ubuntu:~$ update-alternatives --display java
java - status is manual.
 link currently points to /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
/usr/bin/gij-wrapper-4.1 - priority 41
 slave java.1.gz: /usr/share/man/man1/gij-wrapper-4.1.1.gz
/usr/lib/jvm/java-gcj/jre/bin/java - priority 1041
 slave java.1.gz: /usr/lib/jvm/java-gcj/man/man1/java.1.gz
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java - priority 53
 slave java.1.gz: /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/man/man1/java.1.gz
Current `best' version is /usr/lib/jvm/java-gcj/jre/bin/java.

```

I installed Java trough Automatix, the packages also show in synaptics, but the libjava.so is causing problems? Any ideas?

---

### Post by nitromaster101 on 2006-08-22
I have a similar problem, concerning the gnu.java.awt.peer.gtk.GtkToolkit.

I made a driver to display a panel with this:

JFrame frame = new JFrame("Test");
...

it compiles fine, but when I run it, I get:

Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.7)
   at java.awt.Window.<init>(libgcj.so.7)
   at java.awt.Frame.<init>(libgcj.so.7)
   at javax.swing.JFrame.<init>(libgcj.so.7)
   at PixelDriver.main(PixelDriver.java:31)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...5 more


I installed the sdk from sun's website...so I don't know what could be causing this.  Thanks for any help.

---

