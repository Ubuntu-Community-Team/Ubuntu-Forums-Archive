---
title: "Minecraft: THWARTED AT EVERY TURN"
date: 2013-05-28
forum: Gaming &amp; Leisure
---

### Post by charkeybeckles on 2013-05-28
EDIT: So, I went into the Software Center, downloaded the "Set Oracle JDK 6 as default", launched Minecraft, and whadyaknow, it ran!  So... Yeah.  I got it!  Heh

I've scoured the internet and tried just about everything I can find to get minecraft working for Ubuntu 13.04.  Either I'm missing something painfully ovious, I haven't activated the one seemingly insignificant whatever, or I don't know.  But I'm getting frustrated, and if I can't figure this out, I'll have to switch back to Mac OS.  
Because, honestly.  The whole reason to own a computer is so you can play games on it. :P

So Let's start from the top.  Download minecraft.jar, check.
download oracle 7, yup yup.
launch minecraft, login, checkeroo.
Black screen.

Ok, so let's try that code we're supposed to throw at the terminal, the "java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame" one.
Hmm... Ok, so the game launches, I log in, and black screen again.  Close window, and I'm left with this in the terminal:
asdf
java.io.FileNotFoundException: /home/charles/.minecraft/lastlogin (No such file or directory)
    at java.io.FileInputStream.open(Native Method)
    at java.io.FileInputStream.<init>(FileInputStream.java:138)
    at net.minecraft.LoginForm.readUsername(LoginForm.java:110)
    at net.minecraft.LoginForm.<init>(LoginForm.java:55)
    at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:23)
    at net.minecraft.LauncherFrame.main(LauncherFrame.java:167)
Exception in thread "Thread-3" java.lang.UnsatisfiedLinkError: /home/charles/.minecraft/bin/natives/liblwjgl.so: libjawt.so: cannot open shared object file: No such file or directory
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary1(ClassLoader.java:1939)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1864)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1825)
    at java.lang.Runtime.load0(Runtime.java:792)
    at java.lang.System.load(System.java:1059)
    at org.lwjgl.Sys$1.run(Sys.java:69)
    at java.security.AccessController.doPrivileged(Native Method)
    at org.lwjgl.Sys.doLoadLibrary(Sys.java:65)
    at org.lwjgl.Sys.loadLibrary(Sys.java:81)
    at org.lwjgl.Sys.<clinit>(Sys.java:98)
    at net.minecraft.client.Minecraft.G(SourceFile:1985)
    at awe.<init>(SourceFile:20)
    at net.minecraft.client.Minecraft.<init>(SourceFile:76)
    at avv.<init>(SourceFile:38)
    at net.minecraft.client.MinecraftApplet.init(SourceFile:38)
    at net.minecraft.Launcher.replace(Launcher.java:136)
    at net.minecraft.Launcher$1.run(Launcher.java:79)

Ok, so that didn't work... someone said to try java 6 instead.  Alright, So I'll just download that, open minecraft with java 6, and...
black screen after login.

I'm noticing a pattern here. =_=

Alright, something about exporting the ld_library_path?
I don't even know what that is, but ok.  Just run this: "export LD_LIBRARY_PATH=/path/to/java/jre/lib/i386"
Aaaaaaaaaaaaaaaaaaaaaaaand it jumps down a line, awaiting my command, as though I had typed nothing and just hit enter.

So I'm a bit frustrated.  Anyone else gone through this?  Am I missing something?  Please help!

---

### Post by efflandt on 2013-05-28
Do you have openjdk or real Oracle Java installed? In the past (like 12.04) it has worked fine with openjdk-6-jre or 7. But in another thread someone commented that minecraft does not like Oracle Java 7 (can't confirm that).

I guess I need to install 13.04 on a USB drive (or eSata caddy on the good part of my previous drive that went bad towards its far end) to see if there are any issues in 13.04.

In the meantime, what video card or chip do you have and what are you using for video drivers?

Or you may want to try the new MinecraftDev.jar beta launcher [http://www.minecraftforum.net/#article_815](http://www.minecraftforum.net/#article_815) that can either run the most recent snapshot of upcoming minecraft 1.6 (like 13w21a), or current release 1.5.2 .  It uses lwjgl 2.9.0 (at least for the snapshots) and can use the same ~/.minecraft directory, although, you may want to use a different world for snapshots than for current release because snapshots have additions (like horses) that are not in current release. The beta launcher is launched somewhat differently.  It would be launched like **java -Xmx1024M -Xms512M -jar MinecraftDev.jar** (assuming the .jar is in your current dir) or for a desktop launcher in 64-bit I use **sh -c 'java -Xmx2G -Xms1G -jar ~/MC-client/MinecraftDev.jar'**.

---

### Post by ZarathustraDK on 2013-05-29
Black screen = you're missing the lwjgl-files.

Google up "minecraft lwjgl" and it should lead to the solution...

...or use Minecraftier to sort out all that stuff for you ;) [http://ubuntuforums.org/showthread.php?t=2052084](http://ubuntuforums.org/showthread.php?t=2052084)

---

