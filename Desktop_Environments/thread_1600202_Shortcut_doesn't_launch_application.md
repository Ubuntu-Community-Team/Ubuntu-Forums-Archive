---
title: "Shortcut doesn't launch application"
date: 2010-10-18
forum: Desktop Environments
---

### Post by Baneblade on 2010-10-18
I've created a shortcut for minecraft.jar on my top bar and pointed it to the correct file. This shortcut does not launch the application as expected though.

The minecraft.jar itself has the correct permissions and is set as executable. Set to open with Sun Java 6. When using the .jar directly it works as expected, but why can't I create a shortcut to launch it?

---

### Post by 3Miro on 2010-10-18
> **Baneblade said:**
> 
When using the .jar directly it works as expected, but why can't I create a shortcut to launch it?

Do you mean when you double-click? When you double-click on a file in the browser, the browser checks to see which progra is associated with this file and envokes it as:
```
 program file 
```

When you enter a command for shortcut, you have to enter it just as you will in the terminal. Basically, you should wirite the command as:
```
 java minecraft.jar 
```

---

### Post by Baneblade on 2010-10-18
Since it is just an executable and not "installed" I would need to specify the path to the file too right?

iv tried editing the shortcut command to these without luck:

java /[path]/ minecraft.jar
/[path]/ java minecraft.jar

---

### Post by 3Miro on 2010-10-18
I should have thought about the path, sorry.

You have an extra space in your example:

```
 java /home/your_name/some_folder/minecraft.jar 
```

Run the command in the terminal first, if it runs, then you will know that it works. If not, then you can see an error message.

---

### Post by Baneblade on 2010-10-19
I ran it in the terminal and go this error:

```
b3rz3rk3r@Havoc:~$ java /home/b3rz3rk3r/Games/minecraft.jar
Exception in thread "main" java.lang.NoClassDefFoundError: /home/b3rz3rk3r/Games/minecraft/jar
Caused by: java.lang.ClassNotFoundException: .home.b3rz3rk3r.Games.minecraft.jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: /home/b3rz3rk3r/Games/minecraft.jar.  Program will exit.

```

I have the Sun java and dev tools installed rather than the regular open one, since I'm told that can cause issues.

I'm not sure what this error is pointing to though?

---

### Post by 3Miro on 2010-10-19
You said that it runs well if you tell it to run from Nautilus. This means that nautilus is not using the java command to run it (or it is using something more complicated). You have to find out what is it that Nautilus is using to ring the programa nd put it in the command line. You can start by selecting the file in nautilus, right-click -> Properties and then look for what is the default applicaiton to opne it. This should give you a clue to what the command that nautilus is running should be.

---

### Post by ankspo71 on 2010-10-19
Hi,
Have you already tried running it with the 'java -jar' command?

java -jar /home/b3rz3rk3r/Games/minecraft.jar

If this works in the terminal, try editing your shortcut to have the same command.

Hope this helps.

---

### Post by Baneblade on 2010-10-19
> **ankspo71 said:**
> Hi,
Have you already tried running it with the 'java -jar' command?

java -jar /home/b3rz3rk3r/Games/minecraft.jar

If this works in the terminal, try editing your shortcut to have the same command.

Hope this helps.

Thank you Ankspo.. that "-jar" flag did the trick!
Working perfectly now.

Thanks for helping me get this sorted guys :)

---

### Post by I8NY on 2010-10-21
I know i'm a little late to comment on this but there is better way of running minecraft with suggested command from the website. ```
java -Xmx1024M -Xms512M -cp /home/username/Games/Minecraft/Minecraft.jar net.minecraft.LauncherFrame
```It is not necessary but will stop RAM problems if there are any.  To get the icon you can find it in the jar file if you open it up with the archive manager.

---

### Post by Baneblade on 2010-10-22
Thanks I8NY, that's a good tip. 
I'll keep it in mind if I have problems.

---

### Post by Subidubi32 on 2011-10-10
I know, this is an old thread, but I can't run my minecraft from my shortcut. I have the shortcut on my upper panel, I tried use the "java -jar /home/downloads/Minecraft.jar" command, but it doesn't do anything. The application starts normally if I run it directly, but it doesn't with the shortcut. I have the latest sun java installed, and it starts with it by default. I have tried the complicated command for the memory problems too, but it didn't helped me out eighter.

---

### Post by Baneblade on 2011-10-10
Just reboot your machine and try it again. I've had that problem before as well.

---

