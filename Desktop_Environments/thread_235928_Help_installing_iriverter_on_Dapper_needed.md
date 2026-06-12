---
title: "Help installing iriverter on Dapper needed"
date: 2006-08-13
forum: Desktop Environments
---

### Post by beowulf62381 on 2006-08-13
I can not seem to get [iriverter]("http://sourceforge.net/projects/iriverter/") installed on my dapper system. I'm asking for a complete walk-through (I need to install it for a friend as well as my self) if any one has the time. I saw a how to for breezy but it did not work for me. I keep keep getting and error when i issue the make command and I'm not sure i have the needed dependencies.

Thank you in advance.


Making all in src
make[1]: Entering directory `/home/my_home/work/iriverter-0.16/src'
Making all in doc
make[2]: Entering directory `/home/my_home/work/iriverter-0.16/src/doc'
Making all in html
make[3]: Entering directory `/home/my_home/work/iriverter-0.16/src/doc/html'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/my_home/work/iriverter-0.16/src/doc/html'
Making all in images
make[3]: Entering directory `/home/my_home/work/iriverter-0.16/src/doc/images'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/my_home/work/iriverter-0.16/src/doc/images'
make[3]: Entering directory `/home/my_home/work/iriverter-0.16/src/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/my_home/work/iriverter-0.16/src/doc'
make[2]: Leaving directory `/home/my_home/work/iriverter-0.16/src/doc'
Making all in profiles
make[2]: Entering directory `/home/my_home/work/iriverter-0.16/src/profiles'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/my_home/work/iriverter-0.16/src/profiles'
Making all in launcher
make[2]: Entering directory `/home/my_home/work/iriverter-0.16/src/launcher'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/my_home/work/iriverter-0.16/src/launcher'
make[2]: Entering directory `/home/my_home/work/iriverter-0.16/src'
gcj -C -classpath /usr/lib/jni:. org/thestaticvoid/iriverter/Logger.java
make[2]: gcj: Command not found
make[2]: *** [org/thestaticvoid/iriverter/Logger.class] Error 127
make[2]: Leaving directory `/home/my_home/work/iriverter-0.16/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/my_home/work/iriverter-0.16/src'
make: *** [all-recursive] Error 1

---

### Post by hayesey on 2006-08-14
looks like you need to install gcj (GNU Java Compiler).

```
apt-get install gcj
```

---

### Post by tehwa on 2006-08-28
Take a look at the iriver H340 page on the ubuntu wiki:

[https://wiki.ubuntu.com/iRiverH340](https://wiki.ubuntu.com/iRiverH340)

---

### Post by beowulf62381 on 2006-09-12
thank you for the wiki entry I had to do it on a ppc not a x86 system but it seemed mostly the same. Since I'm on ppc i use ibm-java instead of sun-java.

any way that said iriverter compiled fine, but when i try to run it i get

JVM not found: libjvm.so  - libjvm.so

I searched my system and found the file here '/usr/lib/j2sdk1.5-ibm/jre/bin/j9vm' and here '/usr/lib/j2sdk1.5-ibm/jre/bin/j9vm'

douse any one happen to know what file needs to be modified to tell iriverter where to find libjvm.so

thanks for all your help

---

### Post by nikhilk on 2006-09-12
You can create a symlink to the libjvm.so file in /usr/lib.

cd /usr/lib
sudo ln -s /usr/lib/j2sdk1.5-ibm/jre/bin/j9vm/libjvm.so libjvm.so

---

### Post by ftmichael on 2007-03-05
I'm using Edgy and attempting to install iRiverter.

I followed the directions at [https://help.ubuntu.com/community/AudioPlayeriRiverH340](https://help.ubuntu.com/community/AudioPlayeriRiverH340) , which worked fine until I had to execute:

> ./configure --with-swt=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext/swt.jar

It says I should be in the iRiverter directory, which I assume is ~/swt .  I get this:

> michael@jeezychreezy:~/swt$ ./configure --with-swt=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext/swt.jar
bash: ./configure: No such file or directory
michael@jeezychreezy:~/swt$ 

Where the hell is the configure file?  Am I the only one with this issue?  What's up?

The contents of ~/swt:

> michael@jeezychreezy:~/swt$ ls
**about_files**
about.html
libcairo.so.1
libswt-atk-gtk-3138.so
libswt-awt-gtk-3138.so    
libswt-cairo-gtk-3138.so  
libswt-gnome-gtk-3138.so  
libswt-gtk-3138.so        
libswt-mozilla-gtk-3138.so
libswt-pi-gtk-3138.so
src.zip
swt.jar
michael@jeezychreezy:~/swt$ 

Neither src.zip nor swt.jar appears to contain any file called configure.

Michael

---

### Post by tehwa on 2007-03-06
The "Iriverter directory" should be the directory that you extracted the iriverter-[version].tar.bz archive to, such as '/home/tehwa/src/iriverter-0.16'. You will find a configure file in here.

---

### Post by ftmichael on 2007-03-06
Got it; thanks!

Now that it's installed and running, can I delete the **~/src** and **~/swt** directories and all their contents?  They only hold stuff for iRiverter.

Michael

---

