---
title: "Eclipse/JRE 1.5 doesn't terminate on its own"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Coda on 2006-06-02
Hey all,

I'm running Dapper (AMD64), and when I configure Eclipse to run with Sun JRE 1.5 (or 1.6 Beta, for that matter), neither the java nor the eclipse process terminate when the application is exited. When I run Eclipse using Java-GCJ this doesn't happen, but it's also unusably slow, so that's out as a potential solution.

My ~/.eclipse/eclipserc:
```

JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun

```

This is what happens when I run Eclipse:
```

me@my-computer:~$ eclipse
using specified vm: /usr/lib/jvm/java-1.5.0-sun
GTK Accessibility Module initialized
Invalid Menu Extension (Path is invalid): org.rubypeople.rdt.debug.ui.actions.ModifyCatchpoint
GTK Accessibility Module initialized

```

Then Eclipse loads up, and it all works fine, until I exit, at which point the process doesn't terminate. From here I can kill it with ^C, which frees up the terminal, but doesn't actually terminate the java process:

```

me@my-computer:~$ ps aux | grep java
me     10664 21.3  7.1 1440528 110828 pts/2  Sl   10:15   0:18 /usr/lib/jvm/java-1.5.0-sun/bin/java -Djava.library.path=/usr/lib/jni -Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db -Dgnu.gcj.runtime.VMClassLoader.library_control=never -Dosgi.locking=none -jar /usr/share/eclipse/startup.jar -os linux -ws gtk -arch x86_64 -launcher /usr/lib/eclipse/eclipse -name Eclipse -showsplash 600 -exitdata cd0020 -install /usr/share/eclipse -vm /usr/lib/jvm/java-1.5.0-sun/bin/java -vmargs -Djava.library.path=/usr/lib/jni -Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db -Dgnu.gcj.runtime.VMClassLoader.library_control=never -Dosgi.locking=none -jar /usr/share/eclipse/startup.jar
me     10718  0.0  0.0   3940   912 pts/2    S+   10:17   0:00 grep java

```

At this point I can kill -9 the process, and it'll die with dignity.

Here's what I've tried that hasn't worked:
[list]
[*]Completely uninstalling Eclipse and reinstalling it.
[*]Completely uninstalling JRE 1.5 and reinstalling it.
[*]Disabling all my plugins.
[*]Running Eclipse as root.
[*]Nuking my workspace directory.
[*]Nuking my ~/.eclipse directory.
[*]Removing various parameters from the /usr/bin/eclipse script.
[/list]

FWIW, I've got Ruby Development Tools, RadRails, and Subclipse installed.

Any ideas? It didn't do this before a couple of weeks ago, but I have no idea what's changed, if anything.

---

### Post by jvictor on 2006-07-15
[http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)
This should help you

---

### Post by Coda on 2006-07-15
No, actually what worked was disabling GNOME's accessibility utilities. That allowed Eclipse to actually terminate.

---

### Post by jvictor on 2006-07-15
Interesting.. cant figure out whats the relation between these two !!

---

### Post by Moonbuzz on 2006-08-26
> **jvictor said:**
> Interesting.. cant figure out whats the relation between these two !!
Me neither, but it works, disabling the Accessibility does resolve the Eclipse termination problem
Another solution is to install Eclipse from Synaptic, but it's an older version and for some reason forces you to use GCJ and Mozilla. The 3.2 installation is much much better, now that the termination problem is a problem no more.

---

