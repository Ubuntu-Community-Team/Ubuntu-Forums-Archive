---
title: "Minecraft Graphical Issues"
date: 2012-03-05
forum: Gaming &amp; Leisure
---

### Post by BSERIOUSSS on 2012-03-05
First off, I am a total Linux newbie, but have been messing around with it somewhat. I can run terminal commands that are pasted, but some things have to be explained to me. I am computer literate, maybe even techno-savvy, with Windows.Thanks!

Ok, so I am trying out Ubuntu 11.10, just upgraded from Natty last week, and I want to play Minecraft. My only problem? Well, I get these horrific white triangles in th bottom left corner, and my mouse also becomes unresponsive when this happens, which is most of the time. I saw in another thread, with different issues, to run it from terminal, so I did, and got this: 

"
conner@ubuntu:~$ cd ~/ && java -jar minecraft.jar
27 achievements
177 recipes
Setting user: BSERIOUSSS, 86913323842077508
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event6): Failed to open device /dev/input/event6 (13)

Failed to open device (/dev/input/event5): Failed to open device /dev/input/event5 (13)

Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see [http://www.lwjgl.org](http://www.lwjgl.org))
OpenAL initialized.

Placed stronghold in INVALID biome at (57, -35)
java.lang.NullPointerException
    at ack.p(SourceFile:84)
    at ack.c(SourceFile:63)
    at vl.a(SourceFile:91)
    at net.minecraft.client.Minecraft.a(SourceFile:472)
    at xo.a(SourceFile:119)
    at vl.a(SourceFile:68)
    at vl.f(SourceFile:116)
    at vl.i(SourceFile:104)
    at net.minecraft.client.Minecraft.k(SourceFile:1386)
    at net.minecraft.client.Minecraft.x(SourceFile:724)
    at net.minecraft.client.Minecraft.run(SourceFile:664)
    at java.lang.Thread.run(Unknown Source)
java.lang.NullPointerException
    at ack.p(SourceFile:84)
    at ack.c(SourceFile:63)
    at vl.a(SourceFile:91)
    at net.minecraft.client.Minecraft.a(SourceFile:472)
    at ack.a(SourceFile:164)
    at vl.a(SourceFile:68)
    at ack.a(SourceFile:229)
    at vl.f(SourceFile:116)
    at vl.i(SourceFile:104)
    at net.minecraft.client.Minecraft.k(SourceFile:1386)
    at net.minecraft.client.Minecraft.x(SourceFile:724)
    at net.minecraft.client.Minecraft.run(SourceFile:664)
    at java.lang.Thread.run(Unknown Source)
java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
    at java.lang.reflect.Method.invoke(Unknown Source)
    at ej.a(SourceFile:56)
    at vl.a(SourceFile:68)
    at ej.a(SourceFile:74)
    at vl.f(SourceFile:116)
    at vl.i(SourceFile:104)
    at net.minecraft.client.Minecraft.k(SourceFile:1386)
    at net.minecraft.client.Minecraft.x(SourceFile:724)
    at net.minecraft.client.Minecraft.run(SourceFile:664)
    at java.lang.Thread.run(Unknown Source)
Caused by: java.io.IOException: Failed to show URI:file:/home/conner/.minecraft/texturepacks/
    at sun.awt.X11.XDesktopPeer.launch(Unknown Source)
    at sun.awt.X11.XDesktopPeer.browse(Unknown Source)
    at java.awt.Desktop.browse(Unknown Source)
    ... 13 more
Opening via Sys class!
root.render.gameRenderer.level 132865589
root.render.gameRenderer 142144243
root.render 167414091
root 168427235
 201635473
 162680842
 163867849
 178078116
 130425520
root.tick.level 117645981
root.tick 121732448
root 122431436
 169595400
root.tick.level 202498118
root.tick 205168823
root 205807244
 256646920
root.tick.level 181885945
root.tick 183800532
root 190549476
 250699165
root.tick.level 166691721
root.tick 169147800
root 169830917
 219557449
Stopping!

SoundSystem shutting down...
    Author: Paul Lamb, [www.paulscode.com](www.paulscode.com)

Exception in thread "Minecraft main thread" org.lwjgl.LWJGLException: X Error - disp: 0x41a7bf40 serial: 190387 error: GLXBadWindow request_code: 155 minor_code: 32
    at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:268)
    at org.lwjgl.opengl.LinuxDisplay.nDestroyWindow(Native Method)
    at org.lwjgl.opengl.LinuxDisplay.destroyWindow(LinuxDisplay.java:484)
    at org.lwjgl.opengl.Display.destroyWindow(Display.java:352)
    at org.lwjgl.opengl.Display.destroy(Display.java:967)
    at net.minecraft.client.Minecraft.d(SourceFile:520)
    at net.minecraft.client.Minecraft.run(SourceFile:681)
    at java.lang.Thread.run(Unknown Source)
