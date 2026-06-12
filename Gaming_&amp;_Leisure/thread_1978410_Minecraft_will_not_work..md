---
title: "Minecraft will not work."
date: 2012-05-11
forum: Gaming &amp; Leisure
---

### Post by haseo57 on 2012-05-11
Okay, so i have just updated to Ubuntu 12.04, and minecraft will not work for me. It goes through the update screen, then it crashes. i do not understand what i should do. any suggestions? Minecraft has stopped running because it encountered a problem.

--- BEGIN ERROR REPORT 7cf3a456 --------
Generated 5/11/12 4:47 PM

Minecraft: Minecraft 1.2.5
OS: Linux (i386) version 3.2.0-24-generic
Java: 1.6.0_31, Sun Microsystems Inc.
VM: Java HotSpot(TM) Client VM (mixed mode, sharing), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: Could not init GLX
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
	at org.lwjgl.opengl.Display.create(Display.java:854)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:236)
	at net.minecraft.client.Minecraft.run(SourceFile:657)
	at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT 30c5f759 ----------

that is the error report it gave me

---

### Post by linuxman94 on 2012-05-11
Do you have the latest graphics drivers?

---

### Post by regor210 on 2012-05-11
Ubuntu 12.04

Download minecraft.jar from here.
[http://www.minecraft.net/download](http://www.minecraft.net/download)

Download the Lightweight Java Game Library or lwjgl from here
[http://sourceforge.net/projects/java-game-lib/files/latest/download?source=files](http://sourceforge.net/projects/java-game-lib/files/latest/download?source=files)

If you haven&#8217;t yet run Minecraft do so to automatically to create the folder .minecraft in your home folder. Note. You will get a black screen.

Open a terminal then press ctrl+alt+t all at the same time. Cut and paste the following commands into the terminal window one line at a time minus the $.
------------------------------------------------
#make sure you have Openjdk-7 and all the Openjdk-7 extentions.

$ sudo apt-get update

$ sudo apt-get upgrade

$ sudo apt-get install ca-certificates-java icedtea-7-jre-cacao icedtea-7-jre-jamvm java-common libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common libgnome2-0 libgnomevfs2-0 libgnomevfs2-common openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib ttf-dejavu-extra tzdata-java
-------------------------------------------------------------------------

$ cd ~/Downloads

$ sudo chmod a+x minecraft.jar

$ java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame
-------------------------------------------------
Close Minecraft

In Ubuntu 12.04 you have to update lwjgl by hand due to Java 7 or Openjdk-7. You can go here or read down and use the command line.

Lightweight Java Game Library download
lwjgl-2.8.3
[http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)


The command line.

Then open a terminal ctrl+alt+t cut and paste the following commands into the terminal window one line at a time minus the $.
------------------------------------------------------------------------------
#update LWJGL
# Note. lwjgl-2.8.3.zip will change over time as updates become available. so you will have to change the names as needed.
# 4-29-2012 the Minecraft version is 1.2.5. When version 1.2.6 comes out its likely you will have to update lwjgl by hand again. Word is, when Minecraft hits version 2.0 they will switch to Java 7 and you will not need to update lwjgl by hand any more.

# update lwjgl by replacing these 9 files

$ cd ~/Downloads

$ unzip lwjgl-2.8.3.zip

# type A for all

$ sudo cp -f ~/Downloads/lwjgl-2.8.3/jar/jinput.jar ~/.minecraft/bin/jinput.jar
$ sudo cp -f ~/Downloads/lwjgl-2.8.3/jar/lwjgl_util.jar ~/.minecraft/bin/lwjgl_util.jar
$ sudo cp -f ~/Downloads/lwjgl-2.8.3/jar/lwjgl.jar ~/.minecraft/bin/lwjgl.jar


$ sudo cp -f ~/Downloads/lwjgl-2.8.3/native/linux/libjinput-linux.so ~/.minecraft/bin/natives/libjinput-linux.so
$ sudo cp -f ~/Downloads/lwjgl-2.8.3/native/linux/libjinput-linux64.so ~/.minecraft/bin/natives/libjinput-linux64.so
$ sudo cp -f ~/Downloads/lwjgl-2.8.3/native/linux/liblwjgl.so ~/.minecraft/bin/natives/liblwjgl.so
$ sudo cp -f ~/Downloads/lwjgl-2.8.3/native/linux/liblwjgl64.so ~/.minecraft/bin/natives/liblwjgl64.so
$ sudo cp -f ~/Downloads/lwjgl-2.8.3/native/linux/libopenal.so ~/.minecraft/bin/natives/libopenal.so
$ sudo cp -f ~/Downloads/lwjgl-2.8.3/native/linux/libopenal64.so ~/.minecraft/bin/natives/libopenal64.so

# close the terminal.
# Open a new terminal ctrl+alt+t

------------------------------------------------------------------------------------
#make sure everything has permission for you to run it.

$ sudo chmod -R 777 .minecraft

$ cd ~/Downloads

$ sudo chmod a+x minecraft.jar

$ java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame

Note. if you have 2GB or more ram on your mother board you may get better performance by alocating more ram to Minecraft. $ java -Xmx1048M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame



------------------------------------------------------------------------------------

---

