---
title: "Help running Netlogo"
date: 2010-03-20
forum: Education &amp; Science
---

### Post by Juhla Mokka on 2010-03-20
Hello, I am trying to run/install Netlogo simulation tool that I have to use on my Open University course.

I have downloaded & untarred the program in my home directory.** What do I do next?**

I tried this: [http://ubuntuforums.org/showthread.php?t=573176](http://ubuntuforums.org/showthread.php?t=573176)
which tells to run the NetLogo.jar file using Sun Java 6 Runtime (I went to right-click - run). [B]Nothing happened.
[/B]

I also saw this: [http://ubuntuforums.org/showthread.php?t=116441](http://ubuntuforums.org/showthread.php?t=116441)
which says that even I have Sun Java 6, Netlogo tries to use gcj java. I tried the same command on the terminal:
```
tuisku@Frog:~$ sudo update-java-alternatives -l
java-6-sun 63 /usr/lib/jvm/java-6-sun
tuisku@Frog:~$ cd /home/tuisku/Applications/Netlogo
tuisku@Frog:~/Applications/Netlogo$ java -jar NetLogo.jar
Exception in thread "main" java.lang.NoClassDefFoundError: org.nlogo.app.App
   at java.lang.Class.initializeClass(libgcj.so.10)
Caused by: java.lang.ClassNotFoundException: org.picocontainer.Parameter not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:NetLogo.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.10)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.10)
   at java.lang.ClassLoader.loadClass(libgcj.so.10)
   at java.lang.ClassLoader.loadClass(libgcj.so.10)
   at java.lang.Class.initializeClass(libgcj.so.10)
tuisku@Frog:~/Applications/Netlogo$
```

Any ideas? You may need to spell them out as I am not that experienced on Linux. Thanks :)

---

### Post by anagor on 2010-03-20
I've just downloaded the netlogo from their site. I've downloaded the Linux version 4.1, after extracting it, I've seen that there is a netlogo.sh file, which I ran from terminal like this:

mark@mark-desktop:~/Downloads/temp/netlogo-4.1$ ./netlogo.sh 

And it worked just fine. You don't need to run the jar file. this sh script sets all the needed parameters for netlogo to run.

The java alternatives on my system is exactly as yours, so you should run it with no problems either.

Hope this helps.

Cheers;

---

### Post by Juhla Mokka on 2010-03-20
Thanks anagor! Something must have gone wrong with the download - there was no .sh file. I downloaded it again and when extracted, ticked 'recreate folders'. Don't know if that had any significance but the .sh file is there and the folder looks better.

However, something is still not right, but not sure what:

tuisku@Frog:~/Applications/netlogo-4.1$ ./netlogo.sh
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.10)
   at java.awt.Window.<init>(libgcj.so.10)
   at java.awt.Frame.<init>(libgcj.so.10)
   at java.awt.Frame.<init>(libgcj.so.10)
   at org.nlogo.window.VMCheck.warn(VMCheck.java:40)
   at org.nlogo.window.VMCheck.detectBadJVMs(VMCheck.java:31)
   at org.nlogo.app.App.main(App.java:116)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.10)
   at java.lang.Runtime.loadLibrary(libgcj.so.10)
   at java.lang.System.loadLibrary(libgcj.so.10)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.10)
   at java.lang.Class.initializeClass(libgcj.so.10)
   at java.lang.Class.forName(libgcj.so.10)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   ...7 more
tuisku@Frog:~/Applications/netlogo-4.1$ ^C

---

### Post by Juhla Mokka on 2010-03-20
Alright... I am closer to the solution I hope. After the error messages above, I went to Synaptic and installed the missing libgcj10-awt. Then I ran netlogo.sh file. Netlogo started with** a warning box ** (attached) saying that I'm not using Sun Java, I'm using gcj Java. I aborted Netlogo.

**How to get Netlogo to use Sun Java?** :o

---

### Post by Juhla Mokka on 2010-03-20
Yes! I answered my own question! I run a command **sudo update-alternatives --config java**
 to change the default java to Sun Java and then ran the **netlogo.sh** file, that worked beautifully! :KS

Code that I used: (you can see that I chose option 3  - it was 0 before, as marked with the *)
```
tuisku@Frog:~/Applications/netlogo-4.1$ sudo update-alternatives --config java
[sudo] password for tuisku: 
There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                  Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gij-4.4                       1044      auto mode
  1            /usr/bin/gij-4.3                       43        manual mode
  2            /usr/bin/gij-4.4                       1044      manual mode
  3            /usr/lib/jvm/java-6-sun/jre/bin/java   63        manual mode

Press enter to keep the current choice[*], or type selection number: 3
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/java to provide /usr/bin/java (java) in manual mode.

```

---

### Post by Stafke on 2010-10-27
edit: message got obsolete

---

### Post by alexbr77 on 2013-02-24
Hello!!! I am a new Ubuntu user and I'm trying to have an icon to access Netlogo from the desktop.

Somebody knows how to do that?

---

