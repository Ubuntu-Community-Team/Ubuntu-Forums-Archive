---
title: "Minecraft Error"
date: 2010-11-15
forum: Gaming &amp; Leisure
---

### Post by Cousjava on 2010-11-15
Whenever I try to run Minecraft, I get this error:

> 
      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to [email]support@mojang.com[/email].
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 15/11/10 17:26

Minecraft: Minecraft Alpha v1.2.2
OS: Linux (i386) version 2.6.35-22-generic
Java: 1.6.0_20, Sun Microsystems Inc.
VM: OpenJDK Client VM (mixed mode, sharing), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
	at org.lwjgl.opengl.Display.create(Display.java:846)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:201)
	at net.minecraft.client.Minecraft.run(SourceFile:563)
	at java.lang.Thread.run(Thread.java:636)
--- END ERROR REPORT ab40c083 ----------



I have tried the what is written at [http://timashley.me/node/596]("http://timashley.me/node/596") with no success, and in [this thread.]("http://ubuntuforums.org/showthread.php?t=1612164")

I am using Ubuntu 10.10 Maverick with GNOME 2.6.35-22-generic and am trying to play Minecraft Alpha 1.2.2, but I get the same problem trying to play the classic version. I have tried both in-browser, the linux jar file and running the windows version under wine, all without success. I have tried loading with both Open Java and Sun Java, both with the same error message.

When I type 'java' into the search bar of Synaptic Package Manager, the following packages are listed as being installed (in alphabetical order):

brltty
ca-certificates-java
couchdb-bin
dbus
default-jre
default-jre-headless
docbook-xsl
gdb
ikvm
java-common
java-wrappers
javascript-common
libaccess-bridge-java
libaccess-bridge-java-jni
libapache2-mod-php5
libclucene0ldbl
libcommons-cli-java
libcommons-lang-java
libcortado-java
libdbus-1-3
libgtksouceview2.0-common
libgudev-1.0-0
libhsqldb-java
libjinput-java
libjinput-jni
libjmac-java
libjs-jquery
libjs-mootools
libjson-glib-1.0-0
libjutils-java
libkjsapi4
libkjsembed4
liblwjgl-java
liblwjgl-java-jni
libmiglayout-java
libnunit-cil-dev
libnuit2.4-cil
libservlet2.5-java
libvirtodbc0
libwebkit-1.0-2
libwebkit-1.0-common
libwoodstox-java
libxml-sax-perl
monodevelop
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
openoffice.org-base
openoffice.org-java-common
php5
php5cli
php5-common
php5-gd
php5-mcrypt
php5-mysql
plasma-scriptengine-javascript
sun-java6-bin
sun-java6-jre
sun-java6-plugin
tzdata-java
virtuoso-minimal
virtuoso-opensource-6.1-bin
virtuoso-opensource-6.1-common

From reading other threads, its probably something wrong with my Java packages, but I don't know what.

---

### Post by bewarellamas on 2010-11-16
Are you using any custom texture packs? I can't remember my error message but I had a ton of problems with them. Just an idea. Sorry I don't have more.

---

### Post by Cousjava on 2010-11-18
No, I haven't tried any of that. I want to get the game working normally before I add any extras.

---

### Post by Tommy_Dude on 2010-12-01
I too have this same error occur, both in browser and with the jar file... If you hear any solution to this please let me know and I'll do the same for you.

---

### Post by epsolon77 on 2010-12-02
1.2.2 is not the most current version.  Client side the most current version is 1.2.5.  I would start by downloading the newest client.  I think there is an instability in the java package though.  I'm running a minecraft server on 10.04 server CLI and the server is crashing every few hours.

---

### Post by Cousjava on 2010-12-02
I have updated it, and the error is still basically the same:

> --- BEGIN ERROR REPORT a1dce528 --------
Generated 02/12/10 20:30

Minecraft: Minecraft Alpha v1.2.5
OS: Linux (i386) version 2.6.35-23-generic
Java: 1.6.0_22, Sun Microsystems Inc.
VM: Java HotSpot(TM) Client VM (mixed mode, sharing), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
	at org.lwjgl.opengl.Display.create(Display.java:846)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:197)
	at net.minecraft.client.Minecraft.run(SourceFile:559)
	at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT c7cdd03d ----------



---

### Post by Tommy_Dude on 2010-12-02
I've heard that Ubuntu 10.04 users have fewer problems running minecraft than 10.10 players. I'm tempted to try and downgrade to play it if I cannot solve the same error presented in this thread. I also upgraded minecraft but I still get that same error. I'm very new to Linux so even finding help suggestions is hard for me (it took me literally a week to figure out how to correctly install java.)

---

### Post by Cousjava on 2010-12-03
I Think I've worked out what the problem is, but I'm not sure how to solve it. Minecraft works only on Sun Java, rather than OpenJDK or IcedTea. However, Sun Java is missing one key pckage in the download: pluginappletviewer, which should be found in /usr/lib/jvm/java-6-sun-<version>/bin. The other thing that needs to be done is to change all the pointers (I'm not sure what the correct word is, so I'm using pointer) for Java from OpenJDK to SunJava, which can be done with the command

```

sudo update-alternatives --all

```

I have tried just copying the pluginappletviewer from the openjdk directory to the sun java directory, but that didn't work.

---

