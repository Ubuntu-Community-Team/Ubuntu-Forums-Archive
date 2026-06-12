---
title: "New with Ubuntu/LInux, can't figure out how to make this jar run."
date: 2015-04-24
forum: Gaming &amp; Leisure
---

### Post by jeremiah07 on 2015-04-24
I've been using Ubuntu for maybe ~1 week now, and I've downloaded a game, but my attempts at running it have so far been futile. 

Game: [http://7dfps.com/?action=games&id=228](http://7dfps.com/?action=games&id=228)

I put the game's jar in this directory: /home/leafletpamhplet/games/, then try to run it by putting this in terminal:

[TABLE="width: 500"]
[TR]
[TD]cd /home/leafletpamhplet/games
java -jar boarding-party.jar
[/TD]
[/TR]
[/TABLE]

I then receive this error in turn after waiting for ~2 seconds.

[TABLE="width: 500"]
[TR]
[TD]leafletpamhplet@leafletpamhplet-HP-Pavilion-g6-Notebook-PC:~$ cd /home/leafletpamhplet/games 
leafletpamhplet@leafletpamhplet-HP-Pavilion-g6-Notebook-PC:~/games$ java -jar boarding-party.jar
Exception in thread "main" java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:606)
    at org.eclipse.jdt.internal.jarinjarloader.JarRsrcLoader.main(JarRsrcLoader.java:58)
Caused by: java.lang.UnsatisfiedLinkError: Can't load library: /tmp/libgdxleafletpamhplet/2789134151/liblwjgl.so
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1854)
    at java.lang.Runtime.load0(Runtime.java:795)
    at java.lang.System.load(System.java:1062)
    at org.lwjgl.Sys$1.run(Sys.java:70)
    at java.security.AccessController.doPrivileged(Native Method)
    at org.lwjgl.Sys.doLoadLibrary(Sys.java:66)
    at org.lwjgl.Sys.loadLibrary(Sys.java:95)
    at org.lwjgl.Sys.<clinit>(Sys.java:112)
    at org.lwjgl.openal.AL.<clinit>(AL.java:59)
    at com.badlogic.gdx.backends.openal.OpenALAudio.<init>(OpenALAudio.java:70)
    at com.badlogic.gdx.backends.lwjgl.LwjglApplication.<init>(LwjglApplication.java:80)
    at com.badlogic.gdx.backends.lwjgl.LwjglApplication.<init>(LwjglApplication.java:64)
    at com.interrupt.dungeoneer.DesktopStarter.main(DesktopStarter.java:18)
    ... 5 more

[/TD]
[/TR]
[/TABLE]

No idea what to do, or if this a problem with the game, or my java, although I havn't been able to run anything else with the same method.

Here's the full terminal text from when I tryed to run it.

[TABLE="width: 500"]
[TR]
[TD]leafletpamhplet@leafletpamhplet-HP-Pavilion-g6-Notebook-PC:~$ cd /home/leafletpamhplet/games 
leafletpamhplet@leafletpamhplet-HP-Pavilion-g6-Notebook-PC:~/games$ java -jar boarding-party.jar
Exception in thread "main" java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:606)
    at org.eclipse.jdt.internal.jarinjarloader.JarRsrcLoader.main(JarRsrcLoader.java:58)
Caused by: java.lang.UnsatisfiedLinkError: Can't load library: /tmp/libgdxleafletpamhplet/2789134151/liblwjgl.so
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1854)
    at java.lang.Runtime.load0(Runtime.java:795)
    at java.lang.System.load(System.java:1062)
    at org.lwjgl.Sys$1.run(Sys.java:70)
    at java.security.AccessController.doPrivileged(Native Method)
    at org.lwjgl.Sys.doLoadLibrary(Sys.java:66)
    at org.lwjgl.Sys.loadLibrary(Sys.java:95)
    at org.lwjgl.Sys.<clinit>(Sys.java:112)
    at org.lwjgl.openal.AL.<clinit>(AL.java:59)
    at com.badlogic.gdx.backends.openal.OpenALAudio.<init>(OpenALAudio.java:70)
    at com.badlogic.gdx.backends.lwjgl.LwjglApplication.<init>(LwjglApplication.java:80)
    at com.badlogic.gdx.backends.lwjgl.LwjglApplication.<init>(LwjglApplication.java:64)
    at com.interrupt.dungeoneer.DesktopStarter.main(DesktopStarter.java:18)
    ... 5 more

