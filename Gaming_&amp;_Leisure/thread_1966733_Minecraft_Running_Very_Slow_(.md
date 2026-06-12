---
title: "Minecraft Running Very Slow :("
date: 2012-04-27
forum: Gaming &amp; Leisure
---

### Post by UnknownFearNG on 2012-04-27
I have tried pretty much everything I can find on the Internet on how to run Minecraft smoothly. It worked flawlessly in 11.10, but now on Ubuntu 12.04, I'm running into some lag issues. I have the latest version or Oracle Java 7 installed as well as my proprietary AMD/ATi FGLRX driver. Has anyone gotten it running smoothly? I have 4GB or RAM and an AMD Radeon HD 6250 card. I just want to get it running smoothly :(

---

### Post by regor210 on 2012-04-27
Goto 
[http://www.minecraft.net/download](http://www.minecraft.net/download)
and download minecraft.jar

 Press ctrl+alt+t all at the same time. Then cut and paste the following commands into the termminal minus the $ , one at a time.

$ cd Downloads

$ chmod a+x minecraft.jar

$ java -Xmx2048M -Xms1024M -cp minecraft.jar net.minecraft.LauncherFrame

and post what you get

---

### Post by kaldor on 2012-04-27
Using a 6450 here. Seems to be working great.

My recommendation is to try using a lighter desktop environment. Here's how...

1) ```
sudo apt-get install gnome-session-fallback
```

2) Log out of your desktop. 

3) Choose your name (do not type your password yet)

4) Press the Ubuntu logo by your name and select "GNOME Classic (No effects)"

5) Enter your password and log in. 

That drastically increases performance for me. Whenever I know I'll be doing some gaming, I log into the classic session and all is well.

---

### Post by UnknownFearNG on 2012-04-27
> **regor210 said:**
> Goto 
[http://www.minecraft.net/download](http://www.minecraft.net/download)
and download minecraft.jar

and post what you get

```

27 achievements
182 recipes
Setting user: UnknownFearNG, -1545820482247323704
LWJGL Version: 2.8.3
org.lwjgl.LWJGLException: X Error - disp: 0x2a6f2120 serial: 172 error: GLXBadRenderRequest request_code: 154 minor_code: 1
	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:316)
	at org.lwjgl.opengl.LinuxContextImplementation.nSwapBuffers(Native Method)
	at org.lwjgl.opengl.LinuxContextImplementation.swapBuffers(LinuxContextImplementation.java:79)
	at org.lwjgl.opengl.ContextGL.swapBuffers(ContextGL.java:175)
	at org.lwjgl.opengl.DrawableGL.swapBuffers(DrawableGL.java:90)
	at org.lwjgl.opengl.Display.swapBuffers(Display.java:644)
	at net.minecraft.client.Minecraft.v(SourceFile:390)
	at net.minecraft.client.Minecraft.a(SourceFile:256)
	at net.minecraft.client.Minecraft.run(SourceFile:657)
	at java.lang.Thread.run(Thread.java:722)

```

> **kaldor said:**
> Using a 6450 here. Seems to be working great.

That drastically increases performance for me. Whenever I know I'll be doing some gaming, I log into the classic session and all is well.

I'm currently installing a proprietary driver via Additional Drivers and then I'll give this a try :)

---

### Post by regor210 on 2012-04-27
One more thing.
If you are using  java 7 you have to update LWJGL by hand.

[http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)

And check your java 7 by going here

