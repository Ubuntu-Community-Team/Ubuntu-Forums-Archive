---
title: "Java working on browsers only"
date: 2013-08-29
forum: Gaming &amp; Leisure
---

### Post by 700 on 2013-08-29
Conditions:
- System: Ubuntu 12.04 / amd64
- Chromium, Chrome, Firefox ([http://java.com/en/download/testjava.jsp](http://java.com/en/download/testjava.jsp)) - JAVA IS working there, but...
- Minecraft, Cheese, WebcamStudio - JAVA is NOT working
> ~$ java -version
java version "1.7.0_25"
Java(TM) SE Runtime Environment (build 1.7.0_25-b15)
Java HotSpot(TM) 64-Bit Server VM (build 23.25-b01, mixed mode)

How to make JAVA working where it's not working (and keep it working on browsers as well)?

---

### Post by QIII on 2013-08-29
Hello!

Could you start Minecraft from the terminal and post back any messages?

---

### Post by 700 on 2013-08-29
Hello,

~$ java -jar minecraft.jar
> Exception in thread "Thread-3" java.lang.UnsatisfiedLinkError: /home/user/.minecraft/bin/natives/liblwjgl.so: /home/user/.minecraft/bin/natives/liblwjgl.so: wrong class ELF: ELFCLASS32 (Possible cause: architecture word width mismatch)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary1(ClassLoader.java:1957)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1882)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1843)
    at java.lang.Runtime.load0(Runtime.java:795)
    at java.lang.System.load(System.java:1061)
    at org.lwjgl.Sys$1.run(Sys.java:69)
    at java.security.AccessController.doPrivileged(Native Method)
    at org.lwjgl.Sys.doLoadLibrary(Sys.java:65)
    at org.lwjgl.Sys.loadLibrary(Sys.java:81)
    at org.lwjgl.Sys.<clinit>(Sys.java:98)
    at net.minecraft.client.Minecraft.G(SourceFile:1985)
    at awe.<init>(SourceFile:20)
    at net.minecraft.client.Minecraft.<init>(SourceFile:76)
    at avv.<init>(SourceFile:38)
    at net.minecraft.client.MinecraftApplet.init(SourceFile:38)
    at net.minecraft.Launcher.replace(Launcher.java:134)
    at net.minecraft.Launcher$1.run(Launcher.java:78)
Effect:
- black screen after logging in to Minecraft.

---

### Post by QIII on 2013-08-30
How did you install Oracle Java?

---

### Post by 700 on 2013-08-31
> **QIII said:**
> How did you install Oracle Java?
I think it was something like below:
> ~$ sudo apt-get update
~$ sudo apt-get install oracle-java7-installer
~$ sudo apt-get install oracle-java7-set-default

---

### Post by QIII on 2013-08-31
Was it from webupd8.org's PPA?

---

