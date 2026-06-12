---
title: "Minecraft crashing"
date: 2011-09-20
forum: Gaming &amp; Leisure
---

### Post by Uaxoh5ou on 2011-09-20
Hello,

I just tried to run MinecraftSP.jar in the terminal and it crashed during world creation.

Here is the error report:

Hello!
java.io.FileNotFoundException: /root/.minecraft/lastlogin (No such file or directory)
    at java.io.FileInputStream.open(Native Method)
    at java.io.FileInputStream.<init>(FileInputStream.java:137)
    at net.minecraft.LoginForm.readUsername(LoginForm.java:87)
    at net.minecraft.LoginForm.<init>(LoginForm.java:68)
    at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:25)
    at net.minecraft.LauncherFrame.main(LauncherFrame.java:99)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:26)
Path: /root/.minecraft/bin/
[http://s3.amazonaws.com/MinecraftDownload/lwjgl.jar](http://s3.amazonaws.com/MinecraftDownload/lwjgl.jar)
[http://s3.amazonaws.com/MinecraftDownload/jinput.jar](http://s3.amazonaws.com/MinecraftDownload/jinput.jar)
[http://s3.amazonaws.com/MinecraftDownload/lwjgl_util.jar](http://s3.amazonaws.com/MinecraftDownload/lwjgl_util.jar)
[http://s3.amazonaws.com/MinecraftDownload/minecraft.jar](http://s3.amazonaws.com/MinecraftDownload/minecraft.jar)
[http://s3.amazonaws.com/MinecraftDownload/linux_natives.jar.lzma](http://s3.amazonaws.com/MinecraftDownload/linux_natives.jar.lzma)
URL: file:/root/.minecraft/bin/lwjgl.jar
URL: file:/root/.minecraft/bin/jinput.jar
URL: file:/root/.minecraft/bin/lwjgl_util.jar
URL: file:/root/.minecraft/bin/minecraft.jar
URL: file:/root/.minecraft/bin/linux_natives.jar
17 achievements
161 recipes
Setting user: , 12345
Loading: net.java.games.input.LinuxEnvironmentPlugin
Linux plugin claims to have found 5 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see [http://www.lwjgl.org](http://www.lwjgl.org))
OpenAL initialized.

New max size: 400
New max size: 784
New max size: 1764
New max size: 5476
New max size: 18496
New max size: 19044
Placed stronghold in INVALID biome at (-24, 35)
Placed stronghold in INVALID biome at (60, 5)
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb7866424, pid=6638, tid=1461873520
#
# JRE version: 6.0_22-b22
# Java VM: OpenJDK Server VM (20.0-b11 mixed mode linux-x86 )
# Derivative: IcedTea6 1.10.2
# Distribution: Ubuntu 11.04, package 6b22-1.10.2-0ubuntu1~11.04.1
# Problematic frame:
# C  [+0x424]  __kernel_vsyscall+0x10
#
# An error report file with more information is saved as:
# /home/alex/.minecraft/hs_err_pid6638.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#

---

### Post by stejp96 on 2011-09-20
I have a similar issue, do you have a ATI GFX card? I found that to cause the crashing.

---

### Post by Uaxoh5ou on 2011-09-20
A label on my pc says I have ATI radeon. I don't know the differents between those 2. And is there a way to play minecraft with this grapic card, on a windows vista operaring system it worked fine.

---

### Post by Sofox on 2011-09-23
I have the same problem.

---

### Post by markg48 on 2011-09-26
[http://ubuntuforums.org/showthread.php?p=11284165#post11284165](http://ubuntuforums.org/showthread.php?p=11284165#post11284165) made a guide

---

### Post by SlugSlug on 2011-09-26
```
sudo apt-get install sun-java6-jre
```

and then 

```
sudo update-alternatives --config java
```

and select Sun Java as default

---

### Post by wyatt8740 on 2012-02-20
try setting these java arguements from terminal (I haven't used linux/UNIX for a while, so bear with my DOSstyle args):
```
java -Xmx800M -jar MinecraftSP.jar
```

I'm sorry if this doesn't work, but I know that for some reason this forces software rendering. It's slow and CPU based, but if your CPU is good enough, it avoids the GPU altogether and runs reasonably fast.

Also' there is a "Minecraft Coder Pack" that you could use if the above does not work. It decompiles the Minecraftclient (Not the launcher) and you can then edit it if you have the know-how, recompile, and install like a mod after you reobfuscate it. This does require python.

---

### Post by henrywalden on 2012-02-24
> **stejp96 said:**
> I have a similar issue, do you have a ATI GFX card? I found that to cause the crashing.
I also have the same problem.I checked ATI GFX card..I don't think that's the problem.Is there any other solution for that?I purchased a second hand ATI GFX card from a [deluxe hotels in ooty.]("http://www.naharhotels.com/")  From a computer shopping festival held in there...

---

### Post by regor210 on 2012-02-24
Could you run Minecraft in terminal and post the output?

Howto
If your using the newest Ubuntu 11.10 Oneiric Ocelot just click on the Ubuntu icon on the upper left side of your desk top and type term in the search window to bring up your terminal options. Any of them should work fine.

Ubuntu 10.04
Applications > Accessories > Terminal

After you have a terminal open just cut and past or type in the line you would like to run minus the $

# regular MC
$ cd ~/Downloads/ && java -jar minecraft.jar

# ALLOC's
$ cd ~/.minecraft/ && java -jar minecraft.jar

---

