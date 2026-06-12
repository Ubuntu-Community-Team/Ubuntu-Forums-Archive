---
title: "Minecraft, exception in Java"
date: 2015-01-09
forum: Gaming &amp; Leisure
---

### Post by 77_GCSX on 2015-01-09
So I have Minecraft installed and working with the new launcher. Every version from 1.6.2 and up works. However, I had a 1.2.5 Minecraft game set up on the old MS Vista OS using the older Magic Launcher. 

On Ubuntu 14.04 I have set up Minecraft in it's own folder, complete with it's own .minecraft folder. I just copied the files over from the Vista set up to the Ubuntu one and then followed the link I listed below the error listing.

For the life of me I cannot get past the error(s) listed below:

First - I start Magic Launcher:

MagicLauncher 1.2.6
java.home: /usr/lib/jvm/java-7-openjdk-amd64/jre
java.runtime.name: OpenJDK Runtime Environment
java.runtime.version: 1.7.0_65-b32
os.name: Linux
os.version: 3.13.0-43-generic
os.arch: amd64
sun.arch.data.model: 64

OK, everything looks good. I then try to start it and THIS happens:

*** Starting Minecraft ***
Profile: Default
Environment: Classic
Minecraft version: (modified!) 1.2.5
Minecraft.jar: minecraft.jar
Base folder: /home/paul1/Minecraft/MC_1.2.5/.minecraft
Show log: true
Java path: /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java
Memory: 512 MB
LauncherPath: /home/paul1/Desktop/MagicLauncher_1.2.6.jar
Main class: net.minecraft.client.Minecraft
*** MagicMinecraftLauncher 1.2.6 ***
  LCP: ;bin/jinput.jar;bin/lwjgl.jar;bin/lwjgl_util.jar;/home/paul1/Minecraft/MC_1.2.5/.minecraft/bin/minecraft.jar
  ShowLog: true
  McVersion: (modified!) 1.2.5
  MainClass: net.minecraft.client.Minecraft
Restoring disabled mods: mods
Restoring disabled mods: mods/(modified!) 1.2.5
Disable inactive mods: mods
Restoring disabled mods: coremods
Restoring disabled mods: coremods/(modified!) 1.2.5
Disable inactive mods: coremods
27 achievements
182 recipes
*** Main class main() finished ***
[COLOR=#ff0000]Exception in thread "Minecraft main thread" java.lang.UnsatisfiedLinkError: no lwjgl in java.library.path[/COLOR]
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1886)
    at java.lang.Runtime.loadLibrary0(Runtime.java:849)
    at java.lang.System.loadLibrary(System.java:1088)
    at org.lwjgl.Sys$1.run(Sys.java:73)
    at java.security.AccessController.doPrivileged(Native Method)
    at org.lwjgl.Sys.doLoadLibrary(Sys.java:66)
    at org.lwjgl.Sys.loadLibrary(Sys.java:95)
    at org.lwjgl.Sys.<clinit>(Sys.java:112)
    at org.lwjgl.opengl.Display.<clinit>(Display.java:135)
    at net.minecraft.client.Minecraft.a(Minecraft.java:330)
    at net.minecraft.client.Minecraft.run(Minecraft.java:738)
    at java.lang.Thread.run(Thread.java:745)

I searched and found this thread:

[http://askubuntu.com/questions/225432/how-to-install-minecraft-client](http://askubuntu.com/questions/225432/how-to-install-minecraft-client)

I did the overwriting of the folders listed but no change in the error.

Any and all help is GREATLY appreciated!!

Paul

---

### Post by efflandt on 2015-01-10
That link [http://askubuntu.com/questions/22543...necraft-client]("http://askubuntu.com/questions/225432/how-to-install-minecraft-client") is a rather convoluted way to install minecraft in wine when it can easily run natively in Linux if you have any openjdk-jre installed (some mods might need version 7 instead of 6). The minecraft launcher can be set up with different profiles for different minecraft versions, keeping everything in ~/.minecraft. Launching the launcher is as simple as **java -jar path_to/Minecraft.jar** in a terminal or I set up a desktop launcher that does **sh -c 'java -jar ~/Downloads/Minecraft.jar'** However, that is only for vanilla minecraft without mods.

I am not familiar with MagicLauncher though. I use the technic launcher (which keeps separate minecraft things in its own directory) for specific mod packs like tekkit, or MultiMC for different or additional mods.

It appears that for some reason this version of yours cannot find lwjgl. What is in your /home/paul1/Minecraft/MC_1.2.5/.minecraft/bin/ which is where it should be looking for jinput.jar, lwjgl.jar, and lwjgl_util.jar and probably also a natives/ directory under that.```
efflandt@XPS-8100-1404:~$ ls .minecraft/bin/natives
libjinput-linux64.so  liblwjgl64.so  libopenal64.so
libjinput-linux.so    liblwjgl.so    libopenal.so
```

Some of the old minecraft versions included an old lwjgl version 2.4.2 which did not always properly detect key down/key up events (stuck keys) which should work fine if those files were replaced with ones from lwjgl 2.6 or newer.

---

### Post by 77_GCSX on 2015-01-10
Since I posted I have been working on using the new launcher and "trying" to find similar mods to get the same 'type' of game play I had with ver. 1.2.5. So far it's not going to bad. The ONLY mod, so far, I cannot use (at least not yet) is the older 'Laser Mod". I have used the newer one but it doesn't burn through solid objects like dirt, granite, stone, etc... I use to like to make tunnels with a laser wall and or other weird a** laser configurations. 

I DID have a thought that I have yet to try: Taking the old 1.2.5 jar that worked in Vista and making a new profile with the new launcher and pointing it to the modded jar. I'll see if this works tomorrow. 

So far I have 1.5.2 w/ Forge working with about 3 mods so far. 

I'll be in touch if I find anything out.

Thanks!:D

---

### Post by 77_GCSX on 2015-01-28
I figured this out - It was the java libs in the folders that needed updated, or should I say 'downgraded'. I used 2.8.0 files and all is well. Thanks!

---