[/TD]
[/TR]
[/TABLE]

---

### Post by efflandt on 2015-04-25
Not sure exactly what lwjgl is, but it might have something to do with graphics (GL), besides maybe other input/output (openal is audio). I know that when minecraft used to have an old lwjgl version it sometimes resulted in stuck keys because it was not properly sensing "key down" and "key up" events. What graphics card/chip do you have and are you using default drivers or proprietary drivers for it? And which java version are you running (I am running openjdk-7-jre in 64-bit Ubuntu 14.04).

This is what I get on the terminal when I run it through a quick game until I got killed:```
efflandt@XPS-8100-1404:~/Downloads/boarding-party$ java -jar boarding-party.jar
DelverLifeCycle: LibGdx Create
DelverLifeCycle: Created GL2.0 Renderer
DelverLifeCycle: Initializing Renderer
DelverSplashScreen: LibGdx Resize
DelverLifeCycle: Resized!
DelverSplashScreen: LibGdx Resize
DelverLifeCycle: Getting savegames from save
DelverGameScreen: Show
DelverAudio: Error loading whoosh1.ogg
DelverAudio: Error loading hurt.ogg
DelverAudio: Error loading spell-missile-2.ogg
DelverAudio: Error loading clang.ogg
DelverAudio: Error loading splash2.ogg
DelverAudio: Error loading torch.ogg
DelverLifeCycle: READY PLAYER ONE
Controllers: added manager for application, 1 managers active
DelverGenerator: Making level
DelverGenerator: Using theme dir generator/Station/
DelverGenerator: Using theme dir generator/Station/
DelverGenerator: Added tile generator/Station/Beginnings/1.dat
DelverGenerator: Bad level. Trying again
DelverGenerator: Making level
DelverGenerator: Using theme dir generator/Station/
DelverGenerator: Using theme dir generator/Station/
DelverGenerator: Added tile generator/Station/Beginnings/1.dat
DelverGenerator: Added tile generator/Station/Corners/2.dat
DelverGenerator: Added tile generator/Station/Ends/2.dat
DelverGenerator: Added tile generator/Station/Corners/2.dat
DelverGenerator: Added tile generator/Station/Intersections/4.dat
DelverGenerator: Added tile generator/Station/Ends/2.dat
DelverGenerator: Added tile generator/Station/Halls/1.dat
DelverGenerator: Added tile generator/Station/Ends/1.dat
DelverLifeCycle: Initializing HUD
DelverGameScreen: LibGdx Resize
DelverLifeCycle: Resized!
DelverGameScreen: LibGdx Resize
DelverLifeCycle: Game over!
DelverGameScreen: Hide
DelverAudio: Error loading gameover.ogg
```It was written in 7 days, so it may not be perfect. Although, it seemed to get over missing audio (ogg) files and stumbling the first time it tried to generate a level (not even noticed in game).

---

### Post by brian62 on 2015-04-28
[COLOR=#000000]Caused by: java.lang.UnsatisfiedLinkError: Can't load library: /tmp/libgdxleafletpamhplet/2789134151/liblwjgl.so

[/COLOR]It would seem that your system is missing liblwjgl. Check this thread out - [http://askubuntu.com/questions/171991/cant-get-minecraft-to-run-on-ubuntu](http://askubuntu.com/questions/171991/cant-get-minecraft-to-run-on-ubuntu)

---

### Post by TheFadedBrit on 2015-04-30
May i ask where you installed your java from please?

---

