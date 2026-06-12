---
title: "Problem starting Azureus (BT client)"
date: 2005-04-02
forum: Desktop Environments
---

### Post by hkl8324 on 2005-04-02
I downloaded and untar the package and cd to the unpack dir and run ./azureus

the programme says this:

Starting Azureus...
Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in  /home/hkl8324/Desktop/jre1.5.0_02/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://java.sun.com](http://java.sun.com)
hkl8324@ubuntu:~/Desktop/azureus$

then i edited the ./azureus with gedit azureus and changed this line from

JAVADIR=/usr/java/

to

JAVADIR=/home/hkl8324/Desktop/jre1.5.0_02 (where i installed my j2re files)

and later try to change it to

JAVADIR=/home/hkl8324/Desktop/jre1.5.0_02/bin

but the programme still shows that it cat find the java exec....

how can i find it?

thanks in advance

---

### Post by Strider on 2005-04-02
Check out this link on how to install Java system wide... would be better off anyway.

[http://ubuntuguide.org/temp/#jre](http://ubuntuguide.org/temp/#jre)

---

