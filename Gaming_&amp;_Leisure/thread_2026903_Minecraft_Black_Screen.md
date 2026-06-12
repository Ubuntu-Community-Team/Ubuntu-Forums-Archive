---
title: "Minecraft Black Screen"
date: 2012-07-15
forum: Gaming &amp; Leisure
---

### Post by HeyAwesomePeople on 2012-07-15
Hey guys. When i run minecraft, i get this error in terminal.

Exception in thread "Minecraft main thread" java.lang.UnsatisfiedLinkError: /home/bryan/.minecraft/bin/natives/liblwjgl.so: /home/bryan/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
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
    at org.lwjgl.opengl.Display.<clinit>(Display.java:132)
    at net.minecraft.client.Minecraft.a(SourceFile:184)
    at net.minecraft.client.Minecraft.run(SourceFile:657)
    at java.lang.Thread.run(Thread.java:722)




Help anyone?

---

### Post by regor210 on 2012-07-16
Minecraft on Ubuntu 12.04 

On Ubuntu 12.04 you have to update the Lightweight Java Game Library or you will get a black screen.

Sorry [http://modifyubuntu.com/#minecraft](http://modifyubuntu.com/#minecraft) is out of date due to lwjgl-2.8.4. Sorry again but this is a bit long. 

To open a terminal press ctrl+alt+t all at the same time.  Then cut and paste the following commands into the terminal window one line at a time minus the $. 

 #make sure you have Openjdk-7 and all the Openjdk-7 extensions. 

$ sudo apt-get update 

$ sudo apt-get upgrade 

$ sudo apt-get install ca-certificates-java icedtea-7-jre-cacao icedtea-7-jre-jamvm java-common libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common libgnome2-0 libgnomevfs2-0 libgnomevfs2-common openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib ttf-dejavu-extra tzdata-java 

Download minecraft.jar from here. 
[http://www.minecraft.net/download](http://www.minecraft.net/download) 

Download the Lightweight Java Game Library or lwjgl from here 
[http://sourceforge.net/projects/java-game-lib/files/latest/download?source=files](http://sourceforge.net/projects/java-game-lib/files/latest/download?source=files) 

If you haven&#8217;t yet run Minecraft and log in, it will automatically create the folder .minecraft in your home folder. Note. You will get a black screen. Here's how. 

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

After this you can goto your Downloads folder right click on minecraft.jar, scroll down to properties. Use the slider named Open with and select OpenJDK Jave 7 Runtime. Click OK.

Now you can start Minecraft by double clicking the minecraft.jar icon, you can pick it up with your mouse and move it to your desktop if you like.

If you still have problems, sometimes Ubuntu&#8217;s 3D desktop effects has issues with Minecraft. You could try logging out of your Desktop, select Unity 2D then log back in.

---

### Post by redbikemaster on 2012-07-19
I'm running 8GB of RAM running lubuntu 12.04. I want to give the maximum amount of RAM to Minecraft. Instead of typing:
```

java -Xmx1048M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame

```
What should I put in place of '1048' and '512'?

---

### Post by regor210 on 2012-07-19
I'm not sure how much allocating more ram to Minecraft will help as Minecraft will run fine on 256 megs. But feel free to experiment and let us know how it go's.  

$ java -Xmx2096M -Xms1048M -cp minecraft.jar net.minecraft.LauncherFrame

$ java -Xmx4192M -Xms2096M -cp minecraft.jar net.minecraft.LauncherFrame

Note.
-Xmx sets the maximum memory
-Xms sets the minimum memory

---

### Post by redbikemaster on 2012-07-29
Thanks

---

### Post by redbikemaster on 2012-07-29
```


Invalid maximum heap size: -Xmx4192M
The specified size exceeds the maximum representable size.
Error: Could not create the Java Virtual Machine.
Error: A fatal exception has occurred. Program will exit.

```

What does this mean?

---

### Post by efflandt on 2012-08-02
redbikemaster you should not need more that 2G (another way of saying 2048M to java)  for minecraft total.  There was a time when I gave it 2G minimum and max, and it sometimes used a little more than 1G, but minecraft 1.3.1 client seems to be more efficient and does not use all of 1G

So I launch it with this script:

```
#!/bin/sh
# Change cd line to your path to orig minecraft.jar, NOT ~/.minecraft/bin
cd ~/MC-client
java -Xmx2G -Xms1G -cp minecraft.jar net.minecraft.LauncherFrame
```

Are you running 64-bit Ubuntu?  If you are running 32-bit, that 8 GB is wasted because 32-bit can only address around 3 GB total including OS.  Although, a 32-bit pae kernel may be able to use more RAM, but the 32-bit limit might still apply to each program.

What does **free** in a terminal show?

---

