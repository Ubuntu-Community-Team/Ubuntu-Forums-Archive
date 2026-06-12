---
title: "Frostwire not starting up..."
date: 2006-09-06
forum: Desktop Environments
---

### Post by kerme8503 on 2006-09-06
i looked on other fourums and i counld find anything like my scenario so here it goes:  

i installed and reinstalled frostwire like 4 times and the last time i did it in the terminal.  i also installed java 5.  i go to apps, then internet, then frostwire.  i click and the drop down menu goes away, but nothing happens.  im at a loss here... please help

---

### Post by taurus on 2006-09-06
Run it from a terminal, Applications -> Accessories -> Terminal, and see what the error message is...

```
frostwire
```
But I bet you have not configured your java even though you have installed it!

```
java -version
```

---

### Post by kerme8503 on 2006-09-06
yeah, you called it heres waht it came up with:

OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)


ok so how do i configure this whole thing?

---

### Post by taurus on 2006-09-06
> **kerme8503 said:**
> yeah, you called it heres waht it came up with:

OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

ok so how do i configure this whole thing?
Didn't I just tell you that you didn't have your java configured!!!  What is the output of this command then?

```
java -version
```

---

### Post by kerme8503 on 2006-09-06
ha, sry.  

java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

there ya go.

---

### Post by taurus on 2006-09-06
That is the wrong version.  Do you know where you installed java version 5???
If you are not sure, what is the output of this command then!

```

sudo find / -name java -print

```

---

### Post by kerme8503 on 2006-09-06
haha i feel retarted, your all like "your retarted" and im like "yeah":

/var/lib/dpkg/alternatives/java
/etc/alternatives/java
/etc/java
/usr/share/java
/usr/bin/java
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/bin/java
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/bin/java
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/bin/java
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/java
/usr/lib/openoffice/share/Scripts/java


:)

---

### Post by kerme8503 on 2006-09-06
BUMP  -- i need help!

---

### Post by skymt on 2006-09-06
I assume you installed Sun Java from a package. If so, run the following command: ```
sudo update-alternatives --config java
```Pick /usr/lib/jvm/java-1.5.0-sun/jre/bin/java.

---

### Post by kerme8503 on 2006-09-06
awesome, it works...thank you so much!!  :)

---

### Post by akba0012 on 2007-10-03
> **skymt said:**
> I assume you installed Sun Java from a package. If so, run the following command: ```
sudo update-alternatives --config java
```Pick /usr/lib/jvm/java-1.5.0-sun/jre/bin/java.

I dont have that option..

```
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```

what should i do now?

also:

```
 java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

```

---

### Post by LeWy2388 on 2007-11-30
Hey I'm actually going through the same situation. My Frostwire just won't start up and I've read through this thread and have done everything that was told but I havent been able to solve anything. Here are my results

[COLOR="Red"]lewis@lewis-desktop:~$ java -version[/COLOR]
java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


[COLOR="Red"]lewis@lewis-desktop:~$ sudo find / -name java -print[/COLOR]
/var/lib/dpkg/alternatives/java
/media/sda1/var/lib/alternatives/java
/media/sda1/etc/java
/media/sda1/etc/alternatives/java
/media/sda1/usr/share/java
/media/sda1/usr/share/swig/1.3.31/java
/media/sda1/usr/share/doc/db4-devel-4.5.20/ref/java
/media/sda1/usr/share/doc/libidn-devel-0.6.8/contrib/java
/media/sda1/usr/share/apps/kdevappwizard/imports/java
/media/sda1/usr/share/apps/kdevfilecreate/file-templates/java
/media/sda1/usr/bin/java
/media/sda1/usr/lib/java
/media/sda1/usr/lib/openoffice.org/share/Scripts/java
/media/sda1/usr/lib/jvm-exports/java
/media/sda1/usr/lib/jvm/java
/media/sda1/usr/lib/jvm/java-1.5.0-gcj-1.5.0.0/bin/java
/media/sda1/usr/lib/jvm/java-1.5.0-gcj-1.5.0.0/jre/bin/java
/media/sda1/usr/include/c++/4.1.2/java
/media/sda1/usr/include/c++/4.1.2/gnu/java
/media/sda1/usr/include/firefox-2.0.0.9/java
/media/sdb1/var/lib/dpkg/alternatives/java
/media/sdb1/etc/java
/media/sdb1/etc/alternatives/java
/media/sdb1/usr/share/java
/media/sdb1/usr/bin/java
/media/sdb1/usr/lib/openoffice/share/Scripts/java
/etc/alternatives/java
/etc/java
/usr/bin/java
/usr/lib/openoffice/share/Scripts/java
/usr/share/doc/libcupsys2/examples/scripting/java
/usr/share/java

[COLOR="Red"]lewis@lewis-desktop:~$ sudo update-alternatives --config java[/COLOR]

There is only 1 program which provides java
(/usr/bin/gij-4.2). Nothing to configure.

---

