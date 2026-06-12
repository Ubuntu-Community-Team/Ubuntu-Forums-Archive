---
title: "minecraft give's black screen"
date: 2012-07-05
forum: Gaming &amp; Leisure
---

### Post by demalition90 on 2012-07-05
first off, i installed ubuntu yesterday and have very, very low computer experience



i wanted to play minecraft so i watched a youtube video, did what it said, made a file named **m.sh** inside of it it say's  

[B]#!/bin/bash
java -Xmx1024M -Xms1024M -jar minecraft.jar
[/B]

when i click it it asks run in terminal display cancel or run if i click terminal or run the launcher comes up i log in and get a black screen, here's the error that comes in terminal


[B]27 achievements
182 recipes
Setting user: demalition90, 8901931296494895187
Exception in thread "Minecraft main thread" java.lang.UnsatisfiedLinkError: /home/demalition90/.minecraft/bin/natives/liblwjgl.so: libjawt.so: cannot open shared object file: No such file or directory
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1924)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1821)
    at java.lang.Runtime.load0(Runtime.java:792)
    at java.lang.System.load(System.java:1059)
    at org.lwjgl.Sys$1.run(Sys.java:69)
    at java.security.AccessController.doPrivileged(Native Method)
    at org.lwjgl.Sys.doLoadLibrary(Sys.java:65)
    at org.lwjgl.Sys.loadLibrary(Sys.java:81)
    at org.lwjgl.Sys.<clinit>(Sys.java:98)
    at org.lwjgl.opengl.Display.<clinit>(Display.java:132)
    at net.minecraft.client.Minecraft.a(SourceFile:184)
    at net.minecraft.client.Minecraft.run(SourceFile:657)
    at java.lang.Thread.run(Thread.java:722)



[/B]anyone got easy to follow instruction's on how to get it to work?

---

### Post by anewguy on 2012-07-06
I would suggest looking in the Leisure and Gaming forum - click on "The Ubuntu Forum Community" in the line showing the path to this thread, then in the following screen select leisure and gaming.  I would bet more than 1 user has run into this and it's probably the best place to check for a solution.  Yes, the error messages are from java, but don't assume it's a java error and not check the forum.  It looks like you are either missing a lib or a link to it.

---

### Post by ubudog on 2012-07-06
*Thread moved to Gaming & Leisure.*

---

### Post by demalition90 on 2012-07-06
thank's anewguy for the suggestion and ubudog for moving it

---

### Post by ubudog on 2012-07-06
Try this (in a terminal):
```
mv ~/.minecraft ~/.minecraftbak
```

Then, open the Minecraft launcher, click on "Options", then on "Force update!".  Login to your Minecraft account and let it re-download everything.

[B]Edit:  It appears that with Ubuntu 12.04, you must update LWJGL manually or you will get a black screen.
[/B]
The MinecraftWiki has a [nice article]("http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL") on how to do it.

Best,
ubudog

---

### Post by regor210 on 2012-07-06
****The simplest way to get Minecraft up and running is to use this site

