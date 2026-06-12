---
title: "Forge minecraft 1.12.2"
date: 2019-02-02
forum: Gaming &amp; Leisure
---

### Post by jojodi974 on 2019-02-02
[COLOR=#000000][FONT=Arial]Hello I'm using ubuntu 18.04 and i would like to install forge on my minecraft launcher. I've already downloaded and install the last version of forge but when I launch minecraft there's a message error :
[/FONT][/COLOR]
OpenJDK 64-Bit Server VM warning: Option UseConcMarkSweepGC was deprecated in version 9.0 and will likely be removed in a future release.
Unrecognized VM option 'CMSIncrementalMode'
Error: Could not create the Java Virtual Machine.
Error: A fatal exception has occurred. Program will exit.

[COLOR=#000000][FONT=Arial]After deleting "CMSIncrementalMode" in "JVM arguments", I launch a second time and I have a new message error :

[/FONT][/COLOR]OpenJDK 64-Bit Server VM warning: Option UseConcMarkSweepGC was deprecated in version 9.0 and will likely be removed in a future release.
Exception in thread "main" java.lang.ClassCastException: java.base/jdk.internal.loader.ClassLoaders$AppClassLoader cannot be cast to java.base/java.net.URLClassLoader
    at net.minecraft.launchwrapper.Launch.<init>(Launch.java:34)
    at net.minecraft.launchwrapper.Launch.main(Launch.java:28)

[COLOR=#000000][FONT=Arial]Could you help me ? Sorry if my english is approximate. Thanks.[/FONT][/COLOR]

---

### Post by CatKiller on 2019-02-02
Minecraft (and especially mods) really wants Java 8, and the one from Oracle in particular. There is a PPA that has it.

---

### Post by jojodi974 on 2019-02-03
Thanks it works, I love you so much ! Have a nice day !

---

### Post by oldrocker99 on 2019-02-03
> **CatKiller said:**
> Minecraft (and especially mods) really wants Java 8, and the one from Oracle in particular. There is a PPA that has it.

And here it is: [https://launchpad.net/~webupd8team/+archive/ubuntu/java](https://launchpad.net/~webupd8team/+archive/ubuntu/java)

---

### Post by wildmanne39 on 2019-02-03
Glad it worked, please use thread tools at the top of the page to mark the thread solved.

Thanks

---

### Post by yaboyneedhelp on 2019-05-11
I'm Having the same problem and i already downloaded java jre 8 form oracle like as what i saw on another post plz respond

---

