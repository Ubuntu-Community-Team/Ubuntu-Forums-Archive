---
title: "Allocate more memory to minecraft"
date: 2012-03-16
forum: Gaming &amp; Leisure
---

### Post by wilson888888888 on 2012-03-16
I need more memory allocated to minecraft for a realistic texture pack, so I used this command:
java -Xmx2048M -Xms1024M -cp Minecraft.jar net.minecraft.LauncherFrame
it didn't work, and all the terminal says is this

Exception in thread "main" java.lang.NoClassDefFoundError: net/minecraft/LauncherFrame
Caused by: java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: net.minecraft.LauncherFrame. Program will exit.

I used to run minecraft by running the minecraft.jar.

---

### Post by regor210 on 2012-03-17
Like this > minecraft.jar not Minrcraft.jar

$  java  -Xmx2048M -Xms1024M -cp minecraft.jar net.minecraft.LauncherFrame

---

### Post by wilson888888888 on 2012-03-17
I tried it with the lowercase .minecraft, it was the same result.

---

### Post by regor210 on 2012-03-17
Where is minecraft.jar

#MC in Home folder
$ cd ~/ && java -Xmx2048M -Xms1024M -cp minecraft.jar net.minecraft.LauncherFrame

# regular MC in Downloads
$ cd ~/Downloads/ && java -Xmx2048M -Xms1024M -cp minecraft.jar net.minecraft.LauncherFrame

# ALLOC's
$ cd ~/.minecraft/ && java -Xmx2048M -Xms1024M -cp minecraft.jar net.minecraft.LauncherFrame

# MC on your Desktop
$ cd ~/Desktop/ && java -Xmx2048M -Xms1024M -cp minecraft.jar net.minecraft.LauncherFrame

---

### Post by wilson888888888 on 2012-03-17
I have minecraft.jar in the .minecraft folder, so i tried
cd ~/.minecraft/ && java -Xmx2048M -Xms1024M -cp minecraft.jar net.minecraft.LauncherFrame

It still gave me the same result

---

### Post by regor210 on 2012-03-17
How did you install Minecraft?

From 

[http://www.minecraft.net/download](http://www.minecraft.net/download)

Or did you use alloc's installer (Minecraft_Installer_20.sh)

$ cd ~/.minecraft/ && java -Xmx2048M -Xms1024M -cp minecraft.jar net.minecraft.LauncherFrame

should work. Or try

$ cd .minecraft
$ java -Xmx2048M -Xms1024M -cp minecraft.jar net.minecraft.LauncherFrame

---

### Post by wilson888888888 on 2012-03-18
I used the installer from here: 
[http://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/](http://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/)
I tried opening the script with a text editor but i couldn't understand it
also, I tried both ways you suggested and they didn't work

---

### Post by regor210 on 2012-03-18
It looks like they put minecraft.jar in a root file opt. Not a problem, all you need to do is go to 

[http://www.minecraft.net/download](http://www.minecraft.net/download)

and dowload minecraft.jar

then use

$ cd ~/Downloads/ && java -Xmx2048M -Xms1024M -cp minecraft.jar net.minecraft.LauncherFrame

to start minecraft.

---

### Post by wilson888888888 on 2012-03-18
thanks, that worked great

---