[http://modifyubuntu.com/#minecraft](http://modifyubuntu.com/#minecraft)

1st Open a terminal, press ctrl+alt+t all at the same time.  Then cut and paste the following commands into the terminal window one box at a time. Then press enter. Wait after entering a command for the $ before entering the next box. Then cut and paste the following commands into the terminal window one line at a time minus the $.

$ cd ~/Downloads && sudo chmod a+x minecraft.jar


# This starts Minecraft

$ cd ~/Downloads && java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame



After this you can goto your Downloads folder right click on minecraft.jar,  scroll down to properties. Use the slider named **Open with** and select OpenJDK Jave 7 Runtime. Click OK.

Now you can start Minecraft by double clicking the minecraft.jar icon, you can pick it up with your mouse and  move it to your desktop if you like.


Note. After a Minecraft update you will have to go back to [http://modifyubuntu.com/#minecraft](http://modifyubuntu.com/#minecraft) and enter the 3rd box again to update lwjgl.

---

### Post by Ceannfaolaidh on 2012-07-06
What runtime are you using for Java? OpenJDK is prone to errors when working with Minecraft (Notch suggests Sun Java). This will help us figure out what to fix.

---

### Post by demalition90 on 2012-07-06
i downloaded jun java but i'm using JDK 6 (i also have JDK 7 on the computer but alot of the tut's i've found have said 6, they seemed pretty recent and idk when 7 was released so i assumed 6>7)

also i patched the LWJGL and still got a black screen so i did force update to try fresh and i got on and it was working then i tried to add modloader and optifine (was getting 1 fps =o) and when i deleted META-INF i clicked all files and it deleted the whole thing and now i''m stuck with black screen again (i've forced update patched and everything i can think of)

also i'm using 12.04 and ima try regor's suggestion after posting this

---

### Post by demalition90 on 2012-07-06
> **demalition90 said:**
> i downloaded jun java but i'm using JDK 7

also i patched the LWJGL and still got a black screen so i did force update to try fresh and i got on and it was working then i tried to add modloader and optifine (was getting 1 fps =o) and when i deleted META-INF i clicked all files and it deleted the whole thing and now i''m stuck with black screen again (i've forced update patched and everything i can think of)

also i'm using 12.04 and ima try regor's suggestion after posting this
demalition90@demalition90-OptiPlex-GX260:~$ cd ~/Downloads && sudo chmod a+x minecraft.jar
[sudo] password for demalition90: 
demalition90@demalition90-OptiPlex-GX260:~/Downloads$ cd ~/Downloads && java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame
27 achievements
182 recipes
Setting user: demalition90, 1884bd16f0e3abb1eeb083abce089d2829154dbc
LWJGL Version: 2.8.3
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x04522f2b, pid=4675, tid=3000601408
#
# JRE version: 6.0_24-b24
# Java VM: OpenJDK Client VM (20.0-b12 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.11.1
# Distribution: Ubuntu 12.04 LTS, package 6b24-1.11.1-4ubuntu3
# Problematic frame:
# C  [i915_dri.so+0x11f2b]  i830CreateContext+0x18bb
#
# An error report file with more information is saved as:
# /home/demalition90/Downloads/hs_err_pid4675.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted (core dumped)
demalition90@demalition90-OptiPlex-GX260:~/Downloads$ 

this is the error text in the launcher after trying regor's suggestion, i logged in got black screen and it closed

---

### Post by regor210 on 2012-07-07
1.
[https://help.ubuntu.com/community/Java#Choosing_the_default_Java_to_use](https://help.ubuntu.com/community/Java#Choosing_the_default_Java_to_use)

$ sudo update-alternatives --config java

Will let you know what Java version you are using and may let you change it. If Sun java 6 is what you want to use select it.

2. Sometimes there are permission issues when using Mods try

$ sudo chmod -R 777 .minecraft 

3. I'm not sure how you installed Sun Java 6? did you get all of these?
sun-java6-jre
sun-java6-plugin
sun-java6-fonts
 
4. Were you trying to run optifine due to lag?
If yes run

$ lspci -vmk | grep -A 8 -B 2 VGA


$ lspci | grep VGA && glxinfo | grep -w 'direct\|OpenGL'

And post what you get.

---

### Post by demalition90 on 2012-07-07
demalition90@demalition90-OptiPlex-GX260:~$ lspci -vmk | grep -A 8 -B 2 VGA

Device:	00:02.0
Class:	VGA compatible controller
Vendor:	Intel Corporation
Device:	82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
SVendor:	Dell
SDevice:	Device 0126
Rev:	01
Driver:	i915
Module:	intelfb
Module:	i915
demalition90@demalition90-OptiPlex-GX260:~$ lspci | grep VGA && glxinfo | grep -w 'direct\|OpenGL'
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
demalition90@demalition90-OptiPlex-GX260:~$ sudo apt-get install mesa-utils
[sudo] password for demalition90: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.6 kB of archives.
After this operation, 135 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe mesa-utils i386 8.0.1+git20110129+d8f7d6b-0ubuntu2 [27.6 kB]
Fetched 27.6 kB in 0s (58.1 kB/s)
Selecting previously unselected package mesa-utils.
(Reading database ... 174263 files and directories currently installed.)
Unpacking mesa-utils (from .../mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up mesa-utils (8.0.1+git20110129+d8f7d6b-0ubuntu2) ...
demalition90@demalition90-OptiPlex-GX260:~$ lspci | grep VGA && glxinfo | grep -w 'direct\|OpenGL'
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
direct rendering: Yes
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 845G x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 8.0.2
OpenGL extensions:
demalition90@demalition90-OptiPlex-GX260:~$

---

### Post by regor210 on 2012-07-07
Looks like your using the Intell integrated graphics on your Dell P4 OptiPlex.

1st get into your BIOS and max out the ram for your Intell graphics adapter if you can spare it. If you don't blink you will see a message when you start your computer to hold down F2 or the Del key to open your BIOS.

2nd. If you have less then 1 Gigs of system I would start minecraft like this

 $ java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame

or this

$ cd ~/Downloads && java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame

This restricts Minecraft to using only 256 Meg's of ram the minimum need to run Minecraft. This will keep your system from using Swap memory or using your Hard drive as system ram, for gaming this is crazy slow.  

The bad news is  optifine c Light 

&#8220;The Light edition is not compatible with ModLoader and Forge.&#8221;

This means it will likely be tricky to get it working.

[http://www.minecraftforum.net/topic/249637-125-optifine-hd-c3-fps-boost-hd-textures-aa-af-and-much-more/](http://www.minecraftforum.net/topic/249637-125-optifine-hd-c3-fps-boost-hd-textures-aa-af-and-much-more/)

When you get OptiFine_1.1_L_C.zip make sure it has permission for you to run it.  Permission shouldn't change after you unzip it.

$ cd ~/Downloads

$ sudo chmod a+x OptiFine_1.1_L_C.zip

Don't forget to scroll down to Tips and tricks: to get more help with lag.

And if all else fails you can go to your home folder and rename the hidden .minecraft folder. Then when you start Minecraft it will automatically download a new copy of the game

---

### Post by demalition90 on 2012-07-07
i want to be able to atleast play the vanilla game first, only reason it broke when installing optifine was because i clicked the wrong button and didn't have a backup, idk how i got it working the first time and i really want to play the game, i had 1-2 fps but it still played smoothly and was still enjoyable

EDIT: also i chose the 32bit version of ubuntu and i notice some of the LWJGL file's that i am required to patch say 64, is there a 32-bit version of LWJGL or do the file's work on both system types?

---

### Post by regor210 on 2012-07-07
If your using Sun Java 6 you don't need to update LWJGL. A fresh copy of Minecraft should just work, if Java 6 was installed properly.

If your using OpenJDK-7 or Oracle Java 7 you will need to update  LWJGL.  LWJGL or The Lightweight Java Game Library used by Minecraft is outdated and will not work with Java 7.  

Ubuntu 12.04 comes with OpenJDK-7. OpenJDK-6 in the past had issues with Minecraft so on the Minecraft download page they recommend Sun Java 6. Starting at  Minecraft 1.3, Minecraft will change over to Oracle Java 7 and we will not have to update LWJGL any more.

Because Minecraft isn't the only program on my computer that uses Java I'm not downgrading to Sun Java 6 as it will likely cause problems in the future.  

What version of Java are you using and how did you install it?

---

### Post by demalition90 on 2012-07-07
*just walked 2 miles in the rain my hands are numb forgive any spelling error's

i typed "java"  into the software center and downloaded java, idk the version but it was prob the most recent and therefore java7

---

### Post by regor210 on 2012-07-07
Sorry [http://modifyubuntu.com/#minecraft](http://modifyubuntu.com/#minecraft) is out of date due to lwjgl-2.8.4. Will have to install Minecraft manually. I just tried this and its all working and up to date. 

# Rename .minecraft

$ mv .minecraft .minecraft1

 #make sure you have Openjdk-7 and all the Openjdk-7 extensions.

$ sudo apt-get update

$ sudo apt-get upgrade

$ sudo apt-get install ca-certificates-java icedtea-7-jre-cacao icedtea-7-jre-jamvm java-common libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common libgnome2-0 libgnomevfs2-0 libgnomevfs2-common openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib ttf-dejavu-extra tzdata-java

#Look and make sure your using openjdk-7.

$ sudo update-alternatives --config java


Ubuntu 12.04

Sometimes Ubuntu&#8217;s 3D desktop effects has issues with Minecraft. You could try logging out of your Desktop, select Unity 2D then log back in.

Download minecraft.jar from here.
[http://www.minecraft.net/download](http://www.minecraft.net/download)

Download the Lightweight Java Game Library or lwjgl from here
[http://sourceforge.net/projects/java-game-lib/files/latest/download?source=files](http://sourceforge.net/projects/java-game-lib/files/latest/download?source=files)

If you haven&#8217;t yet run Minecraft do so and log in so it will automatically to create the folder .minecraft in your home folder. Note. You will get a black screen. Here's how.

To open a terminal press ctrl+alt+t all at the same time.  Then cut and paste the following commands into the terminal window one line at a time minus the $.
------------------------------------------------

$ cd ~/Downloads

$ sudo chmod a+x minecraft.jar

$ java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame
-------------------------------------------------
Close Minecraft

In Ubuntu 12.04 you have to update lwjgl by hand due to Java 7 or Openjdk-7. You can go here or read down and use the command line.

Lightweight Java Game Library download

[http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)


The command line.

Then open a terminal ctrl+alt+t cut and paste the following commands into the terminal window one line at a time minus the $.
------------------------------------------------------------------------------
#update LWJGL
# Note. lwjgl-2.8.4.zip will change over time as updates become available. so you will have to change the names as needed.
# 4-29-2012 the Minecraft version is 1.2.5. When version 1.2.6 comes out its likely you will have to update lwjgl by hand again. Word is, when Minecraft hits version 2.0 they will switch to Java 7 and you will not need to update lwjgl by hand any more.

# update lwjgl by replacing these 9 files

$ cd ~/Downloads

$ unzip lwjgl-2.8.4.zip

# type A for all

$ sudo cp -f ~/Downloads/lwjgl-2.8.4/jar/jinput.jar ~/.minecraft/bin/jinput.jar
$ sudo cp -f ~/Downloads/lwjgl-2.8.4/jar/lwjgl_util.jar ~/.minecraft/bin/lwjgl_util.jar
$ sudo cp -f ~/Downloads/lwjgl-2.8.4/jar/lwjgl.jar ~/.minecraft/bin/lwjgl.jar


$ sudo cp -f ~/Downloads/lwjgl-2.8.4/native/linux/libjinput-linux.so ~/.minecraft/bin/natives/libjinput-linux.so
$ sudo cp -f ~/Downloads/lwjgl-2.8.4/native/linux/libjinput-linux64.so ~/.minecraft/bin/natives/libjinput-linux64.so
$ sudo cp -f ~/Downloads/lwjgl-2.8.4/native/linux/liblwjgl.so ~/.minecraft/bin/natives/liblwjgl.so
$ sudo cp -f ~/Downloads/lwjgl-2.8.4/native/linux/liblwjgl64.so ~/.minecraft/bin/natives/liblwjgl64.so
$ sudo cp -f ~/Downloads/lwjgl-2.8.4/native/linux/libopenal.so ~/.minecraft/bin/natives/libopenal.so
$ sudo cp -f ~/Downloads/lwjgl-2.8.4/native/linux/libopenal64.so ~/.minecraft/bin/natives/libopenal64.so

# close the terminal.
# Open a new terminal ctrl+alt+t

------------------------------------------------------------------------------------
#make sure everything has permission for you to run it.

$ sudo chmod -R 777 .minecraft

$ cd ~/Downloads

$ sudo chmod a+x minecraft.jar

$ java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame

Note. if you have 2GB or more ram on your mother board you may get better performance by alocating more ram to Minecraft. $ java -Xmx1048M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame

---

### Post by demalition90 on 2012-07-08
=D it works thank you so much

from now on i'll be backing up before i add mod's so if you don't have anything else to add i'll mark this as solved,

---

### Post by regor210 on 2012-07-08
Glad to see you got it up and going. Good  luck with those Mods.

---

