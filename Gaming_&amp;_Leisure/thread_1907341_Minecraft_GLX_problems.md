---
title: "Minecraft GLX problems"
date: 2012-01-11
forum: Gaming &amp; Leisure
---

### Post by Ciro2010 on 2012-01-11
I'm trying to play Minecraft on Ubuntu 11.10 (I'm new to ubuntu)

I have installed java, i tried to boot it with both Sun java and openJDK and I always get this error:

```


      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to support@mojang.com.
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 1/11/12 1:18 PM

Minecraft: Minecraft 1.0.0
OS: Linux (i386) version 3.0.0-14-generic-pae
Java: 1.6.0_26, Sun Microsystems Inc.
VM: Java HotSpot(TM) Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.8.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: Could not init GLX
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:61)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:782)
    at org.lwjgl.opengl.DrawableGL.setPixelFormat(DrawableGL.java:61)
    at org.lwjgl.opengl.Display.create(Display.java:871)
    at org.lwjgl.opengl.Display.create(Display.java:782)
    at org.lwjgl.opengl.Display.create(Display.java:764)
    at net.minecraft.client.Minecraft.a(SourceFile:237)
    at net.minecraft.client.Minecraft.run(SourceFile:644)
    at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT c7599add ----------



```
I checked additional drivers, but the newest one is installed!
I tried searching in the forum and on google, found nothing but a lot of unanswered threads.. I hope this doesn't happen to me :)

Thanks in advance!

---

### Post by Azdour on 2012-01-11
Hi,

If you have an NVidia graphics card the following topic may help you:

