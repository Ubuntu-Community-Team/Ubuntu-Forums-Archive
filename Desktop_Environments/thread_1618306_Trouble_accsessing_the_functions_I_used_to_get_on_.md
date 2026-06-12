---
title: "Trouble accsessing the functions I used to get on GNOME when i right click."
date: 2010-11-10
forum: Desktop Environments
---

### Post by Dielan on 2010-11-10
Hey there, I'm trying to play Minecraft on my netbook like I did before with Ubuntu Netbook Edition 10.04, but on 10.04 i opted at the log in to use the GNOME interface, so to run Minecraft i just right clicked it and chose the option to run with SUN Java(insert version numbers here) and it worked just fine



BUT with the new Unity interface I can't get it to work! I right click and nothing happens. How do I run with Java on Unity? It worked fine when i logged out and switched to the GNOME interface, so I know the game works. I just don't know how to do it in Unity.


Any help would be appreciated.

---

### Post by mcduck on 2010-11-10
I suppose the easiest way would be to create a simple script to start Minecraft and launch *that* from Unity.

This is what I'm using to start Minecraft:
```

#! /bin/sh
java -Xmx1024M -Xms512M -cp /home/mcduck/Programs/Minecraft/Minecraft.jar net.minecraft.LauncherFrame

```

(I also made myself a menu launcher that points to that script. Should be possible with Unity as well.)

edit: I just realized that you might also have problems with multiple installed Java versions. You can safely set SUN Java as the default. To do that just open a terminal and run "sudo update-alternatives --config java" and select the SUN Java from the list.

---

### Post by Dielan on 2010-11-10
I gave the code a shot and this is what pooped out:

```
Exception in thread "main" java.lang.NoClassDefFoundError: net/minecraft/LauncherFrame
Caused by: java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: net.minecraft.LauncherFrame. Program will exit.
dielan@dielan-1005HA:~$ 



```


I'm NOT very good with code.

---

### Post by mcduck on 2010-11-11
You need to change the path to the Minecraft.jar in the command. I doubt you have it in exactly the same place as I do. ;)

java -Xmx1024M -Xms512M -cp **/home/mcduck/Programs/Minecraft/Minecraft.jar** net.minecraft.LauncherFrame

just change the bold part to point to where *you* have the Minecraft.jar and it should work.

---