"
I am running an Intel Integrated gpu, but this was never a problem on Windows. I have 3 gb of ram, plenty of HDD space, and an Intel i3 2nd gen. Please help me! Thank you!

---

### Post by regor210 on 2012-03-06
Looks like you have some lwjgl errors but before addressing them lets see whats up with your video drivers.

Run these in a terminal minus the $ 

$ sudo apt-get update
$ sudo apt-get upgrade

$ sudo apt-get install mesa-utils

video driver 3D test FPS

$ glxgears

video card and driver information

$ lspci -vmk | grep -A 8 -B 2 VGA

$ uname -a

And post what you get.

---

### Post by BSERIOUSSS on 2012-03-11
Sorry I am so late to reply, I had some Windows issues. I am doing this now.

---

### Post by BSERIOUSSS on 2012-03-11
Ok, here it is:

conner@ubuntu:~$ sudo apt-get update
[sudo] password for conner: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]         
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release [40.8 kB]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release [40.8 kB]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages [87.9 kB]
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs InRelease                                      
Hit [http://www.duinsoft.nl](http://www.duinsoft.nl) debs Release.gpg                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://www.duinsoft.nl](http://www.duinsoft.nl) debs Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main amd64 Packages [297 kB]
Hit [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all Sources                                    
Hit [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all amd64 Packages                             
Hit [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all i386 Packages                              
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages [14 B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages [29.7 kB]
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all TranslationIndex                           
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages [3,194 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [88.0 kB]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
  404  Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages [29.8 kB]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
  404  Not Found
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages [3,362 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex [73 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex [72 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en [49.6 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages [2,982 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe amd64 Packages [102 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages [6,202 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages [296 kB]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en [20.7 kB]
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all Translation-en_US                          
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all Translation-en        
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [2,968 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages [102 kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [6,359 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex [74 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [71 B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en [139 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en [61.1 kB]
Fetched 1,410 kB in 6s (230 kB/s)                                              
W: Failed to fetch [http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
conner@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gnome-orca
The following packages will be upgraded:
  apt apt-transport-https apt-utils gzip libapt-inst1.3 libapt-pkg4.11
  libc-bin libc-dev-bin libc6 libc6:i386 libc6-dev linux-headers-3.0.0-16
  linux-headers-3.0.0-16-generic linux-image-3.0.0-16-generic linux-libc-dev
  multiarch-support python-pam tzdata tzdata-java
19 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 64.1 MB of archives.
After this operation, 32.8 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main gzip amd64 1.3.12-9ubuntu1.2 [77.6 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main tzdata-java amd64 2012b-0ubuntu0.11.10 [134 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main tzdata amd64 2012b-0ubuntu0.11.10 [397 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main libc-bin amd64 2.13-20ubuntu5.1 [994 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main libc-dev-bin amd64 2.13-20ubuntu5.1 [84.0 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main libc6-dev amd64 2.13-20ubuntu5.1 [2,572 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main libc6 i386 2.13-20ubuntu5.1 [3,800 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main libc6 amd64 2.13-20ubuntu5.1 [4,149 kB]
18% [8 libc6 4,098 kB/4,149 kB 98%]                                             
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main linux-libc-dev amd64 3.0.0-16.29 [852 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main linux-image-3.0.0-16-generic amd64 3.0.0-16.29 [37.1 MB]
22% [10 linux-image-3.0.0-16-generic 1,572 kB/37.1 MB 4%]                                                                            179 kB/s 4min 36sp23% [10 linux-image-3.0.0-16-generic 1,920 kB/37.1 MB 5%]                                                                            179 kB/s 4min 34sp23% [10 linux-image-3.0.0-16-generic 2,033 kB/37.1 MB 5%]                                                                            179 kB/s 4min 33su24% [10 linux-image-3.0.0-16-generic 2,586 kB/37.1 MB 6%]                                                                            179 kB/s 4min 31sa24% [10 linux-image-3.0.0-16-generic 2,676 kB/37.1 MB 7%]                                                                            179 kB/s 4min 30se
24% [10 linux-image-3.0.0-16-generic 2,855 kB/37.1 MB 7%]                                                                            179 kB/s 4min 29s
25% [10 linux-image-3.0.0-16-generic 3,087 kB/37.1 MB 8%]                                                                            179 kB/s 4min 28s
25% [10 linux-image-3.0.0-16-generic 3,087 kB/37.1 MB 8%]                                                                            179 kB/s 4min 28s
25% [10 linux-image-3.0.0-16-generic 3,087 kB/37.1 MB 8%]                                                                            179 kB/s 4min 28s
76% [10 linux-image-3.0.0-16-generic 36.0 MB/37.1 MB 96%]          248 kB/s 60s 
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main libapt-pkg4.11 amd64 0.8.16~exp5ubuntu13.2 [519 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main apt amd64 0.8.16~exp5ubuntu13.2 [1,062 kB]
80% [12 apt 566 kB/1,062 kB 53%]                              179 kB/s 1min 11s^80% [12 apt 656 kB/1,062 kB 61%]                              179 kB/s 1min 11s^80% [12 apt 745 kB/1,062 kB 70%]                              179 kB/s 1min 10s^80% [12 apt 835 kB/1,062 kB 78%]                              179 kB/s 1min 10s^80% [12 apt 1,013 kB/1,062 kB 95%]                             179 kB/s 1min 9s^Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main multiarch-support amd64 2.13-20ubuntu5.1 [4,476 B]
80% [Working]                                                  179 kB/s 1min 8s^Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main libapt-inst1.3 amd64 0.8.16~exp5ubuntu13.2 [37.1 kB]
80% [Working]                                                  179 kB/s 1min 8s^Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main apt-utils amd64 0.8.16~exp5ubuntu13.2 [190 kB]
80% [15 apt-utils 0 B/190 kB 0%]                               179 kB/s 1min 8s^81% [15 apt-utils 140 kB/190 kB 73%]                           179 kB/s 1min 7s^81% [Working]                                                  179 kB/s 1min 7s^Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main apt-transport-https amd64 0.8.16~exp5ubuntu13.2 [15.8 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main linux-headers-3.0.0-16 all 3.0.0-16.29 [11.2 MB]
Get:18 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main linux-headers-3.0.0-16-generic amd64 3.0.0-16.29 [873 kB]
Get:19 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main python-pam amd64 0.4.2-12.2ubuntu2.11.10.1 [12.1 kB]
Fetched 64.1 MB in 8min 32s (125 kB/s)                                         
Preconfiguring packages ...
(Reading database ... 167526 files and directories currently installed.)
Preparing to replace gzip 1.3.12-9ubuntu1.1 (using .../gzip_1.3.12-9ubuntu1.2_amd64.deb) ...
Unpacking replacement gzip ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Setting up gzip (1.3.12-9ubuntu1.2) ...
(Reading database ... 167525 files and directories currently installed.)
Preparing to replace tzdata-java 2011n-0ubuntu0.11.10 (using .../tzdata-java_2012b-0ubuntu0.11.10_amd64.deb) ...
Unpacking replacement tzdata-java ...
Preparing to replace tzdata 2011n-0ubuntu0.11.10 (using .../tzdata_2012b-0ubuntu0.11.10_amd64.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2012b-0ubuntu0.11.10) ...

Current default time zone: 'America/Los_Angeles'
Local time is now:      Sat Mar 10 22:49:22 PST 2012.
Universal Time is now:  Sun Mar 11 06:49:22 UTC 2012.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

(Reading database ... 167529 files and directories currently installed.)
Preparing to replace libc-bin 2.13-20ubuntu5 (using .../libc-bin_2.13-20ubuntu5.1_amd64.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Setting up libc-bin (2.13-20ubuntu5.1) ...
(Reading database ... 167529 files and directories currently installed.)
Preparing to replace libc-dev-bin 2.13-20ubuntu5 (using .../libc-dev-bin_2.13-20ubuntu5.1_amd64.deb) ...
Unpacking replacement libc-dev-bin ...
Preparing to replace libc6-dev 2.13-20ubuntu5 (using .../libc6-dev_2.13-20ubuntu5.1_amd64.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libc6:i386 2.13-20ubuntu5 (using .../libc6_2.13-20ubuntu5.1_i386.deb) ...
De-configuring libc6 ...
Unpacking replacement libc6:i386 ...
Preparing to replace libc6 2.13-20ubuntu5 (using .../libc6_2.13-20ubuntu5.1_amd64.deb) ...
Unpacking replacement libc6 ...
Preparing to replace linux-libc-dev 3.0.0-16.28 (using .../linux-libc-dev_3.0.0-16.29_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace linux-image-3.0.0-16-generic 3.0.0-16.28 (using .../linux-image-3.0.0-16-generic_3.0.0-16.29_amd64.deb) ...
Done.
Unpacking replacement linux-image-3.0.0-16-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
^[[D^[[C^[[APreparing to replace libapt-pkg4.11 0.8.16~exp5ubuntu13 (using .../libapt-pkg4.11_0.8.16~exp5ubuntu13.2_amd64.deb) ...
Unpacking replacement libapt-pkg4.11 ...
Processing triggers for man-db ...
Setting up libc6 (2.13-20ubuntu5.1) ...
Setting up libapt-pkg4.11 (0.8.16~exp5ubuntu13.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 167529 files and directories currently installed.)
Preparing to replace apt 0.8.16~exp5ubuntu13 (using .../apt_0.8.16~exp5ubuntu13.2_amd64.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.8.16~exp5ubuntu13.2) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
(Reading database ... 167529 files and directories currently installed.)
Preparing to replace multiarch-support 2.13-20ubuntu5 (using .../multiarch-support_2.13-20ubuntu5.1_amd64.deb) ...
Unpacking replacement multiarch-support ...
Setting up multiarch-support (2.13-20ubuntu5.1) ...
(Reading database ... 167529 files and directories currently installed.)
Preparing to replace libapt-inst1.3 0.8.16~exp5ubuntu13 (using .../libapt-inst1.3_0.8.16~exp5ubuntu13.2_amd64.deb) ...
Unpacking replacement libapt-inst1.3 ...
Preparing to replace apt-utils 0.8.16~exp5ubuntu13 (using .../apt-utils_0.8.16~exp5ubuntu13.2_amd64.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace apt-transport-https 0.8.16~exp5ubuntu13 (using .../apt-transport-https_0.8.16~exp5ubuntu13.2_amd64.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace linux-headers-3.0.0-16 3.0.0-16.28 (using .../linux-headers-3.0.0-16_3.0.0-16.29_all.deb) ...
Unpacking replacement linux-headers-3.0.0-16 ...
Preparing to replace linux-headers-3.0.0-16-generic 3.0.0-16.28 (using .../linux-headers-3.0.0-16-generic_3.0.0-16.29_amd64.deb) ...
Unpacking replacement linux-headers-3.0.0-16-generic ...
Preparing to replace python-pam 0.4.2-12.2ubuntu2 (using .../python-pam_0.4.2-12.2ubuntu2.11.10.1_amd64.deb) ...
Unpacking replacement python-pam ...
Processing triggers for man-db ...
Setting up tzdata-java (2012b-0ubuntu0.11.10) ...
Setting up libc-dev-bin (2.13-20ubuntu5.1) ...
Setting up linux-libc-dev (3.0.0-16.29) ...
Setting up libc6-dev (2.13-20ubuntu5.1) ...
Setting up libc6:i386 (2.13-20ubuntu5.1) ...
Setting up linux-image-3.0.0-16-generic (3.0.0-16.29) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.0.0-16.28 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.0.0-16.28 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic
Warning: No support for locale: en_US.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-16-generic
Found initrd image: /boot/initrd.img-3.0.0-16-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found Windows 7 (loader) on /dev/sda1
Skipping Windows 7 (loader) on Wubi system
Found Windows 7 (loader) on /dev/sda2
Skipping Windows 7 (loader) on Wubi system
Found Windows Recovery Environment (loader) on /dev/sda3
Skipping Windows Recovery Environment (loader) on Wubi system
done
Setting up libapt-inst1.3 (0.8.16~exp5ubuntu13.2) ...
Setting up apt-utils (0.8.16~exp5ubuntu13.2) ...
Setting up apt-transport-https (0.8.16~exp5ubuntu13.2) ...
Setting up linux-headers-3.0.0-16 (3.0.0-16.29) ...
Setting up linux-headers-3.0.0-16-generic (3.0.0-16.29) ...
Examining /etc/kernel/header_postinst.d.
Setting up python-pam (0.4.2-12.2ubuntu2.11.10.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
conner@ubuntu:~$ sudo apt-get install mesa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 30.3 kB of archives.
After this operation, 152 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe mesa-utils amd64 8.0.1+git20110129+d8f7d6b-0ubuntu2 [30.3 kB]
Fetched 30.3 kB in 0s (32.0 kB/s)   
Selecting previously deselected package mesa-utils.
(Reading database ... 167529 files and directories currently installed.)
Unpacking mesa-utils (from .../mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up mesa-utils (8.0.1+git20110129+d8f7d6b-0ubuntu2) ...
conner@ubuntu:~$ video driver 3D test FPS
video: command not found
conner@ubuntu:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
300 frames in 5.0 seconds = 59.877 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.857 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.856 FPS
299 frames in 5.0 seconds = 59.658 FPS
300 frames in 5.0 seconds = 59.855 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.858 FPS
300 frames in 5.0 seconds = 59.854 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.858 FPS
300 frames in 5.0 seconds = 59.854 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.856 FPS
279 frames in 5.0 seconds = 55.667 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.855 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.855 FPS
300 frames in 5.0 seconds = 59.857 FPS
300 frames in 5.0 seconds = 59.857 FPS
300 frames in 5.0 seconds = 59.855 FPS
300 frames in 5.0 seconds = 59.856 FPS
300 frames in 5.0 seconds = 59.858 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 20349 requests (20349 known processed) with 0 events remaining.
conner@ubuntu:~$ lspci -vmk | grep -A 8 -B 2 VGA

Device:    00:02.0
Class:    VGA compatible controller
Vendor:    Intel Corporation
Device:    2nd Generation Core Processor Family Integrated Graphics Controller
SVendor:    Toshiba America Info Systems
SDevice:    Device fce0
Rev:    09
Driver:    i915
Module:    i915

conner@ubuntu:~$ uname -a
Linux ubuntu 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by regor210 on 2012-03-11
There's been a lot of people having trouble with Minecraft and there Intel video drivers.  

**Things to try.**

1st. Check your BIOS and see if you can make more ram or memory available to your Intel graphics adapter.

2nd. Try starting Minecraft using this minus the $

$ cd ~/ && java -Dsun.java3d.opengl=true -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame

3rd. In Minecraft goto Options > Video Settings...  > 

Graphics Fast
Smooth Lighting off
Render Distances: Tiny
Performance: Max FPS
Clouds: off

4th. Are you using Sun Java?
Minecracft uses  Sun Java 6 and recommends its use.
Ubuntu uses  java-6-openjdk.
The easiest way to install Sun Java 6 is using a non Ubuntu repository or PPA. Non  Ubuntu repositories can pose a security risk because your getting software and updates from who knows where. 
That said some of us are using this PPA 
[http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric](http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric)

5th. Update LWJGL or LightWeight Java Game Library
[http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)


6th. Here's a thread with a similar Intel issue. 
[http://ubuntuforums.org/showthread.php?t=1901823](http://ubuntuforums.org/showthread.php?t=1901823)

Mars11 said

1st post "It does that with mine too, completely vanilla Minecraft. I think it has to do with the Intel Graphics Drivers and I hear that the Linux 3.2 Kernel has some better ones so if anyone knows how to upgrade that would be nice."

2nd post "I updated to the 3.0.15 or something kernel and the problem is gone. I think it's just the drivers."

A newer kernel may fix the problem. The kernel is the heart and mind of your GNU/Linux Ubuntu operating system.

And you need to know this, that Linux kernel's are updated on a regular basis. When you use a kernel outside the Ubuntu repository's its up to you to keep your kernel updated.

The safest and easiest way to get a newer Kernel would be to wait for Ubuntu 12.04 to come out next month. It looks like it will come with kernel 3.2.0.

Update 03/17/2012

There's a PPA with newer intell drivers here
[http://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/](http://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/)


Most Intel chipset video drivers are supported automatically on the Kernel, so you may not have to install any 3rd party drivers for your video card. But if the Intel Graphics on your system don&#8217;t seem to be working correctly, you can try installing the latest untested alpha drivers for your Intel Graphics (this may leave your system unstable or unusable):

Open your Terminal, cut and paste:

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

---

### Post by BSERIOUSSS on 2012-03-15
Thanks!
I am running Sun Java, not the OpenJDK
 I will try all of those things, and let you and anyone else with this problem know my results! So glad to be part of a nice, friendly community!

---