### Post by 700 on 2013-08-31
Yes, it was probably webupd8.org and also:
[http://www.java.com/en/download/help/linux_x64_install.xml](http://www.java.com/en/download/help/linux_x64_install.xml)

---

### Post by 700 on 2013-09-12
Other hints for "not working" from Cheese:
> Cheese crashed with SIGSEGV in cheese_camera_setup()
> (cheese:12250):  Gtk-WARNING **: Attempting to add a widget with type GtkImage to a  GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only  contain one widget at a time; it already contains a widget of type  GtkLabel

---

### Post by DarkAmbient on 2013-09-12
you could try a ppa-purge, then install openjdk-7-jre instead.

I followed this guide last time I did this, humoristic enough from webupd8.

[http://www.webupd8.org/2012/11/install-ppa-purge-with-multi-arch.html](http://www.webupd8.org/2012/11/install-ppa-purge-with-multi-arch.html)

---

### Post by 700 on 2013-09-21
> **DarkAmbient said:**
> ... install openjdk-7-jre instead.
... tried...

> **DarkAmbient said:**
> [http://www.webupd8.org/2012/11/install-ppa-purge-with-multi-arch.html](http://www.webupd8.org/2012/11/install-ppa-purge-with-multi-arch.html)
... tried...

... still not working :(

---

### Post by 700 on 2013-10-10
There are like 2233 Java packets available through Synaptic Package Manager.
Could anyone of them fix my problem? Maybe I'm missing something from this list, but how to find out which one?

---

### Post by HikariKnight on 2013-10-30
it is complaining about that the libjwgl is 32bit and i am suspecting you are on 64bit
if that is the case then you can
1. install ia32-libs, openjdk-7-jre:i386 and openjdk-7-jre-headless:i386
or
2. rename the bin folder inside $HOME/.minecraft (renaming it so incase it doesnt work you can just rename it back and use option 1 which should work anyway)

also another issue with java7 (and openjdk7) is that java cant find libjawt.so
so you have to run java with LD_LIBRARY_PATH=/usr/lib/jvm/"javafolder that is used"/jre/lib/"amd64 for option 2 and i386 for option 1"/ java

or ofcourse we can go the automatic route and install the wrapper i wrote for java to fix an issue for those that played runescape through the browser and wanted opengl to work but refused to use a client.

perl source:
[https://dl.dropbox.com/u/11631899/opensource/Perl/java-wrapper/java-wrapper](https://dl.dropbox.com/u/11631899/opensource/Perl/java-wrapper/java-wrapper)

tar.gz download:
[https://dl.dropbox.com/u/11631899/opensource/Perl/java-wrapper/java-wrapper.tar.gz](https://dl.dropbox.com/u/11631899/opensource/Perl/java-wrapper/java-wrapper.tar.gz)

usage:
```
sudo ./java-wrapper -install
```
it will then look through your system for all java installs and give you a list of them, you then enter the number for the one you want the wrapper to install inside which will make it rename the java binary to "java-bin" and then make itself take the "java" executables place and forward calls to java-bin with the correct LD_LIBRARY_PATH which it will automatically locate.

if you want to configure overrides for parameters you can do that through $HOME/.config/java-wrapper/overrides.pm
here is the default one it creates on first run
```
package overrides;

# This is a collection of programmable overrides for the java parameters
# _if_overridename is set to(=>) "value",
# _set_overridename set it to(=>) "value",


# NOTE: you can add any if statements if you follow the method above!
$overrides = {
	_if_maxmem => "-Xmx256m",
	_set_maxmem => "-Xmx512m",
	_if_stacksize => "-Xss1m",
	_set_stacksize => "-Xss2m",
};
## END OF OVERRIDES


#
#---------------------------------------- *** ----------------------------------------
#


# Callback, DO NOT TOUCH!
sub get_overrides
{
	return $overrides;
}
1;

```

---

### Post by 700 on 2013-10-30
> **HikariKnight said:**
> it is complaining about that the libjwgl is 32bit and i am suspecting you are on 64bit
if that is the case then you can
1. install ia32-libs, openjdk-7-jre:i386 and openjdk-7-jre-headless:i386

1. DONE (before)

> **HikariKnight said:**
> 2. rename the bin folder inside $HOME/.minecraft (renaming it so incase it doesnt work you can just rename it back and use option 1 which should work anyway)

also another issue with java7 (and openjdk7) is that java cant find libjawt.so
so you have to run java with LD_LIBRARY_PATH=/usr/lib/jvm/"javafolder that is used"/jre/lib/"amd64 for option 2 and i386 for option 1"/ java

It stops here with a message:
> ~$ java LD_LIBRARY_PATH=/usr/lib/jvm
Error: Could not find or load main class LD_LIBRARY_PATH=.usr.lib.jvm

---

### Post by 700 on 2013-11-01
How to get rid of all Java versions from Ubuntu (+ ensure that it's all out) and reinstall it correctly to get everything working as it should? 
Could I get step-by-step assistance, please?

---

### Post by HikariKnight on 2013-11-05
no you run it wrong, you need to have the LD_LIBRARY_PATH=/usr/lib/jvm/"java_youre_using_here"/lib/i386 before the java command.
honestly using the automatic script would be easier as you need to point LD_LIBRARY_PATH to your java native library folder

---

### Post by 700 on 2013-11-06
> **HikariKnight said:**
> LD_LIBRARY_PATH=/usr/lib/jvm/"java_youre_using_here"/lib/i386

Done. It's there, but no improvement. 
Maybe it's because I have amd64 instead of i386?

Java worked before, so I just need to get previous settings. I have some problems to reset it and I don't know why.

---

### Post by HikariKnight on 2013-11-23
openjdk is installed in

/usr/lib/jvm/java-6-openjdk-amd64
/usr/lib/jvm/java-6-openjdk-i386
/usr/lib/jvm/java-7-openjdk-amd64
/usr/lib/jvm/java-7-openjdk-i386

for me if i want opengl i need  to run java like this (java7 only though as it works fine by default in java6)

LD_LIBRARY_PATH=/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64/ java

you can uninstall java with (assuming you used the commands i posted to install 32bit java)

sudo apt-get purge openjdk-7-jre:i386 openjdk-7-jre-headless:i386

---

### Post by 700 on 2013-11-27
[SOLVED] because another problem forced me to reinstall whole Ubuntu system.

---

