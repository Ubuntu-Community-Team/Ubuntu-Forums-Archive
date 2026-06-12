---
title: "Minecraft keeps closing out on me :("
date: 2011-04-18
forum: Gaming &amp; Leisure
---

### Post by AveritasDeo on 2011-04-18
This nooblet needs help, so here goes guys,
Every time I open minecraft, it loads up, and then closes out pretty quickly. I tried using OpenJDK, Java 6, and wine. Wine wants me to download another Java that I am unsure how to do so. With the other two Java programs when I run it through a terminal, it says " Failed to open device (/dev/input/event9): Failed to open device /dev/input/event9 (13) " for events 9-1.
I've been trying to get this to work since tuesday night, and its now monday morning and I still don't have anything. Could someone please help me out?

---

### Post by AveritasDeo on 2011-04-18
Also, I can't get it to play on the website with either Java player. I just get a grey screen. 
Q_Q

---

### Post by Perfect Storm on 2011-04-18
Try use sun Java instead.

---

### Post by AveritasDeo on 2011-04-18
I have Sun Java 6, 
but it keeps closing when I try to create a world in the client. I tried it in browser, and I got as far as "simulating world" then it froze. Upon refresh it now goes to a gray screen after a second of the home menu. 
If i run minecraft in the client it says this
```
Loading: net.java.games.input.LinuxEnvironmentPlugin
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

Linux plugin claims to have found 0 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb773d416, pid=8261, tid=1788009328
#
# JRE version: 6.0_24-b07
# Java VM: Java HotSpot(TM) Server VM (19.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [+0x416]  __kernel_vsyscall+0x2
#
# An error report file with more information is saved as:
# /home/averitasdeo/hs_err_pid8261.log
[thread 2122861424 also had an error]

```

---

### Post by henz103 on 2011-04-19
Are you using ATI Catalyst driver?

If yes, it seems to be ATI Catalyst related issue:
[http://www.minecraftforum.net/viewtopic.php?f=17&t=29864](http://www.minecraftforum.net/viewtopic.php?f=17&t=29864)

---

