---
title: "Minecraft issues with Java/OpenGL/ATI"
date: 2012-05-08
forum: Gaming &amp; Leisure
---

### Post by Adz0rd on 2012-05-08
Hi guys,

So i recently moved to Ubuntu 12.04 and its really great :) however ive been having some problems with some games on Ubuntu, in this case it was minecraft, now originally it wasnt working due to java not working properly, then i followed the installer found here to get java working:

[http://ubuntuforums.org/showthread.php?t=1726735](http://ubuntuforums.org/showthread.php?t=1726735)

After this, minecraft was loading fine and i could successfully get into singleplayer and multiplayer games, however all of my textures were mucked up, like my arms were not there and my player skin was a culmination of block skins and stuff like that. I then deleted the .minecraft folder and re-downloaded the game and it worked perfectly.

I started to notice that i would get FPS lag in the game where usually when i was on windows i was fine. So i looked into my gfx card drivers, and they are ****** up. So i uninstalled all of the proprietary drivers and tried running minecraft without the propreitary drivers installed and now once i login, i hit a black screen and eventually a minecraft crash which gives me these errors:

```

      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.




--- BEGIN ERROR REPORT 7cf3a456 --------
Generated 5/8/12 11:41 PM

Minecraft: Minecraft 1.2.5
OS: Linux (amd64) version 3.2.0-24-generic
Java: 1.6.0_32, Sun Microsystems Inc.
VM: Java HotSpot(TM) 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: X Error - disp: 0x7fbf980465b0 serial: 31 error: BadRequest (invalid request code or no such operation) request_code: 154 minor_code: 14
    at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:268)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
    at org.lwjgl.opengl.Display.create(Display.java:854)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(SourceFile:236)
    at net.minecraft.client.Minecraft.run(SourceFile:657)
    at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT 29d68679 ----------

```i tried reinstalling the proprietary drivers both from the AMD site and through the "Additional Drivers" manager but still no luck.

lspci | grep VGA gives me this:

```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Broadway [ATI Mobility Radeon HD 6800 Series]

```dmesg | grep ATI gives me this:

```

[    3.721176] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.

```glxinfo gives me this:

```

name of display: :0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```Any help would be much appreciated.

Thanks,
Adz0rd

---

### Post by regor210 on 2012-05-08
It looks like you have an ATI dual-GPU ati/intel hybrid video adapter found on notebooks and laptops.

If as of Catalyst 11.4 there is support for dual-GPU notebooks
[http://phoronix.com/forums/showthread.php?41337-PowerXpress-Support-Notebooks-Under-Linux](http://phoronix.com/forums/showthread.php?41337-PowerXpress-Support-Notebooks-Under-Linux)

You may need a newer ATI property driver but first try this. 

$ &#65279;fglrxinfo

returns nothing, make sure you have this installed

$ sudo apt-get update
$ sudo apt-get upgrade 
$ sudo apt-get install fglrx
$ sudo apt-get install fglrx-updates

As for the lag if you have 1Gig or less on your motherboard Minecraft may be using swap memory. In other words your system is trying to use your hard drive to store ram memory that should be stored on the mother boards system ram. For gaming this is very slow.  Start Minecraft like this if its an issue.    

 $  java -Xmx256M -Xms256M  -cp minecraft.jar net.minecraft.LauncherFrame

This assumes  minecraft.jar is in your home folder.

**Update** one more thing. Some people have complained about Ubuntu&#8217;s 3D desktop effects interfering with Minecraft. If Lag and strange graphic problems persist you could try using Ubuntu 2D by logging out out of your desktop session and selecting Ubuntu 2D then log back in.

---

### Post by Adz0rd on 2012-05-08
Hi,

I ran all the commands you wrote with the exception of adding the java parameters to the execution of minecraft since i have 8GB of RAM, when running the game i am still met with this error:

```

      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.




--- BEGIN ERROR REPORT 7cf3a456 --------
Generated 5/9/12 8:47 AM

Minecraft: Minecraft 1.2.5
OS: Linux (amd64) version 3.2.0-24-generic
Java: 1.6.0_32, Sun Microsystems Inc.
VM: Java HotSpot(TM) 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: X Error - disp: 0x7f4ec402b580 serial: 31 error: BadRequest (invalid request code or no such operation) request_code: 154 minor_code: 14
    at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:268)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
    at org.lwjgl.opengl.Display.create(Display.java:854)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(SourceFile:236)
    at net.minecraft.client.Minecraft.run(SourceFile:657)
    at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT bb10d65a ----------

```

glxinfo is still returning this:

```

name of display: :0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

---

### Post by regor210 on 2012-05-08
You can find instructions on how to install the most up to date property ATI drivers here

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

If for what ever reason they still will not work you could try going into your BIOS and turning off the Intel side of your graphic adapter. This would have the down side of a sorter run time on a charge but it should play games well.

---

### Post by Adz0rd on 2012-05-08
Already followed these instructions as well as the instructions on the AMD unofficial ubuntu wiki, im still having these problems.

I have an Alienware M17xR3 and in my BIOS it doesnt give me the option to turn off the intel graphics adapter.

---

### Post by regor210 on 2012-05-09
1st I would like to say you have a nice laptop with grate hardware.

look at this thread  

[http://ati.cchtml.com/show_bug.cgi?id=276](http://ati.cchtml.com/show_bug.cgi?id=276)

&#65279;PowerXpress refers to a laptop with the ability to switch graphics from a power consuming gaming machine to a power conserving net surfer.

see Comment 11, then Comment 21

&#8220;This switching feature was working  pretty well from 11.6 to 11.8 so I didn'tunderstand (now I'm using 11.8 version on ubuntu 10.04 without major problem).As this works before, it's not an impossible task ;)&#8221;

It looks like the latest ATI driver will not work with your hardware. Maybe you should try 11.8 as it seemed to have worked.

Catalyst 11.8

$ wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-8-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-8-x86.x86_64.run)

Just to note.
Ubuntu 12.04 comes with Catalyst 12.4.

Ubuntu 11.10 came with 11.10.

Ubuntu 11.04 came with 11.4.

Ubuntu 10.10 came with 10.10.

Ubuntu 10.04 came with 10.4.

---

### Post by Adz0rd on 2012-05-09
Thank you very much for the comment on my hardware :), it cost me quite a pretty penny so as you can imagine, im kind of annoyed that its not working, i just removed the fglrx drivers and im now downloading the 11.8 version of catalyst, ill install and tell you how it goes :)

EDIT: after installing Catalyst 11.8, unity doesnt load when i login, ive tried both "Unity" and "Unity 2D" but neither work. Anymore suggestions?
EDIT 2: to get unity to work again, i had to reinstall fglrx.

---

### Post by regor210 on 2012-05-09
lots of information about your hardware can be found here

[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)



Hybrid Graphics and Catalyst
ATI/ATI Hybrids

As of Catalyst 11-8, switching between two ATI cards (and maybe Intel/ATI muxless too?) is supposed to be doable, though I don't know if that applies to all ATI/ATI hybrids or only the muxless ones. One would use aticonfig's PowerXpress options to switch back and forth between the integrated and discrete cards, like so:

I&#8217;m not sure if logging out restarts X in Unity maybe its best to restart your laptop the 1st time you try it.

$ aticonfig --pxl            # List current activated GPU
$ sudo aticonfig --px-dgpu   # Activate discrete GPU (High-Performance mode), must re-start X to take effect
$ sudo aticonfig --px-igpu   # Activate integrated GPU (Power-Saving mode), must re-start X to take effect

---

### Post by Adz0rd on 2012-05-09
I cant even use the ati catalyst 11.8 without unity not working

---

### Post by regor210 on 2012-05-09
[http://askubuntu.com/questions/128569/switching-graphics-using-catalyst-control-center](http://askubuntu.com/questions/128569/switching-graphics-using-catalyst-control-center)

&#65279;"and it have not been working between catalysts 11.8(or 11.6?) and 12.1. However it works nowadays.”


Install then use the Ubuntu 12.04 property drivers (jockey). This is  &#65279;catalyst 12.4. 12.4 is grater than 12.1 so it should work.

then use 

&#65279;$ sudo aticonfig --px-dgpu # Activate discrete GPU (High-Performance mode), must re-start X to take effect

Then restart your laptop.

---

### Post by Adz0rd on 2012-05-09
So how do i install the jockey drivers?

---

### Post by regor210 on 2012-05-09
On your Ubuntu desktop click on the Ubuntu icon to the upper left. Type jockey in the search bar. Now you should see an icon marked Applications Additional Drivers, Click on it and hopefully you will see an ATI Property driver listed that you can install.

  Just to let you know where we are at. In post #6 the Bug thread said your hardware wasn’t  supported after &#65279;Catalyst 11.8.

In post #10 they say after &#65279;Catalyst 12.1 ATI started supporting your hardware again.

So with a little luck and  &#65279;aticonfig --px-dgpu maybe we can get it working.

&#65279;Install then use the Ubuntu 12.04 property drivers (jockey)
 
then use 

&#65279;$ sudo aticonfig --px-dgpu # Activate discrete GPU (High-Performance mode), must re-start X to take effect
 
Then restart your laptop.

---

