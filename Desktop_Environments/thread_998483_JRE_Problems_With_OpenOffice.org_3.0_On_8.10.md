---
title: "JRE Problems With OpenOffice.org 3.0 On 8.10"
date: 2008-11-30
forum: Desktop Environments
---

### Post by crashsystems on 2008-11-30
About a month ago I added [this repository]("http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/") to my list, and installed OpenOffice.org version 3 on my 8.10 install (64bit). It has been running fine mostly, except today when I tried to use Base. After creating the database file, when I click on the "Tables" button to the left, I get the following error messages:

> OpenOffice.org requires a Java runtime environment (JRE) to preform this task. The selected JRE is defective. Please select another version or install a new JRE and select it under Tools - Options - OpenOffice.org - Java.
Please install the openoffice.org-java-common package for this functionality.

> The connection to the data source "testing" could not be established.
No Java installation could be found. Please check your installation!

Initially the version of Java in use was OpenJDK-JRE, which is installed by default in Ubuntu. Thinking that this might be a problem with OpenJDK, I installed Sun Java 6 JRE and selected that in the list, but still received the same error messages. I of course checked to make sure openoffice.org-java-common is installed.

I thought that running a Google search on a part of the errors I received would give me some results. However, I can find nothing on the Internets or The Google to help me with this problem. If you can have any good advice, I'd appreciate hearing it.

---

### Post by taurus on 2008-11-30
What's the output of this command from a terminal?

```
java -version
```

---

### Post by crashsystems on 2008-11-30
java -version
> java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)

---

### Post by taurus on 2008-11-30
Looks like you are still using the OpenJDK version.  Perhaps you need to configure java again.

```
sudo update-alternative --config java
```
Make sure you get the right version as your default.  Then, see what happens to this command again.

```
java -version
```

---

### Post by crashsystems on 2008-11-30
I just ran update-alternatives and selected java-6-sun, but I'm still getting the same result. I ran java -version, and got:

> java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-Bit Server VM (build 11.0-b15, mixed mode)


---

### Post by taurus on 2008-11-30
Isn't that the version that you installed and want to use as a default?

---

### Post by crashsystems on 2008-11-30
Well if I can get it to work with OpenJDK-JRE I would prefer that over the closed version, but the most important thing is that I get OpenOffice Base working, regardless of which runtime environment I have installed. I installed java-6-sun to see if it might simply be a probjem with OpenJDK.

---

### Post by jamesstansell on 2008-12-01
The OO.o preferences has a section for java where it lets you tell it which JRE to use.  Please make sure that is set.

---

### Post by crashsystems on 2008-12-01
I've been into the Java settings a number of times now. Currently it is set to use java-6-sun.:confused:

---

### Post by t35t0r on 2008-12-01
Download a 32 bit jdk/jre and point openoffice to that installation. I
don't know if 64bit ubuntu ships with a 32bit compiled version of
openoffice.

---

### Post by NoBugs! on 2009-01-02
Does uninstalling those openoffice packages and installing packages directly from OpenOffice.org make it work? If so, it's not the jre.

---

### Post by paulchinnz on 2009-04-26
I've actually just got the same problem on 9.04 after no problems with 3.0.1 on 8.10, so slightly off topic, but did the OP solve this and how?

---

### Post by richardh9936 on 2009-05-25
I have this issue, too.  I've tried re-installing OOo, but that didn't fix it.  Now I've discovered I had IcedTea, so I've removed the OpenJDK, and will try to get just the Sun version.....[time passes].....

Removing IcedTea also removes the Ubuntu OpenOffice.org (meta) package.... and Synaptic shows all the OOo components uninstalled.  I've installed Sun's Java, and verified it with "java -version".  However, I can't run OOo-base to see if it's still faulty, because it's no longer available.......[time passes].....

---

