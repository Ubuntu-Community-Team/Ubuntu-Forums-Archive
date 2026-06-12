---
title: "Minecraft Ubuntu Black Screen"
date: 2012-07-01
forum: Gaming &amp; Leisure
---

### Post by LukeYAYAY on 2012-07-01
I have followed loads of tutorials, the launcher of Minecraft opens, but once i have logged in it presents me with a black screen. Does anyone have any ideas why this could be?

---

### Post by LukeYAYAY on 2012-07-01
I get these errors:

Exception in thread "main" java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
	at java.net.URLClassLoader$1.run(URLClassLoader.java:366)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:355)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:354)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:423)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:356)
	at Loader.load(Loader.java:25)
	at Loader.main(Loader.java:19)

---

### Post by Dlambert on 2012-07-01
Try this first: > **!!-BLACK SCREEN FIX-!!**
 1) Download Maverik Java Monkey Engine libraries
 32bit: [http://mirrors.kernel.org/ubuntu/pool/universe/l/lwjgl/liblwjgl-java-jni...]("http://mirrors.kernel.org/ubuntu/pool/universe/l/lwjgl/liblwjgl-java-jni_2.4.2+dfsg-3_i386.deb")
 64bit: [http://mirrors.kernel.org/ubuntu/pool/universe/l/lwjgl/liblwjgl-java-jni...]("http://mirrors.kernel.org/ubuntu/pool/universe/l/lwjgl/liblwjgl-java-jni_2.4.2+dfsg-3_amd64.deb")
 2) Extract the Debian package
 32bit: dpkg -x liblwjgl-java-jni_2.4.2+dfsg-3_i386.deb /tmp/lwjgl
 64bit: dpkg -x liblwjgl-java-jni_2.4.2+dfsg-3_amd64.deb /tmp/lwjgl
 3) Move liblwjgl.so to Minecraft folder
 # mv /tmp/lwjgl/usr/lib/jni/liblwjgl.so ~/.minecraft/bin/natives
 4) Download Java Monkey Engine binary package
 [http://code.google.com/p/jmonkeyengine/downloads/detail?name=jME2_0_1-StableDistribution.zip&can=2&q=](http://code.google.com/p/jmonkeyengine/downloads/detail?name=jME2_0_1-StableDistribution.zip&can=2&q=)
 5) Extract Java Monkey Engine binary pacakge and change to its folder
 # unzip jME2_0_1-StableDistribution.zip && cd jME2_0_1-StableDistribution/jME2_0_1-StableDistribution/
 6) Replace jar files in the Minecraft folder
 # mv lib/lwjgl/jinput.jar ~/.minecraft/bin/
 # mv lib/lwjgl/lwjgl.jar ~/.minecraft/bin/
 # mv lib/lwjgl/lwjgl_util.jar ~/.minecraft/bin/
 7) Copy library files to the Minecraft folder
 # mv lib/lwjgl/native/linux/lib*.* ~/.minecraft/bin/natives
 8) Launch minecraft
 # java -jar .minecraft/minecraft_name.jar
 Pick a nickname (for LAN Server games), Login with blank credentials and select "Play offline"

Then, are you using Java from Oracle? or OpenJDK? I would recommend Java from Oracle. How to (JRE v6, yes you can install version 7 but some people report it works best with v6 still.  

> 1) Add the Canonical Partner Repository (For Ubuntu\Mint users) and Update
  ```
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) percise partner" && sudo apt-get update 
``` 2) Install Java6 Runtime Environment
  ```
sudo apt-get install sun-java6-jre
```

---

### Post by LukeYAYAY on 2012-07-01
I used the command you put at the bottom to first install java, or something similar to that.

Sorry, this is my first time using Ubuntu, ever. 
And i have no idea what im really doing

Upon typing
dpkg -x liblwjgl-java-jni_2.4.2+dfsg-3_i386.deb /tmp/lwjgl

I get 

error: failed to read archive `liblwjgl-java-jni_2.4.2+dfsg-3_i386.deb': No such file or directory

---

### Post by LukeYAYAY on 2012-07-01
When i launch Minecraft from the terminal, i get these errors when i get the black screen:


28
Setting user: EvilLittleMonkey, -2765150666204540422
Exception in thread "Minecraft main thread" java.lang.UnsatisfiedLinkError: /home/luke/.minecraft/bin/natives/liblwjgl.so: libjawt.so: cannot open shared object file: No such file or directory
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary1(ClassLoader.java:1939)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1864)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1825)
	at java.lang.Runtime.load0(Runtime.java:792)
	at java.lang.System.load(System.java:1059)
	at org.lwjgl.Sys$1.run(Sys.java:69)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.Sys.doLoadLibrary(Sys.java:65)
	at org.lwjgl.Sys.loadLibrary(Sys.java:81)
	at org.lwjgl.Sys.<clinit>(Sys.java:98)
	at org.lwjgl.opengl.Display.<clinit>(Display.java:129)
	at net.minecraft.client.Minecraft.a(SourceFile:148)
	at net.minecraft.client.Minecraft.run(SourceFile:554)
	at java.lang.Thread.run(Thread.java:722)

---

### Post by regor210 on 2012-07-01
Minecraft

If your looking to install Minecraft on Ubuntu 12.04 many of us are using the how to on this page

To open a terminal press ctrl+alt+t all at the same time. Then cut and paste the following commands into the terminal window one box at a time.

[http://modifyubuntu.com/#minecraft](http://modifyubuntu.com/#minecraft)

---