[http://ubuntuforums.org/showthread.php?t=1810956](http://ubuntuforums.org/showthread.php?t=1810956)

---

### Post by Ciro2010 on 2012-01-11
> **Azdour said:**
> Hi,

If you have an NVidia graphics card the following topic may help you:

[http://ubuntuforums.org/showthread.php?t=1810956](http://ubuntuforums.org/showthread.php?t=1810956)

OH yes, i found that thread on google, and tried the solution given by Artificial Intelligence, but i ended up modifying something i didnt have to modify... So my pc couldn't boot up properly and i had to change everything back to normal in the terminal..
:/

---

### Post by regor210 on 2012-01-11
Are you using &#65279;Sun-Java.

$ sudo update-alternatives --config java

---

### Post by Ciro2010 on 2012-01-11
> **regor210 said:**
> Are you using &#65279;Sun-Java.

$ sudo update-alternatives --config java

Yes i'm using sun java, i also tried openJDK but it gives me the same error

---

### Post by regor210 on 2012-01-11
You could try rolling your NVidia driver back to 177 by using

$ GL_ExtensionStringVersion=17700 java -jar .minecraft/minecraft.jar

to start Minecraft in terminal.

---

### Post by Ciro2010 on 2012-01-11
> **regor210 said:**
> You could try rolling your NVidia driver back to 177 by using

$ GL_ExtensionStringVersion=17700 java -jar .minecraft/minecraft.jar

to start Minecraft in terminal.

Nothing... 

```
Xlib:  extension "GLX" missing on display ":0".
org.lwjgl.LWJGLException: Could not init GLX
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:61)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:782)
    at org.lwjgl.opengl.DrawableGL.setPixelFormat(DrawableGL.java:61)
    at org.lwjgl.opengl.Display.create(Display.java:871)
    at org.lwjgl.opengl.Display.create(Display.java:782)
    at net.minecraft.client.Minecraft.a(SourceFile:205)
    at net.minecraft.client.Minecraft.run(SourceFile:644)
    at java.lang.Thread.run(Thread.java:662)

```

---

### Post by regor210 on 2012-01-11
“Xlib:  extension "GLX" missing on display ":0".”

Is a video driver issue. Have you tried reinstalling your property drivers?

---

### Post by Ciro2010 on 2012-01-11
> **regor210 said:**
> “Xlib:  extension "GLX" missing on display ":0".”

Is a video driver issue. Have you tried reinstalling your property drivers?

Yep, on Additional Drivers it gives me 2 nvidia drivers, i had the one with [Recommended], i tried both of them but nothing changes

---

### Post by Ciro2010 on 2012-01-12
Sorry for double posting, but I made a new install and after that I did all the automatic ubuntu updates and installed the recommended nvidia driver.. still the same error.

---

### Post by regor210 on 2012-01-12
"Release highlights since 290.10:

new NVidia 295.09Beta Linux display driver...

Added support for the following GPU:
Tesla X2090
Fixed an OpenGL bug where using display lists on Fermi-based GPUs could result in missing rendering in some cases.
Fixed an OpenGL bug that caused incorrect rendering when using framebuffer objects to render to 16-bit color textures with alpha.
Fixed two bugs that caused sporadic application crashes in some multi-threaded OpenGL applications.
Fixed a bug that caused creating OpenGL 4.2 contexts with glXCreateContextAttribsARB to fail.
Fixed a bug that caused OpenGL to print"

Looks like there working on the problem. I couldnt find a NVidia 295.09 deb for Ubuntu and I don’t know if installing from source would play nice with Ubuntu 11.10.

Some  NVidia cards are not playing nice. We have 3 computers here up and running using NVidia cards with no problems. Guess we got lucky.

Sorry you went threw the trouble of a reinstall with no luck. 
Been there done that my self.

---

### Post by Ciro2010 on 2012-01-13
> **regor210 said:**
> "Release highlights since 290.10:

new NVidia 295.09Beta Linux display driver...

Added support for the following GPU:
Tesla X2090
Fixed an OpenGL bug where using display lists on Fermi-based GPUs could result in missing rendering in some cases.
Fixed an OpenGL bug that caused incorrect rendering when using framebuffer objects to render to 16-bit color textures with alpha.
Fixed two bugs that caused sporadic application crashes in some multi-threaded OpenGL applications.
Fixed a bug that caused creating OpenGL 4.2 contexts with glXCreateContextAttribsARB to fail.
Fixed a bug that caused OpenGL to print"

Looks like there working on the problem. I couldnt find a NVidia 295.09 deb for Ubuntu and I don’t know if installing from source would play nice with Ubuntu 11.10.

Some  NVidia cards are not playing nice. We have 3 computers here up and running using NVidia cards with no problems. Guess we got lucky.

Sorry you went threw the trouble of a reinstall with no luck. 
Been there done that my self.


What is that stuff? where was it fixed?
If there's a better version of ubuntu i could easily install that now, i already formatted anyway!
(What would change?)

---

### Post by regor210 on 2012-01-13
If it were me I would try installing Ubuntu 10.04

See if that fixed it, if not then use

Artificial Intelligence's fix found here

[http://ubuntuforums.org/showthread.php?t=1810956](http://ubuntuforums.org/showthread.php?t=1810956)

This should work using Ubuntu 10.04. 

Or 
 
Installing the NVidia 295.09 Beta driver from source using the Nvidia installer, this would be a pain and has to be used again every time you get a kernel update. And there has been so many changes in Ubuntu 11.10 I doubt the Nvidia installer would work with the current version of xserver found in Ubuntu 11.10.

Hopefully Ubuntu 12.04 will have NVidia 295.09 drivers or grater, then it would be safe for you to upgrade when it is released.

---

### Post by Ciro2010 on 2012-01-13
> **regor210 said:**
> If it were me I would try installing Ubuntu 10.04

See if that fixed it, if not then use

Artificial Intelligence's fix found here

[http://ubuntuforums.org/showthread.php?t=1810956](http://ubuntuforums.org/showthread.php?t=1810956)

This should work using Ubuntu 10.04. 

Or 
 
Installing the NVidia 295.09 Beta driver from source using the Nvidia installer, this would be a pain and has to be used again every time you get a kernel update. And there has been so many changes in Ubuntu 11.10 I doubt the Nvidia installer would work with the current version of xserver found in Ubuntu 11.10.


Hopefully Ubuntu 12.04 will have NVidia 295.09 drivers or grater, then it would be safe for you to upgrade when it is released.

Ok, i inserted the cd for ubuntu 10.04, and decided to try it first and i noticed a couple things..

first there's a weird resolution, i don't know how to explain that, and then when i check for connections it doesn't look automatically for wireless connections like it did when i tried ubuntu 11.10, so i couldn't connect to internet... is it normal?

**Anyway if someone knows a solution to the primary problem, i would  really prefer that, as i would have no idea how to use ubuntu 10.04**

***I was trying to install the NVidia 295.09 beta driver, but i found a lot of different downloads on google and i have no idea which one to pick and how to install it.. i'm on ubuntu 11.10 32 bit***

---

### Post by Ciro2010 on 2012-01-13
SORRY FOR DOUBLE POST but i have an important update

I think i found the problem, but i have a few questions.

1: I installed the latest drivers for nvidia (apparently i was missing some)
2: I opened "NVidia X server settings" and it said i was not using the NVIDIA X DRIVER
3: I googled it and found THIS: [http://blog.musicvm.com/solved-you-do-not-appear-be-using-nvidia-x-driver-linux-ubuntu](http://blog.musicvm.com/solved-you-do-not-appear-be-using-nvidia-x-driver-linux-ubuntu)

The problem is, last time i tried to do something alone in terminal i broke my pc and had to format, so...

The first thing it says (remove nouveau) Will it cause something bad? I mean, should i put that command on startup (CTRL+ALT+F1) or in the normal terminal?

(Sorry for all the confusion, but i'm kinda new to ubuntu)

---

### Post by regor210 on 2012-01-13
&#65279;
The nouveau video driver is the default open source Nvidia driver that comes with Ubuntu. 

Note.You may able to play Minecraft using the nouveau driver.

If you try to uninstall the nouveau driver it may leave you without a working graphics driver. I think this will reinstall nouveau if you need to.

&#65279;sudo rm /etc/X11/xorg.conf
sudo apt-get purge xserver-xorg-video-nouveau
sudo apt-get install xserver-xorg-video-nouveau

Good luck.

---

### Post by Ciro2010 on 2012-01-14
Here's the updates..

I just formatted again.. still 11.10 because i was not sure about getting 10.04

I formatted because i got a problem on startup, i got a black screen with a lot of messages and one of them had (fail!) on his side
it was like "Stopping automatic crash report generation (fail!)"

Anyway now i don't know what to do about minecraft, but i think i have figured out what was wrong

In the beginning i had windows 7, but my father wanted to install Ubuntu, so i got 11.10 and went on, but when it was installed the computer had 2 partitions, windows on C:/ and a small one, X:/
I thought X:/ was the recovery partition for windows, but all this stuff with NVidia and this "X" I always see but still didn't understand what it was... now that i re-re-reinstalled ubuntu, the PC had only 1 partition: UBUNTU 11.10 (there was no X:) and before reformatting i got that strange error "you do not appear to be using the NVidia X driver"...

Could it be that X got deleted on my pc? what could i do about it?

(Anyway i found out that the error on bootup "stopping automatic crash report fail" was caused by me following this guide: [http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html) )

****UPDATE****
If i try to play minecraft BEFORE installing the nvidia driver from addictional drivers I CAN PLAY IT!!! (But there are problems with the graphics, obviously.. I get a lot of dots and the lower left side of the screen is cut into a triangle.. i don't know how to expain that..)
anyway it's impossible to play with these graphics problems

---

### Post by regor210 on 2012-01-14
I admire your perseverance. You have some good computer skills. Heres how i see the problem your having. Your Nvidia graphic drivers are ether being installed incorrectly by Ubuntu or you need the newest beta Nvidia driver. There were some big changes in Ubuntu 11.10. Ubuntu 11.10 is cutting edge technology. Ubuntu 10.04 LTS is more stable. LTS meaning Long Term Support. Its not hard to manually fix small Nvidia graphic drivers configuration problems in xorg.conf on Ubuntu 10.04. 

Your open source Nouveau driver isnt working well with Minecraft. And the solution is installing the Nivia driver, but it inst working right.

So how old is your computer?

If your computer is newer the latest Nvidia driver or beta Nvidia driver is more likely what you need to run Ubuntu 11.10. 

Installing  Nvidia drivers by hand is, like i said a pain. When you get a kernel update you will have to reinstall your Nvidia drivers before you restart your computer or you will get dumped into a command line system when you reboot. 

There are ppa&#8217;s out there with newer Nvidia drivers available than are found in the Ubuntu repositorys.      
The problem is using these ppa&#8217;s are a huge security risk. Getting updates from who know where is a bad idea.

If you do use that ppa make sure to uninstall your Nvidia drivers in the Additional Drivers if there installed, before installing the new drivers. And don&#8217;t forget to restart your computer after installing the new drivers.

---

### Post by Ciro2010 on 2012-01-14
> **regor210 said:**
> I admire your perseverance. You have some good computer skills. Heres how i see the problem your having. Your Nvidia graphic drivers are ether being installed incorrectly by Ubuntu or you need the newest beta Nvidia driver. There were some big changes in Ubuntu 11.10. Ubuntu 11.10 is cutting edge technology. Ubuntu 10.04 LTS is more stable. LTS meaning Long Term Support. Its not hard to manually fix small Nvidia graphic drivers configuration problems in xorg.conf on Ubuntu 10.04. 

Your open source Nouveau driver isnt working well with Minecraft. And the solution is installing the Nivia driver, but it inst working right.

So how old is your computer?

If your computer is newer the latest Nvidia driver or beta Nvidia driver is more likely what you need to run Ubuntu 11.10. 

Installing  Nvidia drivers by hand is, like i said a pain. When you get a kernel update you will have to reinstall your Nvidia drivers before you restart your computer or you will get dumped into a command line system when you reboot. 

There are ppa’s out there with newer Nvidia drivers available than are found in the Ubuntu repositorys.      
The problem is using these ppa’s are a huge security risk. Getting updates from who know where is a bad idea.

If you do use that ppa make sure to uninstall your Nvidia drivers in the Additional Drivers if there installed, before installing the new drivers. And don’t forget to restart your computer after installing the new drivers.

My computer is really new, it's 2-3 months old!

So.. if i try to install ubuntu 10.04 alongside with ubuntu 11.10, will I be able to fix it at least on the 10.04?

---

### Post by regor210 on 2012-01-15
If the problem is that the Nvidia drivers are being installed incorrectly, the odds are good that 10.40 can be made to work.

If the problem is your Nvidia hardware is too new for the current drivers that are available in the 11.10 repositories then no Ubuntu 10.04 will not help. In this case you would need the NVidia 295.09 beta driver to get it up and working.

---

### Post by Ciro2010 on 2012-01-15
> **regor210 said:**
> If the problem is that the Nvidia drivers are being installed incorrectly, the odds are good that 10.40 can be made to work.

If the problem is your Nvidia hardware is too new for the current drivers that are available in the 11.10 repositories then no Ubuntu 10.04 will not help. In this case you would need the NVidia 295.09 beta driver to get it up and working.


But  as i said the problem is not the driver itself, is the "X" driver or whatever it is that i still don't understand IS MISSING, it's not in the computer, googling this I saw some conversation about an "X" server, I don't know how but it is not in my computer...

---

### Post by regor210 on 2012-01-15
GNU/Linux

I'll over simplify things a bit so a new person can understand.

Back in the old days Linux was grate Internet file server. When you logged in you only got a command prompt $.

Xserver came along and ran on top giving us a GUI or Windows like operating system, you know like the use of the mouse and icons ect....

Xserver was ugly and plain so People made Windows managers like Gnome, KDE and X to run on top of Xserver.  X like in Xubuntu.

Over time Gnome and all of its parts including Xserver became big and messy. When someone tried to place it in a tv or pad or other mobile device it was a poor fit, like trying to put a truck motor in a motorcycle.

As of Ubuntu 11.10 , Ubuntu has gone it own way creating the Unity windows manager. Unity is fast, light and easy to use, but its bran new. And I for one am still trying to catch up with all the changes.
        
So when you start your computer if your not in a command line system $ and you have a GUI or window then your using some from of Xserver and a windows manager.

A problem with using GUN/Linux Ubuntu is some times new hardware does not have a good driver so it will not work properly. Hardware manufacturers make there products to work with the Windows operating system. Linux is an after thought and in some cases we have to wait for Linux drivers.

Your problem is your Linux Nvidia driver ether isn't or cant install the 3D part of the driver you need to play Minecraft. As in OpenGL, GLX.

A newer Nvidia may help.

---

### Post by Ciro2010 on 2012-01-15
> **regor210 said:**
> GNU/Linux

I'll over simplify things a bit so a new person can understand.

Back in the old days Linux was grate Internet file server. When you logged in you only got a command prompt $.

Xserver came along and ran on top giving us a GUI or Windows like operating system, you know like the use of the mouse and icons ect....

Xserver was ugly and plain so People made Windows managers like Gnome, KDE and X to run on top of Xserver.  X like in Xubuntu.

Over time Gnome and all of its parts including Xserver became big and messy. When someone tried to place it in a tv or pad or other mobile device it was a poor fit, like trying to put a truck motor in a motorcycle.

As of Ubuntu 11.10 , Ubuntu has gone it own way creating the Unity windows manager. Unity is fast, light and easy to use, but its bran new. And I for one am still trying to catch up with all the changes.
        
So when you start your computer if your not in a command line system $ and you have a GUI or window then your using some from of Xserver and a windows manager.

A problem with using GUN/Linux Ubuntu is some times new hardware does not have a good driver so it will not work properly. Hardware manufacturers make there products to work with the Windows operating system. Linux is an after thought and in some cases we have to wait for Linux drivers.

Your problem is your Linux Nvidia driver ether isn't or cant install the 3D part of the driver you need to play Minecraft. As in OpenGL, GLX.

A newer Nvidia may help.

WOW that was really clear, thanks for taking the time to explain it all to me!
Anyway that X: that disappeared in my computer was just a little recovery partition that came up with my ASUS laptop, so it was nothing to worry about

And i think i'm going to get ubuntu 10.04 now.. thanks for your help,  I will post results when done!

---

### Post by regor210 on 2012-01-15
Does your ASUS laptop have a Nvidia Optimus/Intel hybrid graphics card?

Run this and post it 
lspci -vmk | grep -A 8 -B 2 VGA

If yes then you may need Bumblebee.

I would be more inclined to trust a ppa from a Linux project like the Hybrid Graphics Linux team.

[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)

---

### Post by Ciro2010 on 2012-01-16
> **regor210 said:**
> Does your ASUS laptop have a Nvidia Optimus/Intel hybrid graphics card?

Run this and post it 
lspci -vmk | grep -A 8 -B 2 VGA

If yes then you may need Bumblebee.

I would be more inclined to trust a ppa from a Linux project like the Hybrid Graphics Linux team.

[https://launchpad.net/~hybrid-graphics-linux]("https://launchpad.net/%7Ehybrid-graphics-linux")


Did it, got this

```
Device:    00:02.0
Class:    VGA compatible controller
Vendor:    Intel Corporation
Device:    2nd Generation Core Processor Family Integrated Graphics Controller
SVendor:    ASUSTeK Computer Inc.
SDevice:    Device 1662
Rev:    09
Driver:    i915
Module:    i915

--

Device:    01:00.0
Class:    VGA compatible controller
Vendor:    nVidia Corporation
Device:    GF106 [GeForce GT 555M]
SVendor:    ASUSTeK Computer Inc.
SDevice:    Device 1662
Rev:    a1
Driver:    nouveau
Module:    nouveau
Module:    nvidiafb

```

---

### Post by regor210 on 2012-01-16
It looks like you do have a Hybrid Graphics card.

You have both an Intel i915 and a NVIDIA GeForce GT 555M graphics card in your laptop.

Looks like you need Bumblebee and they do support Ubuntu 11.10.

Whats your ASUS laptop model?

---

### Post by Ciro2010 on 2012-01-16
> **regor210 said:**
> It looks like you do have a Hybrid Graphics card.

You have both an Intel i915 and a NVIDIA GeForce GT 555M graphics card in your laptop.

Looks like you need Bumblebee and they do support Ubuntu 11.10.

Whats your ASUS laptop model?


ASUS laptop K73S, also here on the box it says the graphics card is NVidia geforce GT 540M :)

---

### Post by regor210 on 2012-01-16
It looks like you do have &#65279;Optimus/Intel hybrid graphics.

Sorry I did not catch it earlier, I never seen a hybrid graphics card before.


nVidia Optimus and Ubuntu explained [UPDATED]

[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

look at this thread. Its a bit old.

---

### Post by Ciro2010 on 2012-01-19
> **regor210 said:**
> It looks like you do have &#65279;Optimus/Intel hybrid graphics.

Sorry I did not catch it earlier, I never seen a hybrid graphics card before.


nVidia Optimus and Ubuntu explained [UPDATED]

[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

look at this thread. Its a bit old.


That says there are no drivers available to fix it.. but at the beginning it says "someone did it" with this link: [https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)

What should I do? :/

---

### Post by regor210 on 2012-01-21
Optimus/Intel hybrid graphics

It looks to me like the Optimus video card was designed to save power on laptops.

The Intel card is simple and should save on battery life.

The Nvidia card is better for playing games like Minecraft but uses more power.

With Bumblebee you can choose the card you would like to use. There should be a menu that lets you pick the card you need.

Your other choice is found in the same thread   

cascade9
&#8220;One adition- some laptops with switchable graphics/optimus have a BIOS setting that allows you to force the nvidia GPU, disable the nvidia GPU and/or disbale the intel video. 

If you can force the nvidia GPU, opr disable the intel video in the BIOS then you can install the nvidia drivers with no issues.&#8221;

So if you check your  BIOS setting there may be a way to force the use of the Nvidia card. But this could shorten your how long your battery will run your laptop.

If it were me I would try Bumblebee. It looks like a good active project that has been up and going for some time now.  

[https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)

Sorry been off-line 2 days due to the ice storm taking down the power lines and Internet.

---

### Post by Ciro2010 on 2012-01-22
> **regor210 said:**
> Optimus/Intel hybrid graphics

It looks to me like the Optimus video card was designed to save power on laptops.

The Intel card is simple and should save on battery life.

The Nvidia card is better for playing games like Minecraft but uses more power.

With Bumblebee you can choose the card you would like to use. There should be a menu that lets you pick the card you need.

Your other choice is found in the same thread   

cascade9
“One adition- some laptops with switchable graphics/optimus have a BIOS setting that allows you to force the nvidia GPU, disable the nvidia GPU and/or disbale the intel video. 

If you can force the nvidia GPU, opr disable the intel video in the BIOS then you can install the nvidia drivers with no issues.”

So if you check your  BIOS setting there may be a way to force the use of the Nvidia card. But this could shorten your how long your battery will run your laptop.

If it were me I would try Bumblebee. It looks like a good active project that has been up and going for some time now.  

[https://launchpad.net/~bumblebee/+archive/stable]("https://launchpad.net/%7Ebumblebee/+archive/stable")

Sorry been off-line 2 days due to the ice storm taking down the power lines and Internet.


Ok, but honestly.. I read how to install the PPA on that link.. but then what should i do to "open" bumblebee and select the nvidia card?

I mean, first I open terminal, then I type  
```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates


```
Then 
```
sudo apt-get update
```

Then what?

---

### Post by Jaxke on 2012-01-22
This is annoying. I got these black dead pixels everywhere. They make the game unplayable. Any fix for this?
[IMG]http://i.minus.com/jV7G24smhlFFp.png[/IMG]
[IMG]http://i.minus.com/jiNZhhJuqN5f6.png[/IMG]

i5 Core 2,4GHz, Intel 3000HD, 6GB.

---

### Post by regor210 on 2012-01-22
**(UPDATED X3)**
**[COLOR="Black"]How to install Bumblebee[/COLOR]**

Ciro2010 try

Bumblebee Stable PPA
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)
[https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)

$ sudo apt-get purge nvidia-current

$ sudo add-apt-repository ppa:bumblebee/stable
$ sudo apt-get update

$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
$ sudo apt-get update

$ sudo apt-get install bumblebee

After installation, allow yourself to use Bumblebee (replace USER by your username):

For me this next line would look like ($ sudo usermod -a -G bumblebee regor) because my user name is regor when I log in. So replace USER with your user name.


$ sudo usermod -a -G bumblebee USER

$ sudo apt-get install virtualgl-libs:i386 libgl1-mesa-glx:i386 libc6:i386

$ sudo reboot


Now after your laptop restarts try
$ glxspheres

Then try

$ optirun glxspheres

Then try 

$ optirun java -jar .minecraft/minecraft.jar

Let me know how it go's.

---

### Post by regor210 on 2012-01-22
Jaxke run this in a terminal 

$ lspci -vmk | grep -A 8 -B 2 VGA

and post it.

---

### Post by Ciro2010 on 2012-01-22
> **regor210 said:**
> Ciro2010 try

Bumblebee Stable PPA
[https://launchpad.net/~bumblebee/+archive/stable]("https://launchpad.net/%7Ebumblebee/+archive/stable")

$ sudo apt-get purge nvidia-current
$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates


After installation, allow yourself to use Bumblebee (replace $USER by your username):

For me this next line would look like ($ sudo usermod -a -G bumblebee $regor) because my user name is regor when I log in. So replace USER with your user name.


$ sudo usermod -a -G bumblebee $USER

$ sudo apt-get install virtualgl-libs:i386 libgl1-mesa-glx:i386 libc6:i386

$ sudo reboot


Now after your laptop restarts try
$ glxspheres

Then try

$ optirun glxspheres

Then try 

$ optirun java -jar .minecraft/minecraft.jar

Let me know how it go's.


when i do $ sudo usermod -a -G bumblebee $USER

It says: usermod: group 'bumblebee' does not exist

*edit: also tried to do apt-get update first, gives me the same error

---

### Post by regor210 on 2012-01-22
sorry
try this


$ sudo apt-get update
$ sudo apt-get install bumblebee
$ sudo usermod -a -G bumblebee $USER
$ sudo apt-get install virtualgl-libs:i386 libgl1-mesa-glx:i386 libc6:i386
$ sudo reboot

---

### Post by Ciro2010 on 2012-01-23
> **regor210 said:**
> sorry
try this


$ sudo apt-get update
$ sudo apt-get install bumblebee
$ sudo usermod -a -G bumblebee $USER
$ sudo apt-get install virtualgl-libs:i386 libgl1-mesa-glx:i386 libc6:i386
$ sudo reboot


When I try to apt-get install bumblebee I get this:

```
sudo apt-get install bumblebee
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bumblebee

```

---

### Post by regor210 on 2012-01-23
bumblebee
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)
[https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)

One more time.

$ sudo add-apt-repository ppa:bumblebee/stable
$ sudo apt-get update
$ sudo apt-get install bumblebee
$ sudo usermod -a -G bumblebee $USER
$ sudo apt-get install virtualgl-libs:i386 libgl1-mesa-glx:i386 libc6:i386
$ sudo reboot

---

### Post by Ciro2010 on 2012-01-23
> **regor210 said:**
> bumblebee
[https://launchpad.net/~hybrid-graphics-linux]("https://launchpad.net/%7Ehybrid-graphics-linux")
[https://launchpad.net/~bumblebee/+archive/stable]("https://launchpad.net/%7Ebumblebee/+archive/stable")

One more time.

$ sudo add-apt-repository ppa:bumblebee/stable
$ sudo apt-get update
$ sudo apt-get install bumblebee
$ sudo usermod -a -G bumblebee $USER
$ sudo apt-get install virtualgl-libs:i386 libgl1-mesa-glx:i386 libc6:i386
$ sudo reboot



OHMYGOD NEVERMIND!!! NEVERMIND!!! READ THIS!!!!!! IT WORKS!!! I ******* LOVE YOU!!! 

Thanks a lot for answering me after all the problems i've had, even after so many days! 


***EDIT: Wait, When i play, i get like half of the screen bugged, like a triangle that bugs out.. should I install the NVidia driver? (the one recommended on additional drivers)??? I mean, will it have problems with bumblebee?

---

### Post by regor210 on 2012-01-23
Don't install the Nvidia drivers unless Bumblebee setup asks you to.  Bumblebee should have set you up with the latest Nvidia driver.

Try starting Minecraft like this

$ optirun java -jar .minecraft/minecraft.jar

if thats no good try this

$  java -jar .minecraft/minecraft.jar

If still no luck, look for the Bumblebee menu and find what works for you.
This should be about the best video driver Linux can offer you.

---

### Post by Ciro2010 on 2012-01-23
> **regor210 said:**
> Don't install the Nvidia drivers unless Bumblebee setup asks you to.  Bumblebee should have set you up with the latest Nvidia driver.

Try starting Minecraft like this

$ optirun java -jar .minecraft/minecraft.jar

if thats no good try this

$  java -jar .minecraft/minecraft.jar

If still no luck, look for the Bumblebee menu and find what works for you.
This should be about the best video driver Linux can offer you.


I have Mineshafter on my desktop, don't have a minecraft premium acc.

Anyway i can't "optirun glxspheres" it says i'm not in the bumblebee group...

```
ciro@K73SV:~$ sudo usermod -a -G bumblebee $ciro
[sudo] password for ciro: 
Usage: usermod [options] LOGIN

Options:
  -c, --comment COMMENT         new value of the GECOS field
  -d, --home HOME_DIR           new home directory for the user account
  -e, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
  -f, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -g, --gid GROUP               force use GROUP as new primary group
  -G, --groups GROUPS           new list of supplementary GROUPS
  -a, --append                  append the user to the supplemental GROUPS
                                mentioned by the -G option without removing
                                him/her from other groups
  -h, --help                    display this help message and exit
  -l, --login NEW_LOGIN         new value of the login name
  -L, --lock                    lock the user account
  -m, --move-home               move contents of the home directory to the
                                new location (use only with -d)
  -o, --non-unique              allow using duplicate (non-unique) UID
  -p, --password PASSWORD       use encrypted password for the new password
  -s, --shell SHELL             new login shell for the user account
  -u, --uid UID                 new UID for the user account
  -U, --unlock                  unlock the user account
  -Z, --selinux-user            new SELinux user mapping for the user account

ciro@K73SV:~$ optirun glxspheres
[ERROR]You've no permission to communicate with the Bumblebee daemon. Try adding yourself to the 'bumblebee' group
[ERROR]Could not connect to bumblebee daemon - is it running?
```

---

### Post by regor210 on 2012-01-23
After installation, allow yourself to use Bumblebee (replace $USER by your username):

For me this next line would look like ($ sudo usermod -a -G bumblebee $regor) because my user name is regor when I log in. So replace **USER** with your user name.


$ sudo usermod -a -G bumblebee $USER

---

### Post by Ciro2010 on 2012-01-23
> **regor210 said:**
> After installation, allow yourself to use Bumblebee (replace $USER by your username):

For me this next line would look like ($ sudo usermod -a -G bumblebee $regor) because my user name is regor when I log in. So replace **USER** with your user name.


$ sudo usermod -a -G bumblebee $USER

Read the beginning of the code in my  last reply, I typed the command correctly and it gives me a list of commands...

---

### Post by regor210 on 2012-01-23
**Sorry no $ needed**

After installation, allow yourself to use Bumblebee (replace $USER by your username):

For me this next line would look like ($ sudo usermod -a -G bumblebee regor) because my user name is regor when I log in. So replace USER with your user name.


$ sudo usermod -a -G bumblebee USER

---

### Post by Ciro2010 on 2012-01-23
> **regor210 said:**
> **Sorry no $ needed**

After installation, allow yourself to use Bumblebee (replace $USER by your username):

For me this next line would look like ($ sudo usermod -a -G bumblebee regor) because my user name is regor when I log in. So replace USER with your user name.


$ sudo usermod -a -G bumblebee USER

Done.

the commands java -jar Desktop/Mineshafter.jar  and optirun java -jar Desktop/Mineshafter.jar
Are not working, it gives me an error,

I am currently using SUN JAVA, if i install OPENJDK the command will work, but with OPENJDK i get the error i had at the beginning of the thread... so what is the command for sun java?

BTW this is the error I get:

```
ciro@K73SV:~$ optirun java -jar Desktop/Mineshafter.jar
Current proxy version: 3.2
Gotten proxy version: 3.2
Error starting launcher:
java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:601)
    at mineshafter.MineClient.startLauncher(MineClient.java:104)
    at mineshafter.MineClient.startLauncher(MineClient.java:108)
    at mineshafter.MineClient.main(MineClient.java:77)
Caused by: java.awt.HeadlessException
    at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:197)
    at java.awt.Window.<init>(Window.java:534)
    at java.awt.Frame.<init>(Frame.java:420)
    at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:27)
    at net.minecraft.LauncherFrame.main(LauncherFrame.java:158)
    ... 7 more

```

EDIT: Also, this is what i get when i open the game with sun java, normally (this thing flashes for like a millisecond every 2-3 seconds)

(attachment)

---

### Post by regor210 on 2012-01-23
I take it that 

$ optirun glxspheres

is working?

Are you running minecraft without Mod's?

We have Minecraft up and going on 6 computers here + family.

I use this sh script to install it

[http://ubuntuforums.org/showthread.php?t=1726735](http://ubuntuforums.org/showthread.php?t=1726735)

You need a sun java ppa up for it to work. like the one found here.

[http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric](http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric)

It may be worth a try.

---

### Post by Ciro2010 on 2012-01-23
> **regor210 said:**
> I take it that 

$ optirun glxspheres

is working?

Are you running minecraft without Mod's?

We have Minecraft up and going on 6 computers here + family.

I use this sh script to install it

[http://ubuntuforums.org/showthread.php?t=1726735](http://ubuntuforums.org/showthread.php?t=1726735)

You need a sun java ppa up for it to work. like the one found here.

[http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric](http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric)

It may be worth a try.

LOL those two links are exactly how i installed minecraft and sun java! and optirun glxspheres is working

EDIT: what is bumblebee is using the intel card instead of the nvidia? maybe thats why the graphics have this problem! (i didnt have it on windows with the nvidia card)

---

### Post by regor210 on 2012-01-23
I&#8217;m about out of ideas.

you could make sure the bumblebeed  daemon is running.

$ sudo bumblebeed --daemon

&#65279;$ optirun java -jar .minecraft/minecraft.jar

Did you try uninstalling and reinstalling Minecraft for the new drivers?


Other than that it looks like we did everything right, heres a post about Minecraft and &#65279;bumblebee

[http://e0d.com/blog/dell-xps-15-l502xrunning-linux-lubuntu-11-04-with-nvidia-optimus-support](http://e0d.com/blog/dell-xps-15-l502xrunning-linux-lubuntu-11-04-with-nvidia-optimus-support)

&#8220;After the install you can launch a program using the command optirun

    Example: optirun java -jar ~/Downloads/minecraft.jar 

This will launch minecraft using the nvidia card.&#8221;

The only deference is are Minecraft isnt in Downloads.


You may find more help with  Bumblebee here.

[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)
Please join the bumblebee channel on Freenode if you wish to help.

And here
 
[https://github.com/Bumblebee-Project/Bumblebee/wiki/](https://github.com/Bumblebee-Project/Bumblebee/wiki/)

And there is this

$ man optirun

$ optirun --help

---

### Post by Ciro2010 on 2012-01-24
> **regor210 said:**
> I&#8217;m about out of ideas.

you could make sure the bumblebeed  daemon is running.

$ sudo bumblebeed --daemon

&#65279;$ optirun java -jar .minecraft/minecraft.jar

Did you try uninstalling and reinstalling Minecraft for the new drivers?


Other than that it looks like we did everything right, heres a post about Minecraft and &#65279;bumblebee

[http://e0d.com/blog/dell-xps-15-l502xrunning-linux-lubuntu-11-04-with-nvidia-optimus-support](http://e0d.com/blog/dell-xps-15-l502xrunning-linux-lubuntu-11-04-with-nvidia-optimus-support)

&#8220;After the install you can launch a program using the command optirun

    Example: optirun java -jar ~/Downloads/minecraft.jar 

This will launch minecraft using the nvidia card.&#8221;

The only deference is are Minecraft isnt in Downloads.


You may find more help with  Bumblebee here.

[https://launchpad.net/~hybrid-graphics-linux]("https://launchpad.net/%7Ehybrid-graphics-linux")
Please join the bumblebee channel on Freenode if you wish to help.

And here
 
[https://github.com/Bumblebee-Project/Bumblebee/wiki/](https://github.com/Bumblebee-Project/Bumblebee/wiki/)

And there is this

$ man optirun

$ optirun --help

Nevermind, i tried it again on a fresh install (I formatted so many times i have only a few important files on dropbox) and it worked! now it works fine with optirun, and without it it gives me the glitch.

I just have one problem now, It has no sound D: (I cheched setting both on MC and my computer, and the audio works on youtube)

---

### Post by regor210 on 2012-01-24
Try this

&#65279;$ optirun  padsp java -jar .minecraft/minecraft.jar

or this

&#65279;$ optirun padsp java -Xms1024M -Xmx1024M -Djava.net.preferIPv4Stack=true -jar  .minecraft/minecraft.jar


[http://ubuntuforums.org/showthread.php?t=1613942](http://ubuntuforums.org/showthread.php?t=1613942)

[http://manpages.ubuntu.com/manpages/hardy/man1/padsp.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/padsp.1.html)
"DESCRIPTION

       padsp  starts  the  specified  program  and redirects its access to OSS
       compatible  audio  devices  (/dev/dsp  and  auxiliary  devices)  to   a
       PulseAudio sound server."

---

### Post by Ciro2010 on 2012-01-24
> **regor210 said:**
> Try this

&#65279;$ optirun  padsp java -jar .minecraft/minecraft.jar

or this

&#65279;$ optirun padsp java -Xms1024M -Xmx1024M -Djava.net.preferIPv4Stack=true -jar  .minecraft/minecraft.jar


[http://ubuntuforums.org/showthread.php?t=1613942](http://ubuntuforums.org/showthread.php?t=1613942)

[http://manpages.ubuntu.com/manpages/hardy/man1/padsp.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/padsp.1.html)
"DESCRIPTION

       padsp  starts  the  specified  program  and redirects its access to OSS
       compatible  audio  devices  (/dev/dsp  and  auxiliary  devices)  to   a
       PulseAudio sound server."

Not working :(

EDIT: When i open minecraft via terminal i get this at the beginning (The game starts and works after it, of course with no sound)
```

Failed to open device (/dev/input/event13): Failed to open device /dev/input/event13 (13)

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

```***EDIT: This is not the problem, i tried opening MC as sudo, and this didn't show up, but audio still didn't work and unfortunately it deleted my save files.. crap

---

### Post by regor210 on 2012-01-24
Looks like a permission issue.

[http://www.worldofminecraft.com/content/linux-error](http://www.worldofminecraft.com/content/linux-error)

 “/dev/input/event ownership problems
If you see an error like:
Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13) 
This means that the current user doesn't have permission to access the direct input devices.

$ sudo chmod go=u /dev/input/event*

Should fix the problems here."

Try this

$ sudo chmod go=u /dev/input/event*

$ optirun padsp java -jar .minecraft/minecraft.jar

---

### Post by Ciro2010 on 2012-01-24
> **regor210 said:**
> Looks like a permission issue.

[http://www.worldofminecraft.com/content/linux-error](http://www.worldofminecraft.com/content/linux-error)

 “/dev/input/event ownership problems
If you see an error like:
Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13) 
This means that the current user doesn't have permission to access the direct input devices.

$ sudo chmod go=u /dev/input/event*

Should fix the problems here."

Try this

$ sudo chmod go=u /dev/input/event*

$ optirun padsp java -jar .minecraft/minecraft.jar

Now i get this instead of that one:
```

(java:10176): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:10176): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:10176): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:10176): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
```

---

### Post by regor210 on 2012-01-24
[http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line](http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line)

There was a bug in Ubuntu 11.10, see if this is installed?

$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install gtk2-engines-pixbuf

---

### Post by Ciro2010 on 2012-01-24
> **regor210 said:**
> [http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line](http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line)

There was a bug in Ubuntu 11.10, see if this is installed?

$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install gtk2-engines-pixbuf

Tried that, now the error doesn't show up but still no sound.. this is the beginning of what i get in terminal while loading minecraft:
```

ciro@K73SV:~$ optirun padsp java -jar Desktop/mc.jar
Current proxy version: 3.2
Gotten proxy version: 3.2
Request: GET http://mcupdate.tumblr.com/
No handler. Piping.
Request: GET http://www.minecraft.net/images/bg_main.png
No handler. Piping.
Piping finished, data size: 29333
Piping finished, data size: 434
Request: GET http://pixel.quantserve.com/pixel/p-19UtqE8ngoZbM.gif
No handler. Piping.
Piping finished, data size: 35
executePost: http://session.minecraft.net/game/getversion.jsp
Request: POST http://session.minecraft.net/game/getversion.jsp
GetVersion
To: http://mineshafter.appspot.com/game/getversion.jsp?proxy=3.2
27 achievements
174 recipes
Setting user: Ciro2010, *whoops, password?*
Loading: net.java.games.input.LinuxEnvironmentPlugin
Linux plugin claims to have found 9 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.

Request: GET http://s3.amazonaws.com/MinecraftResources/
No handler. Piping.
```EDIT::: NEEWS! While I was playing i heard the sound of a creeper dying in lava, and then one of the creepy noises you hear when near caves... but no eating, walking, breaking blocks and other sounds.. I'll try rebooting, will tell you what happens.

*REEDIT: Rebooted pc, but nothing.. i'm wondering what was it when i heard the dieing creeper and the noise..

---

### Post by regor210 on 2012-01-24
Try This

[http://ubuntuforums.org/showthread.php?p=11371050](http://ubuntuforums.org/showthread.php?p=11371050)

$ sudo apt-get update
$ sudo apt-get install dconf-tools
$ dconf-editor

&#65279; 

"navigate to:
 
org/gnome/desktop/sounds.


&#65279;Make sure event sounds & input feedback sounds are both ticked & change theme name to ubuntu.
Done."


$ sudo chmod go=u /dev/input/event*

$ optirun java -jar .minecraft/minecraft.jar

or 

$ optirun padsp java -jar .minecraft/minecraft.jar

---

### Post by Ciro2010 on 2012-01-25
> **regor210 said:**
> Try This

[http://ubuntuforums.org/showthread.php?p=11371050](http://ubuntuforums.org/showthread.php?p=11371050)

$ sudo apt-get update
$ sudo apt-get install dconf-tools
$ dconf-editor

&#65279; 

"navigate to:
 
org/gnome/desktop/sounds.


&#65279;Make sure event sounds & input feedback sounds are both ticked & change theme name to ubuntu.
Done."


$ sudo chmod go=u /dev/input/event*

$ optirun java -jar .minecraft/minecraft.jar

or 

$ optirun padsp java -jar .minecraft/minecraft.jar


Done all that, even rebooted but still no sound :/

EDIT: Remember when i said i heard a creeper die and a cave sound? Well I checked my minecraft folder, and there are a few sounds there, like cows, cowshurt, chicken, chichenhurt, creeper hurt, creeper dead, cave12345, water, rain and any others, so i picked one i can make myself, like WATER, i poured a bucket of water and i hear water... WHAT so the sound works, just some sounds don't work?

... But, some of the sounds in the folder don't work, like creeper 1, 2, 3, 4 (creeper hurt).. when i hit a creeper i won't hear any sound, so i still don't understand the problem

***EDIT: I found out the sound files i opened, will show up in minecraft, but i was missing some sounds, so i downloaded them from the internet.. now i'm trying them.. FIXED! YES! I HAVE SOUND NOW



*LASTEDIT: Damn, my pc gives me an error! on the top right of the screen, near the time i get a STOP sign, saying Error: BrokenCount > 0

When i try to apt-get upgrade or apt-get install anyting It says:

```
dpkg: error: reading package info file '/var/lib/dpkg/status': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by regor210 on 2012-01-25
Restart your computer and when you see the GNU GRUB menu come up use the up or down arrow key to select  

Ubuntu with Linux 3.0.15-generic (**recovery mode)**

The key being (**recovery mode)**
If you only have one operating system installed the GRUB menu will flash by fast. So don&#8217;t blink or you&#8217;ll miss it.LoL.

At the next menu use

dpkg      Repair broken packages

See if this gets it.

If not use this but dont change anything. Look for text in red and post it. 

$ gedit /var/lib/dpkg/status

---

### Post by Ciro2010 on 2012-01-25
> **regor210 said:**
> Restart your computer and when you see the GNU GRUB menu come up use the up or down arrow key to select  

Ubuntu with Linux 3.0.15-generic (**recovery mode)**

The key being (**recovery mode)**
If you only have one operating system installed the GRUB menu will flash by fast. So don’t blink or you’ll miss it.LoL.

At the next menu use

dpkg      Repair broken packages

See if this gets it.


I'm having troubles starting the grub... I can't get it to show! I tried mofidying the 
**/etc/default/grub**



And putting GRUB_HIDDEN_TIMEOUT=1
But i still can't get it to show up not even by holding shift :/

---

### Post by regor210 on 2012-01-25
Try this

$ sudo dpkg --configure -a
$ sudo apt-get -f install
$ sudo apt-get update


if that dose not work just look in here but dont change anything. Look for text in red and post it.

$ gedit /var/lib/dpkg/status

---

### Post by Ciro2010 on 2012-01-26
> **regor210 said:**
> Try this

$ sudo dpkg --configure -a
$ sudo apt-get -f install
$ sudo apt-get update


if that dose not work just look in here but dont change anything. Look for text in red and post it.

$ gedit /var/lib/dpkg/status


Not working, I decided to **** this, backup my current world and the music files (apparently it's a common bug in this last version) and formatted, now it works perfectly, thanks for the help, regor!

---

### Post by regor210 on 2012-01-26
**WHOOOT!!!!!! Yhaaaaa!!!!!!**

Glade to help!!

---

### Post by Jaxke on 2012-01-26
> **regor210 said:**
> Jaxke run this in a terminal 

$ lspci -vmk | grep -A 8 -B 2 VGA

and post it.
Device: 00:02.0
Class:  VGA compatible controller
Vendor: Intel Corporation
Device: 2nd Generation Core Processor Family Integrated Graphics Controller
SVendor:        Acer Incorporated [ALI]
SDevice:        Device 0504
Rev:    09
Driver: i915
Module: i915

It seems it's because of my video card I guess(Laptop's integrated Intel 3000HD). Although Minecraft runs perfectly on my Windows 7 partition(too bad I rarely use it :p )

---

### Post by regor210 on 2012-01-26
Ok, it looks like your using the best drive available.

There are 3 things that may improve your performance.

1st check your computers BIOS and see if you can increase your graphics shared memory.

2nd In Minecraft goto Options > Video settings and make

**Graphics Fast**
**Smooth Lighting OFF**
**Performance Max FPS**
**Clouds off**

Then play with  
**Render Distance **
Far = slow, more lag
Tiny = fast, less lag

Then and try
**Particles minimal**

3rd if you have 2 or more Gigs of system ram you can make more memory available to Minecraft
by launching it with

$ java -Xms1024M -Xmx1024M  -jar .minecraft/minecraft.jar

The 1024M in this command makes 1 Gig available to Minecraft. The default is .5 Gig.
---------------------------
Last are you using sun-java?

Sun-java works best with Minecraft.

You can check to see what java you are using with  
$ sudo update-alternatives --config java

OpenJDK comes with Ubuntu by default.

---

### Post by Jaxke on 2012-01-27
> **regor210 said:**
> Ok, it looks like your using the best drive available.

There are 3 things that may improve your performance.

1st check your computers BIOS and see if you can increase your graphics shared memory.

2nd In Minecraft goto Options > Video settings and make

**Graphics Fast**
**Smooth Lighting OFF**
**Performance Max FPS**
**Clouds off**

Then play with  
**Render Distance **
Far = slow, more lag
Tiny = fast, less lag

Then and try
**Particles minimal**

3rd if you have 2 or more Gigs of system ram you can make more memory available to Minecraft
by launching it with

$ java -Xms1024M -Xmx1024M  -jar .minecraft/minecraft.jar

The 1024M in this command makes 1 Gig available to Minecraft. The default is .5 Gig.
---------------------------
Last are you using sun-java?

Sun-java works best with Minecraft.

You can check to see what java you are using with  
$ sudo update-alternatives --config java

OpenJDK comes with Ubuntu by default.
None of them worked :( 

I tried the java command and here's the output:

```
There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                            Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-6-openjdk/jre/bin/java         1061      auto mode
  1            /usr/bin/gij-4.6                                 1046      manual mode
  2            /usr/lib/jvm/java-6-openjdk/jre/bin/java         1061      manual mode
  3            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1051      manual mode

Press enter to keep the current choice
[*], or type selection number: 
```What am I supposed to do? Sorry for being a noob :P

E: And yeah, there was no option for video card in my BIOS menu. The only thing it has is boot order(and some other basic stuff about hard drives...)

---

### Post by regor210 on 2012-01-27
I use this Bash script to install Minecraft and Java. 
If your using the newest Ubuntu 11.10 Oneiric Ocelot first look at my posts on the Java situation on pages 5 & 6 before you try and run it.

[http://ubuntuforums.org/showthread.php?t=1726735](http://ubuntuforums.org/showthread.php?t=1726735)

--------------------------------
One more thing about integrated Intel graphics.

Minecraft Linux somtimes suffers from sticky keys, When it happens with Intel graphics the mouse loses its lock and will not lock back in with out logging out.

I fix this by changing Ubuntu or Lubuntu keyboard setting 

in Lubuntu 
Repeat delay    400
Repeat interval 30   

works for me.

In Ubuntu press Print Scrn to take a picture of your setting then make the 
Delay a little longer
Speed a little slower

should do the trick.

---

