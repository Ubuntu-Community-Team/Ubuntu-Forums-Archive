---
title: "Need Help With The New Minecraft Launcher"
date: 2017-10-09
forum: Gaming &amp; Leisure
---

### Post by linuxissuperawesome on 2017-10-09
I Have Tried To Install The [New]("http://www.omgubuntu.co.uk/2017/01/help-test-new-minecraft-launcher-linux") Minecraft Launcher On Ubuntu 16.04 LTS. But I Keep On Getting The Following Error.
```
./launcher: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.22' not found (required by ./launcher)

``` And If I Use The Normal Launcher With OpenJDK 8 I Get The Following Crash Report:-
```
---- Minecraft Crash Report ----
// Ooh. Shiny.

Time: 10/9/17 5:07 PM
Description: Initializing game

java.lang.ExceptionInInitializerError
    at bes.ar(SourceFile:626)
    at bes.an(SourceFile:434)
    at bes.a(SourceFile:383)
    at net.minecraft.client.main.Main.main(SourceFile:124)
Caused by: java.lang.ArrayIndexOutOfBoundsException: 0
    at org.lwjgl.opengl.LinuxDisplay.getAvailableDisplayModes(LinuxDisplay.java:951)
    at org.lwjgl.opengl.LinuxDisplay.init(LinuxDisplay.java:738)
    at org.lwjgl.opengl.Display.<clinit>(Display.java:138)
    ... 4 more


A detailed walkthrough of the error, its code path and all known details is as follows:
---------------------------------------------------------------------------------------

-- Head --
Thread: Client thread
Stacktrace:
    at bes.ar(SourceFile:626)
    at bes.an(SourceFile:434)

-- Initialization --
Details:
Stacktrace:
    at bes.a(SourceFile:383)
    at net.minecraft.client.main.Main.main(SourceFile:124)

-- System Details --
Details:
    Minecraft Version: 1.11.2
    Operating System: Linux (amd64) version 4.4.0-96-generic
    Java Version: 1.8.0_131, Oracle Corporation
    Java VM Version: OpenJDK 64-Bit Server VM (mixed mode), Oracle Corporation
    Memory: 45028408 bytes (42 MB) / 152514560 bytes (145 MB) up to 1060372480 bytes (1011 MB)
    JVM Flags: 5 total; -Xmx1G -XX:+UseConcMarkSweepGC -XX:+CMSIncrementalMode -XX:-UseAdaptiveSizePolicy -Xmn128M
    IntCache: cache: 0, tcache: 0, allocated: 0, tallocated: 0
    Launched Version: 1.11.2
    LWJGL: 2.9.4
    OpenGL: ~~ERROR~~ RuntimeException: No OpenGL context found in the current thread.
    GL Caps: 
    Using VBOs: Yes
    Is Modded: Probably not. Jar signature remains and client brand is untouched.
    Type: Client (map_client.txt)
    Resource Packs: 
    Current Language: ~~ERROR~~ NullPointerException: null
    Profiler Position: N/A (disabled)
    CPU: <unknown>
``` 
And I Have Tried The Following To Fix The New Launcher's Error:-
```

$ strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep GLIBCXX
GLIBCXX_3.4
GLIBCXX_3.4.1
GLIBCXX_3.4.2
GLIBCXX_3.4.3
GLIBCXX_3.4.4
GLIBCXX_3.4.5
GLIBCXX_3.4.6
GLIBCXX_3.4.7
GLIBCXX_3.4.8
GLIBCXX_3.4.9
GLIBCXX_3.4.10
GLIBCXX_3.4.11
GLIBCXX_3.4.12
GLIBCXX_3.4.13
GLIBCXX_3.4.14
GLIBCXX_3.4.15
GLIBCXX_3.4.16
GLIBCXX_3.4.17
GLIBCXX_3.4.18
GLIBCXX_3.4.19
GLIBCXX_3.4.20
GLIBCXX_3.4.21
GLIBCXX_DEBUG_MESSAGE_LENGTH

``` And The Fixes Given [Here]("https://stackoverflow.com/questions/43070900/version-glibcxx-3-4-22-not-found") And [Here]("https://askubuntu.com/questions/575505/glibcxx-3-4-20-not-found-how-to-fix-this-error").
Somebody, Please Help.

---

### Post by efflandt on 2017-10-11
Did it work before with the old launcher? The new launcher works for me. I am running Ubuntu 16.10 (I know, end of support, need to move to 16.04 or 17.04) with Oracle Java 8 which I needed for something else. Although, I never had any trouble running minecraft with openjdk.

What graphics card/chip do you have and are you using default graphics drivers or other (version?)?

I do have the file you are missing:```
~$ strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep GLIBCXX
GLIBCXX_3.4
GLIBCXX_3.4.1
GLIBCXX_3.4.2
GLIBCXX_3.4.3
GLIBCXX_3.4.4
GLIBCXX_3.4.5
GLIBCXX_3.4.6
GLIBCXX_3.4.7
GLIBCXX_3.4.8
GLIBCXX_3.4.9
GLIBCXX_3.4.10
GLIBCXX_3.4.11
GLIBCXX_3.4.12
GLIBCXX_3.4.13
GLIBCXX_3.4.14
GLIBCXX_3.4.15
GLIBCXX_3.4.16
GLIBCXX_3.4.17
GLIBCXX_3.4.18
GLIBCXX_3.4.19
GLIBCXX_3.4.20
GLIBCXX_3.4.21
GLIBCXX_3.4.22
GLIBCXX_DEBUG_MESSAGE_LENGTH

~$ dpkg-query -l libstdc* | grep ii
ii  libstdc++-5-dev:amd64     5.4.1-2ubuntu2  amd64        GNU Standard C++ Library v3 (development files)
ii  libstdc++-6-dev:amd64     6.2.0-5ubuntu12 amd64        GNU Standard C++ Library v3 (development files)
ii  libstdc++6:amd64          6.2.0-5ubuntu12 amd64        GNU Standard C++ Library v3
ii  libstdc++6:i386           6.2.0-5ubuntu12 i386         GNU Standard C++ Library v3
```I did have some errors listed when launching the game itself (now 1.12 something), but apparently nothing essential or fatal.

The last world I had was from v1.8, so I started a new world. But days are short. I no sooner hacked some trees for wood, made some wooden tools (had to think for awhile about recipes), and found some coal near a drop off into a deep dark cave when nightfall came and I quickly dug a hole into the ground to hide in. I heard a skeleton outside fall. But I had closed everything up, pitch black. I was thinking that I had to cook some wood to make charcoal, then remembered I had coal and made some torches. But all closed up, I do not know how to tell when it is daylight. About the time I poke a hole, a creeper will drop into it.

---

