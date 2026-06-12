---
title: "Minecraft 1.9 pre-release"
date: 2011-10-22
forum: Gaming &amp; Leisure
---

### Post by pengyou on 2011-10-22
So I went and found that minecraft 1.9 prerelease.
And I run the good 'ol
> java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFramein the same directory where I have minecraft.jar saved.
And what do I get?
Well:
> 
~/Downloads$ java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
Exception in thread "main" java.lang.NoClassDefFoundError: net/minecraft/LauncherFrame
Caused by: java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: net.minecraft.LauncherFrame. Program will exit.
What does this mean!?
I have googled up and down the tubes and have only found people with my issue, [sometimes] with responses like
> 
-have ya tried uncapsing the 'm'?
-omigod! it worked! thankyousomuch!
And I've been fairly careful with my capses as a result.
But nothing.
The 1.8 version works fine.
It's the prerelease that's getting messed up.
Inspection of the contents of the 1.9 .jar file in comparison to the 1.8 release reveals they are pretty different...
I remember when the 1.8 prerelease came out, I had the same problem, and had to wait until official 1.8...
I feel I've ruled out a bad download as well, as I've tried multiple sources...
so wat do?

---

### Post by proteusmoteus on 2011-10-26
There are two minecraft.jar files with minecraft. The pre-release minecraft.jar is the game itself and needs to be placed in ~/.minecraft/bin

The second minecraft.jar is the **launcher file that is downloaded from minecraft.net**.  I keep mine in ~/bin, but it really doesnt matter where you place it.

Trying to launch the game minecraft.jar fails in the manner you posted. Launch your launcher yo

---

