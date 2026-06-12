---
title: "FrostWire - Help!"
date: 2009-05-17
forum: General Help
---

### Post by ConnorIRL on 2009-05-17
I just installed Java 6, and then installed FrostWire, and it gave me this message.

> FrostWire version 4.18.0
Java version 1.6.0_13 from Sun Microsystems Inc.
Linux v. 2.6.28-11-generic on i386
Free/total memory: 4503200/5177344

FATAL ERROR!

java.lang.NoClassDefFoundError: org/apache/http/params/HttpParams
    at org.limewire.http.LimeWireHttpModule.configure(Unknown Source)
    at com.google.inject.AbstractModule.configure(Unknown Source)
    at com.google.inject.BinderImpl.install(Unknown Source)
    at com.limegroup.gnutella.LimeWireCoreModule.configure(Unknown Source)
    at com.google.inject.AbstractModule.configure(Unknown Source)
    at com.google.inject.BinderImpl.install(Unknown Source)
    at com.limegroup.gnutella.gui.LimeWireModule.configure(Unknown Source)
    at com.google.inject.BinderImpl.install(Unknown Source)
    at com.google.inject.Guice.createInjector(Unknown Source)
    at com.google.inject.Guice.createInjector(Unknown Source)
    at com.google.inject.Guice.createInjector(Unknown Source)
    at com.limegroup.gnutella.gui.Initializer.createLimeWire(Unknown Source)
    at com.limegroup.gnutella.gui.Initializer.initialize(Unknown Source)
    at com.limegroup.gnutella.gui.GUILoader.load(Unknown Source)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at com.limegroup.gnutella.gui.Main.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.apache.http.params.HttpParams
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
    ... 19 more


-- listing session information --
Current thread: main
Active Threads: 3
Peak Number of Thread: 4
System Load Avg: 0.91
Objects Pending GC: 0
Free Space In Settings: 69623959552
Free Space In Incomplete: 69623959552
Free Space In Downloads: 0
Heap Memory Usage: init = 0(0K) used = 689736(673K) committed = 5177344(5056K) max = 66650112(65088K)
Non-Heap Memory Usage: init = 33718272(32928K) used = 15872208(15500K) committed = 34242560(33440K) max = 121634816(118784K)

-- listing threads --
AWT-XAWT: 1
Image Fetcher 3: 1
main: 1


-- listing properties --
LAST_EXPIRE_TIME=1242567022265


**************** Comments from the user ****************
null

What did I do wrong? :P

---

### Post by Legace on 2009-05-17
Make sure Java is properly installed: [http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html)

---

### Post by ConnorIRL on 2009-05-17
Started doing the first step, and got this:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-jre-sun-java6-plugin


---

### Post by Legace on 2009-05-17
Applications -> Add/Remove Programs -> search for "Java" and check the "Sun Java 6 Runtime" then press Apply Changes.

---

### Post by ConnorIRL on 2009-05-17
I did a few tests to see what version I'm running, and if it's installed correctly, and it says I have Java 6 Update 13.  When I install FrostWire now and try to open it, it just doesn't open at all.

---

### Post by BslBryan on 2009-05-17
Hello, ConnorIRL. :-)

What "tests" did you do?

Your first post indicates that: 
```
FrostWire version 4.18.0
**Java version 1.6.0_13 from Sun Microsystems Inc.**
Linux v. 2.6.28-11-generic on i386
Free/total memory: 4503200/5177344
```
is what is installed.

Remove Frostwire, and Java, and let's start this over again. :-)  Follow the tutorial Legace's pointed you to, except use Synaptic Package Manager (or Add/Remove) to do a search for "Java" and install it there.

Also, Frostwire's in the repositories as well, so with a ```
sudo apt-get install frostwire
``` you should be as good as new. :-)

Post here and keep us updated.  Best to you, and good luck.

---

### Post by ConnorIRL on 2009-05-17
More trouble, :P

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package frostwire is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package frostwire has no installation candidate


---

### Post by CoreyB. on 2009-05-17
> **BslBryan said:**
> Hello, ConnorIRL. :-)

What "tests" did you do?

Your first post indicates that: 
```
FrostWire version 4.18.0
**Java version 1.6.0_13 from Sun Microsystems Inc.**
Linux v. 2.6.28-11-generic on i386
Free/total memory: 4503200/5177344
```
is what is installed.

Remove Frostwire, and Java, and let's start this over again. :-)  Follow the tutorial Legace's pointed you to, except use Synaptic Package Manager (or Add/Remove) to do a search for "Java" and install it there.

Also, Frostwire's in the repositories as well, so with a ```
sudo apt-get install frostwire
``` you should be as good as new. :-)

Post here and keep us updated.  Best to you, and good luck.

Frostwire is NOT in the repos.  Do other application that require Java work fine?

---

### Post by ConnorIRL on 2009-05-17
Yeah.  FrostWire is the only one so far that has been giving me trouble.

---

### Post by quill3033 on 2009-05-18
I don't know about Jaunty but I have had no luck with Frostwire 4.18 either in Gutsy or in Hardy. I"ve gone back to 4.17 - happy to email to you - it is only 13MB. I kept it just in case 4.18 didn't work, which it didn't and i didn't feel like mucking around with Java when 4.17 works great.

---

### Post by CoreyB. on 2009-05-19
Maybe you could try Frostwire from GetDeb?

---

### Post by Soul-Sing on 2009-05-19
```
sudo update-alternatives --config java
```
select sun java
probl openjdk is also installed.

---

### Post by kostkon on 2009-05-19
> **leoquant said:**
> ```
sudo update-alternatives --config java
```
select sun java
probl openjdk is also installed.
+1

You need to set the Sun Java as the default.

---

### Post by PureLoneWolf on 2009-06-13
That didn't work for me.  Apparently there is an issue with installing from the Gdebi installer.

Run sudo dpkg -i frostwire-4.18.0.i586.deb from a terminal and it should install just fine.

When it launches though, it will be as root.  So close the application, and launh it from the Gnome Menu.

Should be fine at this point.

---

### Post by bigred562 on 2009-06-16
PureLoneWolf has it right. If you check frostwire's forums they are complaining about the same problem. The problem seems to be with Gdebi. It doesn't install frostwire correctly with the correct permissions. You can either log in as root, if you already set up and allowed your root account, and install frostwire with GDebi. Or most likely easier, just use a terminal and type "sudo dpkg -i frostwire-4.18.0.i586.deb" as PureLoneWolf said above. As a side note, I don't advised staying logged in as root.

---

