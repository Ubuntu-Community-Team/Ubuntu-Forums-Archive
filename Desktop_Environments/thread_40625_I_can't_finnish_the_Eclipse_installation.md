---
title: "I can't finnish the Eclipse installation"
date: 2005-06-09
forum: Desktop Environments
---

### Post by banyuken on 2005-06-09
I've already installed Java, jre1.5.0_02, and is working fine. I get the crash when I try to  execute Eclipse. And this is the exit:
[COLOR=Blue]
JVM terminated. Exit code=1
/usr/bin/java
-cp /home/jjmacias/software/eclipse/./startup.jar org.eclipse.core.launcher.Main
-os linux
-ws gtk
-arch x86
-showsplash /home/jjmacias/software/eclipse/./eclipse -showsplash 600
-exitdata /home/jjmacias/software/eclipse/./eclipse -exitdata 4b0018
-vm /usr/bin/java
-vmargs
-cp /home/jjmacias/software/eclipse/./startup.jar org.eclipse.core.launcher.Main [/COLOR]

Some idea? Thanks 4 all,
Banyu.

---

### Post by knorr.orange on 2005-06-09
Have you set your JAVA_HOME environment variable?

To check it, open a terminal and type:
```
echo $JAVA_HOME
```

Here's the output I get:
```
/usr/java/jre1.5.0_02/
```

It is possible that it cannot find your jre.

---

### Post by banyuken on 2005-06-10
Of course I did:

[COLOR=Blue]jjmacias@meteoro:~$ echo $JAVA_HOME
/usr/java/jre1.5.0_02[/COLOR]

Any more ideas?

Banyu.

---

### Post by banyuken on 2005-06-10
This is very strange. Now I do:
[COLOR=Blue]
jjmacias@meteoro:~$ java
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
jjmacias@meteoro:~$ java_vm
java_vm process: You need to set both JAVA_HOME and PLUGIN_HOME
jjmacias@meteoro:~$[/COLOR]

Why? I think this is the cause of not starting Eclipse. You could be ok, knorr.orange.

What can I do?

Banyu.

---

