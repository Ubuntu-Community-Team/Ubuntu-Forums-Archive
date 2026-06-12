---
title: "Minecraft Crash Error"
date: 2012-09-14
forum: Gaming &amp; Leisure
---

### Post by LinuxCharms on 2012-09-14
So I play MC all the time on my laptop (what I'm using to type this now) and all of a sudden it has decided it wants to crash about 2 minutes are I join the game. Works all spiffy for the first few minutes, then it just flat out crashes. I've had it fail before and shoot be back to the main MC screen, but never just outright close.
I just so happen to run MC through my terminal, so I have it's output.
```
icanhazcowz@icanhazcowz-Satellite-L455D:~$ java -jar /home/icanhazcowz/Desktop/Games/Minecraft/minecraft.jar
27 achievements
195 recipes
Setting user: LinuxCharms, 4009537451528800787
LWJGL Version: 2.4.2

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.

Connecting to 168.144.92.106, 25565
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f4dbab7ac2d, pid=13449, tid=139971886733056
#
# JRE version: 6.0_24-b24
# Java VM: OpenJDK 64-Bit Server VM (20.0-b12 mixed mode linux-amd64 compressed oops)
# Derivative: IcedTea6 1.11.4
# Distribution: Ubuntu 12.04 LTS, package 6b24-1.11.4-1ubuntu0.12.04.1
# Problematic frame:
# C  [fglrx_dri.so+0x101dc2d]  ukiCreateContext+0x101dc2d
#
# An error report file with more information is saved as:
# /home/icanhazcowz/hs_err_pid13449.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted (core dumped)
icanhazcowz@icanhazcowz-Satellite-L455D:~$

```

Maybe one of you will have a brilliant idea as to what the heck is happening. Thanks!

---

