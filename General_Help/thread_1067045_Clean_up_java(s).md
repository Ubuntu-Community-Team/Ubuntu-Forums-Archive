---
title: "Clean up java(s)"
date: 2009-02-11
forum: General Help
---

### Post by wyoming on 2009-02-11
After I installed the latest jre from Sun as per their instructions I have *four* different folders with active java stuff: cacao  java-6-sun  java-6-sun-1.6.0.10  jre1.6.0_12 ... 
On the java website the applet can't find my version but everything else appears fine... Can somebody explain how to clean that up?
Thanks.

(8.10)

---

### Post by mozkill on 2009-02-11
Dont take this as an answer but usually there is a symbolic link somewhere that points to the currently "active" version of java that you have installed.  then, applications such as the web browser are trained to use the path via the symbolic link name instead, which forwards them to the proper JRE directory.    if you find this to be true on your system, and you dont see that the symbolic link points to the older JRE directories, then you can probably rename the older directories to jre1.4.old  so they are disabled.   if everything still works then you can probably clean them up later and delete the old ones. 

thats just a little info , i hope that helps.

every linux is different and im not sure about Ubuntu but you should be able to just look and see if its true for your system.

youll probably have to read this:  [http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)

also, read this:  [http://ubuntuforums.org/showthread.php?t=182702](http://ubuntuforums.org/showthread.php?t=182702)

---

### Post by geirha on 2009-02-11
Short version: 
```
update-java-alternatives --list
```
will list all java versions you have installed (through the repositories). To update all symlinks to the java runtime, plugins, compilers etc. Choose the version you want from the list, and set it with the command:
```
sudo update-java-alternatives --set *java-version*
```
You probably want java-6-sun.

---

### Post by wyoming on 2009-02-11
Among those in my jvm folder:
**cacao,  java-6-sun,  java-6-sun-1.6.0.10,  jre1.6.0_12**
java-6-sun is the "active" one, the one with the arrow, which is confirmed by the "update-java-alternatives --list" line.
As I understand it, it is also the one that was installed through the repositories.

All 4 folders have similar directory structures (bin,ext,jre etc...) so I can sorta see why the java website applet can't find nothing anymore...

Maybe I could rename the folder **jre1.6.0_12** as **jre**, and replace the **jre** folder within the [B]java-6-sun-1.6.0_10
[/B] with it?

Or maybe, since the java console indicates the correct version (_12) and since access to media works, I should leave it alone. Until Ubuntu/Sun clarify this version/update mess...

---

