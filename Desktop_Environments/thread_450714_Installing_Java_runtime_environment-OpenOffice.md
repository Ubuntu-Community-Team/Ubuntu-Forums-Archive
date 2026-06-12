---
title: "Installing Java runtime environment-OpenOffice"
date: 2007-05-21
forum: Desktop Environments
---

### Post by JoeS on 2007-05-21
Using Ubuntu 6.10

I accessed the following:
```
File > Wizards > Letter
```
and got this message:
> Openoffice requires a Java runtime environment(JRE) to perform this task.
The selected JRE is defective.  Please select another version or install a
new JRE and install it under Tools - Options - OpenOffice.org - Java.

I downloaded jre-6u1-linux-i586.bin and installed it in /usr/lib/jvm.  I also enabled it.
I'm not sure if I did this right.  I would appreciate help with this.  Also how to get it working in OpenOffice.

---

### Post by taurus on 2007-05-21
Let's see if you have configured it.  What's the output of this command from a terminal?

```
java -version
```

---

### Post by JoeS on 2007-05-21
> **taurus said:**
> Let's see if you have configured it.  What's the output of this command from a terminal?

```
java -version
```

joe@ubuntu:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

I don't know if I installed it right.  Under > /usr/lib/jvm/jre1.6.0_01/  I don't see a jre subdirectory like the other versions.

---

### Post by taurus on 2007-05-21
It means you need to configure it.

```
sudo update-alternatives --config java
```
And pick the latest version from the list.  Then, see if it is the right version again.

```
java -version
```

---

### Post by JoeS on 2007-05-21
I ran the following command:
```
sudo update-alternatives --config java
``` with the following result:
> There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-gcj/jre/bin/java
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
I chose #3 and confirmed it, but still get the error message with OpenOffice.  I didn't see jre1.6.0_01 in the list.

---

### Post by taurus on 2007-05-21
Does it say version 1.6 when you run this command?

```
java -version
```
Perhaps you need to reboot.

---

### Post by JoeS on 2007-05-21
joe@ubuntu:~$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

---

### Post by JoeS on 2007-05-21
Thanks for your help.  I got JRE working in OpenOffice writer.  Accessed: Tools > Options > OpenOffice.org (Java) > then picked JRE 1.5.0_08 from the list.

Is there a newer version of JRE available? I installed  jre1.6.0_01, but couldn't find a JRE directory.

---

### Post by taurus on 2007-05-22
The latest one is 1.6 and it is in the repos.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

