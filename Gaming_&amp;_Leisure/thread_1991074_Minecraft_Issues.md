---
title: "Minecraft Issues"
date: 2012-05-30
forum: Gaming &amp; Leisure
---

### Post by Son of MaxVK on 2012-05-30
First of all I'm sorry if this is in the wrong section, I just wasn't sure where to post this.

I am running 12.04 on my laptop and I want to see if I can get the Minecraft client running smoothly enough to play but I don't really know where to start. (I'm an Ubuntu newbie)

> Download minecraft.jar (89 KB). The jar is executable and might work as-is. If you run into memory issues, try launching it with java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame, also please use Sun's JVM.

This is what it says on the download page for the client, I've tried to run the jar file as an executable file but I can't get it to work, I'm also unsure if I have the correct version of Java installed if any.

I tried to use the terminal command to launch the game but this is all I got:

```
zak@zak-HP-G60-Notebook-PC:~$ java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
Exception in thread "main" java.lang.NoClassDefFoundError: net/minecraft/LauncherFrame
Caused by: java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: net.minecraft.LauncherFrame. Program will exit.
```

Any help would be appreciated. :confused:

---

### Post by brainwash on 2012-05-30
So you downloaded minecraft.jar, but you are trying to run **M**inecraft.jar?

---

### Post by Son of MaxVK on 2012-05-30
The name of the downloaded file is minecraft.jar and using upper case/lower case M in the terminal doesn't make any difference, just the same message.

---

### Post by Megaptera on 2012-05-30
Hopefully this Minecraft fix may be of help? I'm not sure if this link will open on the exact paragraph, but if not it's a couple of scrolls and a click away!

[http://modifyubuntu.com/#minecraft](http://modifyubuntu.com/#minecraft)

My son uses Minecraft but I haven't heard back from him as to if that fix helps or not, but thought you may want to have a look.

---

### Post by pbrane on 2012-05-30
The file you downloaded should be the launcher. make sure you are in the same directory as the minecraft launcher and run the command you posted. Make sure you use the correct case as brainwash pointed out. I run minecraft everyday using the same command.

As for java I have openjdk 7 installed and minecraft runs fine with that.

---

### Post by Son of MaxVK on 2012-05-30
> **Megaptera said:**
> Hopefully this Minecraft fix may be of help? I'm not sure if this link will open on the exact paragraph, but if not it's a couple of scrolls and a click away!

[http://modifyubuntu.com/#minecraft](http://modifyubuntu.com/#minecraft)

My son uses Minecraft but I haven't heard back from him as to if that fix helps or not, but thought you may want to have a look.

That has defiantly helped, now I can login and play the game but it lags so much I can't play. I think that this command should help:

```
java -Xmx1024M -Xms512M -cp Minecraft.jar
net.minecraft.LauncherFrame
```

The problem is whenever I try to use this I get the same message as in my original post, is there something I am missing?

---

### Post by Cardamominal on 2012-05-30
> **Son of MaxVK said:**
> That has defiantly helped, now I can login and play the game but it lags so much I can't play. I think that this command should help:

```
java -Xmx1024M -Xms512M -cp Minecraft.jar
net.minecraft.LauncherFrame
```The problem is whenever I try to use this I get the same message as in my original post, is there something I am missing?

What kind of graphics card are you using? If you have say an Nvidia card, then you need to proprietary drivers for 3D acceleration.

---

### Post by regor210 on 2012-05-30
Assuming minecraft.jar is in your Downloads folder you could start Mincraft like this

Open a terminal, press ctrl+alt+t all at the same time. Cut and paste the following commands into the terminal window minus the $.

$ cd ~/Downloads/ &&  java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame

---

### Post by sffvba[e0rt on 2012-05-30
Perhaps way of the mark, but have you tried marking the file as executable?

[http://askubuntu.com/questions/35478/how-do-i-mark-a-file-as-executable-via-a-gui](http://askubuntu.com/questions/35478/how-do-i-mark-a-file-as-executable-via-a-gui)

(I am not sure why this is needed and indeed if this is needed but I have come across this as a fix on several sites)


404

---

### Post by Son of MaxVK on 2012-06-02
> **regor210 said:**
> Assuming minecraft.jar is in your Downloads folder you could start Mincraft like this

Open a terminal, press ctrl+alt+t all at the same time. Cut and paste the following commands into the terminal window minus the $.

$ cd ~/Downloads/ &&  java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame

Thanks, that has helped a little bit with the lag but I'm afraid that my little laptop simply can't handle Minecraft.

> **not found said:**
> Perhaps way of the mark, but have you tried marking the file as executable?

[http://askubuntu.com/questions/35478/how-do-i-mark-a-file-as-executable-via-a-gui](http://askubuntu.com/questions/35478/how-do-i-mark-a-file-as-executable-via-a-gui)

(I am not sure why this is needed and indeed if this is needed but I have come across this as a fix on several sites)


404

Already Done.

> **Cardamominal said:**
> What kind of graphics card are you using? If you have say an Nvidia card, then you need to proprietary drivers for 3D acceleration.

Here is the on-board graphics my laptop has, I'm pretty sure that it is insufficient to play Minecraft.

Less info.
```
zak@zak-HP-G60-Notebook-PC:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

More info.
```
zak@zak-HP-G60-Notebook-PC:~$ sudo lshw -C video
[sudo] password for zak: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d2500000-d25fffff
```

---

### Post by sffvba[e0rt on 2012-06-02
I have Intel i915 graphics on my laptop and it just couldn't handle the game either... the FPS where just to low.


404

---

### Post by Son of MaxVK on 2012-06-02
I'm getting about 6fps myself, I have however dug up my Windows 7 laptop and tried it on there, it worked but there was no sound because Minecraft is using java 32bit instead of 64bit. I can't be bothered to mess around with Windows restarting 60 times for the smallest changes right now so I'll play without sound for now. :P

---

