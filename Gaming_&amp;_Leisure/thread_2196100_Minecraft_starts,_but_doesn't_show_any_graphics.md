---
title: "Minecraft starts, but doesn't show any graphics"
date: 2013-12-27
forum: Gaming &amp; Leisure
---

### Post by jjmarc on 2013-12-27
Hey all,
I am trying to get minecraft to work on my ubuntu 12.04 LTS computer, but it doesn't exactly work correctly. When I click the "Play" button, the launcher goes away and the game window comes up. The music starts, and I can click on things and hear the clicking sound. However, my Minecraft window is completely white. It doesn't even show the Mojang logo. Note that I am not trying to play minecraft at this time, I just want to make sure it works. I have no idea what the problem might be. If anyone can help it would be much appreciated!

edit: A few days after I posted this, I came across this [error log.]("http://pastebin.com/HXJr7q0h") Don't know if it will mean anything, but I wanted to give you guys as much info as possible.


Specs:
Ubuntu Distro: Ubuntu 12.04 LTS
Processor: Intel Pentium 4 @2.80 GHZ
Memory: 1 GB RAM
Video Card: NVidia GeForce FX5500
Java Distro: OpenJDK Runtime 7
Minecraft Version: Minecraft 1.7.4

---

### Post by ueli-ton on 2013-12-29
Look here: [http://ubuntuforums.org/showthread.php?t=2195639&p=12885969#post12885969](http://ubuntuforums.org/showthread.php?t=2195639&p=12885969#post12885969)

---

### Post by jjmarc on 2013-12-30
> **ueli-ton said:**
> Look here: [http://ubuntuforums.org/showthread.php?t=2195639&p=12885969#post12885969](http://ubuntuforums.org/showthread.php?t=2195639&p=12885969#post12885969)
That did not work for me.

---

### Post by conversationjames on 2014-01-02
[https://mojang.atlassian.net/browse/MC-2067](https://mojang.atlassian.net/browse/MC-2067)

Maybe...?: [http://ubuntuforums.org/showthread.php?t=1980790](http://ubuntuforums.org/showthread.php?t=1980790)

---

### Post by jjmarc on 2014-01-02
> **conversationjames said:**
> [https://mojang.atlassian.net/browse/MC-2067](https://mojang.atlassian.net/browse/MC-2067)

Maybe...?: [http://ubuntuforums.org/showthread.php?t=1980790](http://ubuntuforums.org/showthread.php?t=1980790)
This did not work. The first link corresponds to a problem with fullscreen, which is not my problem. The second link corresponds to an old version of Minecraft, and is therefore unusable. Thank you for your help, but these just are not working for my Minecraft.

---

### Post by jjmarc on 2014-01-02
[SIZE=5][B]UPDATE:
[/B][SIZE=2]Just wanted to let you guys know that I tried uninstalling Sun Java and installing OpenJDK Runtime 7, but that did not work. Anyways, just wanted to let you guys know that that is what I am using currently.[/SIZE][SIZE=2][/SIZE][/SIZE]

---

### Post by alexsmithfanning on 2014-01-03
Try going into the directory of minecraft and changing the settings file. try crapping down the graphics a little bit. 1gb of RAM cant usually play minecraft. 


the directory is: %appdata% .minecraft settings.txt change the opengl to true or false hope this helps!

---

### Post by jjmarc on 2014-01-03
> **alexsmithfanning said:**
> Try going into the directory of minecraft and changing the settings file. try crapping down the graphics a little bit. 1gb of RAM cant usually play minecraft. 


the directory is: %appdata% .minecraft settings.txt change the opengl to true or false hope this helps!
I'd like to try this, unfortunately I can't seem to find a "settings.txt" or anything like that. I have an image below of my .minecraft folder. Can you tell me where to go to find this "settings.txt"?
[ATTACH=CONFIG]249167[/ATTACH]

---

### Post by jjmarc on 2014-01-03
[B]UPDATE:
[/B][SIZE=2]While digging deeper into this issue, I found this error log:
[/SIZE][http://pastebin.com/HXJr7q0h](http://pastebin.com/HXJr7q0h)
Don't know if this will mean anything, but I wanted to provide you guys with as much info as possible.

---

### Post by MrMichaelHill on 2014-01-05
What graphics card do you have? on board, ATI etc... ?

---

### Post by jjmarc on 2014-01-05
> **MrMichaelHill said:**
> What graphics card do you have? on board, ATI etc... ?
I actually had this in the first post, but it is a NVidia GeForce FX5500. Perhaps I ought to label the specs. :P

---

### Post by MrMichaelHill on 2014-01-06
> **jjmarc said:**
> I actually had this in the first post, but it is a NVidia GeForce FX5500. Perhaps I ought to label the specs. :P

Oh! Sorry haha! That card has some age on it now?!!! Have you tried to run any other games?

---

### Post by efflandt on 2014-01-08
When you type **free** in a terminal, what shows in the **+/- buffers/cache** line under **used** and **free**?

By default I think minecraft tries to use 1 GB RAM, but you only have that total including the kernel. So in the minecraft launcher **Edit Profile** and see if under **JVM Arguments** something like **-Xmx256M** works.

---

### Post by MrMichaelHill on 2014-01-09
Also, 1GB ram is not enough. It may be a simple looking game but it uses ram and processor mainly. After a little time in game I can easily be over 3GB ram being used by minecraft alone.

---

### Post by jjmarc on 2014-01-11
> **MrMichaelHill said:**
> Also, 1GB ram is not enough. It may be a simple looking game but it uses ram and processor mainly. After a little time in game I can easily be over 3GB ram being used by minecraft alone.
I am planning to upgrade the RAM to 4 GB very soon, but I just haven't found the time yet. I have been having several problems with Minecraft on this computer before, so I just want to make sure it starts correctly.

---

### Post by jjmarc on 2014-01-11
> **efflandt said:**
> When you type **free** in a terminal, what shows in the **+/- buffers/cache** line under **used** and **free**?

By default I think minecraft tries to use 1 GB RAM, but you only have that total including the kernel. So in the minecraft launcher **Edit Profile** and see if under **JVM Arguments** something like **-Xmx256M** works.
This is the output of "free":
```
josh@Joshs-Computer:~$ free             total       used       free     shared    buffers     cached
Mem:       1025696     947240      78456          0      36688     251160
-/+ buffers/cache:     659392     366304
Swap:      1029116        780    1028336
josh@Joshs-Computer:~$ 

```
When I tried to run the game with 512 MB RAM, instead of a blank white window where I can hear things, the game just immidiately crashed and I got this crash report:
```
---- Minecraft Crash Report ----
// Why is it breaking :(


Time: 1/11/14 8:05 PM
Description: Initializing game


org.lwjgl.LWJGLException: Could not init GLX
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:61)
	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:818)
	at org.lwjgl.opengl.DrawableGL.setPixelFormat(DrawableGL.java:61)
	at org.lwjgl.opengl.Display.create(Display.java:846)
	at org.lwjgl.opengl.Display.create(Display.java:757)
	at org.lwjgl.opengl.Display.create(Display.java:739)
	at azi.ad(SourceFile:325)
	at azi.f(SourceFile:696)
	at net.minecraft.client.main.Main.main(SourceFile:152)




A detailed walkthrough of the error, its code path and all known details is as follows:
---------------------------------------------------------------------------------------


-- Head --
Stacktrace:
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:61)
	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:818)
	at org.lwjgl.opengl.DrawableGL.setPixelFormat(DrawableGL.java:61)
	at org.lwjgl.opengl.Display.create(Display.java:846)
	at org.lwjgl.opengl.Display.create(Display.java:757)
	at org.lwjgl.opengl.Display.create(Display.java:739)
	at azi.ad(SourceFile:325)


-- Initialization --
Details:
Stacktrace:
	at azi.f(SourceFile:696)
	at net.minecraft.client.main.Main.main(SourceFile:152)


-- System Details --
Details:
	Minecraft Version: 1.7.4
	Operating System: Linux (i386) version 3.8.0-35-generic
	Java Version: 1.7.0_25, Oracle Corporation
	Java VM Version: OpenJDK Client VM (mixed mode, sharing), Oracle Corporation
	Memory: 2069016 bytes (1 MB) / 26546176 bytes (25 MB) up to 518979584 bytes (494 MB)
	JVM Flags: 1 total; -Xmx512M
	AABB Pool Size: 0 (0 bytes; 0 MB) allocated, 0 (0 bytes; 0 MB) used
	IntCache: cache: 0, tcache: 0, allocated: 0, tallocated: 0
	Launched Version: 1.7.4
	LWJGL: 2.9.1
	OpenGL: ~~ERROR~~ RuntimeException: No OpenGL context found in the current thread.
	GL Caps: 
	Is Modded: Probably not. Jar signature remains and client brand is untouched.
	Type: Client (map_client.txt)
	Resource Packs: []
	Current Language: ~~ERROR~~ NullPointerException: null
	Profiler Position: N/A (disabled)
	Vec3 Pool Size: ~~ERROR~~ NullPointerException: null
	Anisotropic Filtering: Off (1)

```

---

### Post by jjmarc on 2014-02-24
After a month of searching around, I discovered that I was not using the Nvidia proprietary driver for my card. Whoopsie :oops:
I enabled the driver and also installed 2 more GBs of RAM and now it works! I can see the graphics fine, but the game is extremely laggy. Oh well, guess that's an issue for another time. Marking thread as solved.

---

