---
title: "Possible threat to My Minecraft? (UBUNTU 12.04 LINUX)"
date: 2013-05-12
forum: Gaming &amp; Leisure
---

### Post by soloman469 on 2013-05-12
Ok so a couple of minutes ago, i was peacefully playing Minecraft on this creative server, then all of a sudden, i get this error, which completely shuts Minecraft down:

Bus error

No big deal right?

Well, i started to play Minecraft again, and so i was back on the creative server doing my thing, then, i get this, with Minecraft completely crashing:

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fcd44e891c3, pid=11291, tid=140518576150272
#
# JRE version: 6.0_27-b27
# Java VM: OpenJDK 64-Bit Server VM (20.0-b12 mixed mode linux-amd64 compressed oops)
# Derivative: IcedTea6 1.12.5
# Distribution: Ubuntu 12.04 LTS, package 6b27-1.12.5-0ubuntu0.12.04.1
# Problematic frame:
# J  ard.a(DDD)Larc;
#
# An error report file with more information is saved as:
# /home/chikenpotpah/hs_err_pid11291.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#
Aborted

After that i did it again, then i got this:

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f77e04684b6, pid=11429, tid=140151840892672
#
# JRE version: 6.0_27-b27
# Java VM: OpenJDK 64-Bit Server VM (20.0-b12 mixed mode linux-amd64 compressed oops)
# Derivative: IcedTea6 1.12.5
# Distribution: Ubuntu 12.04 LTS, package 6b27-1.12.5-0ubuntu0.12.04.1
# Problematic frame:
# J  ard.a(DDD)Larc;
#
# An error report file with more information is saved as:
# /home/chikenpotpah/hs_err_pid11429.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#
Aborted


WTF is happening? Plz help!


[COLOR=#000000]My computer specs:[/COLOR]
[COLOR=#000000]-Ubuntu 12.04 (precise)[/COLOR]
[COLOR=#000000]-Intel(R) Pentium(R) D CPU 3.40GHz[/COLOR]
[COLOR=#000000]-Frequency:3389.176 MHz[/COLOR]
[COLOR=#000000]-L2 Cache:2048 KB[/COLOR]
[COLOR=#000000]-Memory Total:3000 MiB[/COLOR]

---

### Post by King Dude on 2013-05-12
Interesting. May I see the log file of the error?

---

### Post by King Dude on 2013-05-12
Actually, I think I know what's happening here.

If it's a bus error, it is because either the program (Minecraft) does not have permission to write in the memory, or the memory is bad. Check your RAM and see if it is a hardware problem.

---

### Post by soloman469 on 2013-05-13
Actually, i think i figured out how to fix it, cause i restarted my computer and everything was fine, including minecraft.

---

