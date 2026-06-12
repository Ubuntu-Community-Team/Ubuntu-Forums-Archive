---
title: "eclipse with sun java"
date: 2006-09-14
forum: Desktop Environments
---

### Post by spur on 2006-09-14
I have used downloaded 3.2 eclipse with sun java downloaded frin sun.
I have used the -vm option as it did not appear to know where it was.
This is the error I am now getting in the terminal window.
----------
meliore@meliore-desktop:~/java/Eclipse/eclipse$ ./eclipse -vm /home/meliore/java/jre1.5.0_06/bin/java_vm
java_vm process: You need to set both JAVA_HOME and PLUGIN_HOME
----------
The Eclipse window says this.
------------
JVM terminated. Exit code=255
/home/meliore/java/jre1.5.0_06/bin/java_vm
-Xms40m
-Xmx256m
-jar /home/meliore/java/Eclipse/eclipse/./startup.jar
-os linux
-ws gtk
-arch x86
-launcher /home/meliore/java/Eclipse/eclipse/./eclipse
-name Eclipse
-showsplash 600
-exitdata 718003
-vm /home/meliore/java/jre1.5.0_06/bin/java_vm
-vmargs
-Xms40m
-Xmx256m
-jar /home/meliore/java/Eclipse/eclipse/./startup.jar 
------------
Any help to overcome this problem by setting the JAVA_HOME and PLUGIN_HOME would be apprecuiated. I can't even see where they are supposed to go.](*,)

---

### Post by spur on 2006-09-14
I hav eread the previous thread on eclipse and sun java but I did not use the one in the repository. If some on could give me the  code to enter the variables for Jsetting JAVA_HOME etc I could finish the install.:-?

---

### Post by spur on 2006-09-16
Problem fixed.

---

### Post by RichardBronosky on 2007-03-19
> **spur said:**
> I hav eread the previous thread on eclipse and sun java but I did not use the one in the repository. If some on could give me the  code to enter the variables for Jsetting JAVA_HOME etc I could finish the install.:-?

Why not share the solution with the community?  I'm looking to setup my JAVA_HOME and PLUGIN_HOME too.  I could have been finished when I found this thread.  Now I have to keep Googling.

---

### Post by sirynx on 2007-03-21
I have a problem with my eclipse instalation. I'm going to start from the beginning. I installed Eclipse under kubuntu using the Sun's JDK version 5 from the Sun website and jre versión 1.4 (using the kubuntu's repositories). I had a problem because when I tried to execute my applications under Eclipse it worked well but when I tried to execute it under de jre (1.4) It doesn't work. Looking in Google I realized that Ubuntu had in their repositories the version 1.5 of the jre, and jdk, so I first installed sun-java5-jre, thinking that by doing that, version 1.4 will be automatically uninstalled, but I was wrong. Eclipse started to fail. At the end I solved this problem uninstalling all and installing the JDK by using the repositories and making eclipse to create a new workspace. My installation of eclipse is made by the repositories as well. I had my plug-ins installed by using the option in the help window. The problem is that I have installed WTP (1.5.3) and when I try to create a new J2EE project, Eclipse shows a message dialog that says JVM Terminated. Exit Code= 1 and then information about the Eclipse execution (JAVA_HOME, OS, some classes as well) I am very worried because I needed it to work. Is there any way to make WTP works with sun-java5-jdk? Thank you for all.

---

### Post by sirynx on 2007-03-21
I've started eclipse from the console and I have caused the error, the console shows that
```
using specified vm: /usr/lib/jvm/java-1.5.0-sun
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xa8b9942f, pid=6713, tid=3085207216
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libdocshell.so+0x42f]  _Z17AppendUTF8toUTF16RK19nsACString_internalR18nsAS                                                                                                   tring_internal+0x42f
#
# An error report file with more information is saved as hs_err_pid6713.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```
Can anyone help me,please? Thank you.

---

### Post by pstracha on 2008-01-03
For others who have similar problems, try calling the java binary not java_vm. It worked for me, the only difference is I'm using v1.6

```
/opt/eclipse/eclipse -vm /opt/jre1.6.0_03/bin/java
```

> **spur said:**
> 
meliore@meliore-desktop:~/java/Eclipse/eclipse$ ./eclipse -vm /home/meliore/java/jre1.5.0_06/bin/java_vm


---