[http://java.com/en/download/installed.jsp?jre_version=1.7.0_03&vendor=Oracle+Corporation&os=Linux&os_version3.2.0-24-generic](http://java.com/en/download/installed.jsp?jre_version=1.7.0_03&vendor=Oracle+Corporation&os=Linux&os_version3.2.0-24-generic)

---

### Post by UnknownFearNG on 2012-04-27
@regor210, I have updated LWJGL manually and still lagging a bit. I even updated and installed a proprietary drive from Additional Drivers and still nothing.

Here is the output that I get from minecraft.jar:

```

27 achievements
182 recipes
Setting user: UnknownFearNG, -5480564741801392119
LWJGL Version: 2.8.3
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event13): Failed to open device /dev/input/event13 (13)

Failed to open device (/dev/input/event12): Failed to open device /dev/input/event12 (13)

Failed to open device (/dev/input/event11): Failed to open device /dev/input/event11 (13)

Failed to open device (/dev/input/event10): Failed to open device /dev/input/event10 (13)

Failed to open device (/dev/input/event9): Failed to open device /dev/input/event9 (13)

Failed to open device (/dev/input/event8): Failed to open device /dev/input/event8 (13)

Failed to open device (/dev/input/event7): Failed to open device /dev/input/event7 (13)

Failed to open device (/dev/input/event6): Failed to open device /dev/input/event6 (13)

Failed to open device (/dev/input/event5): Failed to open device /dev/input/event5 (13)

Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

INSTANCE.absAxesIDs is only 63 long, so 63 not contained
Linux plugin claims to have found 1 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.

Placed stronghold in INVALID biome at (-52, -43)
Stopping!

SoundSystem shutting down...
    Author: Paul Lamb, www.paulscode.com
```

@kaldor: I tried launching classic GNOME and it gave me a few errors. Tried running Minecraft, and it was still lagging.

Is there seriously no fix to this lag??

---

### Post by regor210 on 2012-04-27
That all looks normal.

lets look at your 3D drivers.

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

### Post by UnknownFearNG on 2012-04-27
@regor210: glxgears output:

```

daniel@Darkan:~$ glxgears 
3305 frames in 5.0 seconds = 660.902 FPS
3267 frames in 5.0 seconds = 653.202 FPS
3468 frames in 5.0 seconds = 693.577 FPS
3247 frames in 5.0 seconds = 649.157 FPS
3226 frames in 5.0 seconds = 645.069 FPS
3184 frames in 5.0 seconds = 636.707 FPS
3239 frames in 5.0 seconds = 647.704 FPS
3216 frames in 5.0 seconds = 643.067 FPS
3207 frames in 5.0 seconds = 641.266 FPS
3061 frames in 5.0 seconds = 612.124 FPS

```

lspci -vmk | grep -A 8 -B 2 VGA output:

```

daniel@Darkan:~$ lspci -vmk | grep -A 8 -B 2 VGA

Device:    00:01.0
Class:    VGA compatible controller
Vendor:    Advanced Micro Devices [AMD] nee ATI
Device:    Wrestler [Radeon HD 6250]
SVendor:    Acer Incorporated [ALI]
SDevice:    Device 0602
Driver:    fglrx_pci
Module:    fglrx
Module:    radeon

```

---

### Post by regor210 on 2012-04-27
That looks good too.

When your in minecraft and you press F3 what is your fps ?

And what do you get with 

$ fglrxinfo

---

### Post by UnknownFearNG on 2012-04-27
It fluctuates between 3, 7, 3, 1, 4, 3, etc. Doesn't go passed 10. If I move around, it immediately drops.

---

### Post by regor210 on 2012-04-27
What do you get with

$ fglrxinfo

---

### Post by UnknownFearNG on 2012-04-27
fglrxinfo output:

```

daniel@Darkan:~$ fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6310 Graphics 
OpenGL version string: 4.2.11627 Compatibility Profile Context
```

---

### Post by regor210 on 2012-04-27
Just for kicks lets make sure your not having a permissions issue.


$ sudo chmod -R 775 .minecraft&#65279;

$ cd Downloads

$ sudo chmod a+x minecraft.jar

$ java -Xmx2048M -Xms1024M -cp minecraft.jar net.minecraft.LauncherFrame



-----------------------------------------------------------

Outside of that all I can think of is to rename your .minecraft folder and restart the game then exit, &#65279;update LWJGL by hand and see if a new install works. if yes move your save folder into the new .minecraft folder from your old folder.

Because everything is looking good no errors.

---

### Post by UnknownFearNG on 2012-04-27
Nope, still no good. Nothing is improving the performance at all.

---

### Post by regor210 on 2012-04-27
This is about the last thing I can think of. In the past java , Minecraft seem to confuse aspects of the video driver with a controller. This in these rare cases this solved the problem.
 

$ sudo chmod go=u /dev/input/event*

$ cd Downloads

$ java -Xmx2048M -Xms1024M -cp minecraft.jar net.minecraft.LauncherFrame

If $ sudo chmod go=u /dev/input/event* causes other issues restarting your computer will reset everything back to normal.
  ------------------------------------------------------------
The only other thing that causes minecraft to lag without showing an error would be if for some reason your system was using sawp memory. This normally happens on systems with 1 or less gigs or ram. When this is the case its best to start Minecraft like this   

$ java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame
--------------------------------------------------------------------
There are performance enhancers for Minecraft that work fine with Ubuntu. like Optifine but with your hardware you should'nt need them.

[http://www.minecraftforum.net/topic/249637-125-optifine-hd-a6-fps-boost-hd-textures-aa-af-and-more/](http://www.minecraftforum.net/topic/249637-125-optifine-hd-a6-fps-boost-hd-textures-aa-af-and-more/)

---

### Post by UnknownFearNG on 2012-04-27
I might try it later on, but for now, I've given up lol. So frustrating trying to get this stupid game to work.

---

### Post by UnknownFearNG on 2012-04-27
Actually, I might try installing Windose 7 in VirtualBox and see if Minecraft runs better that way. Think it would?

---

### Post by regor210 on 2012-04-27
Did you try  OpenJDK 7 with all the plugins?

$ sudo apt-get update

$ sudo apt-get install  ca-certificates-java icedtea-7-jre-cacao icedtea-7-jre-jamvm java-common  libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common libgnome2-0 libgnomevfs2-0 libgnomevfs2-common openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib ttf-dejavu-extra tzdata-java

It works for me and if you dont like it you can change back using

$sudo update-alternatives --config java

---

### Post by UnknownFearNG on 2012-04-27
I am actually removing Sun Java and installing all the packages for OpenJDK 6. I will then test it and then uninstall my proprietary drivers for my Radeon card and install open source from the PPA:xorg-edgers source.

---

### Post by UnknownFearNG on 2012-04-27
Alright, installed OpenJDK 6 and it seems to be running a little bit smoother. I installed the ppa for xorg-edgers which has a lot of open source drivers. Now, I already have a proprietary driver installed and active. Do I have to remove fglrx and then install open-source drivers, or can I install them while proprietary is active?

---

### Post by regor210 on 2012-04-27
If its working I wouldn’t change it. The &#65279;proprietary driver are supposed to work better but with ATI cards thats not always the case in GNU/Linux Ubuntu.

Plus edgers can be unstable as they are for testing.

---

### Post by UnknownFearNG on 2012-04-27
I see that now -_-. I don't have a desktop, only terminal login all bevause I installed open-source drivers. Guess I'll just install OpenJDK 7 next time and keep the proprietary drivers.

---

### Post by Dr. McKay on 2012-04-30
I've got a 24" iMac, 2.8Ghz Core2duo, 4Gb of RAM, ATI Radeon HD 2600 Pro/256Mb and Ubuntu 12.04.
I'm having the same problems. Open JDK6, 7 or Oracle 7 don't make any difference. Have installed the additional ADM drivers from Ubuntu repository (NOT from ADM website). Everything else on the system is smooth as butter, except minecraft...

In OS X (Snow leopard) it's like greased lightning...

---

### Post by regor210 on 2012-04-30
In Minecraft what are your FPS when you press F3

What do you get with

$ fglrxinfo

#video card and driver information
$ lspci -vmk | grep -A 8 -B 2 VGA

And post what you get.

---

### Post by Dr. McKay on 2012-05-01
@regor : thanks for the reply, but have removed ubuntu for the time being (only have a 320Gb internal HD and needed the space to manage my photo library and archive on external HD), will be reinstalling soon, I'll get back to you.

In any case, thx for the help in advance !

---

### Post by thatguruguy on 2012-05-01
You have 320 GB worth of pictures?

That's a lot of pictures.

---

### Post by Dr. McKay on 2012-05-01
> **thatguruguy said:**
> You have 320 GB worth of pictures?

That's a lot of pictures.

Nope, about 85Gb worth of photos and 40gb of music. The rest is filled up with all kinds of apps for testing purposes. Oh, and games (World of Warcraft alone gobbles up 30gb). 320Gb is really small, you know...

---

