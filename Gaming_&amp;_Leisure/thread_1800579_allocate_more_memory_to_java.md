---
title: "allocate more memory to java"
date: 2011-07-09
forum: Gaming &amp; Leisure
---

### Post by Metul Burr on 2011-07-09
attempting to allocate more memory to java for minecraft texture pack 256 x 256. can someone explain the steps on doing this?

---

### Post by ExileAmongYou on 2011-07-09
Are you already using the suggested launch options for running Minecraft on Linux?
```
java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
```

In that command, -Xmx is the maximum amount of memory allocated to Minecraft, -Xms is the minimum. I'm not sure exactly how much you'd need to get the texture pack going, but you can play around with it (remember to leave some memory for the rest of the system though!).

I'm not sure how confident you are with terminal commands, so let me know if you want to add that command to your main menu and I'll walk you through it.

---

### Post by Metul Burr on 2011-07-09
These are my previous terminal commands

java -jar mcpatcher-2.1.0_02.jar
padsp java -jar /home/metulburr/.minecraft/minecraft.jar
bash Minecraft_Installer_20.sh

ive been using padsp to launch minecraft otherwise the sound doesnt work at all

---

### Post by ExileAmongYou on 2011-07-09
Well I think you should be able to run it with:

```
padsp java -Xmx1024M -Xms512M -jar /home/metulburr/.minecraft/minecraft.jar
```

---

### Post by Metul Burr on 2011-07-09
it does,but i didn't see any changes... but do i increase java ram by increasing the xmx?
second, i changed your code and doubled it to see what would happen and minecraft went to a black screen
                          padsp java -Xmx2048M -Xmx1024M -jar /home/metulburr/.minecraft/minecraft.jar
i was originally thinking that i would have been using a slider to adjust it.
sorry i am a linux noob tinkering with things...but thanks for posting

---

### Post by ExileAmongYou on 2011-07-09
Yeah, like I said before, -Xmx sets the maximum amount of RAM allocated to Java, and -Xms sets the minimum. You might (and I stress *might*) get better performance out of Minecraft by setting both values higher than they are now, that would be something you would have to tinker with yourself.

There's no slider, unfortunately.

---

### Post by 1clue on 2011-07-09
There are lots of memory settings for Java.

What error message are you getting?

Also, you need to know that -Xmx (and -Xms and -XX:MaxPermSize and all the rest of them) are case sensitive.

The best bet is to copy the out of memory error line and google it.  That generally gets you to a page that tells you how to fix that specific problem.

---

### Post by Metul Burr on 2011-07-09
yeah i tried that and black screen. i dont know if thats the known "black screen" for minecraft or something else...or rather that was too much or not

---

### Post by Metul Burr on 2011-07-09
yeah i tried googling error codes to see what i get, but i find ubuntu forums with the best answers so i posted directly here
I'm not getting an error code when attempting to use a 256 x 256 texture pack...its just is slow as molasses. It's LB Photo Realism Pack 256 x 256. Though he has lower it's just not the same and the highest makes minecraft look great. So i was just figuring if there is a way around the slow movement. Someone suggested increasing java ram but didnt know how ...so here i am...and i am a linux newbie over my head lol

---

### Post by 1clue on 2011-07-09
I still fail to see where you posted any error.  It's pretty much impossible to help you without knowing what sort of OutOfMemoryError you got.

---

### Post by Metul Burr on 2011-07-09
i'm not getting any error code...it's just slow

---

### Post by 1clue on 2011-07-09
OK, try this:
[LIST=1]
[*]Run the application.
[*]In a separate terminal run jconsole.
[*]Choose your app from the list of virtual machines.
[*]Look at memory statistics, they're different based on which version of Java you use.
[*]If you see something that seems to be hitting a hard limit, try adjusting that pool with a command-line argument.
[/LIST]

The arguments can be found by googling your java (java6 for example) and the name of the memory space.

---

### Post by thewildspace on 2012-06-19
i tried what u said and i got this error message

Exception in thread "main" java.lang.NoClassDefFoundError: net/minecraft/LauncherFrame
Caused by: java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: net.minecraft.LauncherFrame. Program will exit.

will u help me?

---

### Post by Dlambert on 2012-06-19
> **thewildspace said:**
> i tried what u said and i got this error message

Exception in thread "main" java.lang.NoClassDefFoundError: net/minecraft/LauncherFrame
Caused by: java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: net.minecraft.LauncherFrame. Program will exit.

will u help me?


This is how I run my minecraft with 8gigs of RAM: ```
java -Xmx8192M -Xms4096M -cp /home/dlambert/Downloads/minecraft.jar net.minecraft.LauncherFrame
```
Try minecraft.jar I had a problem with the case sensitive Minecraft.jar

---

