---
title: "Minecraft"
date: 2014-09-17
forum: Gaming &amp; Leisure
---

### Post by bram6 on 2014-09-17
Hey there peeps!

I recently bought a chromebook. Its a samsung series 3 ARM device. I used Crouton to install Ubuntu Unity on it. I wanted to play minecraft, sO I installed Java etc. So far so good. Well, I opened minecraft, and after clicking Download & Play this is what I got:

[spoiler]
```

OpenJDK Zero VM warning: You have loaded library /home/bram/.minecraft/versions/1.8/1.8-natives-6572278949840/liblwjgl64.so which might have disabled stack guard. The VM will try to fix the stack guard now.
It's highly recommended that you fix the library with 'execstack -c <libfile>', or link it with '-z noexecstack'.
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/bram/.minecraft/versions/1.8/1.8-natives-6572278949840/liblwjgl.so: /home/bram/.minecraft/versions/1.8/1.8-natives-6572278949840/liblwjgl.so: cannot open shared object file: No such file or directory (Possible cause: can't load IA 32-bit .so on a ARM-bit platform)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary1(ClassLoader.java:1965)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1890)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1880)
	at java.lang.Runtime.loadLibrary0(Runtime.java:849)
	at java.lang.System.loadLibrary(System.java:1088)
	at org.lwjgl.Sys$1.run(Sys.java:73)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.Sys.doLoadLibrary(Sys.java:66)
	at org.lwjgl.Sys.loadLibrary(Sys.java:95)
	at org.lwjgl.Sys.<clinit>(Sys.java:112)
	at bsu.I(SourceFile:2462)
	at net.minecraft.client.main.Main.main(SourceFile:40)

```
[/spoiler]

Im not sure, but when I go into my "home folder" all I see is " Desktop and Downloads. If I go up a map theres the map bram. I couldnt find bram/.minecraft. Could someone tell me how to fix this? Also I cant make new "maps" next to Downlaods and Desktop. I could use an external SD card if my laptop doesnt support mapping, but then I must know how to change the minecraft directory :/ could someone explain me how I could do that?

Regards, Bram.

ps; Sorry for my bad English, my main language is Dutch  and I'm only 12 years old.

---

### Post by bram6 on 2014-09-17
A better question is: How do I change mc's desitnation folder? I've inserted an SD card, so I'd like to make the .minecraft folder there. Does someone know how to do that?

---

### Post by CatKiller on 2014-09-17
Files and directories that start with a . are hidden by default. Ctrl-H will show them.

---

### Post by bram6 on 2014-09-18
> **CatKiller said:**
> Files and directories that start with a . are hidden by default. Ctrl-H will show them. Thanks, but still I can't run mc...

---

### Post by mcduck on 2014-09-18
I'd make and educated guess that since ARM (apart from Rasberry Pi) isn't an officially supported platform, Minecraft doesn't come with ARM versions of the LWJGL library. You *might* get things working if you manage to find ARM versions of the files yourself, and replace the ones in minecraft's folder with them...

```
liblwjgl.so: cannot open shared object file: No such file or directory (Possible cause: can't load IA 32-bit .so on a ARM-bit platform)
```
The error is pretty much telling you that it can't load a 32-bit x86 file because you are running on ARM)

---

