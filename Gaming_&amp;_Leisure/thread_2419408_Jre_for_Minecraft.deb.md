---
title: "Jre for Minecraft.deb"
date: 2019-05-21
forum: Gaming &amp; Leisure
---

### Post by zohaiblaghari on 2019-05-21
Hi guys,
I am trying to install minecraft in my ubuntu 18 more specifically Xubuntu 18.10 x64.
the first thing i did was installing the version of jre 1.8.0 manually by copying the files into /usr/bin and /usr/lib. after doing that i run a rimple ```
java -version
``` and it says ```
Java(TM) SE Runtime Environment (build 1.8.0_211-b12) 
``` which means i did everything correctly.
now here is the part the error comes. when i run ```
sudo dpkg -i minecraft.deb
``` it gives me this output :
```

dpkg: dependency problems prevent configuration of minecraft-launcher: minecraft-launcher depends on oracle-java8-installer | openjdk-8-jre; however:
  Package oracle-java8-installer is not installed.
  Package openjdk-8-jre is not installed.
 minecraft-launcher depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not installed.



```
can someone tell me why the java dependency is missing, when i already did it. is java8 same as jre 1.8.0 ? should i install it and will get good performance ?
Please someone help me out. i am new :)

---

### Post by zohaiblaghari on 2019-05-21
i installed x86 java for x64 release.. sorry . my bad

---

