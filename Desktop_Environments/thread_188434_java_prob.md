---
title: "java prob"
date: 2006-06-04
forum: Desktop Environments
---

### Post by Daandaan on 2006-06-04
When i try to run Warsow, i get the following error:

 java -jar /home/warsow/browser/wswBrowser.jar
Exception in thread "main" java.lang.UnsupportedClassVersionError: alx/wswbrowser/Main (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)

I thought my version was not up to date so I did an sudo apt-get install sun-java5-jre but nothing changed. What should I do?](*,)

---

### Post by ebash on 2006-06-04
The 'unsipported major.minor version 49.0' error you got seems to indicate that the version of java that you are running is less than 1.5 or 5.0.

To see what version you are running do:
```
java -version
```

You will need to change the default version of java:
```
sudo update-alternatives --config java
```

For more information take a look at this thread:
[http://www.ubuntuforums.org/showthread.php?p=1086429]("http://www.ubuntuforums.org/showthread.php?p=1086429")

---

### Post by donpaco on 2006-06-04
if ou are in ubuntu 6.06 32bits edition (x86)  then add some sources in your /etc/apt/sources.list file (in sudo mode) like this in a terminal: 

sudo gedit /etc/apt/sources.list

and add those lines



# Seveas' packages (packages, GPG key: 1135D466)
deb [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) dapper-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main

# kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

# Bleeding edge wine packages (packages)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# Bleeding edge wine packages (sources)
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# The Opera browser (packages)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

# Bazaar-NG development (packages, GPG key: 1F44842D)
deb [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./

# Bazaar-NG development (sources, GPG key: 1F44842D)
deb-src [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./

---------------> now you can choose in synaptic (after updating the list!) the sun-j2re1.5 package :D

---

### Post by Daandaan on 2006-06-04
sudo update-alternatives --config java   => That did the trick! Thank u guys. :rolleyes:

---

