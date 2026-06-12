---
title: "Minecraft crashing Problem"
date: 2012-06-18
forum: Gaming &amp; Leisure
---

### Post by RocketPenguin on 2012-06-18
Ok, minecraft/ubuntu is not being easy on me. I was playing minecraft, then closed it, little later try opening it, but get this message:   
        Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.




--- BEGIN ERROR REPORT 7cf3a456 --------
Generated 6/18/12 6:22 PM

Minecraft: Minecraft 1.2.5
OS: Linux (amd64) version 3.2.0-25-generic
Java: 1.6.0_24, Sun Microsystems Inc.
VM: OpenJDK 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: X Error - disp: 0x7fd984085870 serial: 31 error: BadRequest (invalid request code or no such operation) request_code: 135 minor_code: 14
    at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:268)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
    at org.lwjgl.opengl.Display.create(Display.java:854)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(SourceFile:236)
    at net.minecraft.client.Minecraft.run(SourceFile:657)
    at java.lang.Thread.run(Thread.java:679)
--- END ERROR REPORT 8f7632ae ----------



I reinstalled minecraft, deleted .minecraft, redownloaded it, nothing. This is crazy, and i just posted this, but could you help me, maybe?

Edit: I now realize that i am also getting some logs from java in my home folder [http://pastebin.com/DQVP0ySt](http://pastebin.com/DQVP0ySt)

---

### Post by Balmung4500 on 2012-06-18
i get the same thing

---

### Post by RocketPenguin on 2012-06-18
(I know i have) But have you updated the lwjgl ?

---

### Post by RocketPenguin on 2012-06-18
> **Balmung4500 said:**
> i get the same thing
(I know i have) But have you updated Lwjgl?

---

### Post by regor210 on 2012-06-18
If your using Ubuntu 12.04 you will have to update LWJGL after every Minecraft update that is if you are using  OpenJDK 7 that comes with Ubuntu 12.04.

About the easiest way to do this is to use   

[http://modifyubuntu.com/#minecraft](http://modifyubuntu.com/#minecraft)

If you have used this site before you will only need to run the 3rd block starting with “cd ~/Downloads;......”

---

### Post by RocketPenguin on 2012-06-18
but, i have already updated it.

---

### Post by RocketPenguin on 2012-06-18
> **regor210 said:**
> If your using Ubuntu 12.04 you will have to update LWJGL after every Minecraft update that is if you are using  OpenJDK 7 that comes with Ubuntu 12.04.

About the easiest way to do this is to use   

[http://modifyubuntu.com/#minecraft](http://modifyubuntu.com/#minecraft)

If you have used this site before you will only need to run the 3rd block starting with “cd ~/Downloads;......”
still doesn't work... same error

---

### Post by regor210 on 2012-06-18
Looks like it may be a permissions issue. Just for kicks try

Open a terminal, press ctrl+alt+t all at the same time.  Then cut and paste the following command into the terminal window minus the $
 
$ sudo chmod -R 777 .minecraft

Then try running Minecraft again.

---

### Post by Dlambert on 2012-06-19
What I do to run minecraft (Yes I updated the engine files): 

On my desktop I created Minecraft.sh and inside: 

```
java -Xmx8192M -Xms4096M -cp /home/dlambert/Downloads/minecraft.jar net.minecraft.LauncherFrame
```

That runs the launcher with 8Gigs of ram (I mod a lot) 

Just change to your username and link to minecraft launcher and the amount of memory you wish to use and try it!

Example: java -Xmx2048M -Xms1047M -cp /home/**_YOUR NAME_**/Downloads/minecraft.jar net.minecraft.LauncherFrame (Thats 2Gigs)

---

### Post by SlugSlug on 2012-06-19
Use Oracle java

Add PPA
```
 sudo add-apt-repository ppa:webupd8team/java 
```Refresh sources
```
 sudo apt-get update 
```install 
```
 sudo apt-get install oracle-java7-installer
```


Join us on mc.drunkenslug.com ;)

---

### Post by RocketPenguin on 2012-06-19
> **regor210 said:**
> Looks like it may be a permissions issue. Just for kicks try

Open a terminal, press ctrl+alt+t all at the same time.  Then cut and paste the following command into the terminal window minus the $
 
$ sudo chmod -R 777 .minecraft

Then try running Minecraft again.
same prob...

---

### Post by RocketPenguin on 2012-06-19
1

---

### Post by RocketPenguin on 2012-06-19
> **Dlambert said:**
> What I do to run minecraft (Yes I updated the engine files): 

On my desktop I created Minecraft.sh and inside: 

```
java -Xmx8192M -Xms4096M -cp /home/dlambert/Downloads/minecraft.jar net.minecraft.LauncherFrame
```That runs the launcher with 8Gigs of ram (I mod a lot) 

Just change to your username and link to minecraft launcher and the amount of memory you wish to use and try it!

Example: java -Xmx2048M -Xms1047M -cp /home/**_YOUR NAME_**/Downloads/minecraft.jar net.minecraft.LauncherFrame (Thats 2Gigs)
Oh, i see. My minecraft has to be in my downloads folder. ok. It did open it, but crashed. It gave me an error report in the terminal though.  And, i have four gb of ram so... ya...
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f3455842c58, pid=6916, tid=139862776239872
#
# JRE version: 6.0_24-b24
# Java VM: OpenJDK 64-Bit Server VM (20.0-b12 mixed mode linux-amd64 compressed oops)
# Derivative: IcedTea6 1.11.1
# Distribution: Ubuntu 12.04 LTS, package 6b24-1.11.1-4ubuntu3
# Problematic frame:
# C  [libX11.so.6+0x33c58]  XQueryExtension+0x28
#
# An error report file with more information is saved as:
# /home/jeremiah/hs_err_pid6916.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#
Aborted (core dumped)

---

### Post by regor210 on 2012-06-19
What do you get when you run this minus the $

$ lspci | grep VGA && glxinfo | grep -w 'direct\|OpenGL'

---

### Post by RocketPenguin on 2012-06-20
> **regor210 said:**
> What do you get when you run this minus the $

$ lspci | grep VGA && glxinfo | grep -w 'direct\|OpenGL'
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI M64-S [Mobility Radeon X2300]
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

---

### Post by Redshirt4 on 2012-06-20
Do you have any mods installed?

---

### Post by RocketPenguin on 2012-06-20
> **Redshirt4 said:**
> Do you have any mods installed?
Yes, i did. but ounce it stoped working, i reinstalled mincraft (delete .minecraft) so after it stoped working, no mods

---

### Post by SlugSlug on 2012-06-20
[http://ubuntuforums.org/showpost.php?p=12039461&postcount=9](http://ubuntuforums.org/showpost.php?p=12039461&postcount=9)

---

### Post by regor210 on 2012-06-20
Looks like your 3D video drivers are not working.

1st run this and see if your property drivers are installed.

 $ sudo /usr/bin/jockey-gtk

If yes, lets get some more information about your problem.

#video card and driver information
$ lspci -vmk | grep -A 8 -B 2 VGA

And post what you get.

Also because it was working check to see if an update was interrupted

#  This checks to see what upgrades are needed
$ sudo apt-get update

# This upgrades the software in your system.
$ sudo apt-get upgrade

# This will add additional software and will not change your Ubuntu distribution. It will only upgrade your system with upgrades that are held back intel you ok them.    

$ sudo apt-get dist-upgrade

---

### Post by RocketPenguin on 2012-06-20
> **regor210 said:**
> Looks like your 3D video drivers are not working.

1st run this and see if your property drivers are installed.

 $ sudo /usr/bin/jockey-gtk

If yes, lets get some more information about your problem.

#video card and driver information
$ lspci -vmk | grep -A 8 -B 2 VGA

And post what you get.

Also because it was working check to see if an update was interrupted

#  This checks to see what upgrades are needed
$ sudo apt-get update

# This upgrades the software in your system.
$ sudo apt-get upgrade

# This will add additional software and will not change your Ubuntu distribution. It will only upgrade your system with upgrades that are held back lintel you ok them.    

$ sudo apt-get dist-upgrade
Ok, i use opensource driver, because ubuntu does not support mine. but here is the output:
Device:    01:00.0
Class:    VGA compatible controller
Vendor:    Advanced Micro Devices [AMD] nee ATI
Device:    M64-S [Mobility Radeon X2300]
SVendor:    Hewlett-Packard Company
SDevice:    6910p
Module:    radeon

so yes and no, i do and don't have drivers... And it used to work, so i don't think this is the problem... And i did the other stuff too.

---

### Post by RocketPenguin on 2012-06-20
> **SlugSlug said:**
> [http://ubuntuforums.org/showpost.php?p=12039461&postcount=9](http://ubuntuforums.org/showpost.php?p=12039461&postcount=9)
Java, or openjdk 7, Don't work for me with minecraft for some reason.

---

### Post by regor210 on 2012-06-21
When you run 

$ lspci | grep VGA && glxinfo | grep -w 'direct\|OpenGL'

you should see something like

direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 210/PCIe/SSE2
OpenGL version string: 3.3.0 NVIDIA 302.17
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:
GeForce6100PM-M2:~$

Granted it would say ATI not Nvidia but it should not say  
failed request:...

To double check your OpenGL rendering run this

$ LIBGL_DEBUG=verbose glxinfo

Um your thread? I don't want to run you around in circles.
[http://ubuntuforums.org/showthread.php?t=2006172&page=2](http://ubuntuforums.org/showthread.php?t=2006172&page=2)

useful information
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Did you purge the -fglrx drivers? And reinstall the mesa-glx libs as outlined here?

[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

Scroll down to
Problem: Need to purge -fglrx

---

### Post by Dlambert on 2012-06-21
Does this driver page for you card help? [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by RocketPenguin on 2012-06-21
> **regor210 said:**
> When you run 

$ lspci | grep VGA && glxinfo | grep -w 'direct\|OpenGL'

you should see something like

direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 210/PCIe/SSE2
OpenGL version string: 3.3.0 NVIDIA 302.17
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:
GeForce6100PM-M2:~$

Grated it would say ATI not Nvidia but it should not say  
failed request:...

To double check your OpenGL rendering run this

$ LIBGL_DEBUG=verbose glxinfo

Um your thread? I don't want to run you around in circles.
[http://ubuntuforums.org/showthread.php?t=2006172&page=2](http://ubuntuforums.org/showthread.php?t=2006172&page=2)

useful information
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Did you purge the -fglrx drivers? And reinstall the mesa-glx libs as outlined here?

[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

Scroll down to
Problem: Need to purge -fglrx
Same errors for the first.
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI M64-S [Mobility Radeon X2300]
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
the second command
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
[QIII]("http://ubuntuforums.org/member.php?u=628170") Said to stick with the opensource drivers, so i am. Just hope i didn't screw them up in any way....
And, I don't think my graphics card is an HD type..... Not sure.
Plus, those instructions for installing drivers, is outdated.

---

### Post by RocketPenguin on 2012-06-21
I think the reason why it is not working is because i messed up the opensource drivers that came with it, and not completely ruin them, but bad enough so that minecraft no longer works. The thing is, i can't find how to restore the opensource drivers. And when i do, it is out of date, or doesn't work.
EDIT: I made a test, and yes, it is my drivers that are my problem. In another partition, I installed ubuntu, again. Then, i got openJDK 6, tried it, and it worked! I didn't even have to update the lwjgl. So now i am 99% sure it is my drivers.

---

### Post by Balmung4500 on 2012-06-29
ok how do i fix minecraft just closing no error message. just abruptly closing

---

### Post by regor210 on 2012-06-29
Try running Minecraft in terminal and see if theres an error in the  terminal window after Minecraft closes. Here's how.

Download Minecraft here

[http://www.minecraft.net/download](http://www.minecraft.net/download)


Then open a terminal ctrl+alt+t cut and paste the following commands into the terminal window one line at a time minus the $.

$ sudo chmod -R 777 .minecraft

$ cd ~/Downloads

$ sudo chmod a+x minecraft.jar

$ java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame

And post what you get.

---

### Post by Nanur on 2012-07-01
You need to use Oracle Java, if you already are.. then make sure its all updated.

---

