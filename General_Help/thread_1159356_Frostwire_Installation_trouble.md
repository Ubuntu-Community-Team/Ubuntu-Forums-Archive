---
title: "Frostwire Installation trouble"
date: 2009-05-14
forum: General Help
---

### Post by derelict888 on 2009-05-14
After installing FrostWire 4.18.0.deb file for ubuntu and installing it, I received the following error when trying to run it;
```
One or more necessary files appears to be invalid...
```
I've looked around the net a bit and found that usually its a java issue, however I seem to be using a supported version. Here is what sudo update-alternatives --config java returns;

```
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
 +        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java


```


Here is the error from frostwire;
```
FrostWire version 4.17
Java version 1.6.0_07 from Sun Microsystems Inc.
Linux v. 2.6.24-23-generic on amd64
Free/total memory: 61275512/62259200

java.lang.NoClassDefFoundError: org/limewire/util/VersionUtils
	at com.limegroup.gnutella.gui.GUILoader.load(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.limegroup.gnutella.gui.Main.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.limewire.util.VersionUtils
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	... 6 more

STARTUP ERROR!


```

Any ideas?

---

### Post by fooman on 2009-05-14
try opening synaptic (system > administration > synaptic package manager)....search for "openjdk" and uninstall any openjdk packages that are installed.

next search for "sun" and install the following if they are not installed already:

sun-java6-bin
sun-java6-fonts
sun-java6-jre

see if that helps.

---

### Post by derelict888 on 2009-05-14
Just realised I have both JRE and JDK installed, but I need at JDK for some java apps I run. Guess I'm crap out of luck, ty.

---

### Post by Nerv68 on 2009-05-16
I was having pretty much the same error. I got it to work though. Try going to synaptic package manager, install sun java, then uninstall frostwire. (sudo apt-get remove frostwire) then go to the website and re-installed it. Thats what I did and it works fine now.

---

### Post by FIONEX on 2009-05-16
Just so you know, you can have OpenJDK-jre installed at the same time as Sun-Java-Jre.  They are both JRE's but different implementations.  Java is more stable/supported.  When you do:

sudo update-alternatives --config java

It gives you the path to each JRE.  So if you press "2" and then hit enter, your java programs start running with sun-java-jre.  if you press "1" and hit enter, then they'll run using OpenJDK.  The program "java" is just a link to either Sun's or OpenJDK's Java Runtime Environment.



LOOOOOOOOOOL.  I just installed the new 4.18 Frostwire and I ran into your problem.  The developpers forgot to include a class in the package!  try installing 4.17 if u can find it!

---

### Post by cybrsaylr on 2009-05-16
How does Frostwire work?
Do you get any bogus files?

I've been having great results with Nicotine-Plus. 
It's in the repos.

---

### Post by quill3033 on 2009-05-18
> **cybrsaylr said:**
> How does Frostwire work?
Do you get any bogus files?

I've been having great results with Nicotine-Plus. 
It's in the repos.



Yes there are some bogus files and you have to be careful when you play files in windows machine as some have viruses. I usually 'preview' before I finish downloading to make sure it's a fair dinkum file. 

I seem to get a lot less 'junk' results than with limewire - it seems to be better at weeding them out.

---

### Post by themusicwave on 2009-06-02
Here is a link to the i586 version 4.17.  Just change the link as needed for different versions:

[http://main2.frostwire.com/frostwire/4.17.0/frostwire-4.17.0.i586.deb](http://main2.frostwire.com/frostwire/4.17.0/frostwire-4.17.0.i586.deb)

---

### Post by jezza1972 on 2009-06-02
I had this problem. I went back to an earlier version of frostwire and al was well again.

---

### Post by uptheirons1 on 2009-07-26
I think there is something wrong with the newest frostwire debian package. So I went to [www.frostwire.com]("http://www.frostwire.com/download/?os=redhat&") and downloaded the [fedora rpm]("http://www.frostwire.com/download/?os=redhat&") version instead and saved it to my home directory. Then I opened a terminal and installed alien to convert the rpm to a deb. 

Here is what I did in the terminal:```

sudo apt-get install alien
sudo alien -i frostwire-4.18.0.noarch.rpm
```
Now I have the newest version of frostwire working on ubuntu.
You can do that in the terminal or you can just download my converted deb file here: 
[http://www.mediafire.com/?zenzgvyl4wa](http://www.mediafire.com/?zenzgvyl4wa)

---

### Post by hibliss on 2009-07-26
Why not try a non Java native Linux Gnutella client that connects to the same network (Gnutella) and gets the same files?

GTK-Gnutella works nicely -- [http://gtk-gnutella.sourceforge.net/en/?page=news]("http://gtk-gnutella.sourceforge.net/en/?page=news")

---

### Post by kimw08 on 2009-07-31
> **uptheirons1 said:**
> I think there is something wrong with the newest frostwire debian package. So I went to [www.frostwire.com]("http://www.frostwire.com/download/?os=redhat&") and downloaded the [fedora rpm]("http://www.frostwire.com/download/?os=redhat&") version instead and saved it to my home directory. Then I opened a terminal and installed alien to convert the rpm to a deb. 

Here is what I did in the terminal:```

sudo apt-get install alien
sudo alien -i frostwire-4.18.0.noarch.rpm
```Now I have the newest version of frostwire working on ubuntu.
You can do that in the terminal or you can just download my converted deb file here: 
[http://www.mediafire.com/?zenzgvyl4wa](http://www.mediafire.com/?zenzgvyl4wa)

This is great thanks - I used your deb file and now frostwire working perfectly!:P

---

### Post by uptheirons1 on 2009-08-08
That's great. I am glad that it worked for you. :D
I also found out that getdeb has a working version of Frostwire too:
[http://www.getdeb.net/app/Frostwire](http://www.getdeb.net/app/Frostwire)

---

