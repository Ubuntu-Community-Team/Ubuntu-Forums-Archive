---
title: "MineCraft Issues"
date: 2011-08-04
forum: Gaming &amp; Leisure
---

### Post by rogersj9878 on 2011-08-04
Hey all.

Going to try and make this short and to the point for sake of your time; I'm quite new to Ubuntu, and fail very hard at it.

Right then, now that that is out of the way..

Has anyone had issues with installing MineCraft where it simply WILL NOT play? I mean, the second you attempt to enter your world, it just quits? Because I do.

It's 11.04, and as I said, I fail at Ubuntu, so I used the installer I found here. I assumed it worked perfectly. Used to install Java and the game, loads of fine, main menu, then gone. I ran the trouble shooting, reinstalled it several times (years of Windows), yet nothing.

```
rogersj9878@rogersj9878-System-Product-Name:~$ minecraft
16 achievements
151 recipes
Setting user: rogersj9878, 6944452171741392280
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb76ea424, pid=4552, tid=1779518320
#
# JRE version: 6.0_26-b03
# Java VM: Java HotSpot(TM) Server VM (20.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [+0x424]  __kernel_vsyscall+0x10
#
# An error report file with more information is saved as:
# /home/rogersj9878/hs_err_pid4552.log
[thread 1875852144 also had an error]
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
/usr/local/bin/minecraft: line 1:  4552 Aborted                 java -jar /home/rogersj9878/.minecraft/minecraft.jar
rogersj9878@rogersj9878-System-Product-Name:~$ 

```^ Since I assumed if you cared you'd ask anyway.

---

