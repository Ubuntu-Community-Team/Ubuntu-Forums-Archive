---
title: "Minecraft, Ubuntu 12.04, Intel Atom D2500, does not start. Help!"
date: 2013-12-25
forum: Gaming &amp; Leisure
---

### Post by Timo12357 on 2013-12-25
Hello,

my son got a Intel D2500 based netbook as a Christmas present. I installed Ubuntu 12.04 lts on it and it runs fine.
However, Minecraft does not work in this setup. It crashes at startup. 

Error logs can be found at [http://pastebin.com/XBbutbW8](http://pastebin.com/XBbutbW8)

Please help!

Timo

---

### Post by Jonathan Precise on 2013-12-25
Try:
```
ulimit -c unlimited
```
Then run it again and send us the error log. (This serves to have extra debugging info.)

Can you also try it on the latest ubuntu (13.10)?

---

### Post by LinuxCharms on 2013-12-25
You can also run Minecraft with this command:

```
java -jar <path-to-file>
```

That's how I've always installed and run mine.

---

### Post by Bucky Ball on 2013-12-25
*Thread moved to **Gaming & Leisure**.*

---

### Post by Timo12357 on 2013-12-26
I installed 13.10, but that is no good, it is too slow to be usable at all. Reinstalled 12.04 LTS and am writing this on it. 
Tried ulimit -c unlimited, see [http://pastebin.com/qqdzkheP](http://pastebin.com/qqdzkheP) and [http://pastebin.com/qu65zfXK](http://pastebin.com/qu65zfXK) for results.

---

### Post by Timo12357 on 2013-12-26
Same behavior if I try to start the Minecraft.exe using wine.

---

### Post by Timo12357 on 2013-12-26
Could this have something to do with the gma3600 display driver?

---

### Post by Jonathan Precise on 2013-12-28
Try updating your java version to the one in [java.com](java.com). You can see [How to install Java from easy linux tips project]("https://sites.google.com/site/easylinuxtipsproject/java").

---

### Post by ueli-ton on 2013-12-29
**If the problem is black screen in minecraft, this should do it:**
[B]
Some files can is outdated in /.minecraft/, start replacing; libopenal.so, liblwjgl.so, libjinput-linux.so[/B]

```
cd ~; cd .minecraft; cd bin; cd natives; rm libopenal.so; rm liblwjgl.so; rm libjinput-linux.so && wget -c https://f062ab90-a-62cb3a1a-s-sites.googlegroups.com/site/myubuntustudio/libopenal.so; wget -c https://f062ab90-a-62cb3a1a-s-sites.googlegroups.com/site/myubuntustudio/liblwjgl.so; wget -c https://f062ab90-a-62cb3a1a-s-sites.googlegroups.com/site/myubuntustudio/libjinput-linux.so
```

**now; libopenal.so64, liblwjgl.so64, libjinput-linux.so64**

```
cd ~; cd .minecraft; cd bin; cd natives; rm libopenal64.so; rm liblwjgl64.so; rm libjinput-linux64.so && wget -c https://f062ab90-a-62cb3a1a-s-sites.googlegroups.com/site/myubuntustudio/libopenal64.so; wget -c https://f062ab90-a-62cb3a1a-s-sites.googlegroups.com/site/myubuntustudio/liblwjgl64.so; wget -c https://f062ab90-a-62cb3a1a-s-sites.googlegroups.com/site/myubuntustudio/libjinput-linux64.so
```

**Update some libraries: scala-library.jar and bcprov-jdk15on-148.jar**

```
cd ~; cd .minecraft; mkdir lib; cd lib && rm scala-library.jar; rm bcprov-jdk15on-148.jar && wget -c https://f062ab90-a-62cb3a1a-s-sites.googlegroups.com/site/myubuntustudio/scala-library.jar; wget -c https://f062ab90-a-62cb3a1a-s-sites.googlegroups.com/site/myubuntustudio/bcprov-jdk15on-148.jar
```

**Update a few more files: jinput.jar, lwjgl.jar and lwjgl_util.jar**

```
cd ~; cd .minecraft; cd bin; rm jinput.jar; rm lwjgl.jar; rm lwjgl_util.jar && wget -c https://f062ab90-a-62cb3a1a-s-sites.googlegroups.com/site/myubuntustudio/jinput.jar; wget -c https://f062ab90-a-62cb3a1a-s-sites.googlegroups.com/site/myubuntustudio/lwjgl.jar; wget -c https://f062ab90-a-62cb3a1a-s-sites.googlegroups.com/site/myubuntustudio/lwjgl_util.jar
```

**Now start minecraft:**

```
c ~; java -jar minecraft.jar
```
[I]Do not use this command if you renamed the jar file.

[/I][source: http://www.vivaolinux.com.br/topico/Emulacao-de-jogos/MinecraftSPjar-no-Ubuntu-pra-servidores-nao-oficiaisPirata]("http://www.vivaolinux.com.br/topico/Emulacao-de-jogos/MinecraftSPjar-no-Ubuntu-pra-servidores-nao-oficiaisPirata")

---

