---
title: "Help installing juploadr"
date: 2006-07-14
forum: Desktop Environments
---

### Post by gbinal on 2006-07-14
Yes, I know that so many people talk about the flickr uploadr juploadr with talk of how easy it is to install, but hell.  I just don't understand (classic, trying noob).  From the [FAQ page]("http://juploadr.sourceforge.net/faq.html"), I'm given some basic "directions" but I can't figure it for the life of me:

> After it's installed, all Linux users need to do is make sure java is in their path. Type 'java -version' on the command line to check. It should return 1.5.0 (or whatever version of java you have installed).

Anyhoo, I believe I do have an up to date, proprietary Java loaded.  I just don't know what to do from here.  Any help on getting this going would be great.  Thanks as always for being out there and listening.  

Gray B.

---

### Post by Cpt_Fluffy on 2006-09-17
I have just installed this myself after a few minutes of fumbling.

I can give you a basic outline, give me a shout if you need more in depth assistance.

Extract the .tar.gz to a folder.
Open Terminal, cd to the folder.
Type "./juploadr"

That's it.  Presuming your Java is good, then you're set.

Now, that should be enough information for you to add it to the Alacarte menu as well.

Good luck!:-\"

---

### Post by gbinal on 2006-09-17
Thank you, Captain!  

This really is a good tool and it's good to have it working.  

Thank you again.

Gray B.

---

### Post by Paulr-55 on 2006-09-27
I am having difficulty with jUploader under Dapper:

paul@moonstep:~/jUploadr-1.1.1-linuxGTK-i386$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8) **<- that is an 8 and a ')'**

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

paul@moonstep:~/jUploadr-1.1.1-linuxGTK-i386$ ./jUploadr
Starting JUploadr...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
GCJ is an incompatible version of java
Download the official version at [http://java.sun.com](http://java.sun.com)

I have no idea what to do here .. help?

---

### Post by gbinal on 2006-09-27
I'm not an expert here, 

but my guess would be to check what version of java you have (I just look in Add/Remove...well, it turns out I don't have two Java programs I thought I used to have).  Anyway, there is only one java to be found in my repositories (it didn't show up in the quick search but was ).  My point is to install java or update java.  

Actually, as I look at your nots, I realize that in synaptic (when I searched java), I found that I don't have java gcj (java-gcj-compat-dev), I have java gij (java-gcj-compat).  

Again, I am the type of user who screws things up as I learn how to do new things (though rarely with terrible consequences) - but my advice is to go into synaptic and swap the two.  Uninstall the -dev version and install the GIJ one (see Description).

Peace and good luck.

---

### Post by Paulr-55 on 2006-09-27
Thanks for the input... I am still tooling around with it. I will post back if I figure anything out.

Paul

---

### Post by markthecarp on 2006-12-25
Paulr-55,

I'm having the same problem on my edgy system. No problem under dapper.

```
mark@spinach:~/bin/jUploadr-1.1.1-linuxGTK-i386$ ./jUploadr
Starting JUploadr...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2]
Configuring environment...
GCJ is an incompatible version of java
Download the official version at http://java.sun.com
```
No good
```
mark@spinach:~/bin/jUploadr-1.1.1-linuxGTK-i386$ apt-cache show sun-java5-bin
Package: sun-java5-bin
Priority: optional
Section: multiverse/libs
Installed-Size: 65084
Maintainer: Matthias Klose <doko@ubuntu.com>
Architecture: i386
Source: sun-java5
Version: 1.5.0-08-0ubuntu1
Depends: sun-java5-jre (= 1.5.0-08-0ubuntu1), unixodbc, libc6, debconf (>= 0.5) | debconf-2.0
Recommends: libasound2, libx11-6, libxext6, libxi6, libxp6, libxt6, libxtst6
Filename: pool/multiverse/s/sun-java5/sun-java5-bin_1.5.0-08-0ubuntu1_i386.deb
Size: 22335114
MD5sum: 488c7e850d0b166294b16c4a19f9090c
SHA1: 243fb53d03296815f30f16d8f3ee9f7dc6b4b76e
SHA256: c8e533a40c82e02f2686f3e5ec9d14f5d2c48af6c19a02d915711b6c31f19494
Description: Sun Java(TM) Runtime Environment (JRE) 5.0
 The Sun Java Platform Standard Edition Runtime Environment (JRE) 5.0
 contains the Java virtual machine, runtime class libraries, and
 Java application launcher that are necessary to run programs written
 in the Java progamming language. It is not a development environment and
 doesn't contain development tools such as compilers or debuggers.
 For development tools, see the Java Development Kit JDK(TM) 5.0
 (package sun-java5-jdk).
 .
 This package contains architecture dependent files.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```
```
mark@spinach:~/bin/jUploadr-1.1.1-linuxGTK-i386$ sudo apt-get install sun-java5-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java5-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@spinach:~/bin/jUploadr-1.1.1-linuxGTK-i386$ java --version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


```

So I have the latest java installed but "java --version" is returning an older version. I don't know how to fix this but I think it's the core of the problem.

Edit1: I found a solution at [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Java_.26_Non-Media_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Java_.26_Non-Media_Browser_Plug-ins)

-mark

---

### Post by anrom on 2008-05-11
I just downloaded jUploader 1.1.2 to my desktop and extracted the tar.gz file, also to desktop.  when I use the command "./juploadr" in terminal, I get "no such file or directory".  

Should I have saved the download somewhere else, and if so, where?  thanks for any help.

---

### Post by andytgeezer on 2008-05-26
Hi

I've done all the above but no shortcut appears in the applications menu. I'm a complete beginner and not sure where it should appear, but it's not in either Internet or graphics or anywhere easy to find. 

Any tips appreciated.

---

### Post by fedira on 2008-06-18
> **anrom said:**
> I just downloaded jUploader 1.1.2 to my desktop and extracted the tar.gz file, also to desktop.  when I use the command "./juploadr" in terminal, I get "no such file or directory".  

Should I have saved the download somewhere else, and if so, where?  thanks for any help.

Since you saved it to your desktop, you'll want to open a terminal and do:
```
 cd Desktop/jUploadr-1.1.2-linuxGTK-i386/
./jUploadr 

```

2 things:
1. jUploadr-1.1.2-linuxGTK-i386 should be whatever the extracted directory is called -- that's the version I have.
2. Make sure you type ./jUploader (capital U), not ./juploadr.

---

