---
title: "MInecraft Blackscreen"
date: 2012-04-23
forum: Gaming &amp; Leisure
---

### Post by neillyoung on 2012-04-23
I get a blackscreen after login. The launcher works but the actual game doesn't. It's a fresh vanilla install. Any ideas?

---

### Post by regor210 on 2012-04-23
What vertion of Ubuntu are you using? If you dont know just press ctrl+alt+t all at the same time. Then cut and paste the following command into the terminal minus the $

$ lsb_release -a

If you are using Ubuntu 12.04 you have to update LWJGL by hand or you will get a black screen when loading the game and you may need to install some java components.
let us know and we can help you with that

If your not using Ubuntu 12.04 then we need you to start minecraft in terminal so we can see whats wrong.
goto 
[http://www.minecraft.net/download](http://www.minecraft.net/download)
and download minecraft.jar

 Press ctrl+alt+t all at the same time. Then cut and paste the following commands into the termminal one at a time, minus the $

$ cd Downloads

$ sudo chmod a+x minecraft.jar

$ java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame

and post what you get

---

### Post by neillyoung on 2012-04-23
Ubuntu 11.10


```
(java:9819): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:9819): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:9819): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:9819): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
27 achievements
182 recipes
Setting user: Th3Harbinger, 4514366638558932630
Exception in thread "Minecraft main thread" java.lang.ExceptionInInitializerError
	at net.minecraft.client.Minecraft.a(SourceFile:184)
	at net.minecraft.client.Minecraft.run(SourceFile:657)
	at java.lang.Thread.run(Thread.java:679)
Caused by: java.lang.ArrayIndexOutOfBoundsException: 0
	at org.lwjgl.opengl.XRandR$Screen.<init>(XRandR.java:234)
	at org.lwjgl.opengl.XRandR$Screen.<init>(XRandR.java:196)
	at org.lwjgl.opengl.XRandR.populate(XRandR.java:87)
	at org.lwjgl.opengl.XRandR.access$100(XRandR.java:52)
	at org.lwjgl.opengl.XRandR$1.run(XRandR.java:110)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.opengl.XRandR.getConfiguration(XRandR.java:108)
	at org.lwjgl.opengl.LinuxDisplay.init(LinuxDisplay.java:618)
	at org.lwjgl.opengl.Display.<clinit>(Display.java:135)
	... 3 more
```

---

### Post by regor210 on 2012-04-23
There was a bug in Ubuntu 11.10

[http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line](http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line)

&#8220;&#65279;Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",&#8221;

Updating should fix it.

$ sudo apt-get update
$ sudo apt-get upgrade

Make sure you have this installed.

$ sudo apt-get install gtk2-engines-pixbuf

If minecraft still will not work lets look at your 3D drivers.

Try these

# update
$ sudo apt-get update
$ sudo apt-get upgrade

$ sudo apt-get install mesa-utils

# video driver 3D test FPS
$ glxgears

#video card and driver information
$ lspci -vmk | grep -A 8 -B 2 VGA

And post what you get.

---

### Post by neillyoung on 2012-04-24
I tried pixbuf but to no avail. Here is my outout from the other two.

glxgears
```

Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
299 frames in 5.0 seconds = 59.745 FPS
301 frames in 5.0 seconds = 60.018 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1728 requests (1728 known processed) with 0 events remaining.


```

lspci -vmk | grep -A 8 -B 2 VGA
```

Class:	VGA compatible controller
Vendor:	Intel Corporation
Device:	Mobile GM965/GL960 Integrated Graphics Controller (primary)
SVendor:	Dell
SDevice:	Device 01f2
Rev:	0c
Driver:	i915
Module:	intelfb
Module:	i915


```

---

### Post by regor210 on 2012-04-24
The intel i915 video adapter is a low end adapter. I have an intel i915 video adapter in a laptop and in 2 old desktops. It seems if you have 16megs of video ram, or more your go to go.  

1st get into your BIOS and make as much ram or memory available to your  i915 video adapter as you can.

Most Intel chipset video drivers are supported automatically on the Kernel, so you may not have to install any 3rd party drivers for your video card. But if the Intel Graphics on your system don&#8217;t seem to be working correctly, you can try installing the latest drivers for your Intel Graphics.


This is a PPA. By adding this PPA to your system, your package manager will have access to additional software.  

ubuntu-x-swat
ubuntu-x-swat is more stable than xorg-edgers

[https://launchpad.net/~intel-gfx-testing/+archive/ppa](https://launchpad.net/~intel-gfx-testing/+archive/ppa)
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)


$ sudo apt-get update
$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get dist-upgrade

If this driver doesn&#8217;t help there is another unstable driver you can try.

---

### Post by neillyoung on 2012-04-24
thanks for all the help, but i think I'll just boot windows when I want to play Minecraft.

---

### Post by muppetcooter on 2012-04-24
> **neillyoung said:**
> thanks for all the help, but i think I'll just boot windows when I want to play Minecraft.

Seems like the only solution. I don't think Ubuntu can handle Minecraft for more than 10% of accounted people who try. It's sad, but that's how it is.

---

### Post by thatguruguy on 2012-04-24
> **muppetcooter said:**
> Seems like the only solution. I don't think Ubuntu can handle Minecraft for more than 10% of accounted people who try. It's sad, but that's how it is.

Odd. My son is playing it on 12.04 64-bit right now, on an old Dell with an NVIDIA 8400GS.

---

### Post by The_Loko on 2012-04-25
It was so easy for me! I just have installed default-jre now the game works flawless:D
Also you can try updating LWGL as explained here: [http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)

---

### Post by pure1 on 2012-06-21
> **The_Loko said:**
> It was so easy for me! I just have installed default-jre now the game works flawless:D
Also you can try updating LWGL as explained here: [http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)

Thanks this worked for me!

---

