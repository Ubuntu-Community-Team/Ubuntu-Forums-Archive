---
title: "installing GUI conky"
date: 2011-09-26
forum: Desktop Environments
---

### Post by murderd2death on 2011-09-26
i've been trying to get a GUI conky going and i've been following the instructions on [this website]("http://www.webupd8.org/2009/09/gui-for-configuring-conky.html"), but both the options for step four dont work for me at all, and when i put in the code ```
java -jar conkygui.jar
```

this is what i get
```
wintermute32@wintermute32-Lenovo-B570:~/Downloads/conkyguiv1.3.1$ java -jar conkygui.jar
Exception in thread "main" java.lang.NoClassDefFoundError: org/jdesktop/application/SingleFrameApplication
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
    at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Caused by: java.lang.ClassNotFoundException: org.jdesktop.application.SingleFrameApplication
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    ... 11 more
Could not find the main class: conkygui.GUIApp. Program will exit.

```

---

### Post by murderd2death on 2011-09-26
bump

---

### Post by stinkeye on 2011-09-26
I just installed this from a deb file on the conkygui web page.(It installed scala-library as a dependency)
Typed in conkygui in the dash, clicked on the icon and it started up.

The deb file: [**_[COLOR="DarkRed"]Conkygui[/COLOR]_**]("http://downloads.sourceforge.net/project/conkygui/ubuntu/conkyguiv_1.3.1-0ubuntu1_all.deb?r=http%3A%2F%2Fconkygui.sourceforge.net%2F&ts=1317078348&use_mirror=waix")


My java version
```
glen@Natty:~$ java -version
java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK Server VM (build 20.0-b11, mixed mode)
```

---

### Post by murderd2death on 2011-09-27
so i got conkygui installed and i edited the conkyrc file (at least the one conkygui gave me off hand) but it [has not changed]("http://i.imgur.com/Gyr82.png") my conky configuration after i saved it and restarted conky.

---

### Post by stinkeye on 2011-09-27
I don't use this program but try saving as **.conkyrc** in your home folder.
IF you already have a .conkyrc file you may want to backup this first as it will be overwritten.
The preceding dot makes the file hidden (ctrl+h to see hidden files).

When you run "conky" this is the config file it looks for.

In my opinion your better off going [**_[COLOR="DarkRed"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865") and copying someone's config you like and adapting it to your computer and needs.
Start with something simple.
It's not that hard to edit manually.

I have numerous configs in a folder named conky in my home directory.
You can name these configs anything you like.
eg I have a conky config which displays a surf report named "conkysurf".
To run conky with this config I use
```
conky -c /home/glen/conky/conkysurf
```


ie you can run any config using 
```
conky -c **/path/to/your/conkyconfig**
```

[**_[COLOR="darkred"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

