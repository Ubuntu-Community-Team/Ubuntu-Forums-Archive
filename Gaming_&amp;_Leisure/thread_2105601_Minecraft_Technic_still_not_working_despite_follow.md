---
title: "Minecraft Technic still not working despite following Fix's instructions?"
date: 2013-01-16
forum: Gaming &amp; Leisure
---

### Post by Jamie_Edwards on 2013-01-16
Hi guys,

Ok, so I've been using minecraft for a little over two month's and initially had problems with it in Ubuntu ( the fact that the lwjgl it's shipped with is out of date ) but after some research, I managed to sort that out and am happily playing it without a hitch.

Then a friend of mine mentioned Technic so I downloaded the launcher and tried it, and low and behold, same problem with Minecraft... The grey screen freeze. I researched how I could fix it and I found a the same method as the one used in Minecraft, So I tried it, launched the launcher and then Technic SSP, but instead of carrying on it froze... again.

So here I am asking for your help. How can I play Technic on my machine? Here are the details:

Ubuntu 12.04 64-bit,
Gnome Shell Desktop Environment ( don't know if this would help? )
OpenJDK Java 6 and 7
Oracle Java 7.

Hope you guys can help me get this running as I've heard a lot about Technic.

Thanks.

Jamie.

---

### Post by Jamie_Edwards on 2013-01-16
Anyone? :L

---

### Post by holastickboy on 2013-01-16
Have you, by any chance, given the Feed The Beast modpack a try? It's very similar to Technic/Tekkit, but uses a more modern version of Minecraft as a base (1.4.2 currently).

Small write-up on it:
[http://lanpartymania.com/?p=452](http://lanpartymania.com/?p=452)

---

### Post by Jamie_Edwards on 2013-01-17
> **holastickboy said:**
> Have you, by any chance, given the Feed The Beast modpack a try? It's very similar to Technic/Tekkit, but uses a more modern version of Minecraft as a base (1.4.2 currently).

Small write-up on it:
[http://lanpartymania.com/?p=452](http://lanpartymania.com/?p=452)

Thanks for getting back to me. I did have a look at the link and downloaded the .jar file but whilst trying to get it to launch I get the following errors from the console:

```


2013-01-17 18:53:51 [INFO] [STDERR] java.lang.reflect.InvocationTargetException 
2013-01-17 18:53:51 [INFO] [STDERR] at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) 
2013-01-17 18:53:51 [INFO] [STDERR] at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57) 
2013-01-17 18:53:51 [INFO] [STDERR] at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43) 
2013-01-17 18:53:51 [INFO] [STDERR] at java.lang.reflect.Method.invoke(Method.java:601) 
2013-01-17 18:53:51 [INFO] [STDERR] at cpw.mods.fml.relauncher.FMLRelauncher.relaunchApplet(FMLRelauncher.java:230) 
2013-01-17 18:53:51 [INFO] [STDERR] at cpw.mods.fml.relauncher.FMLRelauncher.appletEntry(FMLRelauncher.java:212) 
2013-01-17 18:53:51 [INFO] [STDERR] at net.minecraft.client.MinecraftApplet.init(MinecraftApplet.java:25) 
2013-01-17 18:53:51 [INFO] [STDERR] at net.minecraft.Launcher.replace(Launcher.java:50) 
2013-01-17 18:53:51 [INFO] [STDERR] at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) 
2013-01-17 18:53:51 [INFO] [STDERR] at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57) 
2013-01-17 18:53:51 [INFO] [STDERR] at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43) 
2013-01-17 18:53:51 [INFO] [STDERR] at java.lang.reflect.Method.invoke(Method.java:601) 
2013-01-17 18:53:51 [INFO] [STDERR] at cpw.mods.fml.relauncher.FMLRelauncher.relaunchApplet(FMLRelauncher.java:259) 
2013-01-17 18:53:51 [INFO] [STDERR] at cpw.mods.fml.relauncher.FMLRelauncher.appletEntry(FMLRelauncher.java:212) 
2013-01-17 18:53:51 [INFO] [STDERR] at net.minecraft.client.MinecraftApplet.init(MinecraftApplet.java:25) 
2013-01-17 18:53:51 [INFO] [STDERR] at net.minecraft.Launcher.init(Launcher.java:84) 
2013-01-17 18:53:51 [INFO] [STDERR] at net.ftb.mclauncher.MinecraftFrame.start(MinecraftFrame.java:117) 
2013-01-17 18:53:51 [INFO] [STDERR] at net.ftb.mclauncher.MinecraftLauncher.main(MinecraftLauncher.java:212) 
2013-01-17 18:53:51 [INFO] [STDERR] Caused by: java.lang.UnsatisfiedLinkError: /home/jamie/Direwolf20/minecraft/bin/natives/liblwjgl.so: /home/jamie/Direwolf20/minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch) 
2013-01-17 18:53:51 [INFO] [STDERR] at java.lang.ClassLoader$NativeLibrary.load(Native Method) 
2013-01-17 18:53:51 [INFO] [STDERR] at java.lang.ClassLoader.loadLibrary1(ClassLoader.java:1939) 
2013-01-17 18:53:51 [INFO] [STDERR] at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1864) 
2013-01-17 18:53:51 [INFO] [STDERR] at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1825) 
2013-01-17 18:53:51 [INFO] [STDERR] at java.lang.Runtime.load0(Runtime.java:792) 
2013-01-17 18:53:51 [INFO] [STDERR] at java.lang.System.load(System.java:1059) 
2013-01-17 18:53:51 [INFO] [STDERR] at org.lwjgl.Sys$1.run(Sys.java:69) 
2013-01-17 18:53:51 [INFO] [STDERR] at java.security.AccessController.doPrivileged(Native Method) 
2013-01-17 18:53:51 [INFO] [STDERR] at org.lwjgl.Sys.doLoadLibrary(Sys.java:65) 
2013-01-17 18:53:51 [INFO] [STDERR] at org.lwjgl.Sys.loadLibrary(Sys.java:81) 
2013-01-17 18:53:51 [INFO] [STDERR] at org.lwjgl.Sys.<clinit>(Sys.java:98) 
2013-01-17 18:53:51 [INFO] [STDERR] at net.minecraft.client.Minecraft.F(Minecraft.java:2556) 
2013-01-17 18:53:51 [INFO] [STDERR] at asz.<init>(SourceFile:20) 
2013-01-17 18:53:51 [INFO] [STDERR] at net.minecraft.client.Minecraft.<init>(Minecraft.java:154) 
2013-01-17 18:53:51 [INFO] [STDERR] at asq.<init>(SourceFile:38) 
2013-01-17 18:53:51 [INFO] [STDERR] at net.minecraft.client.MinecraftApplet.fmlInitReentry(MinecraftApplet.java:32) 
2013-01-17 18:53:51 [INFO] [STDERR] ... 18 more 


```

Any idea's?

---

### Post by holastickboy on 2013-01-17
Hmm... weird.    As far as I know with the Oracle Java 7 installation, you're supposed to remove the OpenJDK first. Perhaps it's running with the wrong java environment? I find if I right click the applet, I can select what loads it. Try that?

---

### Post by Jamie_Edwards on 2013-01-17
> **holastickboy said:**
> Hmm... weird.    As far as I know with the Oracle Java 7 installation, you're supposed to remove the OpenJDK first. Perhaps it's running with the wrong java environment? I find if I right click the applet, I can select what loads it. Try that?

Nope, same outcome.

I tried OpenJDK Java 6 then 7.

Although, I did find two logs in my home directory. One being "FTBLauncherLog.txt" and the other being "MinecraftLog.txt".

When looking in the first log there are no errors ( suggesting that it isn't FTB with the problem )

But looking in the second, I find the log errors which means it's a problem with my Minecraft file?

---

### Post by Jamie_Edwards on 2013-01-18
any ideas on what could be causing it if the java version isn't the cause?

---

