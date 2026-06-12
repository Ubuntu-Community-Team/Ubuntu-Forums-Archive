---
title: "Minecraft and Java/OpenGL/Nvidia Driver Issues"
date: 2011-07-24
forum: Gaming &amp; Leisure
---

### Post by dubois928 on 2011-07-24
Hey there.

I'm trying to move from Windows to Ubuntu. Originally I installed Ubuntu  11.04, but had problems with Minecraft running A LOT slower than in  Windows, and crashing very quickly. I found out it had something to do  with my NVIDIA video drivers, but I couldn't install the correct video  drivers because of some dependencies that were missing, and they  couldn't be installed in 11.04 because of the newer version of Xorg. My  graphics card is a NVIDIA GeForce MX4000.

So, I reformatted and installed 10.04 RTS. I removed the Nouveau drivers as per:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) 

and replaced them with nvidia-glx-96 using the Ubuntu Software Center, which *should* be the same as the latest driver for my card listed here:

[http://www.nvidia.com/object/linux-display-ia32-96.43.19-driver.html](http://www.nvidia.com/object/linux-display-ia32-96.43.19-driver.html)

I then ran Alloc's Minecraft Installer script:

[http://ubuntuforums.org/showthread.php?t=1726735](http://ubuntuforums.org/showthread.php?t=1726735)

It installed everything fine, but after I login I get a black screen and then this error:

> Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to [EMAIL="support@mojang.com"]support@mojang.com[/EMAIL].
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 7/23/11 8:13 PM

Minecraft: Minecraft Beta 1.7.3
OS: Linux (i386) version 2.6.32-33-generic
Java: 1.6.0_26, Sun Microsystems Inc.
VM: Java HotSpot(TM) Client VM (mixed mode, sharing), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: Could not init GLX
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
    at org.lwjgl.opengl.Display.create(Display.java:854)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(SourceFile:294)
    at net.minecraft.client.Minecraft.run(SourceFile:716)
    at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT 3eb61b1 ----------

I really want to switch  over to Ubuntu from Windows. Unfortunately getting Minecraft to work  right in Ubuntu (and other distros) has been extremely frustrating,  whereas with Windows it runs perfectly. Hopefully someone can help me  with this, I would extremely appreciate it.

Thanks,
Ken

---

### Post by Perfect Storm on 2011-07-24
Check if the driver is correctly setup:

```
lspci |grep VGA

dmesg |grep NVIDIA

glxinfo | grep direct


cat /etc/X11/xorg.conf

```

---

### Post by dubois928 on 2011-07-24
> **Artificial Intelligence said:**
> Check if the driver is correctly setup

Thanks for the quick reply! Here is what I get:

```
dubois@Terra:~$ lspci |grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
dubois@Terra:~$ dmesg |grep NVIDIA
[   11.070613] nvidia: module license 'NVIDIA' taints kernel.
[   12.259750] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.17  Thu Apr 15 05:28:41 PDT 2010
dubois@Terra:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
dubois@Terra:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
```-Ken

---

### Post by Perfect Storm on 2011-07-24
The driver is installed, but not in use.

```
sudo nano /etc/X11/xorg.conf
```


add:

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

save: [ctrl]+[o]
exit: [ctrl]+[x]

requires reboot.

IF it somehow won't let you into X and you're stranded in CLI, you can remove the lines by using **nano**.

---

### Post by dubois928 on 2011-07-24
Wow, thank you so much! That was a lot simpler than I thought it was going to be. Now it's running much better, exactly like it was in Windows. I just have a couple more problems.

I'm getting lag spikes that causes movement in the game to not be as smooth; it will stop for an instant rather regularly. I had this same problem in Windows. It isn't a game-breaker, but its very annoying. Perhaps there are some settings I can tweak in NVIDIA X Server Settings module? Also, I can hear the hard drive working when the lag spikes. I am using a 160gb ATA (IDE) hard drive, maybe it's slower because of that? Attached is screenshot showing the lag spikes. It also shows that I'm using 96mb out of 247mb of ram, but I have 2gb. It seems to not be using all the ram thats available.

And finally, I can't seem to use the tab key to switch fields in the Minecraft Launcher. This isn't really a problem but I'm curious as to why it doesn't work.

-Ken

---

### Post by Perfect Storm on 2011-07-24
Perhaps starting a new thread or asking on Minecraft about those issues.
I don't play Minecraft so I can't be at help. But what I read from people is that Minecraft is buggy as hell (and may be one of the reason why it sometimes lag/slow), so you may find your answers at Minecraft forum and see/search for a solution.

---

### Post by Jepic Phail on 2011-07-25
From the [Minecraft.net]("http://www.minecraft.net/download.jsp"):
```
java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
```

As for the render distance, are you saying it doesn't work even after you assigned the tab key to Toggle Render Distance?

---

### Post by dubois928 on 2011-07-25
> **Jepic Phail said:**
> As for the render distance, are you saying it doesn't work even after you assigned the tab key to Toggle Render Distance?

I said nothing about render distance. I can change that fine, the defualt key for render distance (fog) is F. I meant using the tab key to switch fields, ie from username to password, when you first launch the application.

Also, it's difficult to run Minecraft with the memory commands from the terminal that way because I have to switch directories (to my .minecraft folder) first. So I just added "-Xmx2048M -Xms1024M" to my desktop launcher command after "java -jar" and before the file path. I *assume* that is the appropriate way of doing it.

As far as the in-game graphics issues, I'll suppse leave that to the Minecraft forums, unless anyone here has knowledge of that feel free to help :)

Thanks,
Ken

---

### Post by Jepic Phail on 2011-07-26
It seems Minecraft does not allow users to change fields using the tab key. [[1]]("http://getsatisfaction.com/mojang/topics/add_tab_key_function_for_login")[[2]]("http://getsatisfaction.com/mojang/topics/tab_text_area_switching") If you want the tab key functionality you should submit a suggestion/feature request.

If you created a simple launcher on your desktop your solution should work just fine.

Your  hard drive should not matter unless you are trying to run a server with  more than dozen people playing at the same time. On the contrary,  Minecraft is very demanding on your memory and the processor due to the  way it handles its chunks. Even on my laptop, which has i5 and 4gb of RAM, java will consume quite a bit of resources. Therefore, RAM and the CPU would be the first place I would  look if I was having a performance issue with Minecraft. However, as to  why Minecraft would ran slower on Ubuntu opposed to XP, I have no idea.  It looks like you already have Sun Java installed so I can't offer you any more  suggestions. If you can, try allocating more memory to java.

---

### Post by dubois928 on 2011-07-26
Yeah, I've allocated more ram to java. I'm running at Xmx2048 Xms1024 for minecraft. I have 2gb of system ram, however my video card is an older AGP card and only has 128mb of ram. It's a hell of a lot better than my netbook though, which only has 8mb.

-Ken

---

